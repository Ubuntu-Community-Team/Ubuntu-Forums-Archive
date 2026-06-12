---
title: "xubuntu 9.04 with kernel 2.6.28-15 wont boot"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by Robert_L on 2009-08-30
Hi
 
I updated my xubuntu 9.04 system with an upgrade using the "upgrade manager" that gave me a new kernel 2.6.28-15. After that it was not possible to reboot the system. Grub ended up with Error 18.
 
I then was able to select the previous kernel 2.6.28-14 via the grub "boot selection menu". Then the system booted OK.
 
So the question is then what has changed between 2.6.28-14 and 2.6.28-15 that may cause this error?
 
I have temporary commented the 2.6.28-15 lines in the menu.lst file so that it automatically picks the 2.6.28-14 instead.
 
/Robert

---

### Post by sandy4linux on 2009-08-30
hi,
   This occur due to broken package during downloads. in order to fix this..
Go to recovery mode...

enter Root shell..

Type in command

sudo dpkg --configure -a

this may upgrade the broken package.

regards

---

### Post by Robert_L on 2009-08-30
Hi
I got "unknown flag --command" as a response to the proposed command.
 
Should I substitude --command with something?
 
Another thing is that if I start synaptic it says zero broken packages?
 
/Robert

---

### Post by sandy4linux on 2009-08-30
sudo dpkg --configure -a

Have your internet connection to fix the error packages.

If it still doesnt work then enter DPKG in recovery window

Regards

---

### Post by Robert_L on 2009-08-30
Hi
I got the dpkg command right this time. There were no output from the command telling about repaired or fixed packages, though. And this match what I noticed in synaptic saying there are no broken packages.
 
Then I tried to boot with 2.6.28-15 but it still fails. Must be some other problem.
 
Thanks anyhow for your efforts!
 
/Robert

---

### Post by sandy4linux on 2009-08-30
Since there is no broken package, this must work. Try this in Root shell..

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

Regards

---

### Post by Robert_L on 2009-08-30
Hi
I tried your proposed commands. I was a little confused about you saying root shell and also stating the sudo. So I did both just in case (sudo run in a shell as root).
I provide the commands and the output in the attached file shell.txt. Beware some of this is in swedish but I hope you understand it anyhow.
 
But there is no difference in result at booting.
 
 
I still get Error 18 "Selected cylinder exceeds maximum spported by BIOS" from grub. This is very strange since nothing else has been changed except for taking the system recommended upgrade.
 
/Robert

---

### Post by sandy4linux on 2009-08-31
"Error 18"
[SIZE=2][COLOR=Black]Selected cylinder exceeds maximum supported by BIOS.

 This error is returned, when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle.

[/COLOR][/SIZE]Change  BIOS settings, you could check hard disk mode. If it's LBA (logical block addressing)or AUTO try changing it to NORMAL. 		

regards,

---

### Post by Robert_L on 2009-08-31
Hi
I tried different setting of BIOS - HD ACCESS MODE. It was set to AUTO originally and I tried LBA, LARGE and finally CHS.
 
The last one CHS worked fine.
 
Thanx a lot for your help. :)
 
/Robert

---

