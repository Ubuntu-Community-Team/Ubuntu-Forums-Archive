---
title: "Running this server headless."
date: 2005-11-11
forum: Hardware &amp; Laptops
---

### Post by kline on 2005-11-11
This test server that I've run Unbuntu on for six months is ready to be set aside;  I'm thinking of buying two new servers, and running this one headless.  What do I need to mod to get this to run happily when it suddenly can't find a keyboard?

thanks much

---

### Post by heimo on 2005-11-12
[LIST=1]
[*]install ssh or vnc or what ever you want to use to manage (I prefer ssh)*
[*]make sure the BIOS settings allow to boot without keyboard/monitor (normally this setting is called something like 'halt on error', correct setting is probably 'none'), boot
[*]connect using method in step 1, reboot from command line and make sure it came back up properly (you want to do this to make sure warm reboots work too)[/LIST]It's usually painless process, I run all my servers headless, some of them I've never seen.

*) Of course you want this to be secure.

---

### Post by kline on 2005-11-12
[QUOTE=heimo][LIST=1]
[*]install ssh or vnc or what ever you want to use to manage (I prefer ssh)*
[*]make sure the BIOS settings allow to boot without keyboard/monitor (normally this setting is called something like 'halt on error', correct setting is probably 'none'), boot
[*]connect using method in step 1, reboot from command line and make sure it came back up properly (you want to do this to make sure warm reboots work too)[/LIST]It's usually painless process, I run all my servers headless, some of them I've never seen.

*) Of course you want this to be secure.[/QUOTE]

The only server directly vulnerable is ns1.thought.org which is pretty secure.  But I
*still* use ssh.  Makes for good habits.  Anyway, I'm running this on an old Emachines that are primarily for the DOS clueless.  What's the magic button to hit on Emachines to get into the BIOS?  Any best guess!   (I'd like to be as sure as possible that this machine boots/reboots. )

Thanks for your ideas; I'm not sure if FreeBSD needs a tweak in some file because it's been years since I ran anything headless.  

One more thing if you have time; how hard is vnc to configure on Ubuntu?  Years ago thru a dial-up link, setting up FBSD was a serious challenge.  I'd like to moniter a couple Windows PC's and another Ubuntu server.  My how-to notes are missing.

gary

---

### Post by heimo on 2005-11-13
Usually the key to enter BIOS is delete key, F1, F2, F10... Many times there's a text on the screen for a short time with instructions how to get to bios.

Installing vnc client/server isn't too hard (I've tested it couple times, but have no use for it), but if you want to use it over insecure network, you must use (for example) ssh tunneling:
[http://pigtail.net/LRP/vnc/](http://pigtail.net/LRP/vnc/)

That may be too slow to be usable over anything else than LAN speeds, so you probaly want to use ssh over internet and vnc only locally (if neccessary).

---

### Post by kline on 2005-11-14
[QUOTE=heimo]Usually the key to enter BIOS is delete key, F1, F2, F10... Many times there's a text on the screen for a short time with instructions how to get to bios.

Installing vnc client/server isn't too hard (I've tested it couple times, but have no use for it), but if you want to use it over insecure network, you must use (for example) ssh tunneling:
[http://pigtail.net/LRP/vnc/](http://pigtail.net/LRP/vnc/)

That may be too slow to be usable over anything else than LAN speeds, so you probaly want to use ssh over internet and vnc only locally (if neccessary).[/QUOTE]

Thanks for the tutorial URL.  (Now I know why I ddn't make any notes; and I was just controlling my Debian machine from my main FBSD box. )  Behind my firewall I've got things going at a 100Mb hut so vnc should be plenty  fast.  Anyway, nice to know that I don't have to dump this old box.

---

