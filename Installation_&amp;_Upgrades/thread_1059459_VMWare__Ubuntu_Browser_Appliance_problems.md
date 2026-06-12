---
title: "VMWare  Ubuntu Browser Appliance problems"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by lintode on 2009-02-03
Hi,

I will apologize in advance in case you find my frustrations to be ... frustrating. This is my first experience with Ubuntu and it is unhappy. I tried to do something simple, or so I thought.

I brought down the VMWare Browser Appliance for the reason of wanting an isolated surfing environment.

I installed the VMWare player and the appliance, and it came up working. My first step was to do what everyone who downloads this thing wants to do, I went a site that needs the flash player. But the flash player was not installed. 

I went to Adobe's site and downloaded the .deb file. I selected the installer to run it after download, but the installer did not start. 

So I opened a GUI to the desktop and launched the deb file. And failed. Why did the Archive Manager open, since obviously it can't handle it?

Next I tried to install from a console window using dpkg. Now it says I don't have permission. So, I use sudo su and try again. This time it tries to install but I get a string of error messages saying my version of ubuntu is too old. There was also some message about installing a previously deselected package. Huh?

So now I try to upgrade Ubuntu using apt-get update (still in super user account). Again, nothing but a string of errors and a fail to install. 

Fault Microsoft as much as you want, I don't have these problems, not with installs and not with updates. 

I would like some help. If you want to tell me that this is easy, please do not reply. I believe in open source, but this is just the latest in a string of years of disappointments. If someone understands why I am havng a problem and can offer some real advice, I will be very very grateful.

Thanks!

---

