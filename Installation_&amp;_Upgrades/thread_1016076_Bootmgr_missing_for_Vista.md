---
title: "Bootmgr missing for Vista"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by rapsball4 on 2008-12-19
My apologies if this thread exists somewhere, but I didn't see one.  I already had a Vista x64 Home Premium running for a while and decided I had been Ubuntu-less for too long (due to some other glitches a while ago I never managed to get fixed).  I installed 8.10 alright to another partition, so with setup like this:

Disk 1:
Partition 1 - Windows
Partition 2 - Ubuntu root
Partition 3 - swap space
Partition 4 - shared data

Disk 2:
Partition 1 - more shared data

GRUB loads up fine and shows the options that it should show, and it boots into Ubuntu no problems.  But when I try to boot into Windows, I get a message that the Bootmgr is missing.  I can use SuperGRUB to get into it still, but that would be a major hassle to do everytime I wanted Windows.  Any ideas on how to fix?

---

### Post by upchucky on 2008-12-19
get advanced supergrub to fix master boot record.

search this forum for chainloader it is needed for win partitions

super grub will set it up for you.

---

### Post by caljohnsmith on 2008-12-19
In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "boot_info_results.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.

---

### Post by rapsball4 on 2008-12-19
The file is attached.  I googled for Advanced Super Grub and got nothing - is it different than normal Super Grub?

---

### Post by caljohnsmith on 2008-12-19
You accidentally posted the bash script and not the results; please post the contents of the "boot_info_[COLOR="Blue"]results[/COLOR].txt" file. :)

---

### Post by upchucky on 2008-12-19
advanced supergrub has more features for finding and fixing, plain supergrub assumes you already know what you are doing.

---

### Post by rapsball4 on 2008-12-19
Oops.  It was the only file that showed up on my desktop so I assumed it was the right one without looking.  Must have typoed and not gotten the results.  Let's try that again.

And where I would get a hold of Advanced Super Grub?

---

### Post by caljohnsmith on 2008-12-19
OK, I believe I found the problem. How about first opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change the Windows entry at the end to:
```
title		Windows Vista
root		(hd0,0)
chainloader	+1
```
Save, reboot, and let me know exactly what happens when you boot Vista from the Grub menu.

---

### Post by rapsball4 on 2008-12-19
Thanks a lot.  Problem solved.

---

### Post by caljohnsmith on 2008-12-19
I'm glad it turned out to be a simple fix; cheers and have fun with Vista and Ubuntu. :)

---

