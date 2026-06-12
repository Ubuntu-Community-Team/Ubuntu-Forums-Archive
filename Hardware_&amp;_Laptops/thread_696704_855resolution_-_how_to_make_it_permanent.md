---
title: "855resolution - how to make it permanent"
date: 2008-02-14
forum: Hardware &amp; Laptops
---

### Post by ifinlay on 2008-02-14
Just getting to grips with Gutsy in my Sony Vaio VGN-T2XP. (Experienced IT type but new to Linux).  The T2 has a wide screen and I'm happy that I've managed to install the 855resolution app.  When I:

[LIST]
[*]sudo 855resolution 5c 1280 768
[*]Press ctrl-alt-backspace twice
[*]Log in again
[/LIST]

Then all is wide screen loveliness.  Bliss.  But how to make it do this automatically every time I boot up?  Through advice on the net I have:

[LIST]
[*]put the "855resolution 5c 1280 768" command line into a file called S09startupscript and parked this in /etc/rc2.d.
[*]Changed the permissions on this file thus "chmod a+x S09startupscript"
[*]Made sure that the file is named something that starts with a number lower than my GDM module S30gdm - which it is"
[/LIST] 

And the net effect? None.  Screen boots up in narrow resolution and I have wide-screen it manually.  Any suggestions? (In newbie-speak).  Much thanks.

---

