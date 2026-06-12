---
title: "Logitech G300 erratic movement"
date: 2011-09-23
forum: Hardware
---

### Post by qrazi on 2011-09-23
Today I just received my new Logitech G300 mouse. Works perfectly under Windows XP and Windows 7, however in my Ubuntu 11.04 install it behaves very weirdly. Its the basic left mouse button that doesnt seem to function properly.

I cant click on an icon, whether its on the desktop or in the launchbar. And when I click once, it does weird stuff, like resize my window. Clicking in the launchbar doesnt do anything.

I found one other guy who has the same problem, but no solution...

Anybody any ideas/suggestions?

---

### Post by EveryWhere on 2011-09-29
I'm having the same problem.

---

### Post by qrazi on 2011-10-01
Well, I kept the mouse, since it works great in Windows 7 (use it for gaming mostly) and I'm sure it will get fixed eventually...

It just irritates me a little bit. I think it is the actually mapping of functions to buttons that is set improperly.

Somebody advised lomoco. It is a configuration software for Logitech mice. It doesnt recognize the G300 yet. I mailed on de the mailinglist of the developers, no reply yet.

---

### Post by EveryWhere on 2011-10-06
I did the same, we'll see! :)

---

### Post by jamesjenner on 2011-10-30
Got the same problem here. I wouldn't say it's erratic movement, it's the fact that pressing left mouse click appears to move the mouse to the top right, sometimes if you try double clicking it appears to do a box select, and if you click on a tab in firefox it often moves the tab off the browser and you get it in a separate window. 

For now I've gone back to my old mouse, but would like a solution to this. Worst case I'll have to dig through the code and see what sense I can make of it. If there are some debugging or capture tools then maybe I can hammer something together.

---

### Post by Zrubi on 2011-11-02
I have the same issue.

But I made further tests, and the result is:

The exact behaviour is if I press the left mouse button, the cursor is  automagically goes to the left upper corner, so the mouse is totally  unusable.

But this is related to a specific Distro and versions:
10.04: the mouse is WORKING fine
11.04: the mosue NOT working as diescribed before
11.10: the mosue NOT working as diescribed before

Fedora 15:  the mouse is WORKING fine

So, this is NOT locomo related, locomo is only for the spec features of the mouse, not the basic movement...

This is definietly Ubuntu specific, se the versions above.

Now I'm currenltly gathering more informartion about the software (module) wersions related to the mouse....

---

### Post by jamesjenner on 2011-11-02
Sounds like a defect then and it should be raised. I'm not familiar with the process but will look into how to raise a defect tonight (in about 10 hours time). If there isn't one already I'll raise one.

---

### Post by qrazi on 2011-11-04
Good to see I am not the only one with this problem. Makes the chance of a freak incident smaller....


Have you filed a bugreport on this? Could you post a link, so we can all chime in?

Some info on mouse debugging:

[https://wiki.ubuntu.com/DebuggingMouseDetection#In_case_some_mouse_buttons_or_scrollwheels_don.27t_work_.28as_expected.29](https://wiki.ubuntu.com/DebuggingMouseDetection#In_case_some_mouse_buttons_or_scrollwheels_don.27t_work_.28as_expected.29)

Okay, I digged some further into the issue. I already suspected the programmability of the G300 might have something to do with it. And when you enter ```
xinput list
```, it shows the G300 as both a mouse and a keyboard. In my case the G300 keyboard entry has id 12.

```
xinput list-props 12
``` gives all properties of the G300 keyboard. It includes this line: > Device Enabled (146):	1
, which means that if we set the property with id 146 to a value of 0 for device id 12, the G300 keyboard is disabled.

Using ```
xinput set-prop 12 146 0
```.

And now I am typing this with my G300 as mouse, select other windows and programs without problems.

Since Fedora 15 doesnt have this problem, it should be permanently fixable. I just wouldnt know how.

---

### Post by Zrubi on 2011-11-05
Many thaks to [qrazi]("http://ubuntuforums.org/member.php?u=753")! :)

This FIX is really working, I just added to the 'Startup Appplications', so don't have to worry about on every login ;)

 I did try on F15 to see the actual xinput settings, but there is still enabled the 'keyboard part' too. And of courese the mouse is WORKING.

---

### Post by jamesjenner on 2011-11-07
Thanks a heap qrazi for the work around.

