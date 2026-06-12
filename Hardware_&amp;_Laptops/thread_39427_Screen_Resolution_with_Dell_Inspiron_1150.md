---
title: "Screen Resolution with Dell Inspiron 1150"
date: 2005-06-04
forum: Hardware &amp; Laptops
---

### Post by kjmorris on 2005-06-04
My laptop is a Dell Inspiron 1150 with Celeron 2.8 Ghz and a 20 GB HDD. I upgraded from Warty to Hoary, hoping that the upgrade might solve my persistent screen resolution problem: even though I selected the recommended screen resolution of 1024 x 768 at installation, the screen defaults to 640 x 480. At the website announcing Hoary, under "X.org 6.8.2," it states that "X autodetection and laptop screen detection have had considerable updates based on community participation," so I was hopeful.

However, as with Warty, the various apps that I open (except Firefox) are still huge and can't fit on the screen, no matter how much resizing I try to do.  I opened the System Configuration window, went to Screen Resolution Preferences, and found the Default Settings to be stuck at  640 x 480, just like with Warty. The only change was that the Refresh Rate was stuck at 86 Hz for Warty but is now stuck at 73 Hz with Hoary. I tried to change both. There should be a drop-down menu where I can select my settings for both, but neither is there so I couldn't change anything.

I would appreciate any guidance.

kjmorris

---

### Post by poofyhairguy on 2005-06-05
Sure. put this in the terminal:

gksudo gedit /etc/X11/xorg.conf

Then paste the contents here.

---

### Post by kjmorris on 2005-06-05
Yesterday, before shutting down the laptop, I tried something that I had found on the Web, but it didn't seem to work. However, today when I rebooted, I have 1024 x 780 ! Problem solved, but now I have to re-trace my steps and find the text that I didn't save because I thought that it hadn't worked. Arrrrrrrgh!

Thanks.  kjmorris

---

### Post by kjmorris on 2005-06-06
OK. I reconstructed what I did that ended up with the desired 1024 x 768 screen resolution:

Ubuntu 4.10 - Warty Warthog - was "stuck" at 640 x 480 screen resolution and I was not able to change it to the 1024 x 768 recommended for my Dell Inspiron 1150 laptop. My apologies for disappearing abruptly for several weeks due to medical reasons.

When I returned my attention to Ubuntu in the last couple of days, I was able to find the solution. The Ubuntu website, in announcing the availability of Ubuntu 5.10 Hoary Hedgehog, noted that "laptop screen detection  had considerable updates based on community participation." So, I downloaded the Hoary iso and burned it to a CD. I then popped it into the CD drive of the laptop and ... nothing happened. So, I returned to the UbuntuGuide website and found "How to upgrade from Warty Warthog to Hoary Hedgehog (Beta)?" at the following URL:

[http://ubuntuguide.org/4.10/index.html#upgradewartytohoary](http://ubuntuguide.org/4.10/index.html#upgradewartytohoary)

I followed the instructions exactly, which allowed me to edit /etc/apt/sources.list according to a provided text, to install Hoary, and to select 1024 x 768 during the installation. I was disappointed after the installation when I saw that nothing seemed to have changed, so I shut down for the night. Upon rebooting today, however, the screen defaulted to 1024 x 768! This was my last obstacle to giving Ubuntu a
good try.

kjmorris

---

