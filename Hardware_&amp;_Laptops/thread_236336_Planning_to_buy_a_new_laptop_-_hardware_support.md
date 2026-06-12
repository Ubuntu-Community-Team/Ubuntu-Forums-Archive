---
title: "Planning to buy a new laptop - hardware support?"
date: 2006-08-14
forum: Hardware &amp; Laptops
---

### Post by el3ktro on 2006-08-14
Hello,
I', planning to buy a new laptop, but I want the best hardware compatibility for Ubuntu, so I want to ask you for advice. Right now I'm looking into this one here:

[http://averatec.de/produkte/s2400_tech.htm](http://averatec.de/produkte/s2400_tech.htm)

It is an Intel Core Duo, and it has an Intel 950 graphics adaptor. How well is Intel Core Duo and this chipset supported in Ubuntu? Will S-ATA, the internal LAN and especially WLAN work (with WPA)? Can I run XGL with this integrated graphics card or is it unsupported/too slow? What about power saving, suspend-to-ram etc., will those work?

Please tell me your experiences with this notebook or this chipset/graphics card/CPU!


Sincerely,
Tom

---

### Post by daou on 2006-08-14
I just started looking for a new laptop as well. Right now I'm looking at Asus A6F which has some similar specs (Intel Core Duo 2300E, onboard Intel gfx, etc.). Keep me informed if you find anything useful about the Intel CPU, chipset, and graphics. 
You might want to check out [this link]("http://support.intel.com/support/graphics/linux/") on what Intel has to say about it's Linux graphics compatibility.

---

### Post by daou on 2006-08-14
You might also want to check whether the store has a full refund policy. That way you can get it, install Ubuntu on it, and return it if it doesn't work well. Make sure you tell them you want it to run Ubuntu flawlessly and won't accept it otherwise. 

And if you don't need the WinXP that comes with it, try to negotiate a way to get a discount for excluding it. Probably won't work, but if people don't start doing it, retailers will never consider selling a laptop package without MS products.

---

### Post by huygens on 2006-08-15
To answer some of your questions:
  - Intel Core Duo and Intel GMA 950 are supported by Ubuntu
  - It is not stated on Averatec web site which type of WLAN and LAN chipset is used. So it is not possible to state something.
  - Xgl should work on this graphic chipset, perhaps not all graphical eye candies. It is not because I have tested it, but I saw some 3D eye candy effects on a MacBook running MacOS X. And it has a similar hardware configuration.
  - for power saving and suspend to RAM, it is hard to guess without testing it on the hardware itself.

So a suggestion for the un-answered questions of yours:[LIST=1]
[*]download Ubuntu Live CD or DVD
[*]download [Kororaa]("http://kororaa.org/"), a Xgl Live CD[/LIST]Then go to a shop [where they sell this laptop]("http://averatec.de/corporate/haendler.htm") (it seems that Karstadt sells it, but many other shop also) and put the Ubuntu CD in, boot the laptop, check that power management is correct, that the WiFi could work, etc. Then, shutdown. Put the Kororaa CD, boot and check if Xgl is working :)

Huygens

---

### Post by el3ktro on 2006-08-15
Hello,
thanks so far to everyone. @huygens: You're right, without knowing the WLAN chipset it's hard to tell. But it's a Centrino laptop, and I thought Centrino means this whole mobile thing with CPUs, chipset, WLAN etc.? So shouldn't it be an Intel WLAN chipset?

About Xgl: I don't care too much about all the effects (Compiz), I want to use Xgl simply because it is so much faster than X.Org. On my desktop machine (Athlon64, latest Nvidia grapics), I can see how windows are being redrawn when I move them, but when I run it with Xgl, it's blazingly fast - so that's why I want Xgl on my laptop :-)

Indeed the best thing would be to just boot an Ubuntu LiveCD, although you can't test everything. (Afaik suspend-to-ram doesn't really work on a LiveCD), but it's something!

