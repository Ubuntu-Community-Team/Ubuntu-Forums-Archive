---
title: "sleep? hibernate? I just want my battery to last longer"
date: 2006-03-09
forum: Hardware &amp; Laptops
---

### Post by Bou on 2006-03-09
Hi, I'm totally new to laptops so I've never used sleep or hibernate before.

Starting this week, I'm using my new laptop with Dapper for my work, and I need it to last at least 2 hours. The power manager says I have 100 minutes when it's fully loaded, so I need to save power.

Currently I just power off the computer when I'm not gonna be using it for a while, but I'd like to know what sleep and hibernate can do for me. I've tried them a couple of times, but the screen just goes black and I don't know how to get it working again. It turns unresponsive and in the end I have to keep the power button pressed to turn the laptop off, then power on again.

Also, is there anything else I can do to extend the battery life? this time limit makes it feel like one of those EVA robots, they were totally awesome but had to be plugged all the time which was a turn-off.

Thanks for any help.

---

### Post by ranf on 2006-03-09
For a general overview look at this guide:
[http://www.gentoo.org/doc/en/power-management-guide.xml](http://www.gentoo.org/doc/en/power-management-guide.xml)

According to the chart the most power consuming component is the display.
So dim it. 
Let the screen saver kick in early.

---

### Post by Bou on 2006-03-09
[QUOTE=ranf]For a general overview look at this guide:
[http://www.gentoo.org/doc/en/power-management-guide.xml](http://www.gentoo.org/doc/en/power-management-guide.xml)

According to the chart the most power consuming component is the display.
So dim it. 
Let the screen saver kick in early.[/QUOTE]

Thanks, I took a good look at the guide (didn't understand most of it, though).

But I would like just to be able to make the computer sleep/hibernate, and still be able to use it.

---

### Post by ranf on 2006-03-09
There are a lot of postings in the forums. Search for them. 
Or tell us what specific brand and model you have.

The wiki also has a lot, i.e.:
[https://wiki.ubuntu.com/LaptopTestingTeam/FAQ?highlight=%28hibernate%29](https://wiki.ubuntu.com/LaptopTestingTeam/FAQ?highlight=%28hibernate%29)

---

### Post by Bou on 2006-03-09
[QUOTE=ranf]There are a lot of postings in the forums. Search for them. 
Or tell us what specific brand and model you have.[/QUOTE]

I already looked, but I haven't found anything useful for me anywhere. Sory, I really need help here.

My laptop is a Packard Bell R9750, please tell me if I can provide any other useful data.

Thanks.

---

### Post by ranf on 2006-03-10
Ouch, only 4 links in google for this model.

Ok let's start with finding out what the kernel knows about ACPI sleep modes:
```
dmesg | grep supports
```

---

### Post by et_the_beta_tester97 on 2006-03-11
dude, when you put ur lappy in hibernate/sleep, its normal for the laptop screen to go blank..the only way you can turn it back on is by pressing the powerbutton...

there are other ways of conserving battery power..those are:
--turning down the brightness on the screen
--turning off the hard drive when it isnt in use for a period of time (software will turn that off for you)
--if you have a mobile processor, setting hte BIOS to turn down the speed will conserve battery power. (the processor will only slow down when the batterie is the only source of power)


---CJ

---

### Post by Bou on 2006-03-12
Thanks guys, and sorry for the delay. I was out for the weeend.

[QUOTE=et_the_beta_tester97]dude, when you put ur lappy in hibernate/sleep, its normal for the laptop screen to go blank..the only way you can turn it back on is by pressing the powerbutton...[/QUOTE]

Yeah I know that... the thing is, the screen remains blank EVEN after pressing the power button.

Ranf, here's the output. I'm afraid I don't really know what it means, though.

> [4294670.765000] ACPI: (supports S0 S3 S4 S5)
[4294672.094000] ACPI: Processor [CPU0] (supports 8 throttling states)

---

### Post by kittycatsexycat on 2006-03-12
what exactly are you trying to find out....

---

### Post by kittycatsexycat on 2006-03-12
what exactly are you trying to do?

---

### Post by kittycatsexycat on 2006-03-12
what exactly are you trying to do? sorry this is multiple copies but my computer just crashed on me...

---

### Post by Bou on 2006-03-12
[QUOTE=kittycatsexycat]sorry this is multiple copies but my computer just crashed on me...[/QUOTE]

Doesn't matter. I want to be able to make my laptop sleep, then when I want to use it again just press the power button and have it work again.

Guess that's how sleep mode works. But when I put my laptop to sleep, then press power, (which should get it running again) the screen remains blank. And I have to keep the power button pressed to fully power the laptop down, then start the whole system again.

Which is NOT supposed to be how sleep mode works.

I don't know if I'm making myself clear.

---

### Post by X-Wes on 2006-03-13
Fun oddity to try:

When your computer comes out of standby or hibernate, try pressing ALT+F7. This may or may not work depending on what is actually wrong. In an ideal case, this will put your display back into the graphical interface.

---

### Post by Bou on 2006-03-13
[QUOTE=X-Wes]When your computer comes out of standby or hibernate, try pressing ALT+F7. This may or may not work depending on what is actually wrong. In an ideal case, this will put your display back into the graphical interface.[/QUOTE]

Just did, nothing happened. I tried CTRL+ALT+F7 as well, just in case.

---

### Post by ranf on 2006-03-13
[QUOTE=Bou]
Ranf, here's the output. I'm afraid I don't really know what it means, though.[/QUOTE]
S3 - sleep mode (suspend to RAM)
S4 - hibernate mode (suspend to disk)

On my machine sleep behaved like yours. That doesn't mean that you can't get it working with some tweaks.

But hibernate should work.
[http://ubuntuforums.org/showthread.php?t=90466](http://ubuntuforums.org/showthread.php?t=90466)

---

