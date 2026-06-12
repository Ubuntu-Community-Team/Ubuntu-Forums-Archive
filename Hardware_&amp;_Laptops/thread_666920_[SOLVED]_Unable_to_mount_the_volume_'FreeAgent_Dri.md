---
title: "[SOLVED] Unable to mount the volume 'FreeAgent Drive'."
date: 2008-01-13
forum: Hardware &amp; Laptops
---

### Post by Pandemic187 on 2008-01-13
Hi all,

I have a Seagate FreeAgent Drive. It has worked before in Ubuntu, but for some reason I'm getting an error message. I'm not sure exactly what the problem is, but this is the whole message:

Cannot mount volume.

Unable to mount the volume 'FreeAgent Drive'.

Details:
$LogFile indicates unclean shutdown (0, 0) Failed to mount '/dev/sbd1': Operation not supported Mount is denied because NTFS is marked is marked to be in use. Choose an action: Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choice 2: If you don't have Windows then you can use the 'force' option for you own responsibility. For example type on the command line: mount -t ntfs-3g /dev/sdb1 /media/FreeAgent Drive -o force Or add the option to the relevant in the /etc/fstab file : /dev/sdb1 /media/FreeAgent Drive ntfs-3g defaults,force 0 0

It seems this error may have been caused by an unsafe removal in Windows, but I'm not sure. I also haven't tried it in Windows since having got this message in Linux, so I may have to try that. Otherwise, does anyone have any suggestions?

---

### Post by 2manydrugsago on 2008-01-21
I have the same exact issue. Its usually cause my seismic activity on a miniature scale. In other words If you look at these things wrong the break. I dont have a windows system  but I have tried the first command in the error details and it gave me the finger. I haven't tried adding the thing in the /ect menu  cause I don't understand it. Hopefully some one will help both of us with a  way to mount it or at least some one from willitblend.com offering to help.

---

### Post by epud on 2008-01-21
What happens is that your harddrives go in a sort of harbination mode. When they do and you try to bring them back to life the problem mentioned above happens. I am not sure how to fix it on a larger scale. However to get to work again temporarily right click on the icon on the desktop and choose *unmount*. Then go to *places >> computer* where you will see it listed. Right click and mount it again.

---

### Post by 2manydrugsago on 2008-01-21
I see it in  places/computer  its unmounted. i try to mount and it gives me the same error.

---

### Post by epud on 2008-01-21
If you have windows installed, did you try booting into windows and then shutting it down as described? I am sorry I don't have any more suggestions.

---

### Post by az on 2008-01-21
You can try to mount it as read-only:

sudo mount -r /dev/sdb1 /mnt

---

### Post by epud on 2008-01-21
Thanks, It is essential for me that I can write too it also though.

---

### Post by 2manydrugsago on 2008-01-21
Ill wait for a windows box and see if that works otherwise its under warranty. I bet it would blend.

---

### Post by mihir3445 on 2008-03-13
I don't have full fladge solution to this but your can try this.

1:> plug the USB external drive to any windows machine

2:> after detection, from the try panel no righthand bottom side select unplug device.

3:> plug the drive and it will be ok.

Regards,
Mihir

---

