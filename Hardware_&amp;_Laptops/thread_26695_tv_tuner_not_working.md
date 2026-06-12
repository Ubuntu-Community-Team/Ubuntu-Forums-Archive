---
title: "tv tuner not working"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by bryan986 on 2005-04-13
I seem to be almost all the way there, but not quite

I do "sudo modprobe bttv card=37 tuner=2"

but when I run "sudo tvtime" it is just all static, you can slightly make out a channel in black in white, but I cant change channels or anything

In the terminal I get this error "Can't get tuner info: Invalid argument", which would suggest I did not give it the right card number for bttv, but I tried many other numbers, and each did not change what tvtime did at all

The card is a Prolink Pixelview Playtv pro ultra

There is more helpful information at [http://www.linuxquestions.org/hcl/showproduct.php?product=1127&sort=8&cat=myprod&page=1](http://www.linuxquestions.org/hcl/showproduct.php?product=1127&sort=8&cat=myprod&page=1) but it did not fix the problem

I have seen some suggestions to "modprobe cx8800" with a card=37 or tuner=2 attached on the end, but when I try to do that it just says "FATAL: Error inserting cx8800 (/lib/modules/2.6.10-5-386/kernel/drivers/media/video/cx88/cx8800.ko): Unknown symbol in module, or unknown parameter (see dmesg)" which is curious if other people have been able to do that

And it works in windoze, so the card itself is not at fault

Thanks in advance

---

### Post by joaoeb on 2005-04-14
If the code of the card is pv-bt878p+ Rev-9f (look in the PCB)
use this:
options bttv card=72 pll=1 radio=0(1 if it have a radio tuner)
options tuner type=5
(And if you have sound problems try this:)
options snd-card-ens snd_index=0
options msp3400 mixer=1
every thing in /etc/modprobe.conf

And audio = mono in the TV software.

---

### Post by bryan986 on 2005-04-14
Well ive got color now, with fairly good quality, but I still get "Can't get tuner info: Invalid argument" in the terminal, and I cannot switch channels. I tried tuner #2 also because of the ntsc but no luck

---

### Post by joaoeb on 2005-04-14
Well, aparently your card is a diferent revision from mine. 
You have to look at the card. Disconect it and search for the model number. 
Probably it will be PV-BT878P+ Rev-XX. the Rev part is very important. Mine is 9F. If I remind there 6 revisions of this board. Take a note from this code. 
Also take note of the codes on every chip in the board. It will help because one of them is the tuner chip.
Try a google search with the entire model number + linux (pv-bt878p+ rev-XX linux). Maybe you find what you need. 
If not, ask me and I will help.

(I hope my english make sense for you)

---

### Post by bryan986 on 2005-04-15
I searched for "PV-TV304P+ linux" which is what mine is, but the only thing I found, in english anyway, was this: [http://www.spinics.net/lists/vfl/msg15015.html](http://www.spinics.net/lists/vfl/msg15015.html)
But that tuner/card combination didnt work either, and I cant get any picture at all now just static, even with the previous settings

---

### Post by joaoeb on 2005-04-15
Try this: [http://anmsid.blogsome.com/2005/03/18/pixelview-play-tv-pro-cx88-quick-installation/](http://anmsid.blogsome.com/2005/03/18/pixelview-play-tv-pro-cx88-quick-installation/)

---

### Post by bryan986 on 2005-04-17
Ah thank you!

There was a bit in there about specifying the options for the cx88xx driver, so I did that instead of for the bttv driver, and it works like a charm!

I put
```

options cx8800 video_nr=0 radio_nr=0
options cx88xx card=3 tuner=2

```
into /etc/modprobe.d/bttv

and then in the terminal I did
```

sudo modprobe -r cx8800
sudo modprobe -r tuner
sudo modprobe cx8800

```

and now it works like charm (with some picture adjusting)

thanks for pointing that site out and thanks for sticking with me!

---

