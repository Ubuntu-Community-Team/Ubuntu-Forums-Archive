---
title: "mute on boot after jaunty upgrade"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by Sendervictorius on 2009-04-28
After booting, the volume control is always set to mute. I can't see how to set it so it starts  un-muted.

I just upgraded to jaunty.

When I boot, I get the bongo drum welcome as the gdm login page comes up. Then when I log in for the first time, the sound mutes, and I don't hear the welcome tune.

I have another partition with a 9.04 clean install, which has no problem.

---

### Post by KillerBOB on 2009-04-28
+1

Coming from Jaunty Alpha 6.

---

### Post by Peedjay on 2009-04-28
+ 2

Same problem here. 
I come from Ubuntu 8.10. Changing preferences in Alsamixer doesn't solve it although it recognizes my soundcard :confused:



System: Asus F3SV, Centrino Duo, Ubuntu 9.04, Soundcard ALC660-VD Analog

---

### Post by jonolumb on 2009-04-29
Same problem here - coming from Ubuntu 8.10 on a Dell XPS M1330 Notebook

---

### Post by guko1111 on 2009-04-30
I'm having this problem also. Tried ```
alsactl store
``` but getting error  "Home directory /home/username not ours" when trying alsactl store.

---

### Post by jonolumb on 2009-04-30
Have a read of this [guide]("http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/"). It fixed all my problems...

Jono

---

### Post by guko1111 on 2009-05-01
jonolumb,
   Thank you that guide solved it for me! :)

---

### Post by zcrar70 on 2009-05-03
I also have the same problem, and I'd like to resolve it without removing Pulseaudio (as the above guide suggests.) 

Did anyone manage to do that?

---

### Post by cornelis1 on 2009-05-05
> **zcrar70 said:**
> I also have the same problem, and I'd like to resolve it without removing Pulseaudio (as the above guide suggests.) 

Did anyone manage to do that?

[This]("http://ubuntuforums.org/showthread.php?t=1139622") workaround worked for me.

---