I've reported the bug, it's [https://bugs.launchpad.net/ubuntu/+source/xinput/+bug/887082](https://bugs.launchpad.net/ubuntu/+source/xinput/+bug/887082). I presume there is some system to record that the bug affects you, if so please flag the bug so the developers can get some idea of the impact. If I get time this weekend I'll look at what's involved in fixing the problem so I can submit a patch (may have to wait until the bug goes through triage first).

It's my first bug report so I hope I did it correctly.

Cheers,
James.

---

### Post by Altiris on 2012-02-23
How did you create a startup program? I did the xinput set-prop 11 121 0  and itworked for me as well

(I had to change mine to 11, beacuse 11 was the ID instead of 12)

How do you make like a file on linux so that it will run that code every time I turn on my pc and load linux? If you do not understand what I mean, I am asking like how you make a batch file but for Linux.

---

### Post by LandRacer on 2012-03-15
Funny, I have the same issues with my Logitech M305. I built a fresh system, using Kubuntu 11.11. This Logitech M305 worked great until I did all my updates a few days ago. Then it started flaking out.

I would have thrown the damn mouse, but thankfully I had this EXACT same issue with another M300(M300 died pups chewed it up). The M300 issues were on LTS 10.04 which was 2 versions ago for me. This problems still exits. Qrazi's work-a-round seems to "kind-of" help my issue... My M305 seems to be skipping far less. BUT still hangs up a bit in some instances. (a plug-in usb mouse HAS NO ISSUES)

<Note: to anyone using Qrazi's instructions. Your device id may be different, you'll need to decipher the proper device ID.> 

This form of mouse skipping is simply unacceptable. Whoever is the maintainer of this package needs to just relinquishment his/her responsibilities. Honestly, I could do a better job. Seriously, this mouse has been around for well over two years now. It still doesn't function properly. This is a popular store shelf mouse, it should really be a plug and play device, PERIOD NO EXCEPTIONS! This sort of crap DOES NOT sell folks on moving OS's. <Not implying this for myself, but for others new to the Linux game> As a full-time Kubuntu user on all of my systems. I am appalled bugs like this exist with relativity low priorities concerning the repair of issues important to furthering the advancement of our OS. I have every right to direct my concerns regarding this issue. I need no asinine responses regarding my firm stance on this issue. 

I SAY GET IT FIXED NOW, or find new maintainers. NO EXCEPTIONS. There are plenty of folks out there like me(hardcore, and willing to help!). Let someone else take-over maintenance. PERIOD.

---

### Post by kamelie1706 on 2012-03-31
Hi,

the whole pupose of this mouse is it has 9 buttons configurable, does it mean that we cannot use those under linux?

No workaround to keep the keyboard side?

:confused:

---

### Post by dikkjo on 2012-04-05
> **kamelie1706 said:**
> Hi,

the whole pupose of this mouse is it has 9 buttons configurable, does it mean that we cannot use those under linux?

No workaround to keep the keyboard side?

:confused:

Hello All,

as noted on [askubuntu]("http://askubuntu.com/questions/63283/logitech-g300-not-working-on-ubuntu") with the command

```
xinput set-mode {id} RELATIVE
```

you have a full working mouse with all additional button working (tested with xev). 
The only problem you have to program your buttons on Windows. I havent tested the app on wine tho...

This is the script I use as Startup App, which extract the id from the output of xinput list :

```
d@dubu:~$ cat bin/g300_xinput_mode.sh
#!/bin/sh
G300_XINPUT_ID=$(xinput list | egrep --color=never "G300.*keyboard" | sed -r 's/.*id=([0-9]+).*/\1/')
xinput set-mode ${G300_XINPUT_ID} RELATIVE
```

Hope it helps,
Cheers

---

### Post by kamelie1706 on 2012-04-06
Great thanks!

I try to convince them to support but feeling talking to a bot/irc :mad:
[http://forums.logitech.com/t5/G-series-Gaming-Mice/G300-Linux-button-configuation/m-p/819115#M13447](http://forums.logitech.com/t5/G-series-Gaming-Mice/G300-Linux-button-configuation/m-p/819115#M13447)

---

### Post by kamelie1706 on 2012-04-06
> **dikkjo said:**
> 
The only problem you have to program your buttons on Windows. I havent tested the app on wine tho...


I have just tried with Playonlinux and this version

[LIST]
[*]**Title:** Logitech Gaming Software (Current)
[*]**Software Version:** 8.20.74
[*]**Post Date:** 12/19/2011
[*]**Platform:** Windows XP
[/LIST]
Software get properly installed but of course mouse does not get detected.
I have tried with Virtualbox/WinXP and it does not work.

Is it the correct software to setup the buttons?
I might have to go to dual_boot solution which I could prevent so far ... just to setup a damn mouse!

---

### Post by Ben_G_9C9 on 2012-04-21
> **Altiris said:**
> How did you create a startup program? I did the xinput set-prop 11 121 0  and itworked for me as well


To create a startup for this fix (In Ubuntu 11.10), press the POWER SYMBOL/SPROCKET in the upper-right hand corner of the desktop. This is the symbol that you normally use to shut down your system.

Select the option "Startup Applications..."

This will open a window labeled "Startup Applications Preferences".
Press the "Add" button to make a new startup program.
In the COMMAND field, insert the same code that you used before 
(xinput set-prop 11 121 0). Write in your own name for the command and save it. The next time you start your system, It should work great!

---

