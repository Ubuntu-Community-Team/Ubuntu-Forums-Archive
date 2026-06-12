---
title: "How can I find out what upgrade would most improve performance?"
date: 2010-05-19
forum: Hardware
---

### Post by Daminator on 2010-05-19
Hello all,

I have an old Laptop that I've given to my wife. It's been great far years, but is finally showing it's age and is struggling a bit with Ubuntu. I know I could install a different Linux, but the whole family uses Ubuntu so I'd like to stick with it to avoid headaches.

Is there a utility that can either simply look at my spec, or even better, examine my usage, and then tell me what upgrades would make the most difference to performance? I don't mind spending a bit of money on it, but can't afford to randomly upgrade things in the hope that performance will improve.

Thanks
Damian

---

### Post by MartyBuntu on 2010-05-19
What brand and model is this laptop?

---

### Post by uOpt on 2010-05-19
If it's a laptop your only choices are more RAM and a newer harddrive anyway, right?

Using `vmstat` to see how short you are of RAM during your workload.

And stop using Firefox :)

---

### Post by snowpine on 2010-05-19
Hi Damian, if you told us the system specs, perhaps we could give meaningful advice. :)

All I can do is steer you towards the [Ubuntu recommended system requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements") and suggest you improve any area where your hardware falls short:

> Ubuntu Desktop (GUI) Installation

    * 1 GHz x86 processor
    * 512 MiB of system memory (RAM)
    * 5 GB of disk space
    * Graphics card and monitor capable of 1024x768
    * CD-ROM drive
    * Sound support
    * Internet access

Failing that, you could install a lighter-weight Ubuntu such as Xubuntu or Lubuntu, which would give you the same applications and functionality with a different user interface.

---

### Post by Daminator on 2010-05-19
Wow, thanks for the quick replies.

The laptop is a Compaq Presario X1000 machine.

CPU = Intel Pentium M Processor - 1600MHz
Memory = 512Mb (it said 497.2, but I'm sure it's 512)
Graphics card = ATI Mobility Radion 9200

Interesting that you said 'stop using Firefox' I have noticed that it crawls a lot when Firefox is running. I haven't noticed that on any other machine though.

Would a bit of memory patch this machine up, or is it just on it's last legs?

Can I even put more memory in this machine? 512 could be the limit for all I know.

Cheers
Damian

---

### Post by cascade9 on 2010-05-20
> **Daminator said:**
> Is there a utility that can either simply look at my spec, or even better, examine my usage, and then tell me what upgrades would make the most difference to performance? I don't mind spending a bit of money on it, but can't afford to randomly upgrade things in the hope that performance will improve.


'sudo lshw' will show you all the system devices (probably in more setail than most people need to be honest). 

'htop' will show you resource usage (CPU time/RAM). 

With those system specs, I would guess that you will be shorter on RAM than on CPU. RAM is pretty easy to upgrade, CPUs can take some work to tell if you can upgrade. 

Edit- measuring CPUs be pure Mhz is a flawed method. There are several Pentuim M chips running at 1600Mhz- the 2 main versions are original P-M 1.6 (1MB cache, 400Mhz FSB) and the P-M 730 (2MB cache, 533Mhz FSB). A P-M 730 is noticable faster than a P-M 1.6. 

Compaq/HP can have a pain-in-the-**** site to navigate. I've tried have a look for the spec sheets there, and I couldnt find it easily. It would help if I have the info from the sticker that in normally under teh body of the laptop, see here- 

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01961011&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&lang=en&product=350715#N1045](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01961011&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&lang=en&product=350715#N1045)

You will need to click on 'find a specification sheet for a pre-configured notebook' ;) 

BTW, I'm sure that you can go to at least 1GB of RAM- 

[http://www.memory-up.com/Memory/CompaqPresarioX906_1GB333MHz.html](http://www.memory-up.com/Memory/CompaqPresarioX906_1GB333MHz.html)

> **uOpt said:**
> If it's a laptop your only choices are more RAM and a newer harddrive anyway, right?

Using `vmstat` to see how short you are of RAM during your workload.

And stop using Firefox :)

