---
title: "Write to disk."
date: 2009-04-16
forum: Hardware
---

### Post by AJNpa80 on 2009-04-16
Is there a reason why changes to file system are lost when i reboot?? It is a wubi install and it is the first reboot after leaving windows, i get the b43 phy0 ucode5.fw error and it takes me to the bash prompt where i fix it, however all changes are lost when i reboot, all files are where they were when i started and new packages are gone depending on which method i use to add the broadcom firmware. Is there a reason it wont write? Is it because it is a wubi install with a virtual disk on a ntfs file system, or because the install is not complete a lack of some driver or tool for writing or something, or is it some kind of privilege or administrator runlevel access-y-ish thingy-ma-doo? I ran everything sudo, everything i did seemed to work, watched the progress, no errors, checked directories each time for files, everything where it needed to be, until the boot, and it all went back or disappeared if it wasn't from the 8.10 disk. I have tried several flavors of ubuntu and want to get it done by wubi on this machine first to be sure i can get it done on here, then i will drop windows altogether. Its an averatec 32o0, the only unit ive ever had trouble loading linux on, goblinx was the only distro i've ever gotten to boot on here. Thank you any help would be appreciated.

---

### Post by AJNpa80 on 2009-04-25
I'm still stuck after another week but haven't had much time to fool with it until now. no replies to any of my posts, and very little from irc. I'm wondering if wubi mounts in readonly mode when you get dropped to bash before the install gets to finish on the first reboot due to an error (the b43 fw error)i have even thought about rebuilding the iso to have b43 installed automaticly, ive tried to access the virtual disk to add it from windows, abd ive tried to figure out custom install to add a package right off the bat but due to my limited experience as a semi new guy, no success, the easiest way would be to find out why it wont stay put after a reboot and the script to alter, or how to go into ubuntu proper from bash while it remembers what i did to do it again once inside and see if it sticks then. im only using wubi because im not willing to wipe xp which i plan to do until i get any linux up and running on this little box, wubi seemed the safest way to test on this box.i have tried several distros and all built on debian had the same error because of the prop. firmware. goblinx is the only linux distro ive ever gotten into completely on here, but no wireless, lack of b43 just doesnt cause it to pitch a fit.every other box ive ever put ubuntu or any of its children on has been a cakewalk. once again when i know i can get full functionality on here i am going to do a dedicated install with only a very small xp partition for silliness. so please reply if you know anything, im running out of blank cds and everyone wants to know where ive been.

---

### Post by jedijf on 2009-04-25
remove via windows (Add/Remove Programs)

Install via cd connected WIRED to internet

all should be well.

---

