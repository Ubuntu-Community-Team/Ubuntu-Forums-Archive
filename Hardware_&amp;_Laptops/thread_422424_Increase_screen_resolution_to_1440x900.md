---
title: "Increase screen resolution to 1440x900?"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by Aergonaut on 2007-04-25
Hi all.  New to Ubuntu, really excited about it and liking it a lot.  I'm making preparations to make the full move away from XP in the very near future.  I tried out the Live CD (that's where I'm writing this post from, as a matter of fact) and was pleased to see that all of my hardware was detected automatically and worked straight away.

I do have one question though.  The max screen resolution in the System > Preferences > Screen Resolution is 1280x800.  When I'm in XP, I get a max resolution of 1440x900.  Is there any way I could get Ubuntu to give me that higher resolution?  I like having as much screen real estate as I can.

I'm on a Dell Inspiron 9300 with a Nvidia GeForce Go 6800 graphics card, 2.0 GHz processor and 2GB RAM.

Thanks in advance!

---

### Post by renzokuken on 2007-04-25
install the official nvidia linux drivers.

this is easy with the Envy script. check [www.albertomilone.com](www.albertomilone.com) and look at the Projects and Guides section for instructions.

with the nvidia drivers you will be able to use higher resolutions (will require a spot of xorg.conf editing but that is easy and i can show you how.)

---

### Post by Aergonaut on 2007-04-25
Thanks for the reply!  Can you tell me what edits I'd need to make to the xorg config file?

---

### Post by strabes on 2007-04-25
Aergonaut: Run a terminal (Applications, Accessories, Terminal) and post the output of this command: ```
cat /etc/X11/xorg.conf
```

Someone else or I will tell you what to change once we see your file.

---

### Post by renzokuken on 2007-04-26
yeah, either post your xorg.conf and we can make/show the changes for you.

another alternative is to use ```
sudo dpkg-reconfigure xserver-xorg
``` leaving everything as default except when you get to the resolutions section, adding in the new resolutions you want. that command brings up a wizard the configures your xorg.conf according to what choices you make.

---

### Post by Aergonaut on 2007-04-26
Thanks for the help guys!

I made the move today and when I went to enable desktop effects, Ubuntu told me I needed a new Nvidia driver, which it installed automatically.  Once I restarted, my screen resolution was bumped up to 1440x900, without me doing anything.

---

### Post by dazlari on 2007-04-27
When I upgaded to feisty desktop and loaded the "proprietary" NVIDIA driver I could find no obvious way of changing the settings :confused: .The Screen Res app and logs showed only that I had a generic monitor and it was defaulting to it's max of 1024x968. I eventually discovered that NVIDIA do provide a GUI based application which you can run from a command line (or Alt-F2): **sudo nvidia-settings**

On the 2nd tab (XServer Display Configuration) I just set the Resolution to Auto.
Note, it also detected the monitor type correctly!

Voila! :) 

Hope this saves someone the effort of messing with the conf files. 
:guitar:

---

### Post by strabes on 2007-04-28
I'm so jealous of nVidia users.

---

### Post by EXCiD3 on 2007-05-03
NVIDIA just flat out rules. Automatix or the new Restritced Drivers Manager takes care of most driver installations for graphics and networking.

---

### Post by mbower on 2007-05-03
Restricted Drivers Manager has made it very easy.  I feel a little lost not having to dig into the xorg.conf file!!

---

