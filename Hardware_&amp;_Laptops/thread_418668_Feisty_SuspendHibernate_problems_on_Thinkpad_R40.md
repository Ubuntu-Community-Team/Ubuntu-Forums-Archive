---
title: "Feisty Suspend/Hibernate problems on Thinkpad R40"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by Sunflower1970 on 2007-04-22
IBM Thinkpad R40 + Feisty.

Maybe I'm doing something wrong, but this morning when I went to put my laptop into suspend (Fn+suspend --or a crescent moon on a button) it will go into it like it's supposed to, but coming out of suspend doesn't do anything. The computer starts fine, as it should but the screen never comes on at all. So, I decided to try hibernate. Never used it before...it sort of works. Once it comes out of hibernation, the sound on the laptop no longer works. 

In Edgy suspend worked like a dream (never tried hibernate on it. Didn't really need to :) ). Not sure why it won't work in Feisty. 

Is there something in the configuration files I can add/delete to make this work like before? I could live with Hibernate, but I don't like that the sound goes away when it 'wakes up' Is there something I can add/delete in those files to get this to work?

If not, I'll just reinstall Edgy...but I reeallyy like Feisty. A lot... 

Oh, yeah. One other odd problem. When I start up Feisty, after logging in, the splash screen comes on, but then it takes forever for the splash to disappear and the wallpaper to show up. It also was acting really goofy with Compiz when I enabled it so I turned it off (which is fine, I reinstalled Beryl, and that, for whatever reason, seems much more stable). 

These oddities only seem to happen on the laptop. The other two computers seem to be fine....Would all these problems, possibly, be with the graphics card (ATI Mobility Radeon 7500)?

---

### Post by Sunflower1970 on 2007-04-22
Bit of an update...I was able to finally see my screen. I went into suspend but this time kept the screen up instead of closing it. This seemed to keep the screen from blacking out. I'm getting an error message:

EXT3-fs error (device sda1) : ext3_find_entry: reading directory #1909446 offset [number] (the number changes 1-10)

Also it says something about: 

scsi 0:0:0:0 rejecting I/O to dead device

I'm thinking this has something to do with it saying sda1 instead of hda1...?

ETA:

If I were to wipe out my hard drive and do a clean install of Feisty, would this take care of the problem?

Or, in my /boot/grub/menu.lst, I have as my kernel: /boot/vmlinuz-2.6.20-15-generic root=UUID=7328b495-b1f7-414c-8969-aae7d709dd3a ro quiet splash

If I were to remove the UUID and instead have something like  /boot/vmlinuz-2.6.20-15-generic root=/dev/sda1 ro quiet splash, would this work?

---

### Post by dj__farde on 2007-04-22
> **Sunflower1970 said:**
> IBM Thinkpad R40 + Feisty.
when I went to put my laptop into suspend (Fn+suspend --or a crescent moon on a button) it will go into it like it's supposed to, but coming out of suspend doesn't do anything. The computer starts fine, as it should but the screen never comes on at all. So, I decided to try hibernate. Never used it before...it sort of works. Once it comes out of hibernation, the sound on the laptop no longer works. 


Hi, I have a Thinkpad T42 and i have the[COLOR="Red"] same problem[/COLOR] (for suspend and hibernate).
I don't know how to fix this!

---

### Post by Sunflower1970 on 2007-04-22
After trying to figure out how to use suspend2 from some posts, I botched Feisty on the laptop. Decided to reinstall Edgy, for now because of the suspend function. But, I'll keep watch to see if/when this problem does become resolved in Feisty.

So, even though it's not a perfect solution, reinstalling Edgy will work for now :)

---

### Post by deerstar on 2007-04-23
Have you tried uswsusp?

[http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

---

### Post by TeTeT on 2007-04-29
There are quite a few people with the same problem, take a look at this bug in Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109762](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109762)

---

### Post by tommie74 on 2007-06-17
I´ve had the same problem, no sound after waking from hibernate, and found a solution in launchpad. 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893)

The problem seems to be related to a change in the kernel. An updated kernel is available for download:

[http://rookery.ubuntu.com/~kyle/kernels/salgado/2007-04-25/linux-image-2.6.20-15-generic_2.6.20-15.28_i386.deb](http://rookery.ubuntu.com/~kyle/kernels/salgado/2007-04-25/linux-image-2.6.20-15-generic_2.6.20-15.28_i386.deb)

install using package manager or 

```
dpkg -i /home/***your user name***/Desktop/linux-image-2.6.20-15-generic_2.6.20-15.28_i386.deb
```

hope this works for you too, as it did for many others,
Thomas.

---

### Post by Sunflower1970 on 2007-07-11
I was just thinking about upgrading to Feisty again on my Thinkpad...and searched for this old thread. Glad I found it (well three weeks late from the last post lol :) ) But I think I'm going to upgrade tonight and try this and see if it works for me..

---

### Post by jsully1 on 2007-07-11
I'm rocking Feisty on my Thinkpad T60, and suspend works well even with Compiz Fusion.  I don't use hibernate since it's quicker to actually shut the machine down and boot it.  I also recall that it worked out of the box for both Dapper and Edgy, though getting it to play nice with Beryl required tweaking /etc/defaults/acpi-support.

---

### Post by louieb on 2007-07-11
Don't know if this is related. But found the UUID of my swap partition had changed and swap wasn't being used. To get hibernate to work again had to put correct UUID in 2 places.
/etc/fstab
/etc/initramfs-tools/conf.d

Then had to run ```
sudo dpkg-reconfigure  initramfs-tools
``` Tired to find the thread where I got this info but could not locate it.

---

### Post by Sunflower1970 on 2007-07-12
I'm going to get this blasted thing to work if it kills me (grrrr)

Update:

I was able to get hibernate to work (yay!) and the fix for the sound in the Launchpad link. (another yay!)...but still having trouble with suspend. Haven't tried the uswsusp--am going to try at lunchtime....I'm now using  newest kernel now 2.6.20-16. Are there any fixes for it like the 2.6.20-15 one? 

I did look at my UUID swap, and that was fine...so that fix won't work for me :(

**Update II**
The uswsusp worked. I haven't done the hack yet, just tried it out with the s2disk command, but it looks like this will be a workaround for the time being. It's not very pretty and takes longer to resume than it did in Edgy (and it's not as 'pretty') but I can live with it until it will be fixed.

---

### Post by Sunflower1970 on 2007-07-19
> **Sunflower1970 said:**
> **Update II**
The uswsusp worked. I haven't done the hack yet, just tried it out with the s2disk command, but it looks like this will be a workaround for the time being. It's not very pretty and takes longer to resume than it did in Edgy (and it's not as 'pretty') but I can live with it until it will be fixed.

So... Last night I finally had some time to sit down and set up the hack to get everything working great...but I ran into a problem. Wireless. After doing what was suggested in this link [http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/) in a post down in the comments section, I lost all wireless connection. I had not even tried to see if suspend would work. I just made the change and at that moment, I lost all connection. WiFi Radar didn't work Network Manager didn't work, tried uninstalling Network Manager and using just WiFi Radar...nothing. Tried to reboot to see if that would clear out the problem...and nothing.  I know my connection was good because my wireless desktop works fine. I began to think my PCIMA wireless card had gone bad. Decided to go ahead and just reinstall since I didn't have anything on the computer anyway. That worked, and now my wireless is back...I'm kind of scared to reinstall uswsusp though and lose the wireless connection again... :shock:

---

