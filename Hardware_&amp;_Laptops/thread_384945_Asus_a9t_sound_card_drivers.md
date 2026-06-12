---
title: "Asus a9t sound card drivers"
date: 2007-03-15
forum: Hardware &amp; Laptops
---

### Post by ramirezz on 2007-03-15
Hi guys... I have a big problem. I am DJ and I have a big party soon. My  Asus A9t have some issues with windows xp so I decided to use Ubuntu.
Everything is working great except my sound card (of course). Ubuntu doesn't recognize it. I couldn't find any drivers for Ubuntu anywhere.
Is there any way to solve this problem?
Please help... I need to fix this ASAP!!!
thanks

---

### Post by mcniac on 2007-03-29
a friend of mine is having the same issue, the soundcard seems to be a sis7012 which should work with some intel module 8x something , sorry for the lack of detail but i don't have that notebook handy right now) linux recognizes the soundcard but never managed to make it work, any help?

Thanxs

---

### Post by AlexanderTumanovsky on 2007-05-14
Same problem here... Asus A9T, no sound... XMMS plays song, but I cannot hear anything... Tryed some things, which I found in google by request "Ubuntu no sound", but nothing worked. Please, help.

---

### Post by Francois Rigault on 2007-06-17
The SiS7012 sound card (the one on the A9T laptop) will work by removing Alsa modules and enabling the corresponding DSP driver (i810_audio). You need to configure XMMS to use the DSP (in XMMS options).

Regards

---

### Post by djuka233 on 2007-10-24
Can someone, please, write more details?

Which steps are?? What commands???

Thanks in advance.

---

### Post by hants on 2008-02-21
hi,

 Same Problem here , checked it with fedora,ubuntu,vector,slackware,debian, sidux,suse in their most current version.
It happens with all Linux distributions although it doesnt happen on 
any windows
freebsd >= 6.x derivates (the only ones i checked)

it furthermore must be determined wether the following fix always works for this card (not just in tha a9t) with the snd_intel8x0 alsa module(default) : 
Card: SiS SI7012                                                     



So here comes the Solution working for any distribution and i just post it here because its the first hit in google ;)

a)
    I) open console
    II) su to root
    III) run alsamixer
        go right with the arrow keys and 
          1) <Master_S> (Master Surround):
                   unmute (press m), increase volume (up-arrow key) 
          2) <PCM>:
                   unmute (press m), increase volume (up-arrow key) 
          3) <Channel> (Channel Mode):
                   set to 4 or 6 (up-arrow key)
          4)<Exchange> (Exchange Front/Surround)
                   unmute (press m)
          5)exit 
                  press Esc
b) (not recommended)
    instead of setting the settings by hand you can also use this working configuration file:
     1) fire up console
     2) su to root
     3) alsactl restore -f mixersettings.txt

So hopefully Ubuntu and other Distributions will include this fix by default in future versions.

cya,
andreas

---

### Post by ZorgTheDestroyer on 2008-06-23
Hey this guy foud the Real sollution!

[http://ubuntuforums.org/showthread.php?p=5247309#post5247309](http://ubuntuforums.org/showthread.php?p=5247309#post5247309)

---

