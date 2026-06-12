---
title: "[HDA-Intel Problem] HP Pavilion dv4-1180br"
date: 2009-05-11
forum: Hardware
---

### Post by Jaypur on 2009-05-11
So, I was having problems with my sound when I played any sound, it was playing all messed-up, so i found:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

So i did it until 

# Reboot
# if you have no sound, run dmesg and look for the string "snd_" 


So, the sound was ok, but if i stopped it keeps playing but all messed-up like last time...

Then I was going thru "Manually Specify Module Parameters" and gone until "options snd-hda-intel model=MODEL" 

Now I don't have any sound, nothing releated works... so I would like some help of you guys....


thx.

---

### Post by NazarXG on 2009-05-12
This is an on going issue, take a look at:

[http://ubuntuforums.org/showthread.php?t=1101098&highlight=dv4+sound](http://ubuntuforums.org/showthread.php?t=1101098&highlight=dv4+sound)

[http://ubuntuforums.org/showthread.php?t=984538&highlight=dv4+sound](http://ubuntuforums.org/showthread.php?t=984538&highlight=dv4+sound)

[http://ubuntuforums.org/showthread.php?t=1142514&highlight=dv4+sound](http://ubuntuforums.org/showthread.php?t=1142514&highlight=dv4+sound)

Use the search function :)

---

### Post by Jaypur on 2009-05-12
thanks a lot, but i used the search and didnt find those threads, anyway thanks a lot!


> 
> **Jorge_C said:**
> This should solve your dv4 sound problems:
```
gksudo gedit /etc/modprobe.d/alsa-base
```
and add this to the end of the file:
```
options snd-hda-intel enable_msi=1
```
Hope this works for you



worked here, thank you a lot....


hp pavilion dv4-1180br


thanks!!!!



---

### Post by cjsteele on 2009-05-12
which kernel are you running?  (`uname -a`) 

There is a flaw in the most current 9.04 kernel image that horks the Intel HDA chipset support.

---

### Post by Jaypur on 2009-05-13
Linux 2.6.28-11-generic


:D

i'm so happy that worked!

---

### Post by cjsteele on 2009-05-14
> **Jaypur said:**
> Linux 2.6.28-11-generic


:D

i'm so happy that worked!

hurrah!  Now, I just need to hunt it down... 


I had downloaded 2.6.28-12, but I suspect I need -11

---

### Post by cjsteele on 2009-05-14
> **Jaypur said:**
> Linux 2.6.28-11-generic


:D

i'm so happy that worked!


You are indeed correct -- 2.6.28-11-generic is 100% functional.  Thank you for sharing your information.  Now I've pinned my kernel package and am going to write a blue-print for functionality testing the kernel before rolling it out to the main-line.

Cheers,
-C

---

