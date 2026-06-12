---
title: "What is the difference between Recovery Mode and Normal Boot?"
date: 2008-10-13
forum: General Help
---

### Post by HousieMousie2 on 2008-10-13
I need to find out what the exact differences are between Normal Boot and Recovery Boot.

My Hardy will not boot in Normal Mode, it will eventually drop back to a text log on, that is very unstable... as in the screen will come and go, making logging on a race to see if I can input my user name and password before it blips off and comes back again.

When I boot into Recovery Mode then select the resume boot (or whatever it is) it boots just fine... this is without using dpkg or fixing X or dropping to root.

Does anyone know where to find the documents that detail the differences between the two boot modes?

---

### Post by Washer on 2008-10-14
from looking at /boot/grub/menu.lst, it's passing different arguments. Maybe try googling for that.

i assume you already tried fixing X from recovery?

---

### Post by HousieMousie2 on 2008-10-14
> **Washer said:**
> from looking at /boot/grub/menu.lst, it's passing different arguments. Maybe try googling for that.

i assume you already tried fixing X from recovery?

Yes, both dpkg and fixing X, no obvious change in results... except that it removes the Options "Emulate3Buttons" "Yes" entry from xorg.conf, annoying.

Perhaps I am not understanding what you are suggesting I search for.
Nothing seems odd in my /boot/grub/menu.lst file.  Comparing it to previous menu.lst files (used on a machine without troubles) it looks almost identical except for the UUID's and /dev/hd*n values.

Your post did however get me to look at my other hard drives... they auto-mounted when using recovery mode to boot.  In normal mode not all of them auto-mount.  It seems doubtful that this would be the cause of the boot failure, but it is interesting.

EDITED: Those other drives are non-Linux drives, two installations of XP.

---

### Post by Washer on 2008-10-14
er.. i mean in my menu.lst the command for normal booting is


```
kernel		/boot/vmlinuz-2.6.25.11 root=UUID=blahblahblah ro quiet splash
```

but for recovery mode it's 


```
kernel		/boot/vmlinuz-2.6.25.11 root=UUID=blahblahblah ro single
```

so maybe search for what ro single & ro quiet splash mean... I dunno

---

### Post by geirha on 2008-10-14
When you boot, select normal mode and hit **e** to edit the entry, then select the kernel line and hit **e** again. Remove the two words at the end; *quiet* and *splash*. Then hit **b** to boot it. It should now boot in normal mode, but without the splash-screen (with the progress bar) and show lots of text instead. See if you can spot any error messages.

---

### Post by HousieMousie2 on 2008-10-14
> **Washer said:**
> er.. i mean in my menu.lst the command for normal booting is


```
kernel		/boot/vmlinuz-2.6.25.11 root=UUID=blahblahblah ro quiet splash
```

but for recovery mode it's 


```
kernel		/boot/vmlinuz-2.6.25.11 root=UUID=blahblahblah ro single
```

so maybe search for what ro single & ro quiet splash mean... I dunno

Single user mode.

Quiet splash is just what is sounds like, it shuts off the graphical splash screen so you can marvel at the text that goes flying by too fast to be read.

Would be nice if they got Upstart working so that it would create a boot log, instead of the less than informative dmesg or any of the others found in /var/log.

Thanks for taking the time and interest though, Washer.

---

### Post by HousieMousie2 on 2008-10-14
> **geirha said:**
> When you boot, select normal mode and hit **e** to edit the entry, then select the kernel line and hit **e** again. Remove the two words at the end; *quiet* and *splash*. Then hit **b** to boot it. It should now boot in normal mode, but without the splash-screen (with the progress bar) and show lots of text instead. See if you can spot any error messages.

lol I had just finished saying to Washer that the text goes by too fast to read.  One of the first things I do after setting up an OS is to get rid of the pretty junk that hides what the system is doing.

The only thing I have been able to pick out is a message about activating the swap failing.  But with 4GB of RAM it seems unlikely that this would be the problem... (please correct me if I am wrong,) but that message is present even in recovery mode.

It is my belief that the swap has not been in use since I installed Hardy and I have only recently been trying to get that sorted out, using:

```
swapoff -a
/sbin/mkswap /dev/hd*n
swapon -a
```

Not meeting with an success, I was planning to try to recreate the swap partition, but first things first, I would like to be able to boot into normal mode.

I had previously seen an error about mounting the NTFS drives, but I couldn't care less about that... HAL and I can sort that out manually.

What are the odds of a bad module causing the boot to abort?  Specifically, the one created by the "NVIDIA-Linux-x86-177.80-pkg1.run" driver.
I have not gotten any 'out of range' errors or anything else to indicate that it is the video driver, except that a part of the screen flickers with bands of colored lines when the boot aborts.

However, this behavior started shortly after it was installed... wiping out glxgears:

```
glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

```

and none of my GL and OpenGL screen savers work now.  (I have a weakness for nice screen savers.)

Thanks, geirha.

---

### Post by geirha on 2008-10-14
I too doubt too that a failed swap mount can cause that problem. Though, it doesn't hurt to fix it. After doing mkswap, you create a new swapfs on the swap partition. This changes the UUID, so you must update /etc/fstab with the new UUID (swapon -a reads /etc/fstab and activates all swap filesystems listed there)

