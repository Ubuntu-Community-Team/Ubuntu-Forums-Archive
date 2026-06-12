---
title: "Ubuntu 8.04 error 17"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by lloyd5867 on 2009-03-12
i was running WinXP PRO SP3 and tried to install 8.04 inside of windows. after install and reboot i got 

Grub Loading Stage 1.5

Grub loading, please wait...

error 21 


the cd im using is a HARDY HERON release dated april 15 2008

its live boot. 


so i booted using the live boot feature, and tried to install that way, rebooted and came back with pretty much the same exact thing except error 17.



i was installing it on my 120 gb hdd. 


i cant load up my install of xp and since i dont know ANYTHING about linux or linux systems i was trying to broaden my horizons. but i think im done with that for now. i just want it gone completely. 


i tried using the windows Repair Console with my boot cd for SP2, i tried FIXMBR, and FIXBOOT. ive also tried resetting my CMOS. 


i really dont want to reboot.



and i am COMPLETELY NEW to Ubuntu. i dont know how to open command consoles or anything like that to get to the GRUB shell thing...


some one help please T.T

---

### Post by ajgreeny on 2009-03-12
You could try the supergrub CD, but you need to boot to a working system to download that first, so it may be a problem to you.  However, if you can get the ubuntu live CD to boot properly you can get your windows MBR back with the following:-

You can install a Windows equivalent MBR to your sda drive by doing the following from your Live CD:
Open a terminal (Applications > Accessories > Terminal) and run the two following commands

```
sudo apt-get install lilo
```then, after that has finished
```
sudo lilo -M  /dev/sda mbr
```

Then you should be able to boot directly into Windows again if all goes well.
Let me know how it goes or if you run into problems.

---

### Post by lloyd5867 on 2009-03-12
well my issue with installing lilo is that i dont have internet on that computer yet, would there be any way i could reboot the mbr without lilo?



edit**


the reason i dont have internet on that computer is because our internet connection is run entirely on wireles. and i dont have a wireless card yet. but i have one available for temporary use. is it possible to install the drivers for the card using the live boot cd?

---

### Post by lloyd5867 on 2009-03-12
ok came up with an issue. 


i tried what you told me, and its still not letting me load directly into windows, or load windows at all.


edit **


now it says NTLDR is compressed ctrl+alT+del to restart

---

### Post by lloyd5867 on 2009-03-12
ok working through one problem and finding more
 

fixed the ntldr error 


now im getting a 

autochk not found

(its in a blue like chkdsk screen)


then it goes black with some error that i cant read and reboots.

---

### Post by lloyd5867 on 2009-03-12
ok i fixed everything. i will be venturing down this ubuntu allyway and maybe eventually completely changing over to ubuntu or other linux type os. 



ill just more careful next time around.



edit**
and thanks be to ajgreeny because he got me started on the right track :D

---

