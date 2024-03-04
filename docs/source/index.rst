Welcome to Project Azariel's documentation!
===================================

**Project Azariel** is an open source energy data project, available to researchers, hobbyists and the wider dev community. For commercial use, please contact us. 

The energy database is hosted on Supabase. It is easily compatible with popular languages like Python and Javascript. For more information on their documentation, visit: https://supabase.com/docs/reference/python/introduction

Here is an example code to connect to the database and perform your first query.

First you must install the Supabase client.

.. code-block:: console

    pip install supabase, pytz

Second, connect to the database with a client.

.. code-block:: python

    import os
    from supabase import create_client, Client


    url: str = 'https://ttkthlctchwhcuhihyxu.supabase.co'
    key: str = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InR0a3RobGN0Y2h3aGN1aGloeXh1Iiwicm9sZSI6ImFub24iLCJpYXQiOjE3MDYwMzI3MTUsImV4cCI6MjAyMTYwODcxNX0.kfwP0rRZJ8wd63zHcCdkF__QDtjIQxbBeQEpxq8kJX8'

    supabase: Client = create_client(url, key)

With this client, you can make your first API call to the Supabase database. Now let's fetch the day ahead for the coming hours.

.. code-block:: python

    # Supabase automatically paginates results from the API. If you want large
    # queries, you have to connect the database via a psql string. Contact us for more info.
    import datetime as dt
    import pytz

    start = dt.datetime.now(tz=pytz.utc)

    query = supabase.table('dayahead_prices').select('*')
    query.gte('mtu', start)
    res = query.execute()

    print(res.data)

You can use this format to create all sorts of queries.

aCheck out the :doc:`usage` section for further information, including
how to :ref:`installation` the project.

.. note::

   This project is under active development.

Contents
--------

.. toctree::

   usage
   api
