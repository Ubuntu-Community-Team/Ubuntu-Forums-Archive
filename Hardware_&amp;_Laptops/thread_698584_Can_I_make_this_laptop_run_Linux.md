---
title: "Can I make this laptop run Linux?"
date: 2008-02-16
forum: Hardware &amp; Laptops
---

### Post by Yes on 2008-02-16
I have a very, very old laptop.  It's got a 75 MHz CPU, 4 MB of RAM, and  ~400 MB hard drive.

Can I install a Linux distro on it, or is it useless?

Thanks.

---

### Post by fedex1993 on 2008-02-16
try um DSl or puppy linux

---

### Post by Yes on 2008-02-16
DSL says it's a desktop oriented OS, how easy will it be to get it to work on a laptop?

---

### Post by dicecca112 on 2008-02-16
same difference.  Desktop and Laptop are really the same thing here.  Ubuntu is a Desktop OS, so is Windows, but they all run on Desktops and Laptops just fine

---

### Post by SixedUp on 2008-02-16
I very much doubt if either Puppy or DSL will fit in only 4MB of RAM. In fact, I very much doubt *any* standard distribution will fit in that much memory. You're talking about lower-specification machines than most embedded systems can muster these days!

[edit]
Puppy claim 64MB ram as the minimum ... [http://www.puppylinux.org/wikka/MinReq](http://www.puppylinux.org/wikka/MinReq)
DSL claim 8MB (recommend 16MB) for a command line only install ... [http://damnsmalllinux.org/wiki/index.php/Minimum_Hardware_Requirements](http://damnsmalllinux.org/wiki/index.php/Minimum_Hardware_Requirements)
[/edit]

Of course, this being Linux, you *can* still do what you describe  (see [http://tldp.org/HOWTO/4mb-Laptops.html](http://tldp.org/HOWTO/4mb-Laptops.html) for how someone else achieved it) but you'll be looking to do all kinds of hacking and unnatural acts, and at the end of it you'll have something that's command-line-only, and pared to the bone and beyond.

Unless you're pretty handy with Linux (and have a real emotional bond to those laptops!) then I suspect you're going to find this a real nightmare.  But if you do manage it, we'd love to hear about it :)

---

### Post by .nedberg on 2008-02-16
DSL or Puppy. Any kind of *buntu will be to much...

You will have to do some adjustments if you are going to use wireless (if that thing has wireless at all...).

---

### Post by Yes on 2008-02-16
Well it used to run Windows 98, which seems to have the same requirements as DSL.

Gonna try DSL, I'll let you all know how it goes.

---

### Post by Yes on 2008-02-17
Ok, I coppied all 36 parts of the iso onto the hard drive via floppy and put it back together.  I get to the DSL boot menu and then it seems to hang after saying "DSL comes with absoultely no warranty...".  Is this because of the low specs of the laptop or is am I doing something wrong?

The laptop actualy has 8 MB of RAM, BTW.

---

### Post by syms on 2008-02-17
> **Yes said:**
> Ok, I coppied all 36 parts of the iso onto the hard drive via floppy and put it back together.  I get to the DSL boot menu and then it seems to hang after saying "DSL comes with absoultely no warranty...".  Is this because of the low specs of the laptop or is am I doing something wrong?

The laptop actualy has 8 MB of RAM, BTW.

i dont think that dsl will work with gui. i think u need at least 64 mb ram to run gui.

---

### Post by polmir on 2008-02-17
> **Yes said:**
> I have a very, very old laptop.  It's got a 75 MHz CPU, 4 MB of RAM, and  ~400 MB hard drive.

Can I install a Linux distro on it, or is it useless?

Thanks.

Connect hd to other computer and install Dam Smal Linux. After, connect disk to laptop and reconfigure Your system.

---

### Post by Yellow Pasque on 2008-02-17
1994 called; it wants its laptop back. (It probably ran out of memory during install)

---

### Post by Yuri77 on 2008-02-17
Try DELI linux: [http://www.delilinux.org/]("http://www.delilinux.org/"). It is especially targeted to old computers, even 486.

---

### Post by Jay Jay on 2008-02-17
> **Yes said:**
> I have a very, very old laptop.  It's got a 75 MHz CPU, 4 MB of RAM, and  ~400 MB hard drive.

Can I install a Linux distro on it, or is it useless

> The laptop actualy has 8 MB of RAM, BTW.

Hardware is _never_ useless, if you have an Ethernet PCMCIA card then you could install [Coyote Linux ]("http://dolly.czi.cz/coyote/")(with the [PCMCIA support]("http://www.xinilux.us/portable_coyote/")) and use it as a firewall. Coyote Linux has a 'massive' system requirement of:

486DX or better
At least 8MB RAM
A floppy drive to load the OS from, which comes on a single 1.44MB disk :)

If you're interested, check it out from [here]("http://sourceforge.net/project/showfiles.php?group_id=63552").

On a side note related to obsolescence. It's ironic to think of what the Space Shuttle's prehistoric computers are capable of, but yet in the consumer world they'd end up on a landfill site as being "useless" or not "powerful enough"...

---

### Post by Yes on 2008-02-17
Deli Linux looks promising... does anyone know if it can boot from a flash card in a PCMCIA slot?  The laptop doesn't have a CD-ROM and it's a big pain to split the iso up and put it on the hard drive 1.4 MB at a time.

e:  Nevermind, apparently Deli is unusable with only 8 MB of RAM.  I installed Windows 3.1 on it just for the heck of it and it runs as well as any Windows product runs.

If anyone can find a *nix distro that'll run on just 8 MB of RAM, please let  me know.

---

### Post by Yes on 2008-02-17
Are there any full Linux distros that are command line based?  How would they run on the laptop?

---

### Post by K.Mandla on 2008-03-03
> **Yes said:**
> I have a very, very old laptop.  It's got a 75 MHz CPU, 4 MB of RAM, and  ~400 MB hard drive.

Can I install a Linux distro on it, or is it useless?
It's usable, the problem that you have is that 8Mb is an exceptionally low amount of memory. For comparison: [http://ubuntuforums.org/showthread.php?t=294292](http://ubuntuforums.org/showthread.php?t=294292)

8Mb won't let you run the Ubuntu installer. If you can get it up to 32Mb or more, it's going to work fine. Slow, but fine.

Other distros might install on less than 32Mb, but that's about the ground level for what I've seen.

---

