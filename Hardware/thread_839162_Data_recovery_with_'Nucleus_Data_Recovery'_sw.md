---
title: "Data recovery with 'Nucleus Data Recovery' s/w"
date: 2008-06-24
forum: Hardware
---

### Post by jpprost on 2008-06-24
Hi there,

I bet you can guess most of the story from the title: my HDD crashed and I'm now missing badly some data for which I have no recent backup... I know, I know, very wrong backup management. I plead guilty, but my problem remains.

I've tried the fridge thing, but it didn't work for me: the drive was not even recognised (I put it in a usb case). Haven't tried the freezer yet; might be better, I'm kind of dubious about it I must say.
So, now the best option that comes to my mind is to use a commercial s/w, like 'Nucleus Data Recovery':
[http://www.datarecoverylinux.com/](http://www.datarecoverylinux.com/)

But I can't find any decent user review for it: does anyone have experience with it? Or maybe with an alternative soft?
Going for expensive services is not an option unfortunately: way out of budget.
Btw, the drive is formatted in ext3.

Cheers,
JP

PS: there seems to be a few alternative softs:
[http://www.freedownloadmanager.org/downloads/ext3_data_recovery_software/](http://www.freedownloadmanager.org/downloads/ext3_data_recovery_software/)
Anything there you'd suggest?

---

### Post by thideras on 2008-06-24
> **jpprost said:**
> the drive was not even recognised (I put it in a usb case)That is the issue right there, either there is a setting incorrect in the BIOS preventing it from being detected or the logistics of the drive are bad.

**Please, never ever put a drive in the freezer, that is not going to fix this issue at all!**

Freezing a drive is a last ditch effort to unstick the platters or heads by making the metal shrink.  After you freeze it and plug it in, you have an extremely high chance of ruining the drive as it reaches room temperature.


What you need to do is test this in another system to make sure that it isn't a setting in the BIOS.  Since it isn't recognized, software recovery will have no affect.

Things to try/check:
-If IDE, try another cable
-If IDE, try its own cable
-If IDE, verify jumpers
-If SATA, change cable and ports, use a known working one
-Try another computer
-Try a known working drive in the exact same cable/port/computer

---

### Post by jpprost on 2008-06-25
Hi,
Thanks for your reply.

> **thideras said:**
> 
Things to try/check:
-If IDE, try another cable
-If IDE, try its own cable
-If IDE, verify jumpers
-If SATA, change cable and ports, use a known working one
-Try another computer
-Try a known working drive in the exact same cable/port/computer

I did all this -- everything's unsuccessful. I still can't see it. In fact, the usb case even shows a red light when I plug it in. The easy guess is that the disk can't be read at all, right? Any chance I can force mounting it anyway? 
It looks to me now very much like a hardware failure, but since I can't recall hearing any suspicious noise I was hoping it's not completely dead yet.

Cheers,
JP

---

### Post by greco8523 on 2008-06-25
sounds to me the hard drive is completely gone. However, whats the brand model and firmware maybe I might be able to help. By the way no data recovery software is going to help in this case.

---

### Post by thideras on 2008-06-26
> **jpprost said:**
> Hi,
Thanks for your reply.



I did all this -- everything's unsuccessful. I still can't see it. In fact, the usb case even shows a red light when I plug it in. The easy guess is that the disk can't be read at all, right? Any chance I can force mounting it anyway? 
It looks to me now very much like a hardware failure, but since I can't recall hearing any suspicious noise I was hoping it's not completely dead yet.

Cheers,
JPJust to verify, my last comment was to try a known working drive in the computer.  You stated that nothing was successful, the working drive did not work in that computer?

---

### Post by jpprost on 2008-07-01
Hi,
sorry for the delay.

I think there's been a misunderstanding, so here's a fresh summary:

(i) the computer's a laptop, so no possibility of changing cables;
(ii) the failing HDD was the main (and only) one;
(iii) last time I tried to boot up from it as an internal drive, I got swearing messages from Linux (bad sectors), so I don' think the problem is coming from the BIOS -- other reasons for that later. For obvious reasons I'd like not to reproduce the message unless really necessary;
(iv) I've unplugged the drive and put it in a working USB case;
(v) in the first place I mistakenly forgot to change the jumper, which is why it wasn't recognised; silly me...
(vi) I now put the jumper on position "device 0", and I got some improvement: I can now see the USB Drive icon in the browser (nautilus), but it still can't be mounted. The drive has three positions for the jumper: device0, device1 and "cable sel.". It was initially set to "cable sel." and it's now on "device0".

> **greco8523 said:**
> sounds to me the hard drive is completely gone. However, whats the brand model and firmware maybe I might be able to help. By the way no data recovery software is going to help in this case.

The drive is a 30GB Fujitsu. I would agree with you on that the drive was gone, until I fixed the jumper. Now I'm not so sure anymore, don't you think?

> **thideras said:**
> Just to verify, my last comment was to try a known working drive in the computer.  You stated that nothing was successful, the working drive did not work in that computer?

Yes, I did try a working hdd on the computer: the bios recognised it fine.

Sorry if I misled you initially.

Cheers,
JP

---

### Post by jpprost on 2008-07-09
Hi,

Does anyone know a way to read or copy or restore or force mounting an external USB HDD that doesn't want to be mounted?
It was an internal hard drive from which I used to boot, until it start failing because of bad sectors. When put in an external USB case the 'USB drive' icon now shows up in Nautilus, but the disk is still unmountable.
Any ideas that might help me recover my data will be very welcome.

Cheers,
JP

---

### Post by Dark_Stang on 2008-07-22
If your hard drive has crashed and you want to save the data, stop what you're doing. Every time that drive spools up you run the huge risk of making it even worse. If you can't mount it and the lower end data recovery tools aren't working, take it to a data recovery center. For example, any best buy/geek squad can have it sent in for you and get an estimate. There may be a local shop around as well.

---