Use blkid on the device-node to read the new UUID. You can also tell swapon which devicenode to use
```
sudo blkid /dev/hda5
sudo swapon /dev/hda5
```

How did you install the nvidia driver?

---

### Post by meganox on 2008-10-14
Try adding xforcevesa to the boot options as well.  If that works then yes, it's a problem with the nvidia drivers.

---

### Post by HousieMousie2 on 2008-10-14
> **geirha said:**
> I too doubt too that a failed swap mount can cause that problem. Though, it doesn't hurt to fix it. After doing mkswap, you create a new swapfs on the swap partition. This changes the UUID, so you must update /etc/fstab with the new UUID (swapon -a reads /etc/fstab and activates all swap filesystems listed there)

Use blkid on the device-node to read the new UUID. You can also tell swapon which devicenode to use
```
sudo blkid /dev/hda5
sudo swapon /dev/hda5
```

Tried that, deleted the old UUID and pasted in the new one, saved the file.  No change, it still can't find/use the swap.  My next course of action is to delete the existing swap and recreate it as per the instructions here:
[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")


> 
How did you install the nvidia driver?

In a run level without the xserver running:
```
sh NVIDIA-Linux-x86-177.80-pkg1.run
```
It did the rest from there, including building the module interface or whatever it was... just a few yes or no questions later it said it was done.  And for a few reboots I had the nVidia splash screen and my beloved screen savers.

Thank you.

---

### Post by HousieMousie2 on 2008-10-14
> **meganox said:**
> Try adding xforcevesa to the boot options as well.  If that works then yes, it's a problem with the nvidia drivers.

***BINGO! WE HAVE A WINNER!***

Yep, adding xforcevesa to the line allowed it to boot in normal mode, no problems.

Damn. lol  This is good news because I now know the cause, but bad news since I don't know how to fix it. lol

Thanks a million, meganox!

And thanks to all who contributed!

---

### Post by geirha on 2008-10-14
> **HousieMousie2 said:**
> Tried that, deleted the old UUID and pasted in the new one, saved the file.  No change, it still can't find/use the swap.  My next course of action is to delete the existing swap and recreate it as per the instructions here:
[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")


You also need to restart either HAL or udev (I think it is the latter), to recreate the symlinks in /dev/disks/by-uuid/ . Probably why it didn't work. 

> **HousieMousie2 said:**
> 
In a run level without the xserver running:
```
sh NVIDIA-Linux-x86-177.80-pkg1.run
```
It did the rest from there, including building the module interface or whatever it was... just a few yes or no questions later it said it was done.  And for a few reboots I had the nVidia splash screen and my beloved screen savers.

Thank you.

It's recommended that you use the nvidia driver that ships with ubuntu. You can enable it in System -> Administration -> Hardware Drivers. If that doesn't work, installing envyng is better than installing it manually.

If you use nvidia's own installer, you need to reinstall it everytime there's a kernel update.

---

### Post by HousieMousie2 on 2008-10-14
> **geirha said:**
> It's recommended that you use the nvidia driver that ships with ubuntu. You can enable it in System -> Administration -> Hardware Drivers. If that doesn't work, installing envyng is better than installing it manually.

If you use nvidia's own installer, you need to reinstall it everytime there's a kernel update.

Unfortunately none of the drivers that came with Hardy work with my nVidia GeForce 9600GT PCI Express XFX Alpha Dog Edition graphics card.

I have not noticed any kernel updates... not that I would know one if it sat in my lap and giggled at me.

I had read a little about envyng but had opted to use the nVidia installer after reading the results of a few others with the same card... I guess it is time to give it a try... how much more broken can it get?  lol

Besides, I have a /home partition, what do I need to fear? lol

> You also need to restart either HAL or udev (I think it is the latter), to recreate the symlinks in /dev/disks/by-uuid/ . Probably why it didn't work. 

Cool.  Thanks.  How do I go about restarting HAL or udev?

Thanks, geirha.

---

### Post by geirha on 2008-10-14
> **HousieMousie2 said:**
> Unfortunately none of the drivers that came with Hardy work with my nVidia GeForce 9600GT PCI Express XFX Alpha Dog Edition graphics card.

I have not noticed any kernel updates... not that I would know one if it sat in my lap and giggled at me.

I had read a little about envyng but had opted to use the nVidia installer after reading the results of a few others with the same card... I guess it is time to give it a try... how much more broken can it get?  lol

Besides, I have a /home partition, what do I need to fear? lol


A kernel update is an update of linux-image-2.6.* packages ...

I wish I could tell you it won't break, but I haven't used it myself and I have heard of problems with it. envyng is officially supported in Hardy though, however, envy is not.

> **HousieMousie2 said:**
> 
Cool.  Thanks.  How do I go about restarting HAL or udev?

Thanks, geirha.

```
sudo /etc/init.d/udev restart
sudo /etc/init.d/hal restart
```

---

### Post by HousieMousie2 on 2008-10-14
geirha,

I did not think that I had seen a kernel update recently as I am still puttering around with 2.6.24-19

lol I have already learned that nothing in the computing world comes with a guarantee, but thank you for the suggestions, I will try out envyng later... it is time for me to try to get some sleep.  Trying out new things when I have a bad case of foggy brain isn't a good idea.

Thank you for the new 'toys.' Good deal.  Nice to know how to restart HAL in particular as it seems to have issues so often.

Thanks again!

Cheers

---

