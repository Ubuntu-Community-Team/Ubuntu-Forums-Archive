---
title: "Amarok doesn't play anything..."
date: 2008-11-28
forum: General Help
---

### Post by geo909 on 2008-11-28
Hello everybody,

Today amarok stop playing!
When I try to play something, I get a popup
window saying:
```
Audio output unavailable; the device is busy.
xine parameters: 
```

I think my last action yesterday was to
install the recommended updates. Nothing more...

ANy ideas on this?

Thanks a lot in advance..


EDIT: The problem seems to be general!
I try to watch a video in youtube and no sound again!
Then I type "alsamixer" on the
terminal and here is what I get to my surprise:

```
jorge@dell-desktop:~$ alsamixer 

alsamixer: function snd_ctl_open failed for default: No such file or directory****
```

Actually I have no sound at all in my laptop..

Is that all because I installed the *recommended* updates?!?!

---

### Post by geo909 on 2008-11-28
Ok, so next time I rebooted, I've chosen an older entry from the grub menu (is than an older version of kernel?) and the sound works again.. SO is that a bug for the latest updates? Should that be fixed or should I load the older version from now on?

---

### Post by zach4618 on 2008-11-29
I'm having the same problem with my audio. Only thing that I did was install recommended updates. BTW - I have the same problem with my desktop and laptop, so Im pretty sure its not a speaker or hardware problem.

---

### Post by zach4618 on 2008-11-29
Fixed:

Applications > Sound & Video > Sound Recorder > File > Open Volume Control > Adjust the PCM Volume (was muted for me)

---

### Post by geo909 on 2008-11-29
> **zach4618 said:**
> Fixed:

Applications > Sound & Video > Sound Recorder > File > Open Volume Control > Adjust the PCM Volume (was muted for me)

defenitely not muted for me..
I'm using the older entry in grub to get my sound working.  
I have heard complaints about the pulse audio implementation in ubuntu, it might be something with it..

---

