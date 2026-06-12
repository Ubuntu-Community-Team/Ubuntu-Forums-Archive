---
title: "cyradm\imapd segfault when running cyradm"
date: 2008-09-24
forum: General Help
---

### Post by BlackHatRob on 2008-09-24
I have a newly installed instance of cyrus and have configured it according to this documentation: [https://help.ubuntu.com/community/Cyrus](https://help.ubuntu.com/community/Cyrus)

I restart everything (cyrus, postfix, saslauthd) and attempt to log into cyrus to create a user but it drops immediately to the command prompt. Below are snippets of logs and commands:

root@core:~# cyradm --user cyrus localhost

root@core:~# tail -1 /var/log/messages
Sep 24 16:21:31 core kernel: [712328.100115] imapd[27407]: segfault at 00000046 eip b79e72cd esp bfbed550 error 4

root@core:~# tail /var/log/auth.log
Sep 24 16:17:06 core saslauthd[26738]: server_exit     : master exited: 26738
Sep 24 16:17:06 core saslauthd[27322]: detach_tty      : master pid is: 27322
Sep 24 16:17:06 core saslauthd[27322]: ipc_init        : listening on socket: /var/run/saslauthd/mux
Sep 24 16:17:33 core cyrus/imap[27365]: sql_select option missing
Sep 24 16:17:33 core cyrus/imap[27365]: auxpropfunc error no mechanism available
Sep 24 16:17:33 core cyrus/imap[27365]: _sasl_plugin_load failed on sasl_auxprop_plug_init for plugin: sql
Sep 24 16:21:31 core cyrus/imap[27407]: sql_select option missing
Sep 24 16:21:31 core cyrus/imap[27407]: auxpropfunc error no mechanism available
Sep 24 16:21:31 core cyrus/imap[27407]: _sasl_plugin_load failed on sasl_auxprop_plug_init for plugin: sql


I have double checked my /etc/default/saslauthd and I am using:

MECHANISMS="pam"

Any help would be greatly appreciated.

---

### Post by starfry on 2009-10-10
For the benefit of anyone else coming across this while looking for an answer to this...

It would appear that the cyrus folders need to be made owned by the cyrus users:

chown -R cyrus:mail /var/lib/cyrus /var/spool/cyrus

---

