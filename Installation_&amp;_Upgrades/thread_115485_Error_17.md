---
title: "Error 17?"
date: 2006-01-10
forum: Installation &amp; Upgrades
---

### Post by Dark Damo on 2006-01-10
After we installed breezy on my sisters partitioned hard drive. 10gb partition for windows which we hadnt installed. 9gb for ubuntu. Ubuntu gave us the error code 17 and wouldent boot.

The specs of her system are...

Pentium 3 slot 1 CPU 450mhz
256mb PC100
3dfx Voodoo Banshee 16mb
19gb HDD (20gb)
Intel 440BX motherboard no bios update since 1999.

---

### Post by Sef on 2006-01-10
Here is what Gentoo's documentation says about it:

5. Grub Error 17

Situation

Code Listing 5.1: Grub Output

root (hd0,0)
filesystem type unknown partition type 0x7

Error 17 : Cannot mount selected partition

Solution

This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

Be sure to check your root(x,y) settings in your grub.conf. 

Also, if you are trying to boot Windows, make sure that your grub.conf file has the root (hdX,Y) (or rootnoverify (hdX,Y)) and chainloader (hdX,Y)+1 in it.

[http://www.gentoo.org/doc/en/grub-error-guide.xml]("http://www.gentoo.org/doc/en/grub-error-guide.xml")

Here is another thread that dealt with this issue:

[http://ubuntuforums.org/showthread.php?t=101316]("http://ubuntuforums.org/showthread.php?t=101316")

---

### Post by Dark Damo on 2006-01-10
I dont have windows installed yet. First it gave me an error which happens after you format the hard drive. 

Maybe i should put ubuntu on the first partition not the second?

---

### Post by Sef on 2006-01-10
> Maybe i should put ubuntu on the first partition not the second?

Windows needs to be on the first partition.  It is easier to dual if it is loaded first because installing it will wipe out GRUB, which will need to be reinstalled.

> After we installed breezy on my sisters partitioned hard drive. 10gb partition for windows which we hadnt installed.

You may not have installed Windows, but there is a partion there.

**Suggestion for fix:**  First install Windows, and then reinstall Ubuntu.

**Tutorial on dual booting:**  [http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by Dark Damo on 2006-01-10
Ok thanks :) 

Will try that. I got my sister on the live cd and she's having a blast!

---

### Post by Dark Damo on 2006-01-11
Same error. We installed windows and partitioned all fine. Installed ubuntu and we just get error 17. Maybe it doesnt like my sisters old computer?

---

### Post by Dark Damo on 2006-01-13
any ideas?

---

### Post by Sef on 2006-01-13
1) How did you partition?  Did you make the Ubuntu partition fat32?  If you did home and root partitions they should be either ext3 or reiserf.  The swap is swap.

2) Did you delete all the partitions (except for windows) and then repartition?  Sometimes you have to do it a couple of times.

---

### Post by Dark Damo on 2006-01-13
Total we distroyed all partitions and reformatted 7 times. Windows 2000 pro was NTFS ubuntu was EXT3 and swap was a swap file. Error 17 all times.

---

### Post by Herman on 2006-01-13
Do you think it is possible for the BIOS on the older computer to still have the 8 GB limit?
Here's a link that explains some technical stuff about that. Don't worry too much if you can't understand all of it, but it will give you a rough idea of what I'm on about... The part about the 8.0 GB limit is right down at the bottom of the page.
 [http://web.inter.nl.net/hcc/J.Steunebrink/bioslim.htm]("http://web.inter.nl.net/hcc/J.Steunebrink/bioslim.htm")
The easiest thing to try might be to reduce the size of your Windows partition down to say 7 1/2 GB or 7 3/4 GB. Then your Ubuntu partition will begin inside the 8 GB limit and should boot okay. I believe from reading that in the old days that's one of the reasons they liked to make a seperate /boot partition for LInux. If you have a /boot partition somewhere inside the 8.0 GB limit, it should boot Ubuntu even if Ubuntu is outside the 8.0 GB limit.
You might be able to update the BIOS with a BIOS flash, that might seem a little bit advanced for the average computer user, but you might find it easier than you think. If a more up-to date BIOS program is available for you old motherboard it might cure your problem. See your motherboard manufacturer's website. If you are able to do that, then you'll be able to leave Windows as 10 GB, like you want.
I have no experience with the 8.0 GB barrier myself, but I did try a similar thing for a computer with a 33.8 GB limit. In my case it didn't help. I had to buy a smaller hard-disk. But it might help you, your situation is a little different. I don't know for sure  if this advice is accurate or not, but it might be worth further investigation. Use your own judgement and take this with a grain of salt. 
Here's another link on the same subject too: [http://www.tldp.org/HOWTO/Large-Disk-HOWTO-4.html]("http://www.tldp.org/HOWTO/Large-Disk-HOWTO-4.html")
Good luck with it, :D (Herman).

---

