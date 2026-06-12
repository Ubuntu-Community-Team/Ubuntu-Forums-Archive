---
title: "login screen oversized - still unsolved"
date: 2008-10-26
forum: General Help
---

### Post by wallydallas on 2008-10-26
My login screen is so oversized that I can't see the box for typing in my username.  The resolution is something greater than 1500x1800

After I logon my screen resolution is good, and I can adjust it. I've found a lot of mixed advice.  People tell me to edit the grub files, do this, do that, etc etc.   I really love if someone could actually solve this by giving clear steps ( not things like "try this" and one line of code )

Here is the screen section of my xorg.conf file 

```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1792    1344
                Modes           "800x600@60"    "832x624@75"    "800x600@85"   $
        EndSubSection
EndSection
```

Here is what I've tried.  I tried changing the "virtual" line from "1792 1344" to "800 600" I restarted.  That fixed the login window, but broke other things.  Once I logged on I was  unable to set my screen resolution larger than 800x600.    I always restart after a change and backup my CONF file beforehand ( thank god for sanity )   I also tried to just remark out the virtual line.  That did not help fix the problem.   I tried adding some lines that other people suggested.  I feel like fixing linux is a lot like voodo, where you listen to some crazy advice, and it is crazy that sometimes it works.   Ubuntu seems to be getting lower quality in the basics and adding too much fluf where it is not needed.

This is a fresh install of 8.04 on a blank 20 gig drive and good machine.  The only other adjustment I needed was to set my monitor model as it was not detected with plug and play.  Dell P780 / Sony OEM 19" high res flat CRT.

I bang my head getting Ubuntu to install and work properly but after that it says working.   With Windoze I used to bang my head to install and then bang my head monthly to keep it working.

Please help!  ](*,)

---

### Post by Logistics64 on 2008-10-26
Someone needs to help get this fixed. I have the same problem. However, I'm running in a VM so it doesn't really matter, because I can scroll around.

---

### Post by teaker1s on 2008-10-26
[http://ubuntuforums.org/showthread.php?t=882463]("http://ubuntuforums.org/showthread.php?t=882463") perhaps may help

---

### Post by wallydallas on 2008-10-28
Good try Mr./Ms. Teaker ( reply #3 )

But your advice is a dead end.   I've been all over these forms and I tried the editing of the virtual code section of my video config file.  

I have the same problem, and I got half way towards a fix.  But half a repair is almost worse.   What makes this hard is that so many people give advice without reading that their advice has been attempted by myself and others.   


I edited my file so it now reads like the code below.  The problem that remains is that the pre-logon screen size sets the limit to the maximum post-logon screen size.   In other words if I want my logon screen to be 640x480 so that it fits on the screen, then after I logon I can not use a resolution larger than 640x480.    

There are a lot of people with the same problem in 8.04.   I guess it will take a lot of users to report this, and then the code people will get their shorts in a bunch because some of the people do it in a nasty way.  I'm trying to be nice here.


```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1280    1024  
                Modes           "800x600@60"    "832x624@75"    "800x600@85"   $
        EndSubSection
EndSection
```


It is possible this only happens with video hardware that has an Nvidia chipset.  But that is a huge percentage of computers that have been built in the last 5 years.

---

