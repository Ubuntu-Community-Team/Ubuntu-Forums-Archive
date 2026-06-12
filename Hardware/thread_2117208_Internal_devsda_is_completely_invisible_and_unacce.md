---
title: "Internal /dev/sda is completely invisible and unaccessible."
date: 2013-02-17
forum: Hardware
---

### Post by LoneSt4r on 2013-02-17
Hello!

I have been using Ubuntu for years, but this one completely stumps me.  I just installed Ubuntu on a Dell E6510 Latitude laptop and the internal hard disk is completely invisible.  The internal hard disk is the one I run Windows 7 from and is, as far as I can tell, healthy and functional.

Here are a few attempts at accessing the disk I made:

gParted shows /dev/sda as completely unallocated.
[HTML]sudo gparted
[sudo] password for jp: 
======================
libparted : 2.3
======================
Erreur d'entrée/sortie lors de la lecture sur /dev/sda
Impossible d'ouvrir /dev/sda - étiquette de disque non reconnue.
[/HTML]

Those errors translate to "Input/output error while reading /dev/sda" and "Unknown disk label".

hd shows this:
[HTML]sudo hd /dev/sda
hd: /dev/sda: Erreur d'entrée/sortie[/HTML]

fdisk does not even show /dev/sda:
[HTML]sudo fdisk -l

Disk /dev/sdb: 500.1 GB, 500074283008 bytes
255 têtes, 63 secteurs/piste, 60797 cylindres, total 976707584 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique)*: 512*octets / 512*octets
taille d'E/S (minimale / optimale)*: 512*octets / 512*octets
Identifiant de disque*: 0x00038a56

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sdb1            2048   204802047   102400000    b  W95 FAT32
/dev/sdb2   *   204802048   245762047    20480000   83  Linux
/dev/sdb3       245762048   249858047     2048000   82  partition d'échange Linux / Solaris
/dev/sdb4       249858048   976707583   363424768   83  Linux
[/HTML]

[HTML]sudo gdisk
GPT fdisk (gdisk) version 0.8.5

Type device filename, or press <Enter> to exit: /dev/sda 
Warning! Read error 5; strange behavior now likely!
Warning! Read error 5; strange behavior now likely!
Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present[/HTML]

Does anyone have an explanation or a solution to this problem?

Thanks!

---

### Post by oldfred on 2013-02-18
Have you converted drive to dynamic partitions in Windows? 
Was drive ever RAID or Intel SRT as that is also RAID?
Have you recently run chkdsk in Windows?

See if this posts, put in code tags (# in edit menu) to preserve formatting. Just wondering if you have an invalid character in the label field. Does Disk Utility show sda and partitions? That also shows labels  & lets you edit them.

       # To clear cache and get new view:
sudo blkid -c /dev/null -o list

---

### Post by LoneSt4r on 2013-02-18
> **oldfred said:**
> Have you converted drive to dynamic partitions in Windows? 
Was drive ever RAID or Intel SRT as that is also RAID?
Have you recently run chkdsk in Windows?

See if this posts, put in code tags (# in edit menu) to preserve formatting. Just wondering if you have an invalid character in the label field. Does Disk Utility show sda and partitions? That also shows labels  & lets you edit them.

       # To clear cache and get new view:
sudo blkid -c /dev/null -o list

Thank you for your reply!

Windows is "as is" and I did not modify it.  So I didn't convert it to DD, and it is not RAID.  According to the Windows disk management tool, I don't have any label on the Disk 0 partitions.

I will try the blkid command tonight, but since this is a fresh installation and that /dev/sda never showed, I don't have much hope.

Could it be a HDD security feature from Dell that is preventing the disk from being found?

---

### Post by oldfred on 2013-02-18
Some have reported a setting in BIOS just to turn on drive? I would be surprises if Windows works if that setting is off. 
But review of settings in BIOS is a good idea.

Is drive set for AHCI, large or LBA, or IDE? AHCI is preferred but if you not have setting now, you will have to add drivers to Windows before changing it. But drive should not be IDE.

---

### Post by LoneSt4r on 2013-02-18
Hi again,

blkid did not reveal new information.  I had gone through the BIOS settings and did not find anything.  The HDD is configured for ATA.

---

### Post by oldfred on 2013-02-19
I think ATA is just IDE, what other settings do you have.

[http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)

---

### Post by LoneSt4r on 2013-02-19
Thanks! 

The BIOS screen menu is SATA, which is different. It is not PATA or IDE. 

The other option is RAID, but I don't have dual HDD.

---

### Post by oldfred on 2013-02-19
SATA should be ok, but you should also have AHCI somewhere unless it is a very old computer. Is your Dell that old?

Some very old Dell's would only boot from first IDE drive even though they had a second SATA drive. Those SATA drives were SATA I not even SATA II.

---

### Post by LoneSt4r on 2013-02-19
It is the E6510, about 2 years old.  I will look for the AHCI mention somewhere.

---

### Post by LoneSt4r on 2013-02-19
AHCI is also part of the selection.  However, as you said, I would need to install Windows drivers before attempting to make that change...  This is uncharted territory for me.  

Is this a new Ubuntu requirement?  SATA worked fine for me on all of my computers up until now?  Is there any certainty that this setting is what is preventing Ubuntu 12.10 from seeing my internal HDD?

---

### Post by oldfred on 2013-02-19
Users have reported different results. Must vary by vendor or BIOS design. Do not know about your specific model.

       > It was in the BIOS. Under Onboard Devices Settings, the SATA Mode was set to SATA. I changed it to AHCI. Then another  showed up in the BIOS that stated "Change the AHCI DID for Linux to Enabled. I booted to win7 and it loaded some new drivers. I booted to Gpart and glory be there were my hard drives.
   Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.
[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8) post #79
Standard BIOS Settings -> [drive you want to change] -> IDE Access -> &#8220;Large&#8221;, did the trick.

---

### Post by LoneSt4r on 2013-04-28
Hello!

Finally, I did a little more digging and solved my problem using [http://support.microsoft.com/kb/922976](http://support.microsoft.com/kb/922976)

1- Upgraded to 13.04 (you never know) --> no effect
2- Made the BIOS switch from SATA to AHCI --> I could see the drive in Ubuntu, but I received the BSOD trying to boot using Windows.
3- Went back to SATA, booted Windows, then made the changes per the KB link above.
4- Switched BIOS back to AHCI --> Windows booted successfully.
5- Booted back to Ubuntu --> My /dev/sda drive was still available!

In summary, making the KB article changes AND changing the BIOS settings to AHCI did the trick.

Thanks for the tip!

---

