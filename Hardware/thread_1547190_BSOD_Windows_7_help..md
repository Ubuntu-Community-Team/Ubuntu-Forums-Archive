---
title: "BSOD Windows 7 help."
date: 2010-08-06
forum: Hardware
---

### Post by Mr_VeRiTy on 2010-08-06
This is probably the WORST place to post this, but my sister's laptop running windows 7 32 bit keeps BSOD-ing, it is a new laptop, only a few days old, My laptop is the same as hers, it's an advent roma 3000, mine did exactly the same thing (infact it's the reason I switched to Ubuntu) when I first bought it. How can I fix hers (she is not tech savvy enough to use Ubuntu) I'd post in seven forums but I cba to create an account if im only going to use it once, plus I trust Ubuntu users more. How can I fix my sister's laptop???

---

### Post by dv3500ea on 2010-08-06
Dual boot with Ubuntu, then she can see for herself which operating system she finds easier to use. Ubuntu is fairly simple to use once all of the drivers, restricted codecs etc. are installed (you could do these tricky things for her). You don't *have* to be tech savvy to use Ubuntu (but it helps). I'm sure a working Ubuntu installation will be much easier to use than a BSODing Windows installation.

PS. you could download the [Ubuntu Manual]("http://ubuntu-manual.org/?lang=en_GB") for her.

---

### Post by Mr_VeRiTy on 2010-08-06
> **dv3500ea said:**
> Dual boot with Ubuntu, then she can see for herself which operating system she finds easier to use. Ubuntu is fairly simple to use once all of the drivers, restricted codecs etc. are installed (you could do these tricky things for her). You don't *have* to be tech savvy to use Ubuntu (but it helps). I'm sure a working Ubuntu installation will be much easier to use than a BSODing Windows installation.

PS. you could download the [Ubuntu Manual]("http://ubuntu-manual.org/?lang=en_GB") for her.
Yes but another reason I didn't install Ubuntu is that our wireless cards aren't fully compatible and disconnect every 30 mins, and she needs her internet for collage and things like that, I've already exhausted the forums on that topic though, so I'm just waiting to see if it's fixed in a future release. The reason I'm worried about her windows installation though, is because after a few days of owning my laptop, it stopped BSOD-ing but then boot up started taking longer and longer each time I turned it on, then one day I booted up and after 10 minutes of booting time the computer found no operating system (which led me to install Ubuntu.)

---

### Post by S.R on 2010-08-06
Did these two systems have this problem right out the box? What have you installed? When do you get the BSOD? What BSOD message are you getting? There are many questions that can be asked to even start to nail this problem down. 

Not all hardware will play well with Win7. You might want to check each device to see if it is compatible. If not you might consider a Vista roll back.

Check the logs to see if you have any obvious red flags as to what is causing the problem. I am guessing since you both have the same system with the same hardware it is a device conflict or driver issue (it could just as well be a program you have both installed). Try to disable devices that you are not using one at a time to see if the problem is isolated. 

Maybe you both by some freak of nature have bad memory modules. You can use Memtest86+ from [http://www.memtest.org/](http://www.memtest.org/) to check them. 

Me personally if I could return the computer and get another make/model that is what I would do. I think you will have better luck getting help to solve your wireless card issue though and then maybe you can migrate her to Ubuntu.

---

### Post by Mr_VeRiTy on 2010-08-06
> **S.R said:**
> Did these two systems have this problem right out the box? What have you installed? When do you get the BSOD? What BSOD message are you getting? There are many questions that can be asked to even start to nail this problem down. 

Not all hardware will play well with Win7. You might want to check each device to see if it is compatible. If not you might consider a Vista roll back.

Check the logs to see if you have any obvious red flags as to what is causing the problem. I am guessing since you both have the same system with the same hardware it is a device conflict or driver issue (it could just as well be a program you have both installed). Try to disable devices that you are not using one at a time to see if the problem is isolated. 

Maybe you both by some freak of nature have bad memory modules. You can use Memtest86+ from [http://www.memtest.org/](http://www.memtest.org/) to check them. 

Me personally if I could return the computer and get another make/model that is what I would do. I think you will have better luck getting help to solve your wireless card issue though and then maybe you can migrate her to Ubuntu.
Yes the BSOD problem was right out of the box, she has nothing installed but the standard bloatware that comes with it, The BSOD comes and goes too fast to read anything, and as for the logs, I don't even know where to find (or even how to read) them in windows. I did a memtest before installing ubuntu for the first time, they are fine.

---

### Post by S.R on 2010-08-06
Off the top of my head ... you should be able to get them with eventvwr.msc in the Run prompt.

Did you also run CHKDSK?

I am thinking you should focus more on a device or driver issue.

---

### Post by Mr_VeRiTy on 2010-08-06
> **S.R said:**
> Off the top of my head ... you should be able to get them with eventvwr.msc in the Run prompt.

Did you also run CHKDSK?

I am thinking you should focus more on a device or driver issue.
I'll have to try that tomorrow, as her laptop isn't here at the moment.

---

### Post by S.R on 2010-08-06
Also .... so you can read the BSOD

Right click Computer >  select properties > in the Start up and Recovery area click Settings> untag the box labeled "Automatic Restart."

I might be getting my Windows versions confused but it should still be along those lines or I know you can google it to find the way.

---

### Post by Mr_VeRiTy on 2010-08-06
> **S.R said:**
> Also .... so you can read the BSOD

Right click Computer >  select properties > in the Start up and Recovery area click Settings> untag the box labeled "Automatic Restart."

I might be getting my Windows versions confused but it should still be along those lines or I know you can google it to find the way.
Thanks :)

---

### Post by Dayofswords on 2010-08-06
> it is a new laptop, only a few days old,
you're still in warrenty, go back to the store and tell them, they have to fix it :p

---

### Post by Mr_VeRiTy on 2010-08-06
> **Dayofswords said:**
> you're still in warrenty, go back to the store and tell them, they have to fix it :p
That thought hadn't occurred to me, does it matter if she bought it online from Pc World, could she still take it to the PcWorld store nearest to her?

---

### Post by v1ad on 2010-08-06
system restore,try that

---

### Post by Dayofswords on 2010-08-07
> **Mr_VeRiTy said:**
> That thought hadn't occurred to me, does it matter if she bought it online from Pc World, could she still take it to the PcWorld store nearest to her?

call up the maker of the computer(hp, sony, w/e the maker is) if you bring it to the store they just handle the process, you just have to do the things manually, have your serial number (sticker on bottom and invopice from the order ready in case

---

