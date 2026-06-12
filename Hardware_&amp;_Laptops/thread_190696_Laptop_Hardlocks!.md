---
title: "Laptop Hardlocks!"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by emrys on 2006-06-06
Hi,

I'm having some random hard locks from time to time (more than once a day is normal) that I thought would be gone with dapper final.

I have an ACER 1502 with the funny Broadcom wireless chip, maybe it is related with that.

Posting here to check out if someone else is having this kind of problems to try to define it better before dipping in bugzilla.

Any help will be highly appreciated :)

---

### Post by gerbman on 2006-06-06
[QUOTE=emrys]Hi,

I'm having some random hard locks from time to time (more than once a day is normal) that I thought would be gone with dapper final.

I have an ACER 1502 with the funny Broadcom wireless chip, maybe it is related with that.

Posting here to check out if someone else is having this kind of problems to try to define it better before dipping in bugzilla.

Any help will be highly appreciated :)[/QUOTE]I started getting the same random hardlocks a while back on my Dell Latitude D810. The hard drive failed the diagnostics test included on the CD that came with the laptop. I sent in for a new drive and haven't had problems since. Just something to keep in mind.

---

### Post by Didjit on 2006-06-06
I have the same problem, but its more frequent then once a day. Nothing obvious in the System log (at least from what I know)..Quite frustrating.... HP Omnibook 6100.

Didjit

---

### Post by Johnsie on 2006-06-07
Same here... locks every hour or so when being used. I never had this problem with Breezy so it's definitely a Dapper downfall... Shame 'cos Dapper ran really fast apart from that.

---

### Post by emrys on 2006-06-07
[QUOTE=gerbman]I started getting the same random hardlocks a while back on my Dell Latitude D810. The hard drive failed the diagnostics test included on the CD that came with the laptop. I sent in for a new drive and haven't had problems since. Just something to keep in mind.[/QUOTE]
Well, the thing is this does not happend with windows so, maybe I can discard some hardware problems?

1.What kind of wifi are you using?
2.Graphic card?
3.¿?

Mine:
1.Broadcom
2.ATI 9600

---

### Post by Patsoe on 2006-06-08
Are you using the fglrx driver with that Radeon 9600?
That caused hardlocks for me. No problems with the "ati" driver.

---

### Post by flurdy on 2006-06-08
[QUOTE=Johnsie]Same here... locks every hour or so when being used. I never had this problem with Breezy so it's definitely a Dapper downfall... Shame 'cos Dapper ran really fast apart from that.[/QUOTE]

Yes . Same here the screen freezes after using for some time. eg 1hr ish . but is not consistent. And nothing obvious in syslog.

No problems in breezy so some new driver must be causing it. 
(My laptop os a Sony vaio PCG-GR300p. )
Actually during dist-upgrade from breezy it reset it self thus foobaring the upgrade. so i had to do a fresh install.



What steps are people planning todo to narrow down what is failing?

---

### Post by emrys on 2006-06-08
[QUOTE=Patsoe]Are you using the fglrx driver with that Radeon 9600?
That caused hardlocks for me. No problems with the "ati" driver.[/QUOTE]
Yep, ATI 9600 and fglrx here.

Will try to change that to ati and see what happens. I'll lose 3D acceleration though, right?

---

### Post by Didjit on 2006-06-09
Have ATI here too (not in front of my lappy now, not sure the exact model). 

I did a fresh install of Dapper and it appears that the default driver is ati (Driver="ati" in Xorg.conf, right?).  I was going to try to flgrx and I followed these instructions [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide). Both manually and using the repos did not work. Couldn't start X, didn't play w/it too much, just reverted back to ati.

So, is the feeling that the ATI drivers are finicky dapper causing us problems?

Didjit

---

### Post by Patsoe on 2006-06-09
hmmm. I tried the fglrx drivers again, this time adding a line "fglrx" to /etc/modules. I'm not sure why that's different from just having the system sort out the loading of this module - maybe the module gets loaded at an earlier stage now - but whatever the reason: no more hardlocks when I switch consoles.

---

### Post by Didjit on 2006-06-09
Ok, I'm conviced ATI drivers are at fault. I changed my Xorg config to:* Driver "vesa" *Probably not getting the full potential out of my graphics card, but the Hardlocks seemed to disappear.

BTW, for the life of me I could not get Driver "fglx" to work w/X. I'll keep playing, but at least now I can use my laptop w/o hardlocks every hour.

Chris

---

### Post by emrys on 2006-06-10
Still having some hardlocks... I'm afraid it can be a hard drive problem...

How can I check that?

---

### Post by flurdy on 2006-06-13
[QUOTE=Didjit]Ok, I'm conviced ATI drivers are at fault. I changed my Xorg config to:* Driver "vesa" *Probably not getting the full potential out of my graphics card, but the Hardlocks seemed to disappear.

BTW, for the life of me I could not get Driver "fglx" to work w/X. I'll keep playing, but at least now I can use my laptop w/o hardlocks every hour.

Chris[/QUOTE]

Cant get fglx to work either.
Using the ati driver and it locks.
Will try the basic vesa driver.

This is annoying, but i think ill persevere for one more week, if not back to breezy.
Been ok if was something trivial that doesnt work. but a complete crash several times a day is tedious.

---

### Post by flurdy on 2006-06-13
[QUOTE=flurdy]Cant get fglx to work either.
Using the ati driver and it locks.
Will try the basic vesa driver.

This is annoying, but i think ill persevere for one more week, if not back to breezy.
Been ok if was something trivial that doesnt work. but a complete crash several times a day is tedious.[/QUOTE]

Yup. used vesa driver all day and no lock ups.
And I cant really see any difference. Will there be, on a laptop with probably neglible 3d capabilities?

---

### Post by Didjit on 2006-06-24
[quote=flurdy]Yup. used vesa driver all day and no lock ups.
And I cant really see any difference. Will there be, on a laptop with probably neglible 3d capabilities?[/quote]

Well, I started to play DVD's (for the kids) and the limitations of the vesa driver was exposed. So, dug around and found this [http://ubuntuforums.org/showthread.php?t=150854](http://ubuntuforums.org/showthread.php?t=150854)

I changed driver back to "ati" and added Option "KernelModuleParm" "agplock=0"
DVD play back is much, much better. Gonna see if this fixes the lockup problems with the ATI driver...... So far so good.  Just sharing.

Didjit

---

### Post by gerbman on 2006-06-24
[QUOTE=flurdy]Yup. used vesa driver all day and no lock ups.
And I cant really see any difference. Will there be, on a laptop with probably neglible 3d capabilities?[/QUOTE]It depends on your video card. I have the X600 in my laptop and it makes an enormous difference.

---

### Post by duffydack on 2006-07-15
You think maybe my problem is related ? 
[http://ubuntuforums.org/showthread.php?t=211553&highlight=lock](http://ubuntuforums.org/showthread.php?t=211553&highlight=lock)
I`ve only tested while using latest ati 3d driver, not the repo`s version or the default standard ati/ubuntu driver.  I got fed up and am back on windows till i find a fix.

---

