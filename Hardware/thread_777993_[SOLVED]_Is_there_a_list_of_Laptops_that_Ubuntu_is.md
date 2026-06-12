---
title: "[SOLVED] Is there a list of Laptops that Ubuntu is known to install on perfectly?"
date: 2008-05-01
forum: Hardware
---

### Post by Rytron on 2008-05-01
Hi,
Is there a **list of Laptop models that Ubuntu is known to install on perfectly**?
The reason I ask is because many web sites that sell laptops, sell them with Vista or XP pre-installed. I want a laptop with no OS pre-installed on it. So therefore if I get a cheap laptop with Vista or XP pre-installed; I'd like to know for certain if I could install Ubuntu on that specific laptop model.

Also, is there a reputable place / website that sells laptops with no operating systems that sell in Ireland?

Thanks.

---

### Post by Vermind on 2008-05-01
Hello,
[Zareason]("http://www.zareason.com/shop/home.php") sells laptops and desktops and other boxes with Ubuntu preinstalled.
I also hear that HP and Dell have their series of laptops that have Ubuntu or OpenSUSE installed. I check [Linux Laptop]("http://www.linux-laptop.net/") for experiences and install guides for laptops when I want to know if something works. The easiest way of course is getting Your friend with the same model to boot a livecd and see how it works.

---

