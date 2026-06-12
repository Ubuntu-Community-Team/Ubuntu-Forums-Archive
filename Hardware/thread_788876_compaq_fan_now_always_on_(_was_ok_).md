---
title: "compaq fan now always on ( was ok )"
date: 2008-05-10
forum: Hardware
---

### Post by westdale on 2008-05-10
Hardy Heron installed on Compaq 1500 laptop and the fan worked fine: full on when hot and went quiet when cool.
I have installed some additional packages (including Dia, Inkscape, Mplayer, additional TT fonts) and the fan now remains permanently on.
The air being blown from the vents is cool and temperatures look OK to me 
  gw@ubuntu:~$ acpi -V
     Battery 1: charged, 0%
     Thermal 1: ok, 41.0 degrees C
     Thermal 2: ok, 50.0 degrees C
     Thermal 3: ok, 16.0 degrees C
     AC Adapter 1: on-line

So,the beginner question: Could someone advise me where to look to see what files might have been affected to cause the fan to stay on all the time?

(later, after leaving it for some hours:  as the fan is quiet after booting until warmed up, I may not have a problem -- but when all three parameters are set OK I expected the fan to be off ? )

(after a day or two of thinking) I think this may be a case of borderline temperatures - we had some very warm weather for a few days, coinciding with the changes I made. Today is cooler by some 10 degrees and the fan behaviour is fine ! 
[ insert embarrassed smiley here ]

---

