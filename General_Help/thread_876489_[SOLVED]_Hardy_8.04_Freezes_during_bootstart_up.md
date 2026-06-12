---
title: "[SOLVED] Hardy 8.04 Freezes during boot/start up"
date: 2008-07-31
forum: General Help
---

### Post by joynoiseprod on 2008-07-31
Have done a fairly thourough search through the forums and I'm totally stuck.  I ran the updates about 4 days ago, and have added a 256mb stick of ram.  I dual boot Win2k and Ubuntu.  Ubuntu is on a second drive.  Use grub to boot.  If I boot 2.6.24.19-rt then it stops at "Starting Samba" and nothing works.  The keyboard doesn't work, and I have to turn off the box with the power switch.  I can boot to "single user mode" or 2.6.24.19 (recovery)  and I can do the following in there.

In /var/log/messages the last messages are:

The program 'cupsd' uses the Apple Bonjour compatibility layer of Avahi.
and
audit (1217510045.423:2):type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5211 profile="/usr/sbin/cpsd" namespace="default"

If I do a dmesg | grep -i error  all I get back is about the ACPI not able to find /DSDT.aml

The are no new logs for samba in the /var/log/samba

I have tried to turn swap off, using:
swapoff /dev/sdb5
mkswap /dev/sdb5
update-initramfs -u

When I run swapon -s I get

Partition         Size          Used     Priority
/dev/sdb5       1510068          0         -1

So I've hit the wall with what I know or where to look further.  

I added 256mb to a 512mb system,.. but from the stuff I've read,.. the swapfile doesn't have a hard/fast rule to it's size.  So I'm not sure wy adding ram would be an issue, and I don't see anyone raising an issue regarding the latest updates locking up their system on boot.

Can anyone offer advise/suggestions on where to go from here??

---

### Post by cprofitt on 2008-07-31
You are not using a FoxCon motherboard are you?

---

### Post by collinp on 2008-07-31
> **indigo196 said:**
> You are not using a FoxCon motherboard are you?

I am worried about the same thing. Foxconn motherboards, as most of us know from the thread, are having problems with Linux ACPI tables in the bios. There is no official fix from Foxconn as of yet, but I believe they are working on one.

---

### Post by joynoiseprod on 2008-07-31
Sorry, forgot that bit,.. 

I have an AMD64 3200+ with an FIC K8-800T MLB.  I'm running the 32bit Ubuntu though, not the 64bit.

---

### Post by linux_tech on 2008-07-31
Did you try disabling ACPI yet?

---

### Post by joynoiseprod on 2008-08-01
Nope, but it was a good suggestion.  A friend of mine I hadn't been able to get a hold of read your suggestion and gave me the command to add that into the grub startup, and sure enough,. it worked.  added the noacpi and the other one I can't remember now, and that worked.
No idea why that all of a sudden became an issue,.. but it's working now,.. Using Firefox in my Ubuntu to reply!

Thanks for the help,.. really appreciate it.

:guitar:

---

