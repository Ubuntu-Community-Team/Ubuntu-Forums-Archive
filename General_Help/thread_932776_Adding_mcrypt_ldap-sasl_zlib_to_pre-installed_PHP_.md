---
title: "Adding mcrypt ldap-sasl zlib to pre-installed PHP after the fact"
date: 2008-09-28
forum: General Help
---

### Post by vtknightmare on 2008-09-28
Hi All:

So my dilemma is this:

After installing php5 and apache via aptitude, my developer came to me and said that he needs mcrypt, openldap with berkeleydb and cyrus-saslv2 support, and openssl.

So, I went ahead and installed, BerkeleyDB, OpenSSL and Cyrus-SASL via aptitude, then grabbed the latest stable OpenLDAP and configured/installed the package with the proper options/flags

Now... I've come across my stump. I had aptitude install the PHP5 package.

Can I somehow "re-configure/re-compile" it to include the new packages I've added?

How does one go about doing that? Do you have any "better" ways of doing this?

TIA!
--VTK

---

