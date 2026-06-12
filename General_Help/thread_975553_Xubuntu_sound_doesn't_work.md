---
title: "Xubuntu sound doesn't work?"
date: 2008-11-08
forum: General Help
---

### Post by faustism on 2008-11-08
hello. Im using xubuntu and the sound doesn't work. It can beep, like if i hit the backspace button in an empty text feild. Because of this i am assuming that the sound card (ISA) is plugged in, because the speaker wire runs from that.  I have seen other threads about problems with xubuntu sound but none of them were resolved.  Has anyone come up with a solution
by the way, this is xubuntu 8.10.

thank you in advance

---

### Post by roger_1960 on 2008-11-08
Hi

This might not be it, but.......

Run 'alsamixer' in terminal and check that the master vol. and the PC speaker vol.(on the far right) are set above zero.  I made this error after a new install.

---

### Post by faustism on 2008-11-08
i tried that and i got this message:

```
alsamixer: function snd_ctl_open failed for default: No such file or directory

```
 do i have to install something?

thanks for the response

---

### Post by faustism on 2008-11-29
Does anyone know what I should do to get rid of that error?

---

### Post by faustism on 2008-12-21
yay! it works now. what i did was...

```
asoundconf list
```

then i picked one of the cads (there was only 1)

```
asoundconf set-default-card cardname
```

replace card name with the card you want from the first list

restart the computer.

```
alsamixer
```

make sure that the volume is above nothing

play music!

---

