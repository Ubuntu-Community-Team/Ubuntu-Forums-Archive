---
title: "Undefined Symbol Perl_Tcurpad_ptr"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by sshaikh on 2009-09-03
Not sure if this is the right forum. I'm trying to install plperl into postgresql using CREATE LANGUAGE. The error I'm getting back is:

ERROR:  could not load library "/opt/PostgreSQL/8.4/lib/postgresql/plperl.so": /opt/PostgreSQL/8.4/lib/postgresql/plperl.so: undefined symbol: Perl_Tcurpad_ptr

Which I assume is a system wide error. Looking at Google, it seems that this is a symbol present in 5.10, but I installed libperl-dev from synaptic (which I believe is 5.10) and no go.

Any ideas?

---

### Post by Partyboi2 on 2009-09-03
Hi, try using the 3rd party repo mentioned [[COLOR=Blue]here[/COLOR]]("http://www.pubbs.net/pgsql/200909/71439/") to install it.

---

