---
title: "Success!!--Dapper on IBM Thinkpad 570e"
date: 2006-07-28
forum: Hardware &amp; Laptops
---

### Post by Brunellus on 2006-07-28
A while back, I reported some [ problems]("http://www.ubuntuforums.org/showthread.php?t=219601") installing Xubuntu Dapper on an old IBM Thinkpad 570e.  

I determined, after some work (a more detailed report on those problems should be forthcoming) that the default Dapper kernel was at fault.  Therefore, I present the following HOWTO for installing Dapper on an IBM Thinkpad 570e:

In all of the following, I am assuming you have access to an Ultrabase docking station equipped with a CD-ROM drive.  I am not aware of any other way of installing OSes on this model Thinkpad that does not involve the Ultrabase.

STEP ONE:  Installing a base system (Breezy)

The default Dapper kernel can't deal with PCMCIA cards on the Thinkpad 570e.  Luckily, Breezy's does--as do later versions of the Dapper kernel available from apt.  Since the _only_ network connectivity you even have a chance of getting with this model is via a PCMCIA adaptor, installing Dapper from CD and then upgrading is not an option.

So first, obtain a BREEZY (5.10) installation CD.  Boot with this in the CD drive.  

When prompted, type 

```
server
```

at the boot:  prompt.

Follow the prompts.  When it's all over, you will reboot into your new--very minimal--breezy install.

Ensure that your pcmcia network adaptor is detected and configured.  

STEP TWO:  Upgrading to Dapper

The next step is to update to dapper, bypassing the broken kernel distributed on the CDs and grabbing a newer version.

For this, you must edit ```
/etc/apt/sources.list
```Use the text editor of your choice.  Mine is vim:

```
sudo vim /etc/apt/sources.list
```

comment out the line for the CD and change all references to "breezy" to "dapper"

when you're done, save and quit.  now execute

```
sudo apt-get update
```

which will download the package lists for dapper.  Then

```
sudo apt-get dist-upgrade
```

will dist-upgrade you from Breezy to Dapper.  Note that because we're in a 'server' install, with nothing but the base system, this will be pretty quick--well, not super-quick, but faster than dist-upgrading a 'full' ubuntu install.

Let the upgrade complete.  Then, reboot.  You're now Dapper!

STEP THREE:  Bells & Whistles

Once we're satisfied that all our hardware is detected, it's a simple matter of getting the necessary packages.  

Since this is an old laptop, the logical choice is Xubuntu:

```
sudo apt-get install xubuntu-desktop
```

will download, configure, and install all the packages that would otherwise be on the Xubuntu Dapper CD.  You might also want to think about a very light install, as recommended by the [LowMemorySystems wikipage]("https://help.ubuntu.com/community/Installation/LowMemorySystems").

EPILOGUE:  Hardware quirks and TODO

There is one notable and well-known hardware quirk when configuring X on these laptops.  They only have enough video ram for 16-bit color depth, but Ubuntu sets them up for 24-bit color depth by default.  Performance consequently suffers.  

Edit /etc/X11/xorg.conf

Scroll until you see the section marked "Screen"  at the "DefaultDepth" line, change the value from 24 to 16.  Save and quit, then kill and restart the X server.  Things should run a bit better now.

TODO:  Enabling APM suspend/hibernate and Fn-keys, test IrDA.

---

### Post by Metacarpal on 2006-07-28
Brilliant, yet simple!

---

### Post by N6546R on 2006-07-28
As a data point, I installed Breezy on a ThinkPad 570 that had no CD. I created a five-floppy set that did a network install, it took half a day on a DSL connection. It runs great, if a bit slow, but I use it mainly as a MOO and web server. A search on this forum for 'network install' should provide the necessary steps.

Perry

---

### Post by Brunellus on 2006-07-31
> **N6546R said:**
> As a data point, I installed Breezy on a ThinkPad 570 that had no CD. I created a five-floppy set that did a network install, it took half a day on a DSL connection. It runs great, if a bit slow, but I use it mainly as a MOO and web server. A search on this forum for 'network install' should provide the necessary steps.

Perry
I had originally acquired the computer without an ultrabase dock.  Subsequently, I bought an ultrabase and CD drive, but no floppy.

I'm quite impressed that 5 floppies was enough to do a netinstall...over a PCMCIA ethernet adaptor, I'm guessing?

Currently, my main problem is enabling hibernation--a lot of fiddling around with partitions, tphdisk, and so forth.   I'm torn between enabling swsusp2 (which requires me to compile a new kernel, blah) or wiping my present install, creating the necessary hibernation partitions, plus swap, and effecting hibernation that way.

Swsusp2 would let me keep my whole hard drive.  The latter solution eats up more space, since I have to maintain *both* a linux swap partition *and* a special hibernation partition.  Complicating matters, of course, is the fact that I have an ungodly amount or RAM on this thing-- 320 MB, from an era where 128 MB was pretty hot!-- so I'm having to fiddle with the size of the hibernation partition.  I've probably been making mine too small lately.

Ok, sorry for ranting, but I figure if I feed the archive, it'll be useful to somebody else.

---

### Post by stani on 2006-08-19
Hi,

I've almost succesfully installed Xubuntu on someones IBM Thinkpad 570. I didn't have a CD-rom or floppy's, so I pushed the hard-disk in my laptop with internet and cd-rom. Afterwards I placed it back in the 570 and did:

```
$sudo dpkg-reconfigure xserver-org
```

Everything installed fine, just the wireless pcmcia card (Gericom, based on realtek 8180) was a bit of a pain but now it seems to work.

BUT my biggest problem is that mounting of USB sticks or any other USB device doesn't work. I put it back in the other laptop and there it works. I've been trying a hell lot of things already and I was wondering if it works on your thinkpad 570?! Did you change something in the BIOS. 

It is driving me crazy, as this laptop is for someone who I convinced to start using Ubuntu instead of Windows. 

Thanks for answering,

Stani
--
[http://www.stani.be](http://www.stani.be)
[http://pythonide.stani.be](http://pythonide.stani.be)

---

### Post by psynapse on 2006-08-27
I too have a Thinkpad 570 and have installed Dapper Drake (from a PCMCIA CDROM and DOS boot diskettes).  It works fine .... except that PCMCIA services do not work. Device Manager recognises the presence/removal/insertion of the cards and cardctl shows functioning cards IRQs etc.  Which part of the kernel do you suspect and do you believe it fixed in 6.06lts.  Many thanks John

---

### Post by Brunellus on 2006-08-27
> **psynapse said:**
> I too have a Thinkpad 570 and have installed Dapper Drake (from a PCMCIA CDROM and DOS boot diskettes).  It works fine .... except that PCMCIA services do not work. Device Manager recognises the presence/removal/insertion of the cards and cardctl shows functioning cards IRQs etc.  Which part of the kernel do you suspect and do you believe it fixed in 6.06lts.  Many thanks John
john:  current dapper kernels work fine;  the kernel as shipped with the install CD, however, is broken.

Please read the first post in this thread for a method to get dapper running on the 570e.  

Essentially, the way to go is to make a minimal ("server") installation of BREEZY, and then to dist-upgrade to the newest DAPPER.  Details above.

---

