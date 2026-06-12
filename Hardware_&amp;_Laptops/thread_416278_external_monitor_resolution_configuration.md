---
title: "external monitor resolution configuration"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by dedmonds on 2007-04-21
[FONT="Microsoft Sans Serif"]I just purchased an external monitor that I would like to use with an IBM ThinkPad T22 running Ubuntu 6.10 (Edgy). I believe the laptop hardware is capable of a maximum resolution of 1600x1200 to an external monitor, which is the native resolution of the monitor (Samsung SyncMaster 204B). However, I have not been able to change the output resolution to anything other than the maximum resolution of the laptop LCD (1400x1050) or lower. I am looking for any help you can provide to fix this.[/FONT]

---

### Post by spin2cool on 2007-04-21
Have you tried editing your xorg.conf to add in higher resolutions?  google 'xorg.conf ubuntu' or search the forums for more detailed explanations

---

### Post by dedmonds on 2007-04-21
I tried adding the 1600x1200 resolution to /etc/X11/xorg.conf file with no obvious effect. I also tried a few other changes to the xorg.conf file based on what I found on this forum, but so far nothing has worked.

---

### Post by dedmonds on 2007-04-21
[FONT="Microsoft Sans Serif"]A bit more information... I was able to confirm that the hardware is capable of the 1600 x 1200 resolution by booting into Windows XP. I have tried changing a number of things in the xorg.conf file without success. This is a bit frustrating.[/FONT]

---

### Post by alanmoore on 2007-06-20
Hello everybody. I've got more or less the same problem. I'm a lecturer. I have a Toshiba Satellite M40x-115 laptop running with Ubuntu Feisty that I used to give classes with powerpoint. The native resolution of my laptop's screen is 1280x800. When I used windows, I could clone my desktop in a external projector by pressing Fn + F5. The output image was perfect. Since I migrated to Ubuntu one problem has arised. I can use the aforementioned combination of keys to clone the image, but the size shown is 4:3. As a result, the projected image is incomplete, there are missing areas, especially at the sides. 

What can I do to see a complete output image? Thanks.

---

### Post by ftp1234 on 2007-08-18
I think the default graphics driver in Ubuntu allowes only resolutions upto 1024X768

I use a Samsung Syncmaster 204B with my desktop.
I have a Nvidia NV34 GeForce FX5200 graphics card.
So I enabled the Nvidia graphics driver by clikcing on 
System->Preferences->Desktop Effects.
(It said, I had to enable Nvidia driver for enabling desktop effects)
I believe you could also do this using
System->Administration->Restricted Drivers Manager

So after a reboot, Nvidia driver was enabled.

Now I had to make changes to the /etc/X11/xorg.conf
So I did 
sudo nvdia-settings from a terminal, it opened up a window.
I changed the resolution.
I saved settings to xorg.conf file (there was a button for this).
And then I hit  CTRL-ALT-BACKSPACE
This restarted the X-server.
And I had my resolution.

NOTE: Remember to backup your xorg.conf before you make any changes. (Just in case, something messes up)

Depending on your graphics chipset, I believe you could install a different driver and change its settings

hth,
ftp1234

---

