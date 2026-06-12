---
title: "Wireless Being disabled after installing 11.04"
date: 2011-05-15
forum: Hardware
---

### Post by airper on 2011-05-15
I'm having a rather serious problem with my wireless cards being disabled a little while after installing 11.04.

This has happen on two laptops different manufacturer, both within 24 hours of a fresh install of 11.04

The two machines in question an Acer Aspire 7551 and a Toshiba Satellite U305, both have been running Ubuntu for over a year 09.10, 10.04, 10.10 and now 11.04 This is a very recent problem.

On initial install everything is working okay (Ubuntu is the only operating system on both laptops and both are a fresh install)

On both and during use the wireless connection is dropped and the connection manager displays a grayed out 'Wireless Networks' with a disconnected message, both Networking and Wireless are enable and ticked.

There are no wireless services showing in the list. Attached is the output from 


sudo lshw -C network

and RFKILL LIST

from the Aspire 7551, but both machines are essentially showing the same info.

It would appear there has been a soft shutdown of the wireless cards on both machines, but how do you restart them?

Nothing in connection manager or network services helps, the cards seem to be totally disabled on boot-up and I can find no way to re-start them. Note a wired connection still works okay, it is just the wireless function that is effected.

Any help or pointers on how to get out of this and re-start these wireless cards, gratefully received.

---

### Post by airper on 2011-05-15
Even worse now. I have tried a fresh install of 11.04 on the Acer Aspire 7551 as above. 

The wireless card remains disabled even with a completely new installation. Something has really messed these machines up, almost down at the hardware level.

I hope someone can help here, it's looking rather serious.

---

### Post by airper on 2011-05-15
Okay I've made some progress but it's not fixed, so far I know this.

Firstly the issue is soft blocking in the driver see thread

