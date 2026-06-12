---
title: "unable to mount mp3 player"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by martbab on 2007-06-04
Well, since I have upgraded my Xubuntu to version 7.04 I can't mount my mp3 player. I plug it into an USB port and nothing happens, file managers don't see it. The weird thing is that my USB pen is detected and mounted without problems. I can't figure out what the problem could be. I would be happy if someone could help me :).

---

### Post by Brinstar on 2007-06-04
most likely it's a different filesystem than ubuntu was expecting. i get the same problem but haven't really bothered solving it yet.

---

### Post by martbab on 2007-06-06
> **Brinstar said:**
> most likely it's a different filesystem than ubuntu was expecting. i get the same problem but haven't really bothered solving it yet.

I have noticed that during upgrade my partitions were renamed from hda# to sda#, maybe this is causing the problem...

---

### Post by samcls on 2007-06-07
I have a samsung mp3 player, i couldnt mount it too, but i put this command 
sudo modprobe -r ehci_hcd
 and it works but i have to put this command in everytime i want to mount the mp3 player

---

### Post by Incarnadine on 2007-06-07
Ignore this reply.

---

### Post by zero244 on 2007-10-19
Try this...........open a terminal window and copy and paste this.

sudo rmmod ehci_hcd

It will then ask you for your password.
Password:

Then try and mount your player. This goes away on reboot. I made a launcher on my desktop, so I just double click it when I want to mount my mp3 players.
This works with Edgy and Feisty.......I havent tried it with Gutsy yet.
It seems some mp3 players are seen as scsi drives instead of plain ole flash drives.
This command has worked on all my mp3 players that wouldn't mount before.
Good Luck.

---

### Post by speedsterdm on 2007-10-22
Hey,

I have a 2nd Gen Dell DJ (old, I know, but I love it) and it just won't mount no matter what I do. I tried both of these commands, they don't seem to do anything. Sometimes i will get an error with the sudo rmmod ehci_hcd command:

ERROR: Module ehci_hcd does not exist in /proc/modules

Any ideas? Maybe it would work with Gutsy? Right now this is one of the only reason why I am keeping my Vista partition alive :(. Help appreciated!

---

### Post by shareMenaPeace on 2007-11-02
> **zero244 said:**
> Try this...........open a terminal window and copy and paste this.

sudo rmmod ehci_hcd

It will then ask you for your password.
Password:

Then try and mount your player. This goes away on reboot. I made a launcher on my desktop, so I just double click it when I want to mount my mp3 players.
This works with Edgy and Feisty.......I havent tried it with Gutsy yet.
It seems some mp3 players are seen as scsi drives instead of plain ole flash drives.
This command has worked on all my mp3 players that wouldn't mount before.
Good Luck.

Thank you, works with AEG MMS 4210 2gb :)
(Before this the device got unmounted when trying to copy mp3 to it.)

Thanks!

---

