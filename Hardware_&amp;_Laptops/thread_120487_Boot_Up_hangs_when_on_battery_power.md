---
title: "Boot Up: hangs when on battery power"
date: 2006-01-21
forum: Hardware &amp; Laptops
---

### Post by harryf on 2006-01-21
Hoping for some advice on where to look (log files etc.) / how to troubleshoot this.

Have a Dell Latitude D800 running Breezy. In general, no problems but when booting up on battery power, it hangs.

The last couple of messages on the (pretty) boot screen are "Enabling Hotplug system" (or similar) then "Initializing ALSA Card 0", which is where it hangs.

Looking in /var/log/messages and /var/log/syslog, there's no record of the failed boot up I can see at all - seems like syslogd starts after the point where the boot hangs.

Any recommendations on how to proceed - I'm only vaguely familiar with Linux boot proceedures and haven't had to troubleshoot it before.

Many thanks.

---

### Post by olddog55 on 2006-01-24
Interesting...

This only happens under battery power?  And when you're on the A/C Mains, everything is OK...?

What kernel and boot options (if any) are you using?
  e.g.  under grub: kernel /vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash

/d

---

### Post by harryf on 2006-01-31
Apologies slowness. Long distraction...

> 
This only happens under battery power? And when you're on the A/C Mains, everything is OK...?


That's right.

What I should also have pointed out is if I boot on A/C mains I can pull out the power and use the battery without any problem - it's only when booting on battery.

> 
What kernel and boot options


```

/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash

```

(It's got multiple partitions on the disk)

---

### Post by harryf on 2006-01-31
OK - back after some reboots. Your post got me to be a bit smarter about booting so via grub came up on;

```

/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro

```

Which told me exactly where it hangs; loading a ndiswrapper driver "bcmwl5a" which is what I use for the wifi card in this laptop. The last message is basically

"ndiswrapper using irq5"

So I guess this an irq conflict.

It's interesting that booting on battery results in different irq use, leading the conflict.

I guess the workaround there will just be to stop loading the ndiswrapper driver until I'm fully booted or not - will be interested to see if that works or not - how irq use will be handled. More if I get there...

BTW: is it worth filing something like this as a bug? I guess ndiswrappers are not really supported.

---

### Post by toorima on 2006-01-31
I had the same problem on my dell inspiron 8600c change boot check (something like that) from simple to thorough in bios, takes 5 sec longer to boot but it works

---

### Post by harryf on 2006-01-31
> 
I had the same problem on my dell inspiron 8600c change boot check (something like that) from simple to thorough in bios, takes 5 sec longer to boot but it works


Interesting. Will have a look at the bios for interest.

In fact just fixed this via a different path (and now booted on battery power) - the solution is [here](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu#If_it_doesn.27t_work) on the ndiswrapper wiki;

> 
With the SMCWUSBT-G (USB) card, it works like a charm by compiling from source the latest version (1.8) (not with the one provided by Breezy) following the provided instructions. However, ndiswrapper may hang if the machine is started with the card plugged in. To avoid this, change line 13 of /etc/init.d/hotplug from

RC_ORDER="pci usb isapnp"

to

RC_ORDER="pci isapnp usb" 


Making that change "fixed it". Quite where loading usb modules fits into being on battery power and having this problem I don't know but it worked.

---

### Post by n0manarmy on 2006-02-10
[QUOTE=harryf]Interesting. Will have a look at the bios for interest.

In fact just fixed this via a different path (and now booted on battery power) - the solution is [here](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu#If_it_doesn.27t_work) on the ndiswrapper wiki;



Making that change "fixed it". Quite where loading usb modules fits into being on battery power and having this problem I don't know but it worked.[/QUOTE]

This actually helped solve the problem i was having. 

I had installed hoary through a floppy/network setup (no cdrom) on my latitude LS, did an apt-get (can't remember the package) to put KDE on the system and then changed my repositories to breezy and did an apt-get dist-upgrade. It started locking at hotplug subsystem so i went into recovery mode and made this change and it fixed it.

---

