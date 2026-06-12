---
title: "Custom PC vs Factory Built"
date: 2011-04-02
forum: Hardware
---

### Post by v5point0 on 2011-04-02
I am keen on building my own PC but I would like to know if such a route is actually a better alternative then factory built options given all the obvious reasons.

I would like to build a editing rig for dual booting OS X and Ubuntu. OS X would mainly be used for creative works - Keynote, Aperture, FCP, while Ubuntu for everything else.

It is just that while I been doing my comparison I have come across some who say it is better of going the factory built option, some who claim to have been building PCs for a significant amount of their lives. In eg:

Chris Bount from Macrumors Forums says "I was custom building PC's for 10 years. My most recent custom built PC before I purchased the iMac had the best of just about everything and it still was not as fast as the iMac for every day tasks. The iMac really shines when it comes to web browsing, ichat and word processing. As far as games, the older games you mention should run fine on the iMac with bootcamp. Another thing to consider is that if you build a PC. You will be upgrading the parts from time to time just to keep up with Vista or whatever else comes up down the line. At the end of 3 years, you probably would have put more money into the PC than if you purchased the iMac. Vista is a beast and very bloated. I kept having to throw hardware at it just to keep it running at a decent speed." Blount, C., 2008. iMac vs custom built pc [Online] (Updated 23 April 2008) Available at: [http://diigo.com/0get8](http://diigo.com/0get8) [Accessed  02 April 2011].

There are others but I am more interested in what this community has to say? I understand the comment above applies to Windows and this shouldn't be an issue on Ubuntu or OS X for that matter at least in the near future but generally is a custom builder on a better of track then a factory built user? Suppose he does his homework and knows what he is doing, even still would it be worth it on the long run?

---

### Post by gradinaruvasile on 2011-04-02
Apple/Mac - they test their OS+drivers on their hardware only so you are out there if you want to use OS X on PC hardware (=non-Apple). OS X does not run on PC in its original form, there are firmware/BIOS differences. It can be hacked to work but it is very unstable plus it is illegal.

For Ubuntu a custom built PC is ok. Most hardware work well with it. Just avoid the "latest and (?) greatest", go for the established mainstream components. As for video cards, i would recommend nvidia, it has the best drivers to date (anyway look up the model before to make sure it is ok).

Bottom line - if you want OS X, use a Mac (if you got the cash...). Ubuntu can be installed on it as far as i know (use an Intel variant), but i dont know details about stability and feature support.

---

### Post by v5point0 on 2011-04-02
> **gradinaruvasile said:**
> Apple/Mac - they test their OS+drivers on their hardware only so you are out there if you want to use OS X on PC hardware (=non-Apple). OS X does not run on PC in its original form, there are firmware/BIOS differences. It can be hacked to work but it is very unstable plus it is illegal.

For Ubuntu a custom built PC is ok. Most hardware work well with it. Just avoid the "latest and (?) greatest", go for the established mainstream components. As for video cards, i would recommend nvidia, it has the best drivers to date (anyway look up the model before to make sure it is ok).

Bottom line - if you want OS X, use a Mac (if you got the cash...). Ubuntu can be installed on it as far as i know (use an Intel variant), but i dont know details about stability and feature support.

Hackintoshes seem to work well if you build on a tried and tested system and maintain the mentality if it ain't broke why fix it.

"I've put together a list of hardware that I'm using and that I can guarantee will (or at least has) run Snow Leopard like a dream." Pash, A., 2009. How to Build a Hackintosh with Snow Leopard, Start to Finish [Online] (Updated 03 September 2009) Available at: [http://diigo.com/0gev8](http://diigo.com/0gev8) [Accessed  02 April 2011].

So I see myself only messing with the installation whenever a version of OS X comes out which is about every 2 years and even so I would be keeping a clone just incase.

But I do agree, it is a process which may render less then ideal results.

In regards to Apple EULA:

"A handful of Mac enthusiasts are not likely to draw the attention of Apple's lawyers. The legal cost to go after each individual over a single copy would be high. If a real movement were to start, then we would likely see Apple ratchet up the protection to its software before it tried to send out the lawyers." Fox, F., 2009. Is Making Your Own Hackintosh Legal? [Online] (Updated 12 March 2009) Available at: [http://diigo.com/0gev2](http://diigo.com/0gev2) [Accessed  02 April 2011].

I am running Ubuntu in a VirtualBox on an Intel MacBook, I don't want to setup a dual boot system and prefer a dedicated one disk one os method. I have an external drive which I would like to install Ubuntu on and the only way I can get it to boot on an Intel Mac is to place /boot on either a CD or the internal drive due to the way Mac's handle legacy OS.

I need help with Step 6 of this guide at: [http://ubuntuforums.org/showthread.php?t=19428](http://ubuntuforums.org/showthread.php?t=19428)

( 6 ) edit bootcd/isolinux.cfg and place the following line
DEFAULT linux initrd=initrd.img ro root=<your-root-dev>
Where, <your-root-dev> will be something like /dev/hda1. If you don't know your root device, look at your current grub config in /boot/grub/menu.lst.

How do I edit a .cfg file? Gedit can't open it

---

### Post by gradinaruvasile on 2011-04-02
> **v5point0 said:**
> Hackintoshes seem to work well if you build on a tried and tested system and maintain the mentality if it ain't broke why fix it.

I need help with Step 6 of this guide at: [http://ubuntuforums.org/showthread.php?t=19428](http://ubuntuforums.org/showthread.php?t=19428)

( 6 ) edit bootcd/isolinux.cfg and place the following line
DEFAULT linux initrd=initrd.img ro root=<your-root-dev>
Where, <your-root-dev> will be something like /dev/hda1. If you don't know your root device, look at your current grub config in /boot/grub/menu.lst.

How do I edit a .cfg file? Gedit can't open it

Any text editor can open it. IF it exist that is. GRUB has changed since then and there is no more menu.lst mentioned there. The file now is /boot/grub/grub.cfg.

Why do you need that anyway?

---

### Post by v5point0 on 2011-04-02
> **gradinaruvasile said:**
> Any text editor can open it. IF it exist that is. GRUB has changed since then and there is no more menu.lst mentioned there. The file now is /boot/grub/grub.cfg.

Why do you need that anyway?

isolinux.cfg was still there on 10.04, haven't checked 10.10. I don't know any other way of booting Ubuntu on an external drive because this is the way Apple has constructed EFI to replace BIOS.

---

### Post by perspectoff on 2011-04-02
I don't think I would ever build my own computer again. It ends up costing 2-3x a pre-built computer.

It is possible (e.g. at Walmart) to get a pretty powerful computer for about $200-$300, often with dual 64-bit Athlon processors, 6-8 Mb RAM (depending on sales), nVidia graphics, and a 500 Gb hard drive. It's not that easy to put one together for that price. (Here's a current example: [http://www.walmart.com/ip/Acer-EL1352G-41w/15686810](http://www.walmart.com/ip/Acer-EL1352G-41w/15686810) ). Remember, if you buy during the sales periods (late January and mid-October), you can get some really killer machines for peanuts. (I got one with 8 Mb, quad-cores, 500 Gb drive for $200.)

Besides, the components that I used to put in a computer (multiple hard drives for RAID, for example), I now use as standalone network devices, so they are not necessary in a home-built rig. For that reason I don't need big cases, anymore, and only a limited number of add-on card slots. Heck, everything is USB or Ethernet connected these days, anyway.

Besides, retail computers usually have a 64-bit OS thrown in (whether Apple OSX or Windows 7) which actually lowers the price (talk about value!), probably due to kickbacks or something. 

I think the only thing I insist on is a second hard drive slot (so I can at least have RAID 1 for the computer itself), but I don't think I've ever seen a retail computer that doesn't have this.

---

### Post by v5point0 on 2011-04-02
> **perspectoff said:**
> 6-8 Mb RAM

I am sure you mean GB.

So all in favor for a factory built system? If that is the case I would be looking at either:

Base Model Mac Pro
[IMG]http://farm6.static.flickr.com/5258/5582443348_56899fc08f_s.jpg[/IMG]

or

Base Model Mac Mini
[IMG]http://farm6.static.flickr.com/5014/5581858359_3cb6fb29ae_s.jpg[/IMG]

I really want a system for the long run.

---

