---
title: "white screen of death with ati proprietary drivers"
date: 2008-07-01
forum: Hardware
---

### Post by DanK2802 on 2008-07-01
Ok, so I just got my laptop for college last week, and I'm setting it up to dual-boot Ubuntu Hardy with Vista Home Premium.

Well, after I got ubuntu installed, I had to update my linux kernel from 2.6.24-16 to 2.6.24-20 because of a bug with my ethernet card.  With the old kernel I had to have the ethernet card disabled in the BIOS to boot into Ubuntu at all; see this thread on launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/225749](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/225749).  My laptop is a Toshiba Satellite A300, which is just a customizable version of the A305 mentioned in that thread.

But then when I install the proprietary drivers for my video card (a Radeon Mobility HD 3650), I get the white screen of death when I try to log into ubuntu (I do get through entering my name and pw, but it doesn't load the desktop after that).

The new kernel works fine without the ati drivers; it lets me boot into ubuntu and use the ethernet card, and it doesn't have the sound bug mentioned in the launchpad topic.  And the ati drivers work fine with the original hardy kernel; I'm actually running Hardy with that kernel right now.

It's also really strange, because I had it working with both the new kernel and the ati drivers yesterday, but then I basically killed the whole system when I was trying to create a /home partition and something didn't get copied correctly.  Now that I reinstalled hardy, I'm getting the white screen.

So, yeah, any help figuring out how to run the updated linux kernel with my ati drivers would be great.  If it helps at all, here are some specs for my computer:
     Core 2 Duo T9300
     Radeon Mobility HD 3650
     3Gb RAM
     Realtek RTL8102E Ethernet card
     Intel 4965 Wireless card

And here are the packages I installed to update the kernel:
     linux-headers-2.6.24-20_2.6.24-20.35ubuntu5_all.deb
     linux-image-2.6.24-20-generic_2.6.24-20.35ubuntu5_i386.deb
     linux-backports-modules-2.6.24-20-generic_2.6.24-20.18ubuntu3_i386.deb
     linux-ubuntu-modules-2.6.24-20-generic_2.6.24-20.29ubuntu2_i386.deb

---

### Post by 796282 on 2008-07-01
Subscribing, Im having the same problem.

---

### Post by Fr0z3n.0n3 on 2008-07-01
I had the same issue yesterday. What fixed it for me was installing the ati drivers through Envy. After that the WSOD dissappeared, even when I removed Envy's drivers to install the latest version from ati.

---

### Post by stchman on 2008-07-01
> **DanK2802 said:**
> Ok, so I just got my laptop for college last week, and I'm setting it up to dual-boot Ubuntu Hardy with Vista Home Premium.

Well, after I got ubuntu installed, I had to update my linux kernel from 2.6.24-16 to 2.6.24-20 because of a bug with my ethernet card.  With the old kernel I had to have the ethernet card disabled in the BIOS to boot into Ubuntu at all; see this thread on launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/225749](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/225749).  My laptop is a Toshiba Satellite A300, which is just a customizable version of the A305 mentioned in that thread.

But then when I install the proprietary drivers for my video card (a Radeon Mobility HD 3650), I get the white screen of death when I try to log into ubuntu (I do get through entering my name and pw, but it doesn't load the desktop after that).

The new kernel works fine without the ati drivers; it lets me boot into ubuntu and use the ethernet card, and it doesn't have the sound bug mentioned in the launchpad topic.  And the ati drivers work fine with the original hardy kernel; I'm actually running Hardy with that kernel right now.

It's also really strange, because I had it working with both the new kernel and the ati drivers yesterday, but then I basically killed the whole system when I was trying to create a /home partition and something didn't get copied correctly.  Now that I reinstalled hardy, I'm getting the white screen.

So, yeah, any help figuring out how to run the updated linux kernel with my ati drivers would be great.  If it helps at all, here are some specs for my computer:
     Core 2 Duo T9300
     Radeon Mobility HD 3650
     3Gb RAM
     Realtek RTL8102E Ethernet card
     Intel 4965 Wireless card

And here are the packages I installed to update the kernel:
     linux-headers-2.6.24-20_2.6.24-20.35ubuntu5_all.deb
     linux-image-2.6.24-20-generic_2.6.24-20.35ubuntu5_i386.deb
     linux-backports-modules-2.6.24-20-generic_2.6.24-20.18ubuntu3_i386.deb
     linux-ubuntu-modules-2.6.24-20-generic_2.6.24-20.29ubuntu2_i386.deb

I just checked ATI's website and I cannot find a listing for a Mobility Radeon HD 3650.

There was a Radeon HD 36xx series.

Did you try the proprietary package?

```
sudo apt-get install xorg-driver-fglrx
```

I thought the repos the kernel was only up to 2.6.24-19?

---

### Post by DanK2802 on 2008-07-01
Ok, I got it working now.  I reinstalled Ubuntu today, and then I found an update to the linux kernel version 2.6.24-19 in the update manager, so I installed that rather than the other packages from before.  Then I installed the ATI drivers using the first method described on this page: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide), rather than using Envy like I had been.  As far as I can tell, that fixed all the problems I was having...

---

### Post by DanK2802 on 2008-07-01
> **stchman said:**
> I thought the repos the kernel was only up to 2.6.24-19?

Yeah, but I was getting packages from the repos linked to in this post: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/225749/comments/21](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/225749/comments/21).  I didn't realize that 2.6.24-19 was already available through the update manager until last night after I made my first post.  And that still gave me the same problem with the Envy drivers, it only worked when I used the ATI drivers from the Ubuntu repos after reinstalling this morning...

---

### Post by Raptor354 on 2008-07-08
What did it for me was an empty folder I created in the user directory.  I could not share it or anything.  The way I fixed it was log in to terminal and manually remove the extra directory.  When I reset, the video drivers were disabled, so after enabling them, everything worked great!

FYI, I'm using Ubuntu Desktop 8.04.

Hope it helped.

Raptor354

---

### Post by tstduke on 2008-09-07
I also have a Toshiba satellite a300 with the Ati 3650 graphics card and have got the white screen of death with the Ati Proprietary drivers.
I have updated after a clean install and then tried to install the Ati driver with Envy but still got the white screen.
How do I revert back to the default ubuntu driver via the command line?
I can press Ctrl Alt F2 to get the command prompt at least.
Any ideas as to which driver works and in which order I should install and update?

---

