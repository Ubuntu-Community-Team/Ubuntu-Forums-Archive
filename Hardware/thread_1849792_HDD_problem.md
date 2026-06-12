---
title: "HDD problem"
date: 2011-09-25
forum: Hardware
---

### Post by m@n4ever on 2011-09-25
First of all i had KDE 4 full monty installed on my pc but after using it for 3 days, and installing a lot of updates on it, it just couldn't start and a lot of errors appeared on the screen every time i tried to boot. I decided to reinstall my OS but i also wanted (and still want) to keep my /home partition. When i start installing KDE 4 full monty it says that i have a hardware problem (it can't find my HDD even thought my bios recognizes it), so i opened my pc and reattached (changed the slot) the cable that connects the HDD with the motherboard and tried installing KDE 4 full monty once again, but it reported the same problem. So i tried installing Ubuntu LTS 10.04 (without formatting the /home partition) but that failed too. When i pressed quit, the Live CD started so i tried to open my old /home partition but it said:
 
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
SO I STARTED THE TERMINAL AND THIS IS WHAT I GOT AFTER TYPING dmesg | tail :

ubuntu@ubuntu:~$ dmesg | tail 
[ 2184.146967] Buffer I/O error on device sr0, logical block 352115
[ 2190.164199] sr 3:0:0:0: [sr0] Unhandled sense code
[ 2190.164202] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2190.164206] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 2190.164211] sr 3:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[ 2190.164216] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 5f 72 00 00 02 00
[ 2190.164226] end_request: I/O error, dev sr0, sector 1408456
[ 2190.164230] Buffer I/O error on device sr0, logical block 352114
[ 2190.164234] Buffer I/O error on device sr0, logical block 352115
[ 2288.614972] EXT4-fs (sda5): unable to read superblock
 
PS: I have always used windows, but i wanted to try and learn something about pclinuxos so i installed it and i was satisfied with wath it had to offer but i must have messed something up because i have never used it before or maybe its just my 2.5 years old pc saying "You overplayed me !" :). Anyhow please help me because i don't want to pay someone to repair it because i'm a little bit thin on cash and also i don't want to lose what i have on the /home partition.

---

### Post by ajgreeny on 2011-09-25
From your live CD run ```
sudo e2fsck /dev/sda5
``` and see if it finds errors and tells you how to fix them.  That may be all that is needed.

---

### Post by m@n4ever on 2011-09-25
This is what i got:

ubuntu@ubuntu:~$ sudo e2fsck /dev/sda5
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda5: clean, 19579/28033024 files, 13944338/112114792 blocks

And once again i have no idea what is wrong. Btw thank u for helping me ajgreeny.

---

