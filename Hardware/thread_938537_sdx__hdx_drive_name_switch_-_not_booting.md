---
title: "sdx / hdx drive name switch - not booting"
date: 2008-10-05
forum: Hardware
---

### Post by bigstan on 2008-10-05
Apologies if this has been dealt with before - i am unable to find any solution either here or Google.

I have a Gigabyte GA-7ZXR system board, with an on-board Promise 20265 IDE RAID chip - set as a regular IDE controller. (ie, no RAID)

After Ubuntu server install, the drives on the mobo IDE channels are listed as **sd[a-c]**, where the drives on the Promise IDE channels are listed as **hd[e-g]**

Installed 8.04.1 Server to mobo IDE 1 master - shows as SCSI1 (0,0,0) (sda)

it is the drive I wanted to install it on - but it's acting like it's not there when i boot after installation - I get the BIOS system disk error.

From what I've read about Ubuntu going with sdx names for better compatibility with sata drives, why would the Promise drives be showing as hdx drives, and the mobo-native IDE drives be the sdx drives?

Fair warning - I am a relative Linux newbie, but have no fear of the command line. It's a new install, so I'm not worried about breaking anything - and I have a win 200 server hdd that I can go back to if i need to. If you need any information, tell me how to get to where to type it in, and I can get it to you.

---

### Post by cariboo on 2008-10-05
You probably have  to change a setting in your bios. Check to see what the raid controller is set for, if you are not going to be using raid, then set it for JBOD. Also check you disk order in the bios and make sure the drive you want to install ubuntu on is first in the list.

Jim

---

### Post by bigstan on 2008-10-05
> **cariboo907 said:**
> You probably have  to change a setting in your bios. Check to see what the raid controller is set for, if you are not going to be using raid, then set it for JBOD. Also check you disk order in the bios and make sure the drive you want to install ubuntu on is first in the list.
Jim

Thanks for the response, Jim.  I ended up going back into the BIOS and changing some settings around and was able to get a Grub 21 error - but at least it was recognizing that something was there! I'd forgotten I had set my 1st HDD to USER instead of Auto Detect in BIOS - once I fixed that, I was up and going.    The drives are still sporting opposite naming, but at least they are accessible.

From here, I'm just going to have to teach myself Samba, Apache and vsftpd.  That's the easy part. :D

Case solved - thanks again.

Stan

---

