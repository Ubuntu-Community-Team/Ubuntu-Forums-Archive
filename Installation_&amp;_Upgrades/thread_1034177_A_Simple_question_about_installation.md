---
title: "A Simple question about installation"
date: 2009-01-08
forum: Installation &amp; Upgrades
---

### Post by Dobbie03 on 2009-01-08
I am going to go with ubuntu 100% on my current pc which is running side by side Vista Home Professional and Ubuntu8.10.

To do a complete install and have Ubuntu only is it as simple as formating my hardrive and on reboot inserting my Ubuntu disc?

---

### Post by spcwingo on 2009-01-08
You can also format from the Ubuntu live disc, so no need to format beforehand.  If you need any help on how to set up partitions, don't hesitate to ask.

---

### Post by Dobbie03 on 2009-01-08
Thanks very much for your help. We may have to do it via msn or something,  I am very new to Ubuntu\Linux so any help would be nice.

---

### Post by theozzlives on 2009-01-08
Boot up live  Ubuntu CD/go to system>administration>partition editor/delete your NTFS partition/resize your ext3 partition. That should do it.

---

### Post by kranny on 2009-01-08
Put your Live Cd and wait until your Partition manager prompts.Select Manual Partitioning.Delete your vista partition and format it to ext3,and select the partition on which you should install ubuntu


Method 2:
Just delete the vista partition You have from partition editor(You can found it at System--->Administration-->Partition editor)

Format your ntfs partition to ext3 and edit your menu.lst to delete your vista entries

---

### Post by spcwingo on 2009-01-08
Just don't forget to make a swap partition approx 1.5-2 times the amount of ram installed.;)

---

### Post by Dobbie03 on 2009-01-08
Ok man this is getting pretty technical for me, can someone explain it in simple terms for a simple long term Windows user.

---

### Post by Dobbie03 on 2009-01-08
also I dont see a Partition mamnager do I need to be logged in as an admin and if so how do I do that?

---

### Post by melojo on 2009-01-08
Boot from the ubuntu cd and during the partition part choose to use the entire disk.  It will do everything for you.

---

### Post by Dobbie03 on 2009-01-08
> **melojo said:**
> Boot from the ubuntu cd and during the partition part choose to use the entire disk.  It will do everything for you.

That sounds like the trick, thanks mate.

---

### Post by kranny on 2009-01-08
> **MattDobson said:**
> also I dont see a Partition mamnager do I need to be logged in as an admin and if so how do I do that?

It isnt installed by default..Install it from Synaptic manager(you can find it at System-->Administration--->Synaptic Manager)
find the package "gparted" and install it..And there u go

---

### Post by Dobbie03 on 2009-01-08
Thanks guys I am now 100% on Ubuntu.

Goodbye windows forever!!

---

