---
title: "Vinagre , can only see a black screen"
date: 2008-11-26
forum: General Help
---

### Post by anirvana on 2008-11-26
Dear All,

I am using two computers and want to use remote desktop with them.

I moved my desktop to a public IP and ssh'ed into it and started the vino server and tried to connect via my laptop to the desktop thru vinagre, but things don't work.

I ssh'ed into my desktop. Used $sudo /usr/lib/vino/vino-server &
no errors, everything is fine

Then I type on the laptop
$vinagre public-IP:5900 the client pops up and I see a black screen and nothing else.

on the desktop with a public IP I see

me@desky:~$ 26/11/2008 03:40:57 PM Autoprobing TCP port
26/11/2008 03:40:57 PM Autoprobing selected port 5900
26/11/2008 03:40:57 PM Advertising security type: 'TLS' (1
26/11/2008 03:40:57 PM Advertising authentication type: 'No Authentication' (1)
26/11/2008 03:40:57 PM Advertising security type: 'No Authentication' (1)
26/11/2008 03:41:46 PM Got connection from client ::ffffx.xx.xx.xx
26/11/2008 03:41:46 PM other clients:

Composite detected, disabling XDamage extension.
This is a workaround while XDamage extension does not work correctly with 3d desktops.
Hopefully it will work at next vino release.

All I get is a black screen. Things were good when both machines were in a LAN, but now it seems something has gone wrong. Any comments?

More info can be found at 

[http://ubuntuforums.org/showthread.php?t=993402&highlight=vinagre](http://ubuntuforums.org/showthread.php?t=993402&highlight=vinagre)

Thanks,
-A

---

### Post by anirvana on 2008-11-28
Some extra info, when I log into my desktop from my laptop to star vino-server I user -XY as ssh options. Also I can see a 

Resolving failed: Timeout reached

when I run
$vinagre <public-ip-for-desktop>:5900

Any help would be greatly appreciated.
-A

---

### Post by jdanm on 2009-04-02
I have the same problem - was this ever resolved?

---

### Post by Sjeti on 2009-04-02
I don't have any experience with Vinagre, but I have used freenx server very, very successfully.  If you can't fix it it might be worth giving freenx a shot.

---

### Post by kurtrr on 2010-02-28
Try this:

System->Preferences->Appearance->"visual Effects" set to "None" on the serving machine.

This worked for me when only my background was showing on the client.

I'm running vino, Ubuntu 9.10 on the server and vinagre,Ubuntu 8.10 on the client.

---

