---
title: "Newbie URGENT Screen Resolution Help..."
date: 2005-04-18
forum: Hardware &amp; Laptops
---

### Post by Loves2 on 2005-04-18
Somewhere in here is probably the answer to my burning question, but since I need step-by-step instructions I thought I would make a new thread. I have just installed kubuntu 5.04 (on a DELL Inspiron 1100 laptop). My screen resolution is at the smallest 640x480. Please give me step-by-step instructions to change this setting to 1024x768 24 bit 60Hz. Thank you.

---

### Post by heimo on 2005-04-18
Hi!

Have you tried changing it from menu System->Preferences->Screen Resolution?

If that doesn't work, all I can offer quicly is this HOWTO (also see my post on this thread):
[http://www.ubuntuforums.org/showthread.php?t=21984](http://www.ubuntuforums.org/showthread.php?t=21984)

---

### Post by Loves2 on 2005-04-19
There is no ->preferences->screen resolution, so I will definately need a quick HOWTO please and thanks.

[QUOTE=heimo]Hi!

Have you tried changing it from menu System->Preferences->Screen Resolution?

If that doesn't work, all I can offer quicly is this HOWTO (also see my post on this thread):
[http://www.ubuntuforums.org/showthread.php?t=21984](http://www.ubuntuforums.org/showthread.php?t=21984)[/QUOTE]

---

### Post by kiddo on 2005-04-19
For now, all I can say is open a terminal, 
* sudo nano /etc/X11/xorg.conf *
and take a look, you should recognize an area where there is "640x480", then you could add other resolutions as you wish

---

### Post by Loves2 on 2005-04-19
I did some extra installations and now I can see the "Display" option in the control panel, but it is stuck at the 640x480 with no other choice. I am unable to manipulate the xconf file since I don't have root priviledges and I have no idea how to enable that... I'm really, really, stuck. I think the problem may be that it is using a "generic" display instead of my Dell 1024x468 Laptop Display. Again, I am unable to change it... Thanks for your help. How to I attach a file here?

[QUOTE=Loves2]There is no ->preferences->screen resolution, so I will definately need a quick HOWTO please and thanks.[/QUOTE]

---

### Post by heimo on 2005-04-19
Don't panic! (Douglas Adams) 
You can use sudo to run programs with root privileges. Just prefix command with sudo, for example: *sudo gedit /etc/X11/xorg.conf *(it'll ask for a password, type your own password).
 
You could change the name from "Generic Monitor", that's fine, but probably doesn't solve the problem. Check the logfile /var/log/Xorg.0.log and see if your 1024x768 mode is disgarded (hsync out of range). In that case, you need to do what is described in that other thread.
 
I'll look up the numbers for you, if I can find specifications for your laptop.

EDIT:
Manuals for Inspiron 1100: (nothing interesting there)
[http://support.dell.com/support/edocs/systems/ins5100/en/index.htm#printed_documentation](http://support.dell.com/support/edocs/systems/ins5100/en/index.htm#printed_documentation)

Post/attach the log and we'll be smarter.

---

