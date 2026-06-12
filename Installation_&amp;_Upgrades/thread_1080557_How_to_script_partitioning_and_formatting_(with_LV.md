---
title: "How to script partitioning and formatting (with LVM and crypto)?"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by MountainX on 2009-02-25
I have a complicated partitioning scheme for a server with a lot of disks. The alternate installer requires too many steps to get this done. Is there a way I can script this?

I want to establish a partition that is the PV for LVM on each disk (separate disks). Then I want to use that for an encrypted volume. Then I want to put Ext3 (or 4?) on and format it. 

I want to specify the various options, labels, mount points, etc. in the script for each disk.

Is this a script that would be easy to write and run? I have not done anything like this before. Thanks.

---

### Post by opscure on 2009-02-25
this is definitely possible, but as for easy that would depend on your previous knowledge.

You can create an expect script to launch your programs for partitioning (fdisk, etc) and such and from there you can go through the process of determining what string of text will show right before you need to do some form of interaction.  Expect will allow you to send that interaction without human intervention.

expect manpage is here:
[http://www.manpagez.com/man/1/expect/](http://www.manpagez.com/man/1/expect/)

---

### Post by MountainX on 2009-02-25
expect looks cool. thank you

---

