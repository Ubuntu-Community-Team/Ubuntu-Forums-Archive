---
title: "Add USB 3.0 or 3.1 in an old computer?"
date: 2017-08-30
forum: Hardware
---

### Post by alforddm on 2017-08-30
I have an old computer (Dell inspiron 531) that was given to me (did I say it was old?).   I put a cheap nvidia graphics card with hdmi out, threw in an old hard drive I had laying around, and added a usb flash drive permanently as  SWAP and have been using it as a mythbuntu system.   It's nothing speedy but it does record and allow us to watch shows (just don't try to transcode anything).   So cheap for the win!

Lately I've been wondering if it would be possible to add a 3.0 or 3.1 usb card?   It only has PCI1 but it does have an open slot.   My idea was to add a larger flash or maybe a usb hard drive for extra movie storage and possibly a bit more speed for the swap?    It occurred to me the swap might be faster than RAM in that case:p.   

 Is it even feasible?   Would I gain anything or would the other  hardware on the system negate any benefit?

---

### Post by mastablasta on 2017-08-31
> **alforddm said:**
> 
Lately I've been wondering if it would be possible to add a 3.0 or 3.1 usb card?   It only has PCI1 but it does have an open slot.   My idea was to add a larger flash or maybe a usb hard drive for extra movie storage and possibly a bit more speed for the swap?    It occurred to me the swap might be faster than RAM in that case:p.   


Do you even need swap? and if you do putting it on USB drive is not really a good idea, that is unless you reduced swapiness.

What benefit would 3.0 add. are you trasnferign files between drives? for watching shows etc. the 2.0 version is enough.

> 
 Is it even feasible?   Would I gain anything or would the other  hardware on the system negate any benefit?

probably not much gain if all you do is watch stuff on it (if it even works at full speed).

not sure what your specs are  but if this is what you have : Dell Inspiron 531 - tower - Athlon 64 X2 3800+ 2 GHz - 2 GB, then the PC is not bad at all.

My main PC is still Athlon 3200 single core and can do most things, just transcoding videos takes a while (1 GB takes about 45 mins). linux runs fast on it, though its OS is still winXP. it can run many games. the 3D intensive ones have to be older than 2008/2009, but some new strategic ones run just fine on it, though they might take a wile to load. it has UBS 2.0 plugs and i can live with that just fine.

for "media PC" i use Raspberry PI (with USB 2.0). it works just fine, though i am not sure about recording since we never recorded. we have back in time feature on the TV set (retains all shows& movies for 7 days), so we didn't have the need for it. 

in short if the baord is compatible with USB3 module and if it can handle the trnasfer speed (check all specs etc.) then go for it. although i think SATA would be faster if you really need the speed.

---

### Post by sudodus on 2017-08-31
> **mastablasta said:**
> Do you even need swap? and if you do putting it on USB drive is not really a good idea, that is unless you reduced swapiness.
...
for watching shows etc. the [USB] 2.0 version is enough.
...
although i think SATA would be faster [than USB 3 and much more likely to work] if you really need the speed.

+1

[additions/clarifications by me within 'square parentheses']

---

### Post by alforddm on 2017-08-31
Thank you for the reply.   

Adding the usb as swap really did help the performance.   I just checked and this machine only has 1G of ram.   It was swapping badly and really laggy until I added the usb drive, now it is usable.     I already have two sata hard drives in it (the one it came with and the one I added) so my sata plugs are full and while I could replace one of the hard drives, I'm not really feeling the desire to swap out hard drives.   I may just get a usb 3.1 and check and see if it works.   If it doesn't, I have a nicer comp that also lacks 3.1 and could use the card.

---

### Post by Autodave on 2017-09-01
What version of Linux did you install on that? I have machines with one gig RAM and rarely if ever see swap.  If you installed Ubuntu, that would explain it: Ubuntu is a rather heavy desktop. Xubuntu is much lighter and still can run all the same programs. Lubuntu is even lighter.

---

### Post by Yellow Pasque on 2017-09-01
Get more RAM and quit using the flash drive as swap before you kill it. $25 will get you a 4GB kit of DDR2-800. 

>  It only has PCI1 but it does have an open slot. 

Is that a classic PCI slot or PCI-Express x1 slot? I googled, but there are a lot of different configurations for the Inspiron 531, so I can't tell.

Maybe you can give some more info on your system:
```
lspci
sudo dmidecode -t memory
```

---

