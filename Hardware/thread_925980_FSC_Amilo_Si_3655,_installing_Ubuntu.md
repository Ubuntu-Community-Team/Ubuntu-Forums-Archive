---
title: "FSC Amilo Si 3655, installing Ubuntu"
date: 2008-09-21
forum: Hardware
---

### Post by askeluv on 2008-09-21
Just thought I'd share my frustration of not being able to get a proper install of Ubuntu (neither 7.10 nor 8.04), and hope that someone, in near future, will be able to sort out the problems I encountered.

I bought a Fujitsu-Siemens Amilo Si 3655 about 5 days ago: 
[http://www.fujitsu-siemens.com/home/products/notebooks/amilo_si_3655.html](http://www.fujitsu-siemens.com/home/products/notebooks/amilo_si_3655.html) (visit link for specs), and was hoping, as a Linux-newbie, to get either Fedora 9 or Ubuntu 8.04 installed on it. I started off with Fedora, basically just because I had an installation CD available.

The installation went smooth, but rebooting after the installation, the only thing I got which was related to an operating system, was the message: "Operating system not found". I did the installation over again, but the same thing happened. I called up some friends with more Linux experience than me, and after fiddling with the rescue system, trying to understand why GRUB wasn't doing it's job, we concluded to try Ubuntu instead.

When the Ubuntu menu popped up, one of my curious friends decided to try the "Boot from first hard drive", just for the sake of it... Thus, we enter Fedora 9!

Strange as hell, we thought. Eventually my friend fixed the booting problem, although I'm not quite sure how he did it. I think he installed GRUB in /dev/sda instead of /dev/sda1 or something like that (like I said, I'm quite a Linux newbie). After a short time we decided that Fedora was acting too unstable, without any proper drivers for the computer's hardware, and (again) decided to try Ubuntu.

Running the Ubuntu CD gave the "ata: revalidation failed (errno=-5)"-error, which seems to be a well-known bug. None of the tips from the forums helped, though (like adding "all_generic_ide", "irqpoll", etc. as boot arguments, or changing from IDE to RAID in the BIOS (didn't have the option)). Using the Ubuntu 8.04.1 CD did not help, either.

Eventually I installed 7.10 successfully, although returning to the "Operating system not found" error. This time I just bypassed it by choosing "Boot from first hard drive" from the CD menu. The installation seemed ok, but like Fedora, I had no drivers available, and so the search for them began.

The first was the ethernet controller. After some research, I downloaded the "e1000e" driver for my Intel Gigabit Ethernet 82567 controller, and it worked like a charm. So far, so good.

Second, I needed the driver for the WLAN controller - an Intel WiFi Link 5100. This site: [http://intellinuxwireless.org/](http://intellinuxwireless.org/) provided me with info about drivers, etc. Long story short; I got a driver (iwlagn.ko) which gave me a "wlan0" entry in my iwconfig, but I was unable to use the WLAN for anything - i.e. I could not connect to networks, nor get control the power or radio of the unit.

Meanwhile I upgraded into 8.04, just to check if any of these drivers would be present in a later kernel. No luck, though.

The last thing I tried, was getting a decent graphics driver, so I could get a higher resolution. [http://intellinuxgraphics.org/](http://intellinuxgraphics.org/) gave me good info, but I was unable to install because I was missing a libdrm2.4 package. Trying to apt-get install it got me nowhere, since it would only tell me that I already had the latest package. Changing the sources.list file did not help.

The outcome now, is that I'm installing Vista, which apparently is the only OS I can use for the damn computer.

If anybody has ANY info or tips about installing Ubuntu or any other Linux distro on the Si 3655, I would be very grateful. If not, I'll just wait for 8.10 and pray.

---

### Post by JohnDefault on 2008-09-28
Uh and i just wanted to buy that notebook... 
This Amilo si 3655 is built on new centrino2 technology (chipset, graphics, everything). I was searching a bit and for most core components, the support has only been included into kernel since 2.6.26. But the releases you tested (fedora9,ubuntu 8.04) use only 2.6.24 or 2.6.25. I would suggest trying for example Debian testing (lenny) on that notebook, which should have newer kernel (2.6.26) with the support for your new hardware. This is just theoretical because i don't have the notebook to test it yet. You can try it parallel with your vista(whatever) main system, just dual-boot it. Testing new hardware is surely not easy task for beginner and there is currently no information about this anywhere. Hope that i will manage to buy it soon and will be able to post some positive results : ) Good luck. (and rule no.56:never buy week-old hw technology for open operating system, it just takes a while to develop new drivers)

---

### Post by Peter Cordes on 2008-10-06
> **JohnDefault said:**
> Uh and i just wanted to buy that notebook... 


 That laptop caught my eye, too, except maybe that the screen is too reflective and non-uniform brightness.  :(  And the keys aren't full-size, even though there looks like room on all sides of the keyboard.  why waste space?

 Having Intel ethernet and wireless is great (although some Intel integrated gigE chips don't support jumbo frames, unlike any add-in e1000.)  wifi drivers can be a problem, but you know with Intel that they won't be for long.

>  (and rule no.56:never buy week-old hw technology for open operating system, it just takes a while to develop new drivers)

 It's not always that drivers take time to develop.  They take time to get into a stable release that you already have a CD of sitting around, though!  Intrepid alpha6 (or 5 if 6 wasn't out yet) probably already had GM45 support in xorg-server-video-intel when the original poster bought this laptop.  check out phoronix.com...  Intel sometimes even has support for their HW available before its even released (i.e. support in the latest dev version of the driver, not a stable release).  Other mfgs, not so much.

---

### Post by nightfrost on 2008-11-04
I'm really interested in purchasing this laptop. Did you ever try it with Intrepid? If you did, I'd appreciate it a lot if you could find the time to give us a little report on it.

Thanks a lot in advance!

---

### Post by dschohennes on 2009-01-20
Any news on this? I'm thinking of buying a Si 3655 but i'd NEED a working Linux on it...

---

### Post by Tich666 on 2009-01-21
see my thread about running intrepid on this laptop here:
[http://ubuntuforums.org/showthread.php?t=1004456](http://ubuntuforums.org/showthread.php?t=1004456)

I have recently upgraded to jaunty alpha 3 and the performance of the intel gfx drivers is still a joke. The update also broke gnome-brightness-applet being able to change my screen brightness and the fn-keys still don't work.

my recommendation: unless you get a really good deal on this notebook (as I did, since my dad works with fujitsu) get a lenovo or dell which is more common and offers better linux support.

---

### Post by Jon_kanon on 2009-02-20
I bought the same computer 1 month ago, and have now installed Ubuntu 8.10 on it.

Now everything is working fine on it, but got the same error as above, that it couldn't find my OS when booting. I looked at grub installation and it seemed to me, that ubuntu install grub on a wrong partition (don't know why!!).

I ran this command in a shell and restarted the pc with succes:

sudo grub-install /dev/sda1

Hope this will help..  ;)

Cheers Jon

---

