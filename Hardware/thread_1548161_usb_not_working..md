---
title: "usb not working."
date: 2010-08-07
forum: Hardware
---

### Post by frozonecom on 2010-08-07
Whenever i attach an external flash drive, i cant see my files on the usb. It doesn't even mount. 

I know that I attached the USB device at the port correctly, cause they are lights on the usb. How can I make my USB work?

---

### Post by varunendra on 2010-08-08
Is it happening with any one particular usb drive or all the usb drives you try?
If it is a particular one, does it work on other computers?

---

### Post by frozonecom on 2010-08-11
im sorry for the late reply, been busy lately. :D

all the usb devices i connect to my laptop, it doesnt work. I dont know why.

---

### Post by varunendra on 2010-08-11
First, make sure the device you are trying is not defective (see if it is working on other computers).
Next, see if it is failing on all the ports (your laptop should have more than one port - right?)

If the device is ok & is still failing on all the ports, then check if USB support is enabled in BIOS of your laptop. If there is an option for 'Legacy USB Support' in the BIOS, try enabling it.

If these don't help, please provide following details:

[LIST]
[*]What is the model of your laptop & how old is it?
[*]Which operating system is installed on it? Please mention if there is more than one.
[*]Did the usb use to work before? Or is it a problem from the beginning?
[*]What are the USB-related options in your laptop's BIOS?
[/LIST]

---

### Post by frozonecom on 2010-08-11
First of all, thank you for helping me. :D

> >The device is not defective. I have tested it on my desktop computer and it worked fine.> >The device did not work on ALL the ports.> >There is no 'Legacy USB Support' in my BIOS.> >I have an Acer Aspire 1681WLMi> >I have it for 2 years from now.> >There are no other OS in this laptop. ONLY ubuntu 10.04.> >The USB worked before when it had Windows XP. Now, when I installed Ubuntu 10.04, I removed(completely) Windows, and now, I have no USB support.> >The only option that my BIOS have is the USB speed(HiSpeed,etc)Hope we can solve this problem. :)

---

### Post by IcarusR on 2010-08-11
If you type in a terminal

```
sudo fdisk -l
```

does it show up there ??

Post output.

Have you tried mounting manually ??

---

### Post by frozonecom on 2010-08-11
The output of 

```
sudo fdisk -l
```

is 
```

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ac0eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7206    57874432   83  Linux
/dev/sda2            7206        7296      728065    5  Extended
/dev/sda5            7206        7296      728064   82  Linux swap / Solaris

```I have the USB device plugged when I did that.

How do I mount it manually?

---

### Post by varunendra on 2010-08-11
Well... your flash drive doesn't even seem to be detected by the OS, so I don't think manual mounting option has any relevance here.

This [thread]("http://ubuntuforums.org/showthread.php?t=1437344") may be interesting for you.
Have you tried updating the system via Update Manager?

---

### Post by frozonecom on 2010-08-12
I did what the people suggests in the thread, but nothing solved my problem.

I installed the package **USB Mount** through Synaptic Package Manager, and still it did not solve it. Got any more ideas? :popcorn:

I also ran an update via **Update Manager** like you said, but nothing changed.

---

### Post by varunendra on 2010-08-12
Since the drive isn't even detected by the kernel, it is either a problem with kernel compatibility (which I thought might get fixed by updating), or is beyond my knowledge.

I'll try to look deeper into this problem as I get time, but for now I'm afraid I may not offer much help.

The only thing I can suggest right now is to try Live CD of a different version like [Karmik]("http://releases.ubuntu.com/9.10/") or [Slax]("http://www.slax.org/") (smaller & useful) and see if the USB works with it.

Even if you want to keep Lucid, testing USB with these may help deciding next step.

---

