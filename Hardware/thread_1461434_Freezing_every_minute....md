---
title: "Freezing every minute..."
date: 2010-04-24
forum: Hardware
---

### Post by argos3016 on 2010-04-24
dmesg output:

[  886.215222] ata1.00: status: { DRDY ERR }
[  886.215232] ata1.00: error: { UNC }
[  886.236569] ata1.00: configured for UDMA/133
[  886.236606] ata1: EH complete
[  891.129301] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  891.129319] ata1.00: BMDMA stat 0x25
[  891.129352] ata1.00: cmd c8/00:08:cf:f4:12/00:00:00:00:00/e0 tag 0 dma 4096 in
[  891.129358]          res 51/40:00:d2:f4:12/00:00:00:00:00/e0 Emask 0x9 (media error)
[  891.129373] ata1.00: status: { DRDY ERR }
[  891.129384] ata1.00: error: { UNC }
[  891.156610] ata1.00: configured for UDMA/133
[  891.156654] ata1: EH complete
[  922.670393] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 256

and a lot of time more...

palimpsest says that i have 553 bad sectors.
make a fsck? how?
apocalypsis? Help, please!:(

---

### Post by argos3016 on 2010-04-24
I've noticed that when I open any program that uses flash (either firefox or totem) is when the computer freezes (about 5 seconds.) It is because the flash libraries are in a bad sector?

[LEFT][IMG]http://www.google.es/images/cleardot.gif[/IMG][/LEFT]

---

### Post by argos3016 on 2010-04-24
Now I've discovered that it seems that the partition (or hard disk readable limits) do not fit with the 160 GB total should have. Also, dmesg "says" I have a "DDRY error"

---

### Post by termin on 2010-04-24
im sorry to tell you this, but you'll have to reinstall Ubuntu and say "erase and use entire hardrive" as your option. its a corrupted drive, i use to have one just be sure to back up before you reinstall(if you can)

---

### Post by argos3016 on 2010-04-24
Begin to be afraid. Well, googling, I discovered that there are not (in any forum of ubuntu or even linux) anyone who has given a real solution to the (now famous) "ata1.00", "(UNC)" or " DDRY." One solution would be to download the manufacturer's tool, Seagate, functioning only in * indows (personally, I do not want to go to the "dark side "...). In summary:
-It's a physical error or just software? As I can know?
-I'm wasting my time? Should I buy a new one?
-I should (embarassing...) go to the" dark side "TEMPORARILY?

Please check the attachments...

---

### Post by argos3016 on 2010-04-24
> **termin said:**
> im sorry to tell you this, but you'll have to reinstall Ubuntu and say "erase and use entire hardrive" as your option. its a corrupted drive, i use to have one just be sure to back up before you reinstall(if you can)
To answer your question, fails even having done that ... I'm going back to, just in case ...

---

### Post by argos3016 on 2010-04-24
See...

---

### Post by 2hot6ft2 on 2010-04-24
> **argos3016 said:**
> 
make a fsck? how?

To safely run fsck use
```
sudo touch /forcefsck
```
and on the next reboot it will start the fsck checking like if it had reached 30 boots.

Any time you want to force the system to do a fsck, give the above command and reboot.

Sounds like your problem goes even deeper like you said though. I don't have a solution for it. I stopped buying Seagate drives years ago. Warranty it out if you can and tell them you're aware of the problems with that model and would like another model if at all possible.

---

### Post by argos3016 on 2010-04-25
Well, the computer takes all night with the last command "fsck -f -v -y /dev/sda." And not for printing:
"Error reading block ******* (Attempt to read block from filesystem resulting in short read) while reading inode Indirect blocks of ******* Ignore error? Yes

Force rewrite? yes "
I suppose it is fixing ...
I read in this thread [http://ubuntuforums.org/archive/index.php/t-1135021.html](http://ubuntuforums.org/archive/index.php/t-1135021.html)

---

### Post by argos3016 on 2010-04-25
ubuntu@ubuntu:~$ uptime
 07:57:49 up 12:35,  9 users,  load average: 2.42, 2.43, 2.28

The longest LiveCD session that I've ever done!

---

### Post by argos3016 on 2010-04-25
> **2hot6ft2 said:**
> To safely run fsck use
```
sudo touch /forcefsck
```and on the next reboot it will start the fsck checking like if it had reached 30 boots.

Any time you want to force the system to do a fsck, give the above command and reboot.

Sounds like your problem goes even deeper like you said though. I don't have a solution for it. I stopped buying Seagate drives years ago. Warranty it out if you can and tell them you're aware of the problems with that model and would like another model if at all possible.

The computer has only one year and little...

---

### Post by P4man on 2010-04-25
Looks like a bad harddrive to me. Doesnt matter how old it is (well it does for warranty), drives fail, thats a fact of life. Try running disk utility from system > administration and report the smart status.

---

### Post by argos3016 on 2010-04-25
Palimpsest says:
DISK HAS MANY BAD SECTORS.
Please backup all data and replace the disk

---

### Post by P4man on 2010-04-25
So backup your data and replace the drive :)

---

### Post by P4man on 2010-04-25
BTW, if you have data on that drive that you havent been able to back up yet, here is a trick: put the drive in a sealed bag and put the bag in the freezer for several hours (im not joking). Reinsert the drive and try copying your data as fast as you can before it heats up again. This usually works (for a short while) if its a mechanical failure inside the drive.

---

### Post by argos3016 on 2010-04-25
But, I can't repair it?
What means :

infinite - (joke)

Error reading block 11370848 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 11370849 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 11370851 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 11370852 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Error reading block 11370853 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

infinite + (joke)

---