[http://ubuntuforums.org/showthread.php?t=1661539](http://ubuntuforums.org/showthread.php?t=1661539)

However doing this did not fix the problem.

Then I found this, which I think means there are clashes between the drivers

----------------------------

Here is what you need to do. Use other Broadcom drivers. Download these  drivers (from Windows or through wired network or a friend’s computer or  from wherever you are reading this article  ).

For 32 bit: [http://ie.archive.ubuntu.com/ubuntu/...untu5_i386.deb]("http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb")

For 64 bit: [http://ie.archive.ubuntu.com/ubuntu/...ntu5_amd64.deb]("http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb")

(Don’t know which Ubuntu you are using? Click here: Check you Ubuntu architecture)

Now remove the previous drivers in Ubuntu 11.04 by using: sudo apt-get remove bcmwl-kernel-source

Now install the appropriate driver (you have downloaded from the above  links). Restart your computer. If restarting doesn’t work try shut down  and then start it (strange…but works). 

---------------------------------------

No this hasn't worked either. At this point I'm assuming 11.04 is not shipping with the right wireless drivers, or is creating clashes with ready installed or manufactures drivers.

At this point I still haven't managed to resolve this.

---

### Post by hakanali on 2011-05-15
i have the same exact problem. my os was ubuntu 10.10 but i had this problem too with toshiba satellite L650-11F and it is still unsolved

---

### Post by airper on 2011-05-15
I found this, tried it, but my connection is still not working.


Quote:
 	 	 		 			 				 					Originally Posted by **megsona** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10567049#post10567049") 				
 				[I][...] which pointed to acer-wmi module being loaded and causing the fault.

As soon as I did a 'sudo modprobe -r acer-wmi' my wireless sprang into life. At last!

I've since blacklisted the module and all seems well, the wifi LED is not lit but I can live with that.[/I]
 			 		 	 	 
Thank you!

I recently got a 7551g, and had the wireless working fine with the  proprietary drivers from Ubuntu. However, the wireless was always  disabled at boot. Blacklisting that module fixed it!

By the way, for those who don't feel like searching more (if you don't  already know how), blacklist a module like so, at the terminal (replace  "sudo vi" with "gksudo gedit" if you're not a masochist like me):

 	Code:
 	$ cd /etc/modprobe.d
$ sudo vi blacklist.conf 
Add the new line "blacklist acer-wmi" (without quotes) to the end of the file.

Let me also note that my wi-fi LED works fine. If I turn it off with  Fn+F3, the light goes out and wi-fi turns off, but network-manager still  thinks it's enabled and continually attempts to reconnect. Fn+F3 again  turns the light back on, and NM reconnects. No more than a minor  annoyance to me, just wanted to point it out in case anyone else looks  here for help.

----------------------------------------
I've got the wireless active led on now, but still cannot establish a connection. Just can't see where to look next???

---

### Post by coffeecat on 2011-05-15
@airper, thanks for posting the successful results of your investigation. There have been  other threads in the past where the acer_wmi module has interfered with wireless. This doesn't happen on all Acers. On my Acer Aspire 7540 I have the same Atheros 928X wireless chipset as yourself, yet I have been running Natty on it since the alpha1 stage and I don't get this problem - I'm lucky.

The difference is probably because of a different implementation of [DSDT]("http://en.wikipedia.org/wiki/DSDT#Firmware_interface") in different Acer models. Here's a thread with  a similar  wireless related acer_wmi issue:

[http://ubuntuforums.org/showthread.php?t=1333700](http://ubuntuforums.org/showthread.php?t=1333700)

That linked to this:

[http://www.mjmwired.net/kernel/Documentation/laptops/acer-wmi.txt](http://www.mjmwired.net/kernel/Documentation/laptops/acer-wmi.txt)

That link is three years old now, so I don't know whether that developer is still interested in the DSDT's from affected Acers.

---

### Post by airper on 2011-05-15
Thanks Coffeecat,

I've looked at these and installed the wicd network manager, now I can see a bit more what is happening.

The connection looks to be working now and the card is trying to connect to the router.

What appears to be happening is the laptop and the router can't validate the connection. Now I know the WPA password is valid, it is working on two other machines as I type this, but for whatever reason, the Acer Aspire 7551 and the route can't validate the connection and just times out.

So I guess I'm now looking to see why the WPA password is not being passed to the router properly, or have I missed something really basic???

---

### Post by airper on 2011-05-15
I'm getting this in wicd, but still it won't make a valid connection.

I don't understand the logic of the passkey working on two machines and not this one, is there a setting I'm missing somewhere

wicd output in screenshot attached.

---

### Post by coffeecat on 2011-05-15
Sorry - I don't really have anything constructive... Apart from one very long shot.

When I was using Lucid and Maverick with my Acer with the Atheros 928X wireless, I acquired an N-capable wireless router. My Acer would connect OK - and with WPA2-PSK - but some weird things would happen. Some websites I couldn't resolve properly and this forum I could view, but not post - which makes absolutely no sense. Even though the 928X is a b/g/n chipset, I set my wireless router to 802.11g only and the problem melted away.

I haven't checked to see if this is still so in Natty but, although your problem is quite different, if your router is an N one, try setting it to G only.

---

### Post by fritz269 on 2011-05-16
> **airper said:**
> I'm getting this in wicd, but still it won't make a valid connection.

I don't understand the logic of the passkey working on two machines and not this one, is there a setting I'm missing somewhere

wicd output in screenshot attached.

I have had issues with my connection I have a Toshiba Satallite C655. Have you tried deleting all the wireless connections that are listed and try connecting them that way. It always works for me.

---

### Post by dsawyer777 on 2011-07-11
I have the exact same problem.. My laptop is a Hp G60.. Help anyone???

---

### Post by airper on 2011-07-11
I think we have to wait for the next update to the Kernel, I understand having read something, that the next kernel update will include many more driver updates, particularly for Wifi and wireless.

Hope this is correct, it is a bit off when a machine works with an older version of Linux, then updates break it, which is exactly what has happened here. I think all these machines worked fine pre 10.10 but kernel updates since have disabled wireless and it appears fairly widespread.

This is not a very helpful situation, if you are trying to promote Linux in general and Ubuntu in particular.

---

### Post by dsawyer777 on 2011-07-11
So what should I do???

---

### Post by airper on 2011-07-12
I'm not sure there is a solution to this at the moment, so it is either wait for a kernel update which will hopefully fix these driver issues, or go install that other 'operating system'. 

Either that or it's wires strung out all over the place for a wired connection to the router, this is what I've got at present, or a new laptop with difference wireless card!!!

I don't think there is any Linux distro which has got around these kernel issues for the wifi drivers yet.

I have to say this does Linux no good at all, there are two basic things needed for most people even contemplating switching to Linux, one is a working Internet connection and for most that means wireless, the other is being able to read and write files from work and other people (never a problem so far). 

Without these things working out the box, anyone looking at installing or switching to any version of Linux will not hang around more that two minutes  - just longer enough to see it is not working and back to familiar ground.

I've been using Linux and Ubuntu for more than three years, in fact all our home machines are on Ubuntu, we don't even have dual boot machines, but sometimes you have to have the patience of a saint. Having to string wires around everywhere to get a Internet connection is to say the least a pain and really didn't go down too well with the Management :(.

I really do hope this get fixed fairly quickly, these wireless cards are very common, as are Acer machines so lots of people will be affected by this, even if they do not post or comment here or elsewhere.

---

### Post by coffeecat on 2011-07-12
> **airper said:**
> I don't think there is any Linux distro which has got around these kernel issues for the wifi drivers yet.

The WiFi driver is probably fine. It works just dandy in Natty in my Acer with the same Atheros chipset as yours. The problem is probably down to buggy dsdt and/or buggy acpi. It's well-known that manufacturers introduce non-standard workarounds in acpi to cope with bugs in the Windows implementation of acpi. Which makes life difficult for the Linux kernel developers when they try to stick to the standards.

---

### Post by airper on 2011-07-12
Understand the point you are making Coffeecat, indeed it is very valid. But is does not remove the frustration, particularly when the machine did work with Ubuntu pre 10.10 and the kernel updates look to have broken it.

I actually went out and bought this machine to run Linux on the basis Acer, Toshiba, HP, Dell are all so large, Linux must accommodate these ranges. 

Anyway got the thing home and within an hour MS was off and Ubuntu installed, 10.04 everything worked fine, really pleased with it. The subsequent updates and I suspect the Kernel updates in particular were the problem.

On that basis I only partially agree with the comment about standards etc, for these large manufacturers, Linux really does need to work right and certainly not remove or restrict compatibility in updates.

I am still a big fan and won't go back to MS, but to convert folk, this kind of thing really is a no no.

What might be helpful  is a really good, up to date machine compatibility list, one that Linux developers guarantee to maintain compatibility with. I know there are lists out there, but I'm not aware of one that has official or at least semi-official status, or a reasonable guarantee of long term support ???

---

