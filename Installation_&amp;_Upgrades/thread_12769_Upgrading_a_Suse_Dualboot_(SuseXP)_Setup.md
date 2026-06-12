---
title: "Upgrading a Suse Dualboot (Suse/XP) Setup"
date: 2005-01-26
forum: Installation &amp; Upgrades
---

### Post by nzjrs on 2005-01-26
Hey everyone,

Well i have been recommended Ubuntu on good authority by a friend, so now I am going to install it this weekend. I currently am running Suse 9.2 dual boothing with windows.

On my system drive (200gig) I have 
NTFS partiition for windows
FAT32 partition for storage
Linux Ext3 partition for suse
Linux Swap partition 

And grub boots up by default with a nice boot menu to choose suse and XP

I am just wondering what to expect when I install Ubuntu - will i be able to format the linux partitions without having to repartition my drive and risk killing my windows installation?

Will ubuntus boot menu go over the current grub one provided by suse?

Will everyting go smoothly - ish?  Is there anything i should remember?

Alternatively do you think I should just use partition magic to delete the linux partitions first?

---

### Post by rudi on 2005-01-26
> I am just wondering what to expect when I install Ubuntu - will i be able to format the linux partitions without having to repartition my drive and risk killing my windows installation? 
   --> Yes, no problem
     > Will ubuntus boot menu go over the current grub one provided by suse? 
   --> Yes, on default
     > Will everyting go smoothly - ish?  Is there anything i should remember? 
    --> Remember your partition numbers,  don't accidentally erase your windows
    >  Alternatively do you think I should just use partition magic to delete the linux partitions first?
   --> neh [img]http://www.ubuntuforums.org/images/smilies/icon_wink.gif[/img]

---

### Post by rh6866 on 2005-01-26
[QUOTE=nzjrs]Hey everyone,

Well i have been recommended Ubuntu on good authority by a friend, so now I am going to install it this weekend. I currently am running Suse 9.2 dual boothing with windows.

On my system drive (200gig) I have 
NTFS partiition for windows
FAT32 partition for storage
Linux Ext3 partition for suse
Linux Swap partition 

And grub boots up by default with a nice boot menu to choose suse and XP

I am just wondering what to expect when I install Ubuntu - will i be able to format the linux partitions without having to repartition my drive and risk killing my windows installation?

Will ubuntus boot menu go over the current grub one provided by suse?

Will everyting go smoothly - ish?  Is there anything i should remember?

Alternatively do you think I should just use partition magic to delete the linux partitions first?[/QUOTE]

You shouldn't have any problems....  You may be able to even keep Suse on your system.  That being said, I make no guarantees and YMMV.  I'm a nug at linux and may have just got lucky with this.

Here's what I've done that worked without a hitch.

HD1 40gig
20G for WinXP Pro (NTFS) first OS installed
20G for Ubuntu (ext3 + swap) last OS installed

HD2 80gig
2gig for WinXP's Page/Swap file (NTFS) I had the room and the time......
38gig for WinXP's Apps and Data (NTFS) I load all programs into this partition as well as some data.  Most of my data is kept on an external 160gig HD attached to my server.
40gig  for Novell Linux Desktop 9 (ReiserFS) second OS installed

I hadn't planned on keeping the Novell Linux on my PC.  But durring the Ubuntu install I noticed the extra 20gig part on HD1 that I had forgot about.  I decided to go ahead and install Ubuntu on that partition, not caring if I could access the Novell Linux afterwards.

When I installed the Novell Linux I used Grub as the boot loader and did so again when I installed Ubuntu.  Grub has not only picked up the WinXP partition but the Novell Linux as well.  I can get into both systems after selecting them from the Grub menu without issue, just as if there was no other OS loaded on the box.

I was shocked to see this happen as I had always heard horror stories about trying to dual boot two linux systems.

Has anyone else seen this before?  Or am I just todays freak of nature?

Rick

Quick edit:  I forgot to tell you that you may be able to boot your Suse disk and use it to shrink you Win partition.  I don't know if it will shrink any of your partitions/slices that are setup already for Suse but I've used it before to make room on a HD for Suse itself.

---

### Post by rudi on 2005-01-26
[QUOTE=rh6866]
 When I installed the Novell Linux I used Grub as the boot loader and did so again when I installed Ubuntu. Grub has not only picked up the WinXP partition but the Novell Linux as well. I can get into both systems after selecting them from the Grub menu without issue, just as if there was no other OS loaded on the box.
 
 I was shocked to see this happen as I had always heard horror stories about trying to dual boot two linux systems.
 
 Has anyone else seen this before?  Or am I just todays freak of nature?
 
 Rick[/QUOTE]
 Wow, i tried a dualboot with Slackware and Archlinux once, i still have nightmares once in a while [img]http://www.ubuntuforums.org/images/smilies/icon_eek.gif[/img] I haven't tried Ubunto for that long, maybe two weeks now, but i must say i am impressed by the way it handles hardware, packages and the speed/ responsiveness is also awesome. Perhaps Grub has matured, or the Ubunto guru's have used their magic on it

---

