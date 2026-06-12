---
title: "Dual Boot Vista/Ubutnu Problems"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by dmanno on 2009-06-04
Summary: Unable to install Grub. Lilo boots directly to Linux with no Vista boot option. 
 
Hi all. I am new to Linux and have spent the last three afternoons trying to install Ubuntu 9.04. I have Vista 64 Home Premium installed on a Seagate 1.5tb hd and have repartitioned space to create a Linux root partition, /home partition and /swap partition. 
 
I have installed the desktop Ubuntu 64 bit version about 5 times with a critical error every time when it gets to the part where it installs grub. I read that I could work around this using the alternate cd download and installing Lilo instead. This worked for me, however then I was unable to get back into Vista, probably due to all of my previous installation attempts and messing with installing Grub in multiple partitions to try to get something to work. When my computer started, it always went directly into Ubuntu with no boot selection screen.
 
Anyways, I was able to get Vista loading again after a few hours of Googling solutions and then installed EasyBCD. I was unable to get back into Linux after adding Lilo boot options in EasyBCD on all partitions. So I just re-installed Ubuntu again using the alternate cd and Lilo from the get-go in hopes that everything would magically work. Now I have my original problem which is that my computer boots straight into Ubuntu with no option to go to Vista.
 
I guess I need to know what to do next. Do I need to simply configure Lilo to add Vista as a boot option? Or am I missing something? As I said before, I'm a Linux n00b so please help with specific commands, if applicable! 
 
Other info:
I have one hard drive, with:
Windows on partition dev/hda1
ubuntu root on dev/hda4
ubuntu /home on dev/hda2 and
swap on dev/hda5. 
 
I think that's the proper notation, but I'm on the gf's computer now as I don't want to touch mine anymore due to frustration.
 
Thanks in advance for your help!

---

### Post by zman58 on 2009-06-04
Interesting problem you have described. Grub has always worked for my systems. I wonder why it is failing. Is there any error output generated you can provide?

As a test, you can try Ubuntu 386 desktop version. I find the 32 bit version seems to be more stable. I run the 64 bit on my AMD server, but stick with the 32 bit even in my AMD X2 desktop machines. So it would be interesting to find out if you have the same problem with the 32 bit version.

---

### Post by zman58 on 2009-06-04
I have not used Lilo in a long time, but I remember that once you changed Lilo configuration to add another boot vector (Windows) you have to run Lilo from command line to re-configure it in your system. Did you do this? This is not the case with Grub--it does not need to be run after you change the menu.list (boot entries).

---

### Post by dmanno on 2009-06-04
Thanks for your reply, zman. I'm at work now so I can't try again to get the precise error, but the error had something to do with Ubiquity crashing during configure_bootloader(). 

With regards to reconfiguring Lilo, during the alternate installation I was told that I had to do this and that the installer could do this for me now or I could do it after I restarted, so I just chose (both times I installed with alternate version) to just have the installer do it now. I'm not sure if that's what you're referring to. Again, I'm a Linux n00b! 

I have not configured Lilo as I'm not sure how to do it. I think my eyes have glazed over by all of the googling I did yesterday trying to make my system work correctly. I tried the Vista recovery disk to repair the Vista boot, but it said there were no errors. This is opposite of what I had earlier, where it wouldn't even show that there was an installation of Vista on my system, so I HOPE I'm in good shape thus far. Do you think if I add another boot vector in Lilo I will be able to get Vista as a boot option? After this, I would like to configure EasyBCD and use it as the bootloader so that I can chose Vista or point to the Lilo Linux installaion. But I need to know how to configure Lilo. Do you/anyone know a good link to tell me how to do this for the Linux n00b?

---

### Post by dmanno on 2009-06-04
Anyone? I really want to try out Ubuntu, but am discouraged thus far. Any additional help would be very much appreciated! Thanks!

---

### Post by andy price on 2009-06-10
Hi

I am looking at this dual boot problem too, though for Vector Linux. From what I have read, the easiest way to dual boot is to put Vista's bootloader into the MBR (i.e. a normal install) and then install and use EasyBCD to load either Vista or Linux. 

The important point thing for you to note is that you need to install GRUB or LILO onto your Linux partition and not into the MBR. By default Ubuntu installs to the MBR, but the last time I installed Ubuntu there was an Advanced button at one stage of the installation where you could choose where to put the bootloader. You need to install it on hda4.

So, if you can, get Vista working again and booting normally. The install Ubuntu one more time, taking care to install the bootloader to hda4. When it's finished you should boot back into Vista automatically. Install EasyBCD and configure it to load your two operating systems. I haven't tried it yet but a friend told me that's the way he does it.

Andy

---

### Post by dmanno on 2009-06-10
Andy, thank you for your response! I ended up posting a new thread with more specific information regarding my problem. No one responded, but I eventually was able to fix my problem. I posted the solution. I was attempting to do exactly what you described, but was having difficulty then getting Linux to install Lilo to sda4. I had the option when I was installing Grub, but since I was never able to install Grub, I ended up having to install Lilo and don't remember seeing an option. Anyway, I got it working using the Ubuntu Live CD and re-configuring Lilo. Here's my other post with solution:

[http://ubuntuforums.org/showthread.php?t=1178899](http://ubuntuforums.org/showthread.php?t=1178899)

---

### Post by andy price on 2009-06-10
Glad you got it fixed - with such perserverence you are bound to go far! Since no-one was able to offer a workable solution I guess we're the only people trying to dual boot with Vista :)

---

