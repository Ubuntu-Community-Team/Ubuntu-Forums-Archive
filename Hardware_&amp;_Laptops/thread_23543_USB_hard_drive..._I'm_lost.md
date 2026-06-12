---
title: "USB hard drive... I'm lost"
date: 2005-04-02
forum: Hardware &amp; Laptops
---

### Post by gw90se on 2005-04-02
Okay, I have an external 3.5" hard drive in a USB case. It's an 80GB that I use for backups. I will use this on my Ubuntu machine and my wife's Windows XP machine for backups. When I plug it into my Ubuntu box, it is recognized and I can copy files off of it, but it is labeled as a read-only drive, so I can't write to it. I was trying to research this issue before I asked for helped, but I got even more confused. One thread led me to beleive that this was due to it being formatted as a Windows fat drive. Is this so? How can I have this drive writeable by both Ubuntu & Windows. We back up music and family pictures to it.

TIA

---

### Post by Whiffle on 2005-04-02
FAT shouldn't be a problem to write.  My camera (USB) and my 20 gig firewire are fat32 formatted and they work just peachy.  Are you sure its not ntfs formatted?  If so (as far as I know), ntfs isn't writable.

---

### Post by Zwack on 2005-04-02
I have the same issue with my MP3 player/flash drive.  It mounts as read only, I had problems with it in Warty (It wasn't worth trying to use).  My other USB flash drive worked perfectly in Warty and mounts RW in Hoary.  

Is it an issue with the USB drive rather than the driver?

Z.

---

### Post by Zwack on 2005-04-02
Hmmmm.... It works as well under hoary as under Warty (The lock button doubles as write protect and I hadn't noticed) but I get hordes of error messages...

Oh well...

Z.

---

### Post by gw90se on 2005-04-02
Good catch, Whiffle.  =D>   It is ntfs formatted. Don't know why I was thinking it was fat. I hooked it back up to the XP to reformat and the only option I had was ntfs. So, I guess I'll figure out another way to format it.

---

### Post by mthaddon on 2005-04-04
[QUOTE=Zwack]I have the same issue with my MP3 player/flash drive.  It mounts as read only, I had problems with it in Warty (It wasn't worth trying to use).  My other USB flash drive worked perfectly in Warty and mounts RW in Hoary.  

Is it an issue with the USB drive rather than the driver?

Z.[/QUOTE]

Did you ever get this resolved (the mp3 issue) - I have the same with my current mp3 player in Hoary.

Thanks, Tom

---

### Post by Zwack on 2005-04-07
Not yet... 

Mine is definitely using FAT, but it doesn't have a partition table.   Instead it turns up as /dev/sda not /dev/sda1.

I'm using my wife's windows machine for the moment.  When I've got an idle few hours I'll try and track down more info/debug/... but for the moment it can wait.

Z.

---

