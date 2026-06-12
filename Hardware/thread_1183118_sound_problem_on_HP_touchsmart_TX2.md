---
title: "sound problem on HP touchsmart TX2"
date: 2009-06-09
forum: Hardware
---

### Post by digisax on 2009-06-09
I've installed Ubuntu on my touchsmart tx2 and it works great but when i tried to adjust the volume the computer looked like it was changing the volume but it stopped making sounds except for the beep in terminal and at shutdown. Any help is greatly appreciated and thank you in advance.

---

### Post by Favux on 2009-06-09
Hi digisax,

You could try what exophobe recommends on post #72 here:  [http://ubuntuforums.org/showthread.php?t=1038898&page=8](http://ubuntuforums.org/showthread.php?t=1038898&page=8)

---

### Post by digisax on 2009-06-09
thank you although when i try to edit the file with the command
[COLOR=Lime]sudo echo "options snd-hda-intel model=toshiba" >> /etc/modprobe.d/alsa-base
[COLOR=Black]it comes up with the error in terminal
[COLOR=Lime]bash: /etc/modprobe.d/alsa-base: Permission denied[/COLOR]
[/COLOR][/COLOR]

---

### Post by Favux on 2009-06-09
Hi digisax,

I think in Jaunty it is now called "alsa-base.conf".  You can edit it directly and add the line to it by using:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
And you can check if I am right about the name by navigating to it using Places (Nautilus).

---

### Post by digisax on 2009-06-10
i have that open but i don't know what to edit it to say

---

### Post by mycoted on 2009-06-10
Add 
> options snd-hda-intel model=toshiba
to the end of the file, as the new last line of the file.

---

### Post by digisax on 2009-06-10
Thank you both for helping me i got the problem solved completely

---

### Post by boujei on 2009-07-12
what hang ups did you encounter with the Ubuntu installation on this notebook?..I have the same one and have been reluctant to try?

Thanks!!

---

### Post by digisax on 2009-07-12
> **boujei said:**
> what hang ups did you encounter with the Ubuntu installation on this notebook?..I have the same one and have been reluctant to try?

Thanks!!



Other than the sound problem I have had no hangups once I stopped quitting installations in terminal
I would definately install it if I were u

---

### Post by javier_8r on 2010-03-10
Hey ya all thanks for the information but i got a question.. I got that tx2 touchsmart tablet either but i use to have ubuntu 9.10 and i format it twice cause every time the kernel was updated it change my sound card to dummy output so I was tired of this and switch back to 9.04 because either I couldn't suspend or hibernate it never turn back on!! about the sound now it recongnizes my card but it won't make any sound exept for the shut-down beep like shown above so could anyone help me please?

thanks in advance regards!

---

