---
title: "Multi-Boot/Installer USB Drive"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by khalis on 2009-06-17
I'm looking to use a small 60GB 2.5" external drive I got years ago as a quick-recovery and installer tool.  I routinely am reinstalling or recovering systems as I mess with things trying to get a better grip on linux.  So I'd like a quick and easy way to recover from it.  I only have one working DVD drive between 5 computers, so CD/DVD's are somewhat of a barrier.

Ideally what I'd like to do is install GRUB on the USB drive along with a full install of Ubuntu Desktop and 5 installers. (Ubuntu Desktop/Server/Netbook Remix, Windows Vista/7)  The problem I'm having is I'm really not sure how to go about setting up the different boot parameters, since I'll probably have to configure GRUB myself.

What would be the easiest way to go about doing this?  Would a separate partition be required for each installer?  From what I understand with making a windows vista bootable USB installer, it essentially comes down to copying the files to a directory and configuring the boot manager on the drive.  So replacing the default windows boot manager with grub should work, correct?

Any help is appreciated.  I wouldn't mind creating a guide on the wiki if this might be useful for others in a similar situation.

On a side note: after both my laptop's dvd drives died, getting a EEE and discarding the dvd drive on my server, this really has become a nuisance with only one drive between 5 computers.

---

### Post by khalis on 2009-06-19
Is it even possible to use Grub in the manner I described?  If someone could at least let me know that there is light at the end of the tunnel I would feel okay dumping more time into it.

Can I drop the ubuntu image files into a directory on a partition and setup grub on that disk with an entry for each installer?  Is it also possible to have grub boot the windows cd installer?

---

### Post by Mighty_Joe on 2009-06-19
A quick search with the google brought up [this page]("http://www.justlinux.com/forum/showthread.php?threadid=150078").  I haven't tried it but it looks plausible.

---

### Post by markbuntu on 2009-06-19
If you put the isos on separate partitions you could maybe grub into them by uuid. I have not tried that so I am just guessing here. 

The link above looks promising but seems very complicated.

---

### Post by khalis on 2009-06-20
Thanks for the suggestions, you got me looking in the right direction.  I think this process will work for me:

[http://www.linuxquestions.org/questions/linux-software-2/booting-of-raw-iso-from-grublilo-though-preferably-grub-367901/#post2931546](http://www.linuxquestions.org/questions/linux-software-2/booting-of-raw-iso-from-grublilo-though-preferably-grub-367901/#post2931546)

To re-iterate, I'd simply create a partition for each disk I want to boot from and "burn" that iso to that filesystem.  Configuring grub to pass the bootloading on to the bootloader from the installer and that's it.

However, I don't know much about GUID partition tables / UUIDs and that seems necessary to continue.  So I've got some research before I move forward.  If I figure out how, I'll try to remember to post it here.

---

### Post by markbuntu on 2009-06-21
You can get uuids by using the command 

blkid

The reason to use UUIDs is that the stick will not always have the same drive number.

---

