---
title: "Fresh install XP / Ubuntu Dual boot:  Need advice"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by dptulk on 2009-01-12
I am planning on reinstalling XP on my desktop at work.  I would like to experiment with ubuntu in my work environment so I think I should do a dual boot.

Questions:

Should i install XP first and partition the disk from the xp install or should I install ubuntu first and partition from there?

I have a 250GB drive in it, I thought it would make sense to partition 80 for each OS and use the leftover for storage that is accessible to both.  How should the leftover space be formatted?  My assumption is that NTFS is not friendly with Linux.

Is there software that I need to set up get the dual boot option?

Thanks for the help,
Dave

---

### Post by kranny on 2009-01-12
Either way it works..

-->Insert a Xp cd and create two 80 gb partitions (one for xp and the other for ubuntu)
-->Install Xp
--->Now pop up your ubuntu live cd and install Ubuntu
--->At the partition setup select the second 80 gb partition as the root partition.
--->You dont need to explicitly install any software for dual boot...Linux comes with bootloader called grub which takes care of everything for you

---

### Post by Partyboi2 on 2009-01-12
>  How should the leftover space be formatted?  My assumption is that NTFS is not friendly with Linux. Ubuntu can read/write to NTFS so creating a NTFS partition to use between the 2 will work.

---

### Post by kranny on 2009-01-12
@Partyboi2
Why icant i see the dangers of rm command page
[http://ubuntuforums.org/announcement.php?a=54..I](http://ubuntuforums.org/announcement.php?a=54..I) get a vbulletin message

---

### Post by Partyboi2 on 2009-01-12
> **kranny said:**
> @Partyboi2
Why icant i see the dangers of rm command page
[http://ubuntuforums.org/announcement.php?a=54..I](http://ubuntuforums.org/announcement.php?a=54..I) get a vbulletin message
Thanks for pointing this out, I would have never known if you had not pointed it out. I have now changed my sig.

---

### Post by frost151n on 2009-01-12
If it's a Work comp. you're experimenting on i suggest the wubi method.

Load the Ubuntu CD in Windows and select the Install Ubuntu Inside Windows option.

You can do a full install once you're more sure about what you're doing.

---

### Post by dptulk on 2009-01-12
Thanks all.  I ended up jumping right into it instead of favoring caution.  I installed Vista first and got some of my work done then I moved on to Ubuntu. while I was going through the setup, I ran into questions in the partitioner and ended up googling the answer within the install (live install is brilliant!)  Anyway, for any other noobs who are looking for the step-by-step, I used this: [http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2)

I was installing 8.10 but it still worked like a charm.

Now it's off to configuring stuff...

Regards,
Dave

---

