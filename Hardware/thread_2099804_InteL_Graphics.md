---
title: "InteL Graphics"
date: 2012-12-30
forum: Hardware
---

### Post by bpb101 on 2012-12-30
I Bet Im proably the first one ever on linux to have a graphics problem.
Right anyway

Ive Got and intel i7 2600 Cpu Clocking in at 3.4ghz ( its graphics Built in is **INTEL HD Graphics 2000)(**only vga )

ive also got an AMD Radon HD 6670 graphics card. ( it has a vga , dvi and hdmi input)

Now, I Have a AOC 24 inch screen with only a Vga output.
And a Prestigio 17in screen with a vga and dvi output

Right, I Pluged in the AOC and all works grand in both windows and ubuntu.
Then i got a 17 in Prestigo. When i Pluged in the prestigo with a vga -vga (with dvi converter) to the graphics card, It just simply didnt display ( on windows or ubuntu)
 However When i Pluged it in to the vga from the on board graphics it did. ( Windows)
try it in ubuntu and no joy. (only the orginial 24IN AOC works)

**I havent **installed the graphics for the intel and thats why im here. How Can i? The Intel site just links me to [http://intellinuxgraphics.org/](http://intellinuxgraphics.org/) but i cant find my On board Graphics.Plus Installing seams painfull

The Strange this is however , when i turn off the pc , ( just as we see the purple screen with the ubuntu logo it switches to the Prestigo 17in)

Running ubuntu 12.04 64 bit

Help us Please 
Thanks 
Barry

---

### Post by mikewhatever on 2013-01-03
Installing drivers is a Windows mind set, you don't normally need to do it in Ubuntu. A graphics driver for Intel GPUs is included with Ubuntu, so I'd suggest troubleshooting.
[https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

PS: I'd also suggest cleaning up the question by removing irrelevant info, and by correcting the spelling.

---

### Post by bpb101 on 2013-01-03
> **mikewhatever said:**
> Installing drivers is a Windows mind set, you don't normally need to do it in Ubuntu. A graphics driver for Intel GPUs is included with Ubuntu, so I'd suggest troubleshooting.
[https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

PS: I'd also suggest cleaning up the question by removing irrelevant info, and by correcting the spelling.


Nither of these seam to help. I think it has something to do with the fact that there is a second graphics card, (amd hd radon 6670)

Today , i tried removing the main 24 inch screen and just let the smaller screen on the internal graphics - the bios did not show -

i Should mention that i see a completely black screen, with the darkest of black lights

---

### Post by mikewhatever on 2013-01-03
> **bpb101 said:**
> Nither of these seam to help. I think it has something to do with the fact that there is a second graphics card, (amd hd radon 6670)

Today , i tried removing the main 24 inch screen and just let the smaller screen on the internal graphics - the bios did not show -

i Should mention that i see a completely black screen, with the darkest of black lights

That was quick (even for an expert). I doubt you've even looked at the links.

---

### Post by tgalati4 on 2013-01-03
Search the forums for how to turn off modeset in the kernel boot parameters.  This is a common problem that frequently trips up folks, right?

---

### Post by bpb101 on 2013-01-03
> **mikewhatever said:**
> That was quick (even for an expert). I doubt you've even looked at the links.



[LIST]
[*]If you never see your BIOS screen, then that points to perhaps some hardware issue.  **- Not a hardware problem**
[*]The screen displays but is far too time and/or the backlight can't be adjusted.  See [Kernel/Debugging/Backlight -   ]("https://wiki.ubuntu.com/Kernel/Debugging/Backlight")**Cant see the screen , cant access it , unless ctrl alt f1 ( then terminal appears on the second scren**
[*]If you see "Out of Scan Range" or similar, you don't have this bug.  See [X/Troubleshooting/Resolution]("https://wiki.ubuntu.com/X/Troubleshooting/Resolution") instead.  **( dont see it)**
[*]If the blank/black screen occurs after resuming from suspend, you have a different class of bug.  See [DebuggingKernelSuspend]("https://wiki.ubuntu.com/DebuggingKernelSuspend") or [UnderstandingSuspend  ]("https://wiki.ubuntu.com/UnderstandingSuspend")- **Not happing after suspend**
[*]If it occurs when closing your laptop lid, see the [PipeA Quirk]("https://wiki.ubuntu.com/X/Quirks") as a better possibility. **( not a laptop)**
[*]If the blank/black screen comes after your screen saver has been running, you may either have a screensaver-induced crash (see [X/Backtracing]("https://wiki.ubuntu.com/X/Backtracing")) or a power management failure (See [PowerManagement]("https://wiki.ubuntu.com/PowerManagement")) **(nothing to do with screen saver**
[*]If  you see a screen of a different color (brown, white, multi-colored  corruption, etc.) you are seeing a different class of graphics bug.   Obtaining register dumps (see below) may still be of value however.**( no colurs)**
[*]If  it occurs *after* entering your password on the login page, you have  some different class of issue, such as an issue with 3D / DRM.  Try  disabling compiz (sudo chmod a-x /usr/bin/compiz), logging in as a different user, or turning off DRI.**(not getting as far as password)**
[/LIST]
The second link had nothing concering it , i cant see anything on the screen not even the boot (where you enter setup ) on the second screen


I appericate the help and im doing my best on this side to get the second screen working , as to help myself and other who in the future may have this problem I can asure you i looked through the links 



Most of these links were talking about dual booting problems asscoiated , i however am not techincaly dual booting , As i select my hard drive before i boot ,


I have had nomodeset on to first install the graphics chip for the amd card , the 2nd screen didnt work here either

---

### Post by Yellow Pasque on 2013-01-04
Okay, so you're plugging the AOC into the IGP and the other one into the AMD card? I really doubt that will work under Linux with Intel/ATI hybrid graphics.

---

### Post by bpb101 on 2013-01-04
> **Temüjin said:**
> Okay, so you're plugging the AOC into the IGP and the other one into the AMD card? I really doubt that will work under Linux with Intel/ATI hybrid graphics.

No, i pluuged the AOC into the amd and the 17in prestigio into the intel on board.

When i click ctrl alt f1 , the aoc turns black and the terminal apears on the 17inch prestigio. When i click , ctrl . alt f7 , the terminal still apears on the 17in prestigio but i cant access it ( and the AOC apears as normal),,

Also , when i shutdown the pc, the ubuntu logo for shuting down , apears on the second 17 inch prestigio

---

