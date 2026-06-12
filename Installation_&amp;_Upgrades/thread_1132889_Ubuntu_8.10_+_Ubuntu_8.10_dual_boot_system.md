---
title: "Ubuntu 8.10 + Ubuntu 8.10 dual boot system"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by knixo4 on 2009-04-22
I'll try to be brief.  I've googled the above using various keywords with no luck in finding the necessary steps to create said system.  It seems like it should be ridiculously easy, but for some reason I can't get it done!  I just used Gparted, created an unallocated partition, and am trying to install Ubuntu 8.10 in that space, mount point "/", as I type.  What should I expect?

Thanks in advance.

---

### Post by JK3mp on 2009-04-22
Why would you wanna dual boot like that? One for testing and one for actual work i guess. Are you actually having problems installing? Any error's? etc. A little more information would be helpful in helping you out with this issue

---

### Post by miegiel on 2009-04-22
Possibly there's something wrong with the empty partition you made. As you said "it should be ridiculously easy" and it is. I've always dualbooted 2 linuxes. Since I'm the "what does this button do?" type, I knew I'd break my 1st linux installation on the 1st day exploring the OS (hence I neded the backup OS). From what you wrote, I can only say you're doing it the right way

---

### Post by knixo4 on 2009-04-22
Hey guys, thanks for the replies.  The "method" above did work out for me.  I guess now I'm a little less of a partition virgin.

---

### Post by miegiel on 2009-04-22
great :D

---

### Post by coffeecat on 2009-04-22
**knixo4**, I hope you're still there, but there's one helluva big gotcha if you dual-boot with two instances of the same release of Ubuntu. It's little known, mainly because hardly anyone does this. It will also affect you if you dual-boot Ubuntu and Mint where the Mint version is based on the same Ubuntu release.

What happens is that when there's a kernel upgrade the installer gets horribly muddled and gets menu.lst disastrously wrong as it rewrites it. I can't remember the exact details - something about UUIDs - but a year or so ago I had two instances of Hardy on adjacent partitions (long story - there was a good reason). I updated the kernels and then watched in mystification as a usplash theme I'd only installed in version A appeared when I booted up version B.

Took me ages to work that one out. In fact, iirc correctly, at one point one or the other system became unbootable until I fixed menu.lst.

Enjoy! :wink:

---

### Post by markbuntu on 2009-04-22
A little handy tip.

When you install a distro put its grub in the same partition as / and chainload it from the grub on the mbr. This will save you a lot of headaches with UUIDs and kenrel updates etc in the future. I know, I have 5 distros on this machine. This is what I have at the end of /boot/grub/menu.lst on the mbr. Chainloader does not really care what's on the other end which is a good thing for me since I am so lazy about updating the menu.lst


#This entry added to get for 8.04 UnbutuStudio amd64 on sdb

title		Chainload Ubuntu 8.04 amd64
root		(hd1)
chainloader	+1

#This entry added for Mandriva i386 on sdc (actually another jaunty now)

title		Chainload Mandriva 2009
root		(hd2)
chainloader	+1


#This entry added for Intrepid on sdd

title		Chainload Intrepid
root		(hd3,0)
chainloader	+1

#This entry added for Jaunty on sdd3 ( with KDE4.2 and ubuntustudio)
title		Ubuntu Jaunty 9.04 kernel 2.28-6-generic ( kernel 2.6.28-11 now)
root		(hd3,2)
chainloader      +1

---

