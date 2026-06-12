---
title: "Alot of bios'ed questions!"
date: 2008-05-16
forum: Hardware
---

### Post by yogo on 2008-05-16
When changing the mbr with grub, does that alter the bios?

Reason I am asking is, out of three hard drives where Ubuntu has been installed, my bios is screwed up. On an HP, I can no longer get into bios from the HP logo via F1 or F10. On one Dell, the mobo is now a play toy but I could not even POST.

On my main Dell, I have no issues, other than I hear no beeps like before when it was just Windows.

So back to my mobo (toy) It is a Dell 2400. I have read extensively about removing the bios chip. This is no easy feat short of taking a sledge  hammer and chisel to it. I will add a jpg of it. It says American Megatrends on it so I assume this is my bios chip. I really want to build a new box, BUT after the frustrations of trying to first locate and then remove the bios chip, I am having second thoughts. 
[IMG]http://i26.tinypic.com/23m6ftl.jpg[/IMG]

---

### Post by nicedude on 2008-05-16
NO grub does not mess with your bios. You should investigate this situation furthur though as 3 systems with bios changes in short order is pretty weird and I have never seen it.

Do you ever set an administrator password on your BIOS? Because this would make it harder for anything to change them.

Also have you tried using the CMOS reset jumper on your mobo you say is dead?

---

### Post by BlueSkyNIS on 2008-05-16
Ubuntu (and windows) does not alter your bios image in any way, it can only change some bios settings stored in cmos(like time and date, cmos is a kind of bios memory), except if you install some 3rd party programs for updating bios...

Have you tried to clear your cmos?

EDIT: You can't remove your bios out, it would make your computer useless!

---

### Post by nicedude on 2008-05-16
PS thats not your bios chip thats your input/output controller.

Link to its datasheet and specs
[http://www.smsc.com/main/catalog/lpc47m112.html](http://www.smsc.com/main/catalog/lpc47m112.html)

---

### Post by nicedude on 2008-05-16
Try reseting CMOS by unplugging your PC and then moving the jumper located in picture below at red arrow location to different position. meaning if it is on pins 1 & 2 now change to pins 2 & 3 with power off and leave for 15 seconds then replace to original position and replug power and try to fire it up.

Hope it works as I have seen it take a seemingly dead box and fix instantly many times.

---

### Post by yogo on 2008-05-16
I did try using the jumper from your diagram, however it did not work for me. I am at a loss as to where the bios chip is at on that board?

The board is a toy, no recovering it now but at least I would like to learn from it.

Ok, I did not think that Ubuntu would alter my bios but since I had so many issues, just just trying to think why.

As for the HP, it could possibly be a battery as to why I can not get into bios? I did check the battery from my Dell and that was good.

I also tried the jumper that is nearest the battery from your diagram, not the one that clears cmos, not sure what that did?

There are not three pins, only two on my board.

Where do I begin my hunt for the bios chip?

TIA

ETA, I see that I did the wrong jumper first from your diagram, I tried the password jumper first.

There was not a jumper pin on the cmos one to begin with. What position should it have gone in? Covered both pins?[IMG]http://i25.tinypic.com/2e1t1yd.jpg[/IMG]

---

### Post by nicedude on 2008-05-16
here is what allot of bios look like it will be removable but care must be used don't chisel anything, use care instead.

---

### Post by nicedude on 2008-05-16
Before you jump the gun and think it is your BIOS that are ruined you should look here at Dell support advanced troubleshooting

I am assuming you have a Dell Dimension 2400 as there are several Dell 2400 models


Error code page look at this
[http://support.dell.com/support/edocs/systems/dim2400/en/sm_en/advtshoo.htm](http://support.dell.com/support/edocs/systems/dim2400/en/sm_en/advtshoo.htm)

Main support page read the manual
[http://support.dell.com/support/edocs/systems/dim2400/en/index.htm](http://support.dell.com/support/edocs/systems/dim2400/en/index.htm)


Your welcome

---

### Post by .nedberg on 2008-05-16
On some of my computers I have to move the password jumper, then power on the computer. After it has booted just power off and replace the jumper.

On others it is enough to remove the battery and power for a while.

---

### Post by yogo on 2008-05-16
> **nicedude said:**
> here is what allot of bios look like it will be removable but care must be used don't chisel anything, use care instead.

I looked at several pics of bios from varios web sites last night and most all look similiar to the one you posted however, after staring at my board for hours on end, and even using reading glasses, I can not find anything that remotely resembles a bios chip.

Next I will upload a pic of the whole mobo.

here is a link to the mobo, as the pic will stretch page margins.

[http://i30.tinypic.com/ie4gpe.jpg](http://i30.tinypic.com/ie4gpe.jpg)

---

### Post by yogo on 2008-05-16
> **nicedude said:**
> 


Error code page look at this
[http://support.dell.com/support/edocs/systems/dim2400/en/sm_en/advtshoo.htm](http://support.dell.com/support/edocs/systems/dim2400/en/sm_en/advtshoo.htm)

Main support page read the manual
[http://support.dell.com/support/edocs/systems/dim2400/en/index.htm](http://support.dell.com/support/edocs/systems/dim2400/en/index.htm)


Your welcome
  Thanks, I did look at those last week and even was with a tech person discussing the error codes, since mine does not beep, we had to go by lights and my light values would change  basically having just a yellow light in either b,c,or d but mainly in c and sometimes d.

So yes this mobo is trashed/ a toy but I still have no idea where the bios chip is?

Curiosity has got me

---

### Post by yogo on 2008-05-16
Anyone find a bios chip on this mobo?

[http://i30.tinypic.com/ie4gpe.jpg](http://i30.tinypic.com/ie4gpe.jpg)

---

