---
title: "Gateway T-1623"
date: 2008-05-07
forum: Hardware
---

### Post by Geomancer626 on 2008-05-07
I recently purchased this laptop. However, I'm having three issues.

1.) I get no indication of my battery life. 

2.) My realtek wireless card doesn't appear in my hardware

3.) my ATI graphics card doesn't allow me to use the advanced desktop effects.

are there any ways to fix these three issues? I'm still very new to  Linux and would appreciate any help.

---

### Post by Geomancer626 on 2008-05-08
Hello again. I just realized that during the boot process with a live cd that a message briefly appears that mentions something about not being able to utilize some resources or something like that. I know that one of the resources is 6, but I can't quite catch the other ones.

---

### Post by crosswalker21 on 2008-07-18
I am a commiserate sufferer in the Gateway/Ubuntu world with a T-1623.

You can enable the **wireless card** by building and using a modified realtek driver ([found here]("http://www.datanorth.net/~cuervo/rtl8187b/")).  Instructions for installation are on the page.  If you run into problems post back here and we'll see what we can do.

**Video effects** require you to install a proprietary video card driver from ATI (not hard, but it can be finicky).  Before you begin please note that while running through this several times the system sometimes decided to display a white screen instead of my desktop and apps.  I believe it has something to do with a conflict between ATI's driver and the driver provided by the "Hardware Drivers" system menu option.  Unfortunately, I don't know exactly what caused it, nor how I fixed it.  That out of the way, go to [this page]("http://ati.amd.com/support/driver.html"), choose your OS (linux x86 for the standard ubuntu or linux x86_64 if you installed the amd64 version), then choose Integrated/Motherboard in the second column, followed by Radeon Xpress 1250 in the right column (note: most of the choices in the middle/right menus lead to the same file.  The Radeon Xpress 1250 is the one that worked for me).  Once you've downloaded the file (I'll assume to the desktop) you'll need to open the terminal and type: ```
cd ~/Desktop; chmod +x atidriver
```
where atidriver is the name of the file you just downloaded.  You can then double click the file to run ATI's installer.  Automatic mode works fine, unless you know that you need to adjust the install path.  After the install is complete, open up the terminal and type:```
sudo aticonfig --initial
``` hit enter, and you should be good to go.  The next time you reboot you should be able to enable desktop effects.

I haven't noticed the first problem you mentioned, so I'm afraid I can't help much there.

Here's hoping ATI, compiz, realtek and gateway take notice of us linux users.

---

### Post by onewithnature83 on 2008-07-20
Here is my solution:

for wireless.

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

--TJ (creator)

---

### Post by Geomancer626 on 2008-07-21
Wow, I had given up on this thread a while ago and forgot about it. Thanks to help from both of you my Gateway is working flawlessly now. Thanks!

---

