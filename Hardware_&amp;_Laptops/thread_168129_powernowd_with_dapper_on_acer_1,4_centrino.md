---
title: "powernowd with dapper on acer 1,4 centrino"
date: 2006-04-29
forum: Hardware &amp; Laptops
---

### Post by Dr. Cox on 2006-04-29
Hi there,

I have recently switched to the Dapper Drake beta release from Kanotix... I enjoy the look and the hardware support of ubuntu. it seems to be almost as good as the one of kanotix. i don't regret the step. 

one problem remains: with powernowd under kanotix my battery life was about 3:40 hours.  with dapper it is only 2:18.

are there any tools to monitor my cpu-freq on the desktop and is there a way to tune powernowd so that I enjoy a longer battery life? 

where does the difference come from? :confused: 

any help is highly appreciated.

thnx. johannes

---

### Post by snipe122 on 2006-04-30
you can add a an icon to your panel (where the clock is) which shows the frequency. Its under system -> hardware and called sth. like monitoring cpu-frequency. dont know the right translation cause mine is german. anyway, the icon is a cpu ;)

---

### Post by Dr. Cox on 2006-04-30
yep, found the icon. thanx. now i can see my cpu almost always reaching top speed with only one application open....

are there other tools than powernowd which throttle the cpu more efficiently or is there a way to tune its limits?  i always heard powernowd being highly praised.  is there a config file or similar?

thanx for now.

---

### Post by paritybit on 2006-04-30
man powernowd is your friend. :)
Some good information contained therein.
To add the options so they are always on you will need to edit (or create)
```
/etc/default/powernowd
```
and add something like
```
OPTIONS="-q -m 2"
``` 
I think this should work from all reports I have seen it does, I don't particularly like powernowd but haven't got around to 
investegating alternatives.

EDIT
Cleaned up some things and made a bit more sense I hope.
-m 2 will set it to passive which from the looks of things will use the least power.
From the manpage:
MODES
       There are 4 modes supported by this client:

       Mode  0,  SINE,  changes the frequency as a sine wave function, raising
       the frequency by "step" Hz every time the CPU usage goes over 80%,  and
       decreases it by "step" Hz when the CPU usage falls under 20%.

       Mode 1, AGGRESSIVE, changes frequency by a sawtooth function.     Imme-
       diately jumps to the highest frequency whenever  CPU  usage  goes  over
       80%,  and decreases by "step" Hz as usage drops below 20%.  This is the
       default behavior.

       Mode 2, PASSIVE, is the inverse of  AGGRESSIVE.   Immediately  jump  to
       lowest  frequency when usage drops below 20%.  Raise by "step" Hz if it
       goes above 80%.

       Mode 3, LEAPS, immediately jumps to the highest frequency if  usage  is
       above  80%,  and  immediately jumps to the lowest frequency if usage is
       below 20%.

---

### Post by shof2k on 2006-05-04
You can also try emifreq to manually set your clock speed, usefull if you're only browsing.

---

