---
title: "[Help] squid+videocache+squidguard"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by tendabiru on 2009-08-26
Dear Ubuntu..
I'm trying ubuntu server 9.04 as proxy / squid server.
start from update anything, setup squid, videocache, everything is fine until test from client browser.
Next install squidguard, after installation prosess, and add one line in the squid.conf "redirect_program /usr/bin/squidGuard -c /etc/squid/squidGuard.conf". After that, when we restart squid.conf, but in the dispaly error for squid.conf.

[COLOR=#ff0000]#/etc/init.d/squid restart[/COLOR]
[COLOR=#ff0000]root@ubuntu2:~# /etc/init.d/squid restart[/COLOR]
[COLOR=#ff0000] * Restarting Squid HTTP proxy squid                                             *  Waiting...                                                                   * ...                                                                           * ...                                                                           * ...                                                                   [ OK ][/COLOR]
[COLOR=#ff0000]FATAL: Bungled squid.conf line  761: url_rewrite_program /usr/bin/python /usr/share/videocache/videocache.py[/COLOR]
[COLOR=#ff0000]Squid Cache (Version 2.7.STABLE3): Terminated abnormally.[/COLOR]

can we use both videocache and squidGuard  :confused::confused:

note: squid.conf, squidGuard.conf and videocache.conf in the attachment as file1.zip

---

