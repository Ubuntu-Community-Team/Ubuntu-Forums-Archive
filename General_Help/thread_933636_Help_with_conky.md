---
title: "Help with conky"
date: 2008-09-29
forum: General Help
---

### Post by dlm4849 on 2008-09-29
k. Ive got conky to show what I want from amarok, but I want it to say "paused" when amarok is either not running or it is paused. I got it to say paused when its off, but now it wont show the info Im asking for when something is playing. It still says paused. If i get rid of the "if_empty" variables everything works fine, but then its not able to use the "else" variable. Anyone know what to do? Hopefully I understand this stuff enough to give you enough info on how to diagnose this.

Here's the portion of my .conkyrc

```
Now Playing: ${if_empty execi}${color B9B9B9}${execi 10 ~/amarok artist} - ${execi 10 ~/amarok title} on ${execi 10 ~/amarok album}${color}${else}${color B9B9B9}Paused${color}${else}${endif}
```

Thanks much

---

### Post by dlm4849 on 2008-09-29
Also, if someone has experience with amarok (specifically) and conky, would you mind saying if you have issues with your processor usage spiking with this script? If amarok isnt running, processor usage is normal, but when its running, its much greater than before i tried to use this script, even if it is paused. I got mine off the conky screenshots page.

---

### Post by binbash on 2008-09-29
you will get your questions answered faster if you post them here : 

[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by dlm4849 on 2008-09-29
I thought about that, but I thought it might just get buried in that huge thing. Ill try though.

Thanks

---

### Post by dlm4849 on 2008-09-30
Anyone else?

---

