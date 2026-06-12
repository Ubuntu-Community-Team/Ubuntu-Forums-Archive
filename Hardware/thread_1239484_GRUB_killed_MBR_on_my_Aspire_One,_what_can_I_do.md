---
title: "GRUB killed MBR on my Aspire One, what can I do?"
date: 2009-08-13
forum: Hardware
---

### Post by miguelavin on 2009-08-13
Hi people, hope you can give me a hand with this one:

Here goes:
I Installed UNR on my aspire One D150-1920 which comes with windows XP out of the box. Everything worked fine. I was happy, if a little curious about why GRUB labeled the factory recovery partition of my acer as "Windows Vista Loader".

Then I lent my little laptop to a coworker, and all hell broke loose. While using XP he could not get onto a wireless network and figured that maybe things would be better if he booted onto Windows Vista. Neddless to say, there's no such thing as vista on my HDD, Grub sort off booted onto an XP recovery partition.

Laptop reboots, goes into a comma, Grub throws an error 22.

No problem, I think. I'll boot onto the UNR flash drive I keep handy, go to the partition thingamajig and sort things out manualy. Big surprise: No matter what option I choose (try ubuntu without installing, check disk for errors, install ubuntu), I get the ubuntu progress bar and then !BAM! I'm sent to an (initramfs) prompt.

What the hell happened? Has anyone else gotten this error? As far as I know error 22 means a partition has been deleted. In all honesty It seems  silly to have GRUB give you an option that disables the computer but oh well... >_<

What sould I do?

---

### Post by miguelavin on 2009-08-13
!BUMP!

[IMG]http://www.breaktaker.com/albums/pictures/signs/Bump.jpg[/IMG]

---

### Post by Ranax on 2009-08-13
What does it say just before the initramfs prompt?

---

### Post by miguelavin on 2009-08-13
Ok... It says:

|||||||||||||||||
[            4.606544]   IO APIC resources could not be located.
Loading, please wait...


BusyBox  v1.10.2 (Ubintu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
||||||||||||||||

Another funky thing:
if I type "exit" it comes back with:

||||||||||
cp: could not create '/root/var/log/' : No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.

BusyBox  v1.10.2 (Ubintu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
||||||||||||||||

I'm at a loss as to what is going on. :'(

---

### Post by Ranax on 2009-08-14
This seems to be a bug in the kernel Jaunty uses as every other modern Ubuntu distro runs great from a flash drive. I can only suggest waiting until Karmic UNR comes out.... :(

---

