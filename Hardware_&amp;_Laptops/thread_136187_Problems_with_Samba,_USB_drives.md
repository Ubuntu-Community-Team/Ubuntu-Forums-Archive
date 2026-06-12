---
title: "Problems with Samba, USB drives"
date: 2006-02-25
forum: Hardware &amp; Laptops
---

### Post by schatz on 2006-02-25
Hi,
Here a description of what I was intending to do:
1) I have some PCs with Windows XP, and a radio able to play audio streams.
2) I installed Ubuntu on an "old" PC, and the intention was to have it as a file and streaming server.
3) In order to be sure that I don't loose any data if the "old" PC crashes, I want to have my data stored on on external USB mounted drives. Currently I use the external drive to make backup of my PC data. 

So I did the following:
1) Installed Ubuntu, works fine, I'm really impressed how easy things have changed since my Solaris days. 
2) Installed Samba, and after some configurations of the /etc/smb.conf I could read and write at the PCs from a /home/public folder exported via Samba. No user protection, no passwords, simply set it to  = share. The time to write and read data to/from the "old" PC internal drive is OK. All computers are at a wired 100Mbps LAN. It's click and the folder on the Ubunut "old" PC expands. 
3) Then I installed the USB external drive on the Ubuntu "old" PC. The drive is formatted as FAT32, and it contained the backup data from the PC. On the PCs the drive works fine. 
4) The USB drive did not appeared as an icon. I thought, well may be the "old" PC might be having some problems with the USB controller. So I started to "dig" around. "sudo fdisk -l" has shown that there was a device at: /dev/sda1, but it was not mounted on /media. I can mount it with "sudo pmount /dev/sda1 /media/sda1" but not with "sudo mount /dev/sda1 /media/sda1". If i try the mount without the "p" I get an error message.
5) As mounting by hand is not really practical, as the "old" PC is in the basement, and the computers are on the 2nd floor, I added to the /etc/fstab the follwing line:
/dev/sda1 /media/sda1     auto    defaults     0     0
6) after rebooting the USB disk appears at the desktop as a sda1 icon. I can read and write on teh folders of sda1.
7) I changed the Samba configuration to share the /media/sda1, instead of the /home/public folder. And then the problems started. 

My problems:
a) I can only access the files and folders at /media/sda1 when I'm logged on the Ubuntu "old" PC. Trying to access the folder from Windows after a boot of the Ubuntu "old" PC ends with a timeout. 
b) Answer times are very, very, long. It takes about 20 seconds to show the content of folders of the USB external disk (connected to the Ubuntu "old" PC) on the windows PC.
c) I cannot write on the folders from the PCs, I can only read from them.

I have the impression I'm running in problems with access rights as the sda1 appears having only dxrw--xr--xr access rights. Maybe also some form of timeouts, but I have no idea of where to start looking for the problems. I tried some "sudo chown 777 /media/sda1/data" but it didn't work. Any idea what could be wrong.

---

