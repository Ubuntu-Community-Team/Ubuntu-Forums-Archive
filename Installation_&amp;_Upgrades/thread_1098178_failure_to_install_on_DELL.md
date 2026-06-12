---
title: "failure to install on DELL"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by makaymurray on 2009-03-16
Hey boys I'm trying to install Ubuntu 8.10 on a Dell Dimension C521 with a AMD Sempron CPU, 512MB of RAM and a 80GB SATA HDD.


first ill give you my error then ill tell you what I have tried so far. 

#ERROR
when i insert the Ubuntu 8.10 live CD into the DELL and boot it loads the CD's landing page just fine, asks me to select a language then shows me the options: live CD, install, check CD, Check RAM etc. when i select LIVE-CD, INSTALL, or CHECK CD it loads a little bit then gives me this error:

"
[ 0.420026] ..MP-BIOS bug: 8254 timer not connected to IO-APIC 
loading, please wait...

BusyBox v1.10.2 (ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash) 
Enter 'help' for a list of built in commands.

(initramfs)_
"

now to me it seems as if the installation process simply gets sidetracked and puts me into a limited terminal window. 





now for what i have tried:
i own another Compaq tower and have successfully installed unbuntu on it using the same live CD. it never gave me this error. i have also removed the drive from the computer and attached it to my mac, wipped the drive clean using disk utility and formatted it with FAT-32. then i put it back in the DELL and i got the same installation problem. i also tried installing ubuntu on it using the compaq with the drive externally mounted (using a universal drive adapter) and i am confident that i told the compaq the correct procedure to install ubuntu on the external drive but when i put it back in the DELL it gave me a failed to boot error and would not proceed. 


any help or pointers would be appreciated. if I'm a tool and am not seeing something obvious please let me know also.

---

### Post by PenguinsFan on 2009-03-16
Sorry your having trouble :(

You may want to try this thread, it has some similar errors:
[http://ubuntuforums.org/showthread.php?t=191355]("http://ubuntuforums.org/showthread.php?t=191355")

---

### Post by upchucky on 2009-03-16
i thought i read something about this here somewhere, change apic in bios to no apic. check for posts about it first though, my photographic memory is running outta film.

---

