---
title: "Problems with Intel video in Karmic"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by trx64 on 2009-10-31
I've an Intel 82945G/GZ, that works perfectly in Jaunty. In Karmic, the only resolutions avaiable are 800x600 and 640x480. My xorg.conf is empty (just the default sections, nothing especial). How can I enable 1024x768?

---

### Post by Turtle.net on 2009-10-31
Could you post your xorg.conf ?
You could also try
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` to regenerate the xorg.conf file

---

### Post by jwang on 2009-11-01
dpkg-reconfigure is not working on Karmic anymore, I'm very surprised this is not mentioned in the release note;

Xorg -configure does the work, however in your case, you may still not be able to get 1024x768, I suspect this is a Intel specific driver bug - I'm having the same issue as you!

I've raised a bug report and hopefully this can be fixed soon.

---

### Post by trx64 on 2009-11-10
The Xorg.conf is empty, just the default. Someone has an working Xorg.conf for Intel video?

---

### Post by trx64 on 2009-11-13
I've solved the problem by disabling KMS (Kernel Mode Setting) in Intel driver, leaving the detection of my screen resolution just with X. There is no need to change xorg.conf, just leave it at default values.

Edit the file /boot/grub/menu.lst (if you have GRUB 2, use [Startup Manager]("apt:startupmanager")). In the end of the "kernel" line of the OS entry, add "nomodesetting":

```

title           Ubuntu 9.10, kernel 2.6.31-14-generic
root            (hd0,4)                              
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=92583a31-1693-438c-ae3f-61ab9b8ca13a ro quiet splash locale=pt_BR **nomodesetting**                                       
initrd          /boot/initrd.img-2.6.31-14-generic                                   
quiet

```

---

### Post by ben44b on 2009-12-13
Adding the line *nomodesetting* did nothing for me.

I have the 82845G Brookdale intel chipset.


TY

---

### Post by Terry of Astoria on 2010-03-19
I have the 82845G Brookdale intel chipset, on my HP Pavillion 754v and no AGP or PCIx slot, and man it's been a headache trying all sorts of "fixes" for this problem of being stuck in 800x600 in 10.04. I spent an evening, and this was literally the last try I was going to allow myself. There are other things to do in my life. 
   IT WORKED! One thing though - I do have GRUB 2 and startupmanager did not offer any options for adding kernel boot options so I looked it up. 
  What I ended up doing is this:
```
sudo gedit /etc/default/grub
```
I added nomodesetting to the GRUB_CMDLINE_LINUX_DEFAULT line so that the line looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodesetting" 
```
And then DON'T FORGET TO RUN
```
sudo update-grub
```
Reboot and voila! It works! Higher resolutions!

---

