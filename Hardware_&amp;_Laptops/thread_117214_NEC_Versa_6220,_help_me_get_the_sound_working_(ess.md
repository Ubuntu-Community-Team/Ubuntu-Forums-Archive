---
title: "NEC Versa 6220, help me get the sound working (ess1869)."
date: 2006-01-14
forum: Hardware &amp; Laptops
---

### Post by shaolin95 on 2006-01-14
Ive tried lots of things here and cant get it to work. I tried writing a file to the etc/modprobe.d folder but ubuntu wont let me put anything in there casue I am not "owner".
Regards

---

### Post by christhemonkey on 2006-01-14
if you type sudo before any commands, then you shud be able to write in there.

---

### Post by shaolin95 on 2006-01-14
I needed to use kgsudo nautilus to access it but while I was able to add the file that i wanted to, it didnt help my sound card issue. Anyone knows what to try. I  cant find on my bios all the ports info needed for the sound card. Stuff like this is what makes some people just go back to windows... at least I was able to solve the nic issue but the sound card is a no go till now.
Regards

---

### Post by shaolin95 on 2006-01-15
Please guys I need some help here. Ive been trying on my own so its not like I am sitting around waiting for someone to fix this for me. I just  need some extra help. :)

---

### Post by shaolin95 on 2006-01-17
One more try...please guys I need some help here. :(

---

### Post by christhemonkey on 2006-01-17
what exactly is the problem?
just no sound at all?

---

### Post by shaolin95 on 2006-01-17
Yes, no sound at all. I have tried all solutions here but nothing yet.

---

### Post by christhemonkey on 2006-01-18
have you loaded the es1869 module?
sudo lsmod snd_es1869
i think that is what it is called!

---

### Post by shaolin95 on 2006-01-19
Tried it and nothing. I got the following message:
USAGE: lsmod

---

### Post by christhemonkey on 2006-01-19
You got that?
weird!
Maybe the module name was wrong?

---

### Post by FarEast on 2006-01-27
> christhemonkey
> have you loaded the es1869 module?
> sudo lsmod snd_es1869

I think that it should be 'sudo [COLOR="Red"]modprobe[/COLOR] snd-es18xx'.
[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-ESS_Technology#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-ESS_Technology#matrix)

I have posted a reply to wukkkie the other day.
[http://ubuntuforums.org/showthread.php?t=114493](http://ubuntuforums.org/showthread.php?t=114493)

---

