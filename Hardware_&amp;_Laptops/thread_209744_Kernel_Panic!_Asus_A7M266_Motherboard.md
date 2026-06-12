---
title: "Kernel Panic! Asus A7M266 Motherboard"
date: 2006-07-05
forum: Hardware &amp; Laptops
---

### Post by roxics on 2006-07-05
Honestly I've never been able to get things working right on this motherboard. I bought it several years ago brand new for $200 (the most I've ever spent on a motherboard) because Tomshardware.com said it was the best board out at the time.

I've never been able to really use it because windows always gives me a blue screen of death saying something about the ACPI. So it's been sitting in my basement for years now and I just got the bright idea that maybe it would work with ubuntu. It's got a stick of crucial 256MB DDR ram on it.

So I load ubuntu 6.06 and it says Kernel panic! and won't start. So I figured I'd try puppy linux just for kicks and once again it also says kernel panic but it also mentions the ACPI thing being shut off.

I look in my Bios (Award Medialion v6 1007 ...I think) and it says nothing about ACPI anywhere. So I load the BIOS defaults and still the same thing happens.

This thing has been sitting around too long and I've spent too much money on it back then so I've either got to get it working or throw it in the trash and say the hell with it once and for all.

Figured I'd ask around. Thanks

---

### Post by christhemonkey on 2006-07-05
Can you do a memtest on it?
(whilst booting select memtest option from grub menu)
((that is if its not kernel panicking before you've got round to installing it!))

Are you sure theres nothing in the BIOS about power managment?

---

### Post by roxics on 2006-07-05
[QUOTE=christhemonkey]Can you do a memtest on it?[/QUOTE]

Yeah I can do a memtest, what am I looking for though? I don't know what any of that means.
If the RAM was bad though would I just get a black screen. I've had ram go bad on me before and the result is just a nothing happening besides the sound of system fans.

[QUOTE=christhemonkey]Are you sure theres nothing in the BIOS about power managment?[/QUOTE]

Nothing that says or lets me select ACPI like the BIOS does on my other system.

---

### Post by cracker on 2006-07-05
If Windows BSODs and linux kernel panics every time, I'd have to say there is something seriously wrong with the motherboard. I would have RMA'd it two years ago when Windows refused to work with it.

---

### Post by randyh on 2006-07-05
Try turning on the acpi in the bios. (running 1008 beta1 bios on mine) I have the same bd and have ran several different linux distos on it, ubuntu 6.06 right now. Only issue is my crappy modem. right now have it triple booting w98, wxp, and ubuntu 6.06

randy

---

### Post by roxics on 2006-07-05
How do you turn on ACPI in the BIOS?

I think the board is just toast though. Same with the RAM.

---

### Post by randyh on 2006-07-05
Start pc, hit the "Delete Key" imediately. Should go into the setup

Look for the Power Tab at top of the setup page, one option in there is ACPI enable or disable, disable will give you crashes in loading of windows, and sounds like linux is complaining as well.

change it to enabled, then save your change and retry your install. 

i have used several of these bds with w2k, win xp, and linux. Have two of them running now. 

let me know how it works,

good luck
randy

---

### Post by randyh on 2006-07-05
I went to asus site, is your board just a model a7n266? or
 a7n266-c 
 a7n266-e
 a7n266-vm

lots of help at thier site (hope it is ok to input a web adress)

  [http://support.asus.com/download/download.aspx?SLanguage=en-us](http://support.asus.com/download/download.aspx?SLanguage=en-us)

randy

---

### Post by roxics on 2006-07-06
It's just a plain jane A7**M**266 and it says nothing about ACPI under the power tab it the BIOS. 

I did a test where I put the RAM into my working computer and my computer kept crashing. Vice versa I put my working RAM onto the A7M266 and I got a little further and then I got a message from ubutu saying on the the hard drivers or controllers could be bar or something. I know the hard drive isn't bad. 

So I'm thinking that maybe both are just junk.

[EDIT]
Seems I'm not the only one who has had this problem. I just found this:
[http://www.abxzone.com/forums/archive/index.php/t-55856.html](http://www.abxzone.com/forums/archive/index.php/t-55856.html)

---

