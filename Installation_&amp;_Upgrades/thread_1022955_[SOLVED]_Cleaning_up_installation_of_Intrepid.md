---
title: "[SOLVED] Cleaning up installation of Intrepid"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by GrahamM on 2008-12-27
I installed I-I a few weeks ago and am in the early learning stage!

I have been messing with trying to install a later Nvidia driver without success. Did same with HP printer.  

Everything still works, but I have noticed a slow down in boot up and see at least one error message relating to video driver loading. 

Is there a way to just clean up present installation without re-installing?

---

### Post by wpshooter on 2008-12-27
GrahamM:

Others may tell you different, but my experience has been that installing any thing other than the stock/default video drivers that are installed by the O/S is USUALLY a mistake !!!  Most every time I have tried video drivers from either the restricted driver offering or from the actual maker of the video card, I have had nothing but problems.  I am not necessarily a proponent of the "don't fix it if it ain't broken school of thought", but in this case I think changing from the O/S installed driver is most likely a mistake.

Good luck.

---

### Post by GrahamM on 2008-12-27
> **wpshooter said:**
> GrahamM:

Others may tell you different, but my experience has been that installing any thing other than the stock/default video drivers that are installed by the O/S is USUALLY a mistake !!!  Most every time I have tried video drivers from either the restricted driver offering or from the actual maker of the video card, I have had nothing but problems.  I am not necessarily a proponent of the "don't fix it if it ain't broken school of thought", but in this case I think changing from the O/S installed driver is most likely a mistake.

Good luck.

I have also come to that conclusion!

But, after a number of attempts to upgrade to the nVidia driver and in the case of the HP AIO printer, whatever I might have done while getting the scanner to work, I think I have added unnecessary stuff that is slowing down the boot time. 

I just want to clean it all up. If I have to do a re-install, I would like to do it in a way that keeps my Firefox and Evolution configurations at least as well as the desktop link that took some effort to convert from Windows links.

---

### Post by GrahamM on 2008-12-28
Right now, my current installation has two issues. Maybe if I could fix these, present installation would be OK.

1. During boot-up, I get every boot step displayed on screen - Never used to do that. How do i switch that off?

2. I get a message Run DKMS auto installationof service for kernel 2.6.27-9-generic-nbidia (71.86.04)   [COLOR="Red"]FAIL[/COLOR]. How do I fix this? It causes a long delay during boot.

One other thing - when looking at X,org log, it reports operating system as 2.6.27-7-generic.  I don't really understand what x.org is, but this seems like a discrepancy.

So question is - do I try and clean up this installation or re-install?

Can I install a different distribution - say 8.04 or Kubuntu 8.10 and then transfer my Evolution and Desktop settings between the two?

---

### Post by GrahamM on 2008-12-29
No answers?  

I have tried just about everything and I still get that FAIL message and my system now will only run with the generic vesa video drivers.

I have tried using ENVYNG and it appears to work, but I do not get back to the nvidia driver.

I have tried installing using the nvidia .run file and it seems to be working, but in the end fails to install.

I mean, this is crazy. Downloading and installing new driver in Windows is a cinch. 

How did I get into this mess? Just by trying to update the nVidia driver to the latest one shown on their site for my Riva TNT2 card. 

Seems to me that Ubuntu is more of a pastime than a a workable operating system. Maybe time to give up....  W2K works flawlessly anyway.

---

### Post by cariboo on 2008-12-29
You must be missing some dependencies, to install the nvidia restricted drivers, make sure you have build-essential installed. build-essential is available in the repositories, and on the LiveCD. You can use Sysnaptic Package Manager and of course the command line to install it.

Jim

---

### Post by GrahamM on 2008-12-29
> **cariboo907 said:**
> You must be missing some dependencies, to install the nvidia restricted drivers, make sure you have build-essential installed. build-essential is available in the repositories, and on the LiveCD. You can use Sysnaptic Package Manager and of course the command line to install it.

Jim

Jim - Thanks for input!

I checked and build essential is installed.

All I would like to do is get back to the driver that Ubuntu first installed or the one that Envyng should install.

I still get that Run DKMS Auto with service for Kernel 2.6.27-9-gneric-Nvidia (71.86.04) FAIL error during boot up. It hangs quite a while before displaying FAIL, then continues and I receive a message asking if I want to continue with minimal graphics or try and repair or something else. 

So, I am basically in minimal vesa graphics - 1028x780 an 0Hz!

Graham

---

### Post by skern03 on 2008-12-30
> **GrahamM said:**
> Jim - Thanks for input!

I checked and build essential is installed.

All I would like to do is get back to the driver that Ubuntu first installed or the one that Envyng should install.

I still get that Run DKMS Auto with service for Kernel 2.6.27-9-gneric-Nvidia (71.86.04) FAIL error during boot up. It hangs quite a while before displaying FAIL, then continues and I receive a message asking if I want to continue with minimal graphics or try and repair or something else. 

So, I am basically in minimal vesa graphics - 1028x780 an 0Hz!

Graham

Underneath the generic kernel listings, there should be a recovery entry. Try running that. It sometimes cleans up installation issues.

Did you disable the NVidia driver from the restricted window?