Tom

---

### Post by huygens on 2006-08-15
I did not find that it was a Centrino platform (not written on the page you sent, neither on the others)... Having a Core Duo processor, does not always mean that it is a centrino platform (at least that what I thought). So the manufacturer could be using other components. Also, eventhough I have a Centrino laptop from Dell, it is not using the Intel graphic card but an ATI one (which is not compatible with Xgl...).
By the way, on [Intel web site]("http://www.intel.com/"), it is called "[Centrino Duo]("http://www.intel.com/products/centrino/duo/index.htm")" the new platform for Core Duo processor. The WLAN is a Intel PRO/Wireless 3945AGB. I do not have this card (I have a older one the 2100 3B, for the first Centrino platform with Pentium M, but mine was working out of the box...) Intel has a [Linux driver for the Intel PRO/Wireless 3945ABG card]("http://support.intel.com/support/notebook/sb/cs-006408.htm").

Regarding Xgl and testing it. Just get the Kororaa CD and go to the shop where you intend to buy the laptop (if you do not buy it online). Then tell the vendor that you want to buy this laptop, but you need to see if it is running the version of Linux you have on the CD. If he doesn't want, you can explain him what a Lice CD is, and that it does not touch the hard disk nor harm or modify anything on the hardware it is tested on.
If he feels like this can be the thing to make you buy this laptop, he might not hesitate long ;)

Huygens

---

### Post by el3ktro on 2006-08-15
Thanks again for your tipps. Well I really think just trying a LiveCD is the best + most accurate way to test how well Ubuntu works on this machine. Besides that, what doyou think of this laptop? I want to be very mobile, not more than 12", lightweight, I need a good working machine (no gaming or fancy graphics at all), I need wireless, and that's about it. This Averatec thing costs 999€ which I think is a good price.

Tom

---

### Post by vcrfix on 2006-08-15
I have an older Averatec 3220H1 with 256MB Ram and the Wifi, and have successfuly installed Ubuntu 6.06 with Wifi working without any further customizations. Audio also is clear. All hardware was detected and works properly.

There is only one issue I had, was trying to install ubuntu as dual boot with Windows XP Home, and when I choose manual partitioning, ubuntu hung. Rebooted and choose to automatic partitioning to use entire disk and no problems. Since I have wifi working, and have other XP machines, do not really care of keeping XP on the Averatec. Would have been nice though.

Also at the time that I attempted to install Ubuntu as dual boot, I already had Fedora 2 working with XP as dual and using Grub boot loader. 

Like I said, happy with Ubuntu because I have wifi working without having to rebuild the kernel and ralink driver code.

Thanks Ubuntu!

---

### Post by JamesB on 2006-08-15
I was looking a few weeks ago and decided on the asus a8jc. everything worked out of the box, even the card reader, except the grafix card, but downloaded the driver, nvidia geforce go7300, and all works. Really happy:-) the only thing I haven't tryed yet is the inbuilt camera, but I'm not too keen on looking at myself anyway.
Happy hunting

James

---

### Post by el3ktro on 2006-08-22
Thanks so far. Well I've looked a little bit more, and actually the laptop I intend to buy is a Centrino laptop, it's just not stated on the Averatec site itself, but I've found pictures of this laptop with a small Centrino sticker on it. So I guess WLAN, graphics & sound should be no problem right?

I have another question about the Core Duo CPIU though: To fully support it, would I need to install an i686 SMP kernel? And a related question: I've looked trough a lot of benchmarks and found that ReiserFS is generally very fast, but also uses more CPU. Would you recommend formatting everything with ReiserFS instead of Ext3 (looking at speed vs. battery)?

Tom

---

### Post by huygens on 2006-08-23
> **el3ktro said:**
> I have another question about the Core Duo CPIU though: To fully support it, would I need to install an i686 SMP kernel? And a related question: I've looked trough a lot of benchmarks and found that ReiserFS is generally very fast, but also uses more CPU. Would you recommend formatting everything with ReiserFS instead of Ext3 (looking at speed vs. battery)?

