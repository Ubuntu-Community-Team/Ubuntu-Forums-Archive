---
title: "thinkpad t410 partitioning question ......."
date: 2010-09-08
forum: Hardware
---

### Post by Immolatus on 2010-09-08
I'd like to install Ubuntu on a new Thinkpad t410. I know however that there is a recovery partition and i need to know if I can just leave it alone. I was reading a snippet of an Arch forum post that said not to install grub to the MBR for some reason. 

Any thoughts??

---

### Post by stickyfoot on 2010-11-16
I'm looking in to exactly the same thing currently.

From reading around it seems to be suggested that you can create extended partitions and let grub do its usual installation thing. You can then edit grub to add the recovery partition to the list that shows up so you can still access it should you need.

There's a thread discussing it with a screenshot from someone who has got more partitions than I imagined possible here: [http://ubuntuforums.org/showthread.php?t=1580706]("http://ubuntuforums.org/showthread.php?t=1580706")

There's also some information on the Lenovo support site that describes what to do if the recovery partition becomes hidden after installing Linux here: [http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-46088]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-46088")

It would be great if someone could confirm they have successfully done this with their T410.

---

### Post by jlh68 on 2010-11-16
I have an Acer TimelineX and I just made the W7 partition smaller using gparted, Then I used the Ubuntu install CD and installed using manual partitioning.  I like to have a separate **/home** partition.

Ubuntu will take care of it and you will then get a B/W grub boot screen with Ubuntu as defaul OS and operators choice to cursor down and boot W7.

My laptop will now boot either Ubuntu or W7 without problem.

Actually there are 3 windows partitions: one is the restore that you copy to DVD, the second is the windows boot loader, and the third is the W7 OS and data partition.  Windows only sees the OS, while a Linux OS will see all three.

---

### Post by kleskjr on 2010-11-16
format worked excellent for me :guitar:

---

### Post by stickyfoot on 2010-11-16
> **jlh68 said:**
> I have an Acer TimelineX

Thanks for the replies.

I don't think I've been clear enough about my question.

I've partitioned and installed Linux on a range of machines but Lenovo ThinkPad's have got a recovery partition which is booted if you press the ThinkVantage button while starting the machine.

Research suggests that it is okay to install Ubuntu as normal but the ThinkVantage button for recovering a damaged Windows install won't work anymore. Instead you need to edit your grub config file to show it as an option in the menu.

Can anyone confirm that this has worked on a modern ThinkPad (preferably a T410)?

---

