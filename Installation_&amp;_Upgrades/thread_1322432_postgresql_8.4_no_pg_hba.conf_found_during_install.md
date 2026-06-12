---
title: "postgresql 8.4 no pg_hba.conf found during install"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by jfleming9232 on 2009-11-10
I am trying to install postgresql 8.4 (from synaptic and again from command line) but I get the following error message:

The PostgreSQL server failed to start. Please check the log output:
2009-11-10 22:05:49 CST LOG:  could not open configuration file "/etc/postgresql/8.4/main/pg_hba.conf": No such file or directory
2009-11-10 22:05:49 CST FATAL:  could not load pg_hba.conf

It appears that the pg_hba.conf and pg_ident.conf files are not in the /etc/postgresql/8.4/main/ folder.  Any idea where I can find these files?

I have tried uninstalling and reinstalling but with the same results.

---

