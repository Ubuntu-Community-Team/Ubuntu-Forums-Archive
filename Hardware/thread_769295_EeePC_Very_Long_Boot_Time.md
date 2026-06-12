---
title: "EeePC Very Long Boot Time"
date: 2008-04-26
forum: Hardware
---

### Post by davejrice on 2008-04-26
Hi all,

I've got Hardy working nicely on my Eee - everything is now working!

Trouble is it takes ages to boot!  Here is the culprit output from dmesg:

```

<snip>
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 630.082 MHz processor.
[  204.722892] Console: colour VGA+ 80x25
[  204.722901] console [tty0] enabled
<snip>

```

everything else seems to be fine - no failures and no other long gaps in the timeline. All configs are standard, no other software installed yet - just the eee-acpi and eee.ko modules in.
 
suggestions?

EeePC701 (black) 2gb RAM - no other mods - Ubuntu Hardy 8.04

cheers

---

### Post by davejrice on 2008-04-26
OK i got a work around.

It seemed to be stalling on the detection of the USB Card Reader.  Taking the card out fixed the hang - but then fstab complained it couldn't find the entry.

I read somewhere there is a problem with the kernel logger on hardy - thinking about that i started playing with the boot options.

booting with nosplash made no difference - however booting with the 'quiet' option removed solved the problem completely.

The boot process does appear on the splash screen - not a big issue.

So whatever is running the 'quiet' option is broken for the eee at least.

What looks after the 'quiet' option? and is it a bug known or unknown?

cheers

---

### Post by reh4c on 2008-05-01
Based on your installation success, can you help these folks with the ubuntu eee distro that's being developed?
[http://ubuntu-eee.tuxfamily.org/index.php5?title=Main_Page](http://ubuntu-eee.tuxfamily.org/index.php5?title=Main_Page)
Thanks!

---

### Post by davejrice on 2008-05-01
Always happy to help - any idea what sort of thing they are looking for?

I've had a quick look at the site (i'm at work at the min - on my hardy eee ;) )

looks like a great idea!

cheers

---

