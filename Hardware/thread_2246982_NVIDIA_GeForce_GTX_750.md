---
title: "NVIDIA GeForce GTX 750"
date: 2014-10-04
forum: Hardware
---

### Post by angus5 on 2014-10-04
So today I got my NVIDIA GeForce GTX 750, and when I plug it into my PC, it will boot up and show this screen.  [http://m.imgur.com/N8oMEN0](http://m.imgur.com/N8oMEN0)

Does anyone have any idea what I should do? I run Linux mint Debian 64 bit if that helps.

it works fine on my windows computer, just not on my Linux one.

---

### Post by sns4rnr on 2014-10-04
Can't say for sure the entire meaning of the error.  I know Nouveau is the default "open-source" driver that Linux uses for Nvidia cards.
It is generally considered that you will get better performance installing Nvidia's proprietary drivers, thus replacing Nouveau.
I expect that eventually you will want to do that to get the most from your new card.

If you can figure out how to work around your errors and install the proprietary drivers, it may solve your problem.

Hopefully someone else here can give some pointers on how to get around your errors to install such drivers.
You may also find some instructions and a source for the drivers poking around the following:

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Plug in your card information and it will take you to their "recommended" driver.   There is a newer driver as well that is reported to support that card, but, this page still takes you to this driver which is still being actively updated as needed by Nvidia.

Sorry can't offer more direct instructions.  Maybe someone else will follow.  Good Luck.

---

### Post by sns4rnr on 2014-10-10
I just got my GT730 installed.
Did not have your same Nouveau driver errors, but I installed Nvidia's drivers anyway.
Maybe something useful here where I describe my process for swapping to my new card.

[http://ubuntuforums.org/showthread.php?t=2247699](http://ubuntuforums.org/showthread.php?t=2247699)

---

### Post by oldfred on 2014-10-10
Maxwell 750 
[http://ubuntuforums.org/showthread.php?t=2214805](http://ubuntuforums.org/showthread.php?t=2214805)
[http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1](http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1)
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1)

Did you try nomodeset?
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