If you do decide to reinstall, and you haven't done so already, I set mine up as follows to keep my settings (in this order):
1. / -- Set the root to 5 - 20 GB, depending on your drive space, using ext3 journaling file system. 
2. Linux swap -- 1 - 2 GB
3. /home -- rest of drive, also ext3

Now when you reinstall, you can mark the root for a reformat. Set the /home partition to be used, but not reformatted. You won't get all the nifty programs you loaded back, but it will keep your files and settings. Reinstallation is ~30 minutes with this method.

---

### Post by lazman on 2008-12-30
Is there a way to move the home after you have installed to say... another hd?

~laz

---

### Post by VastOne on 2008-12-30
> **lazman said:**
> Is there a way to move the home after you have installed to say... another hd?

~laz

Yes....Search for "move home partition" here and you will find hundreds of hits...

---

### Post by GrahamM on 2008-12-30
> **skern03 said:**
> Underneath the generic kernel listings, there should be a recovery entry. Try running that. It sometimes cleans up installation issues.

Did you disable the NVidia driver from the restricted window?

If you do decide to reinstall, and you haven't done so already, I set mine up as follows to keep my settings (in this order):
1. / -- Set the root to 5 - 20 GB, depending on your drive space, using ext3 journaling file system. 
2. Linux swap -- 1 - 2 GB
3. /home -- rest of drive, also ext3

Now when you reinstall, you can mark the root for a reformat. Set the /home partition to be used, but not reformatted. You won't get all the nifty programs you loaded back, but it will keep your files and settings. Reinstallation is ~30 minutes with this method.

I did get the driver situation sorted out - see this link:
[http://ubuntuforums.org/showpost.php?p=6426108&postcount=1](http://ubuntuforums.org/showpost.php?p=6426108&postcount=1)

Will look at creating anotehr partition for /Home. I have multiple drives, so I should be able to do that before any re-installation, then copy it back. But, I think I am now good to go without need for re-install.

---

### Post by stderr on 2008-12-30
Glad to hear it.

With regards to the boot text on startup, I find it tends to do that anyway when something goes wrong; I would imagine so you get a chance to notice and fix it. If you haven't got any startup errors though, there's an outside chance your menu.lst settings are non-standard...

If you run in a terminal:

```
cat /boot/grub/menu.lst | grep `uname -r` | grep vmlinuz
```

you'll get two long lines of output. These are the boot menu entries for your current kernel - one normal boot, one recovery boot. At the end of the first line, does it have "quiet splash" like mine:

```
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1227aa30-9bf3-40d0-bc37-3ff22b4c1a7d ro quiet splash 
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1227aa30-9bf3-40d0-bc37-3ff22b4c1a7d ro  single
```

---

### Post by GrahamM on 2009-01-01
> **stderr said:**
> Glad to hear it.

With regards to the boot text on startup, I find it tends to do that anyway when something goes wrong; I would imagine so you get a chance to notice and fix it. If you haven't got any startup errors though, there's an outside chance your menu.lst settings are non-standard...

If you run in a terminal:

```
cat /boot/grub/menu.lst | grep `uname -r` | grep vmlinuz
```

you'll get two long lines of output. These are the boot menu entries for your current kernel - one normal boot, one recovery boot. At the end of the first line, does it have "quiet splash" like mine:

```
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1227aa30-9bf3-40d0-bc37-3ff22b4c1a7d ro quiet splash 
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1227aa30-9bf3-40d0-bc37-3ff22b4c1a7d ro  single
```

Thanks for the reply! I ran that and this was output:

graham@graham-desktop:~$ cat /boot/grub/menu.lst | grep `uname -r` | grep vmlinuz

kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ef646dc3-ecca-4afa-9236-8646cbf6a986 ro quiet splash all_generic_ide floppy=off irqpoll
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ef646dc3-ecca-4afa-9236-8646cbf6a986 ro  single

So it looks like I do have quiet splash there. Not sure it is a problem - maybe some text is supposed to scroll by?

---

### Post by GrahamM on 2009-01-02
Checked during start u and I do get pages of items going by with result at end - I think it say [OK} or something like that.

Should having Splash Quiet prevent that or is there something else I should be turning off?

---

### Post by skern03 on 2009-01-02
> **GrahamM said:**
> Checked during start u and I do get pages of items going by with result at end - I think it say [OK} or something like that.

Should having Splash Quiet prevent that or is there something else I should be turning off?

You might consider posting a new thread. This one is marked as solved, so people aren't likely to review it.

JMHO...:)

---

### Post by GrahamM on 2009-01-02
> **skern03 said:**
> You might consider posting a new thread. This one is marked as solved, so people aren't likely to review it.

JMHO...:)

You are right! I should do that!

---

### Post by stderr on 2009-01-03
That's probably a good idea :)

No, quiet splash on that line is normal. Without that I think it should display the boot steps as you describe. 

> Should having Splash Quiet prevent that or is there something else I should be turning off?
I believe it should prevent displaying the boot steps as you describe, but I know the boot text kicks in anyway at times... and I'm not sure what all the conditions are that cause it. (So it would appear that your menu.lst isn't the problem). I can only speculate that there's something in the boot sequence that's returned a failure code, in which case you *may* be able to find it in your system logs. 

I could easily be entirely wrong, however :) Maybe there's another setting somewhere too.

---

### Post by GrahamM on 2009-01-03
Just about to post new question. Thanks for interest!

---

