---
title: "KWorld 878 RF TV Tuner Card"
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by PaRRoT.it on 2005-05-07
I've a KWorld 878 RF TV Tuner Card that doesn't work under Ubuntu.

Someone know what conf and what software I need to use?

---

### Post by stepper on 2005-05-07
Hope this helps:

```

sudo gedit /etc/modules
```
and then put bttv in the list of modules like this:
> 
ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
snd_via82xx
8139too
bttv
ptserialNow create the bttv module like this
```
 sudo gedit /etc/modprobe.d/bttv
```
And copy this into this file
> # i2c
alias char-major-89 i2c-devb
options i2c-algo-bit bit_test=1
# bttv
alias char-major-81 videodev
alias char-major-81-0 bttv
# My TV Card
options bttv card=78 tuner=1 radio=1 pll=1 adc_crush=0

Change the tuner options :
1= Phillips Pal
Get the full list here [http://xawdecode.sourceforge.net/aideUS/htmlpage/TVCardall.htm](http://xawdecode.sourceforge.net/aideUS/htmlpage/TVCardall.htm) and choose the appropriate one for you.

---

### Post by PaRRoT.it on 2005-05-07
Thank you.
What software (for Gnome) you suggest me to use my tv tuner?

---

### Post by stepper on 2005-05-08
[QUOTE=PaRRoT.it]Thank you.
What software (for Gnome) you suggest me to use my tv tuner?[/QUOTE]
Glad I could help!

Zapping Tv viewer: 
sudo apt-get install zapping

or TVtime
sudo apt-get install tvtime

---

### Post by digiital on 2005-05-14
NEVER MIND. Stupid me some how had disconnected the coax and of course it wasn't able to find anything when scanning for the channels. All is well now.

=======================

Has anyone had luck with this kworld card?

The tuner I have in mine is labels as TNF-5831-MMF and I can't seem to find any tuner that works with this one. I've just about when from 1 to 45 and nothing. Looks like I might be out of luck. Anyone have any ideas?

I could swear I had at one point had it up and running in Mandrake.

---

### Post by xonuxus on 2006-11-25
I have a Much Tv tuner... I've installed TV time, Xawtv, Zapping tv viewer but none of these programs seem to work... I have only one channel found and no sound... I tried to change setting... for Europe... Pal... nothing works...](*,)

---