For the CPU/kernel question, yes you could use the i686 SMP version or you could also use the i386 SMP version. The i686 should be faster, but I am not convince you will see the difference ;-)
I asked myself the same question for my laptop. Which FS? My partition scheme is:
/boot 128MiB
/ 4GiB
/home 3GiB

I decided first to go for ext3 for /boot (so no compatibility problem with the bootloader), XFS for / (for best performance at boot time or when launching application) and JFS for /home (to minimize battery, at least I hope).
On which figure did I base my choice? I looked for several benchmarks on Google, and find out that XFS was having really good performance (comparable to Reiser4) and sometimes can use less CPU than Reiser4. So it was a good deal. JFS is one of the least CPU intensive FS, so it was good to fiddle with my personnal data as this is what I manipulate most.

My experience was that XFS journaling was constantly active, so the HD never got a chance to sleep... Thus, I had really bad autonomy when on battery. (perhaps a Dapper beta problem...)

Nowadays, I switched to ext3 for the / partition and keeping the other as said before. My autonomy is still lower than when I am under Windows, but has much improved (my HD goes to sleep!!!) ;-) And I'm pretty happy with it now.
I did not go to Reiser* FS, the former 3 version is not enough interesting in my opinion (CPU utilisation vs. better perf does not seem that interesting to me), and the version 4, I think it is not available on the Ubuntu installer, isn't it?

Huygens

---

### Post by el3ktro on 2006-08-23
Yeah the filesystem question is a tough one. XFS seems to be a good choice, I've heard that it is pretty fast but uses less CPU. ReiserFS may really be too CPU hungry. But I think I'll just stick with Ext3 probably, it should be one of the most marture filesystems, and you definitely will not have any compatibility problems. But I'll look trough a few benchmarks again, and see if I find something interesting about recommended filesystems for laptops.

Thanks!
Tom

---

### Post by huygens on 2006-08-24
One more argument is that ext3 has a Windows driver. So if you want to access your home partition from Windows (dual boot), it would be a good idea to have it in ext3. The driver for Windows is an ext2 driver (no journaling), but as ext3 is backward compatible with ext2, this driver can handle properly this format.
Check the forums for more information.

Then, you can still go for another FS for the systems partitions, so it is not visible from Windows and you avoid mistakes ;-)

Huygens

---

### Post by el3ktro on 2006-08-26
Damn, damn, damn. I didn't find any shop in my town to actually look at the laptop, so I just ordered it only to find out that the Ubuntu Desktop CD doesn't boot at all. I've been fiddling around for several hours now, and I finally got the Gentoo Install CD to run, but only when I turn hardware detection of. The 8139too module for the onboard NIC hard freezes the system, but there must be another module causing a freeze - it always happens during hardware detection. Other than that, the laptop runs fine also with ACPI enabled. Any ideas? Does anybody have an Averatec 2460??

Tom

---

### Post by cruiseraddict on 2006-08-26
I purchased an Averatec 2260eh1 and had no luck with Ubuntu Red Hat or Suse. The Wlan card is a mini usb. Ubuntu could see it but no one on the averatec forums could get it to work. The video card in the 2260 also would lock X up randomly. I returned the laptop and bought an Acer 5102WLMI and am using it currently with Ubuntu working fully with no special configuration. I would look at the Acers and Asus laptops before going with the Averatec.

Dave

---

### Post by daou on 2006-08-27
> Damn, damn, damn. I didn't find any shop in my town to actually look at the laptop, so I just ordered it only to find out that the Ubuntu Desktop CD doesn't boot at all. I've been fiddling around for several hours now, and I finally got the Gentoo Install CD to run, but only when I turn hardware detection of. The 8139too module for the onboard NIC hard freezes the system, but there must be another module causing a freeze - it always happens during hardware detection. Other than that, the laptop runs fine also with ACPI enabled. Any ideas? Does anybody have an Averatec 2460??