No, you've got more choices than just RAM/HDD. CPU upgrades are possible in a lot fo cases, and newer laptops can have upgradeable video cards (not that the OPs laptop can do this). 

Stop using firefox? Hopefully not thats not a push to chrome/chromium..google has enough power already IMO.

---

### Post by 00b00nt00 on 2010-05-20
Looking at your profile, are you still using Breezy?

Perhaps a fresh install of the latest and greatest Ubuntu (10.04 as of writing) is what you need. You should probably bag the 32 bit edition for your PC.

---

### Post by uOpt on 2010-05-20
That thing with be fine with 1.5 GB or whereabouts RAM.

For good measure slam in a modern harddrive. Doesn't have to be 7200 rpm (waste of money and battery), just a current production drive.

---

### Post by Daminator on 2010-05-21
That Compaq site is truely awful!

I know I have a "Compaq Presario X1097AP Notebook PC"

But there's no specification sheet for it!
[http://h10025.www1.hp.com/ewfrf/wc/documentSubCategory?tmp_task=prodinfoCategory&lc=en&dlc=en&cc=sg&product=374135&lang=en](http://h10025.www1.hp.com/ewfrf/wc/documentSubCategory?tmp_task=prodinfoCategory&lc=en&dlc=en&cc=sg&product=374135&lang=en)

This seems to indicate that I can go up to 2 gig of memory:
[http://www.crucial.com/uk/store/listparts.aspx?model=Presario%20X1000%20Series](http://www.crucial.com/uk/store/listparts.aspx?model=Presario%20X1000%20Series)

and thinks that there's 2x256 in there. I could buy one 1gig stick and leave one of the 245 sticks in there and see how that goes.

And don't worry cascade9. Google have some great products, but I refuse to use them.

Not sure how to check which of the 2 CPU types I have installed, but memory is probably the way to go from here anyway.

Thanks all
Damian

---

### Post by 00b00nt00 on 2010-05-22
OP, checked out your PC and there are BIOS and video firmware updates available. These may sort out your performance issues:

[http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?os=228&lc=en&cc=us&dlc=en&sw_lang=&product=374135#N2883](http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?os=228&lc=en&cc=us&dlc=en&sw_lang=&product=374135#N2883)

I'd say that 512MB is plenty for 'net surfing and the like.

---

### Post by cascade9 on 2010-05-23
> **Daminator said:**
> That Compaq site is truely awful!

It is....right pain to navigate IMO. 

> **Daminator said:**
> 
This seems to indicate that I can go up to 2 gig of memory:
[http://www.crucial.com/uk/store/listparts.aspx?model=Presario%20X1000%20Series](http://www.crucial.com/uk/store/listparts.aspx?model=Presario%20X1000%20Series)

and thinks that there's 2x256 in there. I could buy one 1gig stick and leave one of the 245 sticks in there and see how that goes.


You should be able to go to 2GB, that is the max RAM for most of the Pentium -M chipsts. Sometimes corporate manufacturers do put artifical limits on the max RAM however. :( 

> **Daminator said:**
> 
And don't worry cascade9. Google have some great products, but I refuse to use them.


;) 

> **Daminator said:**
> 
Not sure how to check which of the 2 CPU types I have installed, but memory is probably the way to go from here anyway.

Thanks all
Damian

The easiers way to check what CPU you are running is with sudo lshw. 

If you CPU cache (1) is 1024k, is a original P-M 1.6Ghz, if its 2048k, then its the later 730. 

lshw will also show what RAM slots are filled, and what size memory sticks are in there ;)

---

### Post by Daminator on 2010-05-28
I threw a 1gig card in there and took out one of the 256's. All seems significantly better now. Thanks for the help all !!

D

---

### Post by cascade9 on 2010-05-29
No problems :)

---

