---
title: "Easiest way to flash prom"
date: 2008-08-09
forum: General Help
---

### Post by Spark19 on 2008-08-09
Guys,

After some research I agree with the others before me that the easiest way to flash an Ultra1 or any UltraSparc rom is via the net.

Sometimes the linux/ubuntu installation might start well without a flash update to the latest version, but then its something which will always bug you when some thing does not go the way you want it to. You'll always ask yourself, could this be a bug in the flash?

Hey, don't get intimidated, I was too. Flashing the prom over the net is really easy, an actual five minute job. If you feel you dont have a LAN, i am sure you do, but do not recognize it.

For this flash activity you only need an ethernet/wireless router and another intel m/c running 9x/2k/xp anything.

Just connect the two machines to the router like you usually do to connect to the internet.

And on the PC start a tftpd and rarpd servers. 

To do that read this [http://www.smtps.net/netboot_flash_obp.html]("article")


The only things the above article will confuse you on is:

1. You do not need the BillgPC zip file but the rarpd zip files.

2. Once the tftpd is running, u can connect to it and put the flash files there. (the application is a client binary too, so while the server is running you can connect from it as a client from the same machine/window.)

3. When u bring up the sparc m/c and on ok type boot net go look at the log files on the tftpd server. The sparc machine sends out a request for a specific file, named something like C09S21A. Rename the flash update file on the tftp server to this name. 

4. Now shutdown and re boot the sparc with "boot net".

5. This should bring up the flash update stuff.

-s

---

### Post by Spark19 on 2008-08-09
Or flash the rom BEFORE you take the solaris OS off the machine.

Why?

1. Flashing from the hard disk requires the disks to have ufs and solaris installed.

2. Burning from a cdrom and trying to boot cdrom will not work due to the structure differences betwen intel and sparc. The sparc cdrom u burnt will not have the VTOC, slices etc and will give you a Bad Magic number error. Or some disk label missing error.

3. Running from at ext2/3 fs disk will give an execution / loading error.

4. ufs disk with no solaris will give a ... file not executable error.

Believe me i tried all these before a five minute net boot worked.

:lolflag:

---

