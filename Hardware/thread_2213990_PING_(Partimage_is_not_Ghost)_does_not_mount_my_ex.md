---
title: "PING (Partimage is not Ghost) does not mount my external hard drive."
date: 2014-03-29
forum: Hardware
---

### Post by pavelexpertov on 2014-03-29
Hi, I have bought a new laptop and I use its pre-installed hard drive as an external hard drive for back up of my files. When I was done cleaning my laptop for my parents, I decided to create an image so that I could restore Windows if there was trouble, but I got in trouble. My PING does not mount the hard drive for the image to be stored. The hard drive has been fully formatted and turned into NTFS format so that it could avoid bad sectors since it had some. The hard drive works fine. I attached some screenshots of the process while using PING.

In Screen1, I used fdisk and it showed my external hard drive's system/format as GPI EFI rather than NTFS. I remember I formatted it and selected NTFS for it.
[ATTACH=CONFIG]251578[/ATTACH]


In screen2 and Screen4 is usual process and in screen3 it showed a hard drive that I could store an image into.

[ATTACH=CONFIG]251577[/ATTACH][ATTACH=CONFIG]251575[/ATTACH]

In screen3, I get a message saying the drive could not be mounted onto /mnt/dos if I understand it correctly after hitting enter in Screen3. 

[ATTACH=CONFIG]251576[/ATTACH]


I was going to do manual mount in a shell before proceeding, but then I did not know how to restart the process. Can anyone help please?

---

### Post by pavelexpertov on 2014-03-30
Update: I have researched about GUID efi partition table and now I figured out how to onvert it from GUID efi to MBR partition table. Basically I used Windows's Disk manager to do that and you can follow their step by step instructions in Help page by searching guid efi. Hopefully it will help anyone who are facing the same problem.

---

