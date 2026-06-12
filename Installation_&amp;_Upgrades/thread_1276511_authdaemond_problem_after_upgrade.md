---
title: "authdaemond problem after upgrade"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by twan_van_der_poel on 2009-09-27
Guys,

i have upgraded from ubuntu 6.06 lts plain to 8.04 hardy.
After the upgrade it looks like IMAP isn't working properly, the logs 
tell me there's a problem with authdaemon;

----
Sep 27 13:44:41 amsterdam023 imapd: Connection, ip=[::ffff:82.170.207.215]
Sep 27 13:44:44 amsterdam023 authdaemond: received auth request, service=imap, authtype=login
Sep 27 13:44:44 amsterdam023 authdaemond: FAIL, all modules rejected
Sep 27 13:44:44 amsterdam023 imapd: LOGIN FAILED, user=xxxx, ip=[::ffff:82.170.207.215]
---

As response on "authdaemond: FAIL, all modules rejected", I restarted courier-authdaemon with stop- and start.

Unfortunatly, it did not work. Does anyone have suggestions ?

Best Regards,


Twan van der Poel

---

### Post by twan_van_der_poel on 2009-09-28
Any suggestions ?

---

### Post by twan_van_der_poel on 2009-09-28
For those who are interested;

The actual error was;
**[SIZE=3]  authdaemond: libauthmysql.so: cannot open shared object file: No such file or directory[/SIZE]**

A friend of mine helped me out with the solution;

it seemed that the link loader couldn't find the shared objects for the courier-authdaemon module, therefor he suggested to create a file " /etc/ld.so.conf.d/authconf.conf " which was going to contain the path to the courier-auth library ( /usr/lib/courier-authlib ).

Then the link loader needed to read the (new) link to the shared objects by running " ldconfig "

After a restart I was able to login again, finally : - )


Now if you'll excuse me, I got some mails to reply :P lol

---

