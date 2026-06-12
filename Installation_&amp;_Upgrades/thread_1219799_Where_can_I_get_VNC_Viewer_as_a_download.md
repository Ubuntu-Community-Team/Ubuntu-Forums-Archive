---
title: "Where can I get VNC Viewer as a download?"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by rannable on 2009-07-22
Hey everyone, im a newbie to Ubuntu and I have seen loads of threads here and on the rest of the web how to configure or download various VNC packages but I havent been able to get them to work because I am a moron!

But anyway my question is where can i find a VNC viewer as a .deb download? I had an ubuntu VNC package a few months back where i just downloaded it from somewhere but stupidly deleted it ! Basically the download enabled me to access other machines (mostly Windows) on my network that had VNC server running and the program was located in Applications\System Tools and was just called VNC viewer but i havent been able to find it anywhere! 
Thanks

PS my system is a Dell E5500 running x64 Ubuntu 9.04

Thanks guys!
Rob
:popcorn:

---

### Post by prshah on 2009-07-22
> **rannable said:**
> 
But anyway my question is where can i find a VNC viewer as a .deb download? 

Ubuntu comes with a number of vnc-compatiable viwers; check Applications-Internet-Remote Desktop Viewer. You can also have Applications-Internet-Terminal Server Client.

If you have none of these, the current default vnc compatible viwer in Ubuntu is Vinagre; press Alt+F2, type in ```
vinagre
``` and press enter.

If you can't find any of these, you can install a vncviewer with the command ```
sudo apt-get install vncviewer
``` Which will install xtightvncviewer (does a similar job).

---

### Post by rannable on 2009-07-27
Thanks for the quick reply, the advice you gave was really helpful. I ran sudo apt-get install vncviewer which installed tightvnc without any problems.

I did try that but for some reason when i press enter after entering the IP address the little window just vanishes. I suspect this is more to do with the network than anything.

The annoying thing is i downloaded this .deb client that installed vncviewer on my laptop ages ago and it worked perfectly, it looked exactly like Real VNC in every way and allowed me to connect to my Windows Servers running VNC enterprise without any issues and the GUI was exactly like the Windows version, i guess that will teach me a lesson to mess around with a laptop thats running beautifully!

---

### Post by rannable on 2009-07-27
Actually guys i found a link to the vnc viewer for ubuntu on the realvnc site, thanks again for your advice...

---