I hope you get it working. I'm getting nervous after reading your post :( . I changed my order from the Asus to a Fujitsu-Siemens Amilo Si 1520-22. It's 12" but with nearly the same specs as the Asus and I'm getting it about 2 weeks from now.

EDIT: But I suggest you make a post about your laptop in the [Hardware Incompatibility List]("http://www.ubuntuforums.org/showthread.php?t=207916") to help others make their choice.

---

### Post by daou on 2006-08-27
By the way, has anyone noticed the fact that a lot of manufacturers sell laptops with Windows XP Home, a product that is outdated and will have support cut off in 2007? And not just laptops meant for home use, but for businesses as well. Then they stick a "Vista ready" sticker on it, knowing you'll have to buy Vista within a year if you stick with the XP Home, especially if you are a security concious user.

I smell M$ ripoff.

---

### Post by jogege on 2006-08-28
> **daou said:**
> I hope you get it working. I'm getting nervous after reading your post :( . I changed my order from the Asus to a Fujitsu-Siemens Amilo Si 1520-22. It's 12" but with nearly the same specs as the Asus and I'm getting it about 2 weeks from now.

EDIT: But I suggest you make a post about your laptop in the [Hardware Incompatibility List]("http://www.ubuntuforums.org/showthread.php?t=207916") to help others make their choice.



Could you kindly let's have your take on the FSC si-1520 once you get it? I had wanted to get one but cos I could find little or nothing about it on the net, I am now thinking of an Asus A8JC or A8F instead. I would really prefer a 12" screen though and am not bothered about integrated graphics.

---

### Post by el3ktro on 2006-08-28
Ok a little update now:

I have now managed - by deactivating hardware auto detection during boot - to install Gentoo on my Averatec 2460. Gentoo offers a networkless install, which worked fine. After booting the laptop I was able to recompile the kernel and load the 8139too module with PIO instead of MMIO - and it works! Now I also have successfully installed the ipw3945 module for the wireless network card - and it works! Plus I've installed the latest XOrg and I have accelerated graphics in full widescreen resolution (1280x800) - so this also works! USB, the SATA harddisk and the DVD burner also work flawlessly. I didn't test Firewire, the Memory card reader & sound yet but I'll do this soon. All in all, the laptop works perfectly - you just can't install Ubuntu on it because it crashes during the LiveCD boot - which I think is caused by the 8139too module, which crashes for me too in Gentoo, except when I load it with using PIO instead of MMIO.

So there is hope - and I hope that this annoying issue is fixed at least with Edgy! I'll try the daily builds of Edgy every few days and as soon as one of these daily builds boot successfully I'll post here.

So don't give up - Intel 945GM, Intel GMA 950 graphics, the RTL8139C and the Intel 3945ABG wireless work perfectly, there's just a bug in the Ubuntu installer it seems!

Tom

---

### Post by daou on 2006-08-28
> Could you kindly let's have your take on the FSC si-1520 once you get it? I had wanted to get one but cos I could find little or nothing about it on the net, I am now thinking of an Asus A8JC or A8F instead. I would really prefer a 12" screen though and am not bothered about integrated graphics.

Sure. I'll get it 12th or 13th of September, so keep an eye out for this thread then. I will have tested it at least by weekend after that.

I switched to 12" because I went to a store to compare the 15.4" and 12". And 15.4" is HUGE](*,) . Especially for me because I have a good desktop at home. I will only use the laptop away from home and what's the point of a laptop if its too big to want to carry it around.

---

### Post by daou on 2006-08-28
> 
So don't give up - Intel 945GM, Intel GMA 950 graphics, the RTL8139C and the Intel 3945ABG wireless work perfectly, there's just a bug in the Ubuntu installer it seems!

Have you considered filing a bug report?

---