### Post by degenerate1991 on 2008-05-01
My Acer Aspire 3620 installed ubuntu perfectly. However, it is a bit slow (512 ram, 1.6 Celeron M :(, GMA 915) and the battery life isn't so great. It is probably really cheap at the moment (being a over 1 year old design). The fun joke is that it is also labeled "vista capable" :lolflag: Oh, don't drop it, mine has been dropped one too many times and is starting to fall apart.

---

### Post by chrisby on 2008-05-01
I just bought a acer extensa 5620-4025 from circuit city for $450, and everything works out of the box including hibernate!

---

### Post by sifon187 on 2008-05-02
Dell XPS m140

Everything went very smooth without much problems

---

### Post by MaindotC on 2008-05-02
> **Vermind said:**
> Hello,
[Zareason]("http://www.zareason.com/shop/home.php") sells laptops and desktops and other boxes with Ubuntu preinstalled.

Ugh - eye candy - how I wish...in the meantime I'm stuck with crappy T60 :(  Maybe after I get my tax refund cheque.

---

### Post by formerflyboy on 2008-05-02
I have a Toshiba Satellite A105-S4397 that I bought from Walmart last year and 7.20 installed without a hitch and the upgrade to 8.04 was easy.

---

### Post by svega85 on 2008-05-02
here is a list of what works and what doesn't in different laptops [https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)

---

### Post by subzero316 on 2008-05-02
Ubuntu will install on all laptops perfectly. even in the ones your vista will not..:lolflag:...you might have driver issues that can be solved read the respective threads for tat.

---

### Post by Rytron on 2008-05-02
> **Vermind said:**
> Hello,
[Zareason]("http://www.zareason.com/shop/home.php") sells laptops and desktops and other boxes with Ubuntu preinstalled.
I also hear that HP and Dell have their series of laptops that have Ubuntu or OpenSUSE installed. I check [Linux Laptop]("http://www.linux-laptop.net/") for experiences and install guides for laptops when I want to know if something works. The easiest way of course is getting Your friend with the same model to boot a livecd and see how it works.

So I presume that if Ubuntu worked on a laptop (on any computer for that matter) as a live cd, then it would install without problems on that computer?

---

### Post by Rytron on 2008-05-02
> **degenerate1991 said:**
> My Acer Aspire 3620 installed ubuntu perfectly. However, it is a bit slow (512 ram, 1.6 Celeron M :(, GMA 915) and the battery life isn't so great. It is probably really cheap at the moment (being a over 1 year old design). The fun joke is that it is also labeled "vista capable" :lolflag: Oh, don't drop it, mine has been dropped one too many times and is starting to fall apart.

I'd say you'd need Ram nearing 750MB / 800MB to run Ubuntu more smoothly. You could try Xubuntu. It is excellent for lower spec machines.

---

### Post by Vermind on 2008-05-02
Hello,
Yes, that's generally the case. Also, if You want to really make sure, You can use the livecd and install to a USB memory stick or a portable hard drive, using the model in question, then see how well that works.

Most of my problems with previous Ubuntu versions have not been with installing. Once, I had to install on software RAID, that required some work. 
Other problems I have had were with sound drivers (had to get the latest ALSA 16 for one laptop, Realtek's own bundle of ALSA for another), wireless drivers (for intel, iwlwifi is much better than ipw, but ipw is enabled in Ubuntu by default), graphics drivers (nvidia card on my desktop failed to boot livecd without safe graphics, but after install and manual install of nvidia drivers, worked well).
So, if sound, graphics and wireless work on the livecd, that's perfect. if one of these don't, You can install drivers on the livecd too, and then try if they work. if You can't get stuff to work, usually the installed version is more flexible than the livecd in accepting new stuff You install, so even if the livecd does not run 100% perfect, the installed system could.

---

### Post by Dennis Beekman on 2008-05-02
I have 2 laptops and it workes fine on both...

Acer 3690 Celeron 1,7Ghz Processor Intel Chipset.
Acer 5103 WLMI 1,7 AMD Thurion Dual Core with amd chipset.

Both work straight out of the box under ubuntu 7.10 and 8.04 LTS both the 32 and 64 bit version if applicable.

I hope this help you decide or that this will be added to a list of known laptops.

---

### Post by Rytron on 2008-05-02
> **Vermind said:**
> Hello,
[Zareason]("http://www.zareason.com/shop/home.php") sells laptops and desktops and other boxes with Ubuntu preinstalled.
I also hear that HP and Dell have their series of laptops that have Ubuntu or OpenSUSE installed. I check [Linux Laptop]("http://www.linux-laptop.net/") for experiences and install guides for laptops when I want to know if something works. The easiest way of course is getting Your friend with the same model to boot a livecd and see how it works.

Thank you very much Vermind for the [http://www.zareason.com/shop/home.php](http://www.zareason.com/shop/home.php) link. I emailed them regarding whether or not they deliver to the Republic of Ireland. They do, I guess they deliver to just about anywhere in the world. And they were very prompt in replying

---

### Post by myturntohide on 2008-05-03
> **subzero316 said:**
> Ubuntu will install on all laptops perfectly. even in the ones your vista will not..:lolflag:...you might have driver issues that can be solved read the respective threads for tat.

Well this is a false presumption, there are more often than not problems with installing linux on machines that are natively made for windows and haven't been manufactured with Linux in mind. Ubuntu won't install perfectly, a driver issue is definately not perfect. 

But no doubt, if the live CD works on your machine, you will be able to run Ubuntu. I would advise using the live CD for as long as you can in a session, try out the terminal try out all the programs and settings, basically run about the OS trying to alter every possible thing. If it goes without a hitch do a clean install on the drive and you should be fine. There are plenty of tutorials on here. I found them all extremely useful so just keep a high head and try out the liveCD.:KS

---

### Post by intense.ego on 2008-05-03
> **strAlan said:**
> Ugh - eye candy - how I wish...in the meantime I'm stuck with crappy T60 :(  Maybe after I get my tax refund cheque.

I also have a T60 and I like the simple, look. No stange curves or parts sticking out for me, just a perfect box.

On topic: I installed ubuntu perfectly on my T60, but there does seem to be a bit of a problem with Hibernation, at least in Gutsy (haven't installed Hardy yet).

---

### Post by teddfox on 2010-12-25
HP Mini 5103 Ubuntu 10.10 install perfectly, but you have to remove  /etc/modprobe.d/intel-5300-iwlagn-disable11n.conf to make the wireless work at more that 14.4 modem speeds.

---

### Post by Rytron on 2010-12-27
> **teddfox said:**
> HP Mini 5103 Ubuntu 10.10 install perfectly, but you have to remove  /etc/modprobe.d/intel-5300-iwlagn-disable11n.conf to make the wireless work at more that 14.4 modem speeds.

Thanks for the info, teddfox.

---

### Post by Phantom3D on 2011-01-20
I currently have the Dell mini 1018, that I am quite happy with. But is the HP 5103 worth it. I see it has a dualcore N550, will it be a big difference compared to the Atom N450?

---

### Post by teddfox on 2011-02-22
> **Phantom3D said:**
> I currently have the Dell mini 1018, that I am quite happy with. But is the HP 5103 worth it. I see it has a dualcore N550, will it be a big difference compared to the Atom N450?

The screen with hi res makes it all worth it.  I spent a little more and got the SSD too :-)  Super AWESOME little laptop.  It can even drive a 30-inch dell monitor with no real issues.:guitar:

---

### Post by ubuntu27 on 2011-02-22
Before this thread gets closed for Necromancy, I want to comment that [Canonical]("http://www.canonical.com/") has created a list of [Ubuntu-Certified Hardware]("http://www.ubuntu.com/certification/")

[Ubuntu Hardware Certification]("http://www.canonical.com/engineering-services/certification")

____

You might be also interested in helping to test laptops:

[https://wiki.ubuntu.com/Testing/Laptop](https://wiki.ubuntu.com/Testing/Laptop)

---

### Post by Rytron on 2011-02-22
> **ubuntu27 said:**
> I want to comment that [Canonical]("http://www.canonical.com/") has created a list of [Ubuntu-Certified Hardware]("http://www.ubuntu.com/certification/")

[Ubuntu Hardware Certification]("http://www.canonical.com/engineering-services/certification")

____

You might be also interested in helping to test laptops:

[https://wiki.ubuntu.com/Testing/Laptop](https://wiki.ubuntu.com/Testing/Laptop)

Thanks.

---

### Post by cascade9 on 2011-02-22
> **ubuntu27 said:**
> Before this thread gets closed for Necromancy, I want to comment that [Canonical]("http://www.canonical.com/") has created a list of [Ubuntu-Certified Hardware]("http://www.ubuntu.com/certification/")


Warning, the ubuntu certified hardware list is flawed. 

At least some of the laptops on that list have several sub-models. Some of those sub-models will have hardware that is unusable with ubuntu (mainly nvidia optimus). Since canonical hasnt listed the actual hardware in the tested laptops, it would be easy to buy a model that isnt 100% compatible. In the case of the optimus models, it could take quite a bit of command line work to even disable the nvidia GPU, or an even larger amount of trying if someone hasnt figured out how to do it and posted directions.

---

### Post by teddfox on 2011-02-23
I think 1/2 of the issue why people do not look at those certified lists are that they are so far behind.  Many of us run HP laptops but Only 1 HP laptop is on the list.  odd

---

### Post by mephisto1991 on 2011-02-23
> **cascade9 said:**
> Warning, the ubuntu certified hardware list is flawed. 
 
At least some of the laptops on that list have several sub-models. Some of those sub-models will have hardware that is unusable with ubuntu (mainly nvidia optimus). Since canonical hasnt listed the actual hardware in the tested laptops, it would be easy to buy a model that isnt 100% compatible. In the case of the optimus models, it could take quite a bit of command line work to even disable the nvidia GPU, or an even larger amount of trying if someone hasnt figured out how to do it and posted directions.
 my lappy model is Asus X88 series and my nVidia couldn't function with Ubuntu, i've tried to upgrade the driver/install the driver, after installation it seems like the driver still couldn't activate the functions of the graphic card, hence the customization/higher utility of graphics inactivated. =/
 
i tried all I could all night long, other than that, everything's perfect, the flashplayer works as it's supposed to.
 
btw. i've installed the 32-bit version of Ubuntu 10.10 inside Windows 7.

---

### Post by Rytron on 2011-02-23
Thanks for the tip cascade9.

---

### Post by cascade9 on 2011-02-23
No problem. ;) 

> **teddfox said:**
> I think 1/2 of the issue why people do not look at those certified lists are that they are so far behind.  Many of us run HP laptops but Only 1 HP laptop is on the list.  odd

Possibly because the manufacturer needs to pay to get them tested/on the list. I'm pretty sure that HP leans more toward 
 novell/SUSE and RedHat than ubuntu.

---

### Post by bluestreak patriot on 2011-06-28
I did a Google search for "ubuntu certified laptops" and found many, many links. One is provided below. Hope it may be of some help.
[http://www.ubuntu.com/certification/release/10.10/laptops](http://www.ubuntu.com/certification/release/10.10/laptops) 

Cheers

---

### Post by Naggobot on 2011-06-28
There is also a laptop compatibility list thread here in the forums

[http://ubuntuforums.org/showthread.php?t=1543006](http://ubuntuforums.org/showthread.php?t=1543006)

There also is an incompatibility list in a separate thread. 

Getting a laptop can be a tricky business so good luck. I run eMachines E642G and Lucid. Proprietary ATI driver works but for some reason I could not get open source driver to work. Touch pad works but is not recognized as touch pad. Even two finger scroll works but it can not be disabled automatically while typing. 

In short try to get a computer with Synaptic touchpad not some other copy, most of the bugs have been ironed out in latest kernels though but not for Lucid. Do not get a one with Nvidia optimus card (note this is an opinion).

---

### Post by collisionystm on 2011-06-28
Pretty much any Dell Vostro will work.

I have a Vostro 1014 laptop that came with a Core 2 Duo and 3gb of ram with 11.04 x64 installed. Worked perfectly. let me rephrase.... EVERYTHING worked perfectly. I have also done this on 3 other, different model vostro laptops and several desktops from the vostro line. Works great!

---

### Post by rreyes3713 on 2011-06-28
I had an HP G71-340US laptop with Window 7 and I did a Wubi installation. 

No issues.
I did a "migration" [search Wubi installation to new partition thread] into a new partition. No issues!

Well make a long story short, this HP laptop of 1 year and two weeks literaly dies on me. Motherboard went kaput! 

I was able to get my buddy's Dell Inspiron 8600 laptop. I did a whole installation and partition to dual boot Ununtu and XP. The only issues I encountered in Ubuntu was getting the WiFi to work, and the video card to work properly. 

The WiFi is now working and I may get the Nvidia video card working properly [look at my thread Nvidia Installation ordeal]

But question arises ...

... is a Wubi installation using "Window" resources (drivers) because installation was clean. Then I'm just wondering if "migrating" to the new partition Ubuntu is still using Window resources.

---

### Post by quevedo200 on 2011-06-28
hi i have all dell inspiron 1564 and installed ubuntu 11.04 perfectly without any errors. everything worked out of the box 

i hope that helped

---

