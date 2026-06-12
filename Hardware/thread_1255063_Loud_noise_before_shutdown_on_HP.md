---
title: "Loud noise before shutdown on HP"
date: 2009-09-01
forum: Hardware
---

### Post by kut77less on 2009-09-01
Right when  my Ubuntu shutdown there is a loud cracking noise. I know what the problem is. It has to do with the audio. The audio is not unloaded, so it sounds as if I held the power button. This does not happen in vista. I can see that the audio is mute before vista shutdown, because it glows read on my touch pad. How can I mute the audio before shutdown, for a quieter shutdown. 


Thanks for all your help

---

### Post by mihalisla on 2009-09-01
I have the same problem with kubuntu 9.04 on a hp dv6770!!!

---

### Post by roger_la_fee on 2009-10-06
I had the same problem and found the solution here :
[http://art.ubuntuforums.org/showthread.php?t=1259307](http://art.ubuntuforums.org/showthread.php?t=1259307)
> 
Add this line:
 "blacklist pcspkr"

into
/etc/modprobe.d/blacklist.conf

Tip: Open the configuration file as root, i.e.,
Code:

 gksudo gedit /etc/modprobe.d/blacklist.conf


---

