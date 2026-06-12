---
title: "problem connecting two external hard drives"
date: 2008-11-30
forum: Hardware
---

### Post by TxAg2011 on 2008-11-30
Hi, I'm running Ubuntu Intrepid on a Dell XPS M1710 and recently made the switch to this form vista. So far everythings working well except I can't find any information on getting my two external NTFS format hard drives to work.

Ones a free agent 250 GB thats hooked in through a USB. The other is a Western Digital Terabyte that i can hook in through either USB or an eSATA expansion card.

now from what I understand, most notebook expansion cards don't play nice with linux distros, so i've given up trying to find a driver to get the card working with this. So when i go to plug either hard disk in via USB, I get the following messages

1st one
Unable to mount EXTR HDD 1
> DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Second one
Cannot mount volume
Unable to mount the volume 'EXTR HDD 1'.
> $LogFile indicates unclean shutdown (0,0) Failed to mount '/dev/sdb1': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs-3g /dev/sdb1 /media/EXTR HDD 1 -o force Or add the option to the relevant row in the /etc/fstab file: /dev/sdb1 /media/EXTR HDD 1 ntfs-3g force 0 0

I've had a few friends who've used ubuntu for an umber of years and they don't have a lcue on how to resolve this. I've tried doing the force mount options and a few other things to no avail.

what else can i do short of getting a friend's computer running windows, dumping everything onto their disks then using drop box to send every single file to the ubuntu box?

---

### Post by TxAg2011 on 2008-11-30
bump. seriously, does no one have an idea on how to remedy this? i've gone through countless threads here and elsewhere and haven't made any headway in resolving my problem.

---

