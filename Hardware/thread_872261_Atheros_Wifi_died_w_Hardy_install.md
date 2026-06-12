---
title: "Atheros Wifi died w/ Hardy install"
date: 2008-07-27
forum: Hardware
---

### Post by musicafterglow on 2008-07-27
Hey everyone -

I'm pretty new to all this, so I'm going to apologize up front if I'm posting in the wrong area or if this problem has already been addressed.

I've been toying around with Ubuntu a bit for a year or so now on my Acer Aspire 5570z laptop. The atheros wifi card has always been a bit of a pain, but I've always managed to get it to work with ndiswrapper. Anyway, I recently upgraded to Hardy 8.04LTS, and it completely stopped working. 

I stumbled across [this post]("http://ubuntuforums.org/showthread.php?t=800686") which seems to address exactly the same problem I'm having. (Using lspci, my card comes up as "Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)"). 

However, when I extracted the tarball, it only contained a single readme file, which read: 

[INDENT]You most likely downloaded this tarball since you are looking for a version
of MadWifi which supports the AR5007 chipset family, which is for example
used in the EeePC.

However, since you've downloaded this tarball, you've followed outdated
instructions. The code that this tarball once contained is now obsolete.
Please follow these instructions to enable your AR5007-based WLAN device:
[http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)[/INDENT]

I then cruised on over to [http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192), grabbed the most recent version (here: [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/)). 

It said:
[INDENT]Please use the instructions as in UserDocs/FirstTimeHowTo to compile the code, but substituting the relevant parts for acquiring the source. [/INDENT]
but I'm not entirely sure what this means.

When I use the "make" command from the madwifi directory, it gives me the following error: 
[INDENT]cd: 1: can't cd to /lib/modules/2.6.22-14-generic/build
Makefile.inc:66: *** /lib/modules/2.6.22-14-generic/build is missing, please set KERNELPATH.  Stop.
[/INDENT]

Despite feeling a little frustrated that an ubuntu 'update' would cripple my system, I'm trying really hard and I feel like I'm pretty close to getting this thing working. Any help would be greatly appreciated

Thanks in advance.

---

### Post by gradedcheese on 2008-07-27
It's complaining because you don't have headers for the Linux kernel against which it's trying to compile the driver.  Try:

```

sudo apt-get install linux-headers-`uname -r`

```

And then repeat the 'make' step again.

---

### Post by kvelandia on 2008-07-29
I am having the same problem...well not me, but I installed Ubuntu for a friend and now..well...you know.

I tried using the madwifi-0.9.4. driver...and I followed some instructions, and it was supposed to work after restart. And, well it didn't.

I would like a complete set of instructions. From the very beginning, to be sure I am not messing it up.

---

