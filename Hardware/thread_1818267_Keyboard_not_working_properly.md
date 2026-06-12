---
title: "Keyboard not working properly"
date: 2011-08-04
forum: Hardware
---

### Post by fero4u123 on 2011-08-04
I recently installed Ubuntu 11.04 64bit on my HP dv6-6135dx. Everything is working fine...except my keyboard is not fully function/typing keys when I type fast.

Its hard to describe but basically, when I type fast the cursor kind of pauses and when it un pauses it only catches the last part of what i was typing.

So if i were to type "The Quick Brown Fox Jumps Over The Log" faster than 30wpm I would get something like

"The Quiwn Fox Jum Over THe Log"

It does not happen EVERYTIME. but it happens often enough, that when I'm working on a report or doing any intense typing I have to slow down so the keyboard can catch my keystrokes.

I can type around 100wpm but I'm usually just casually typing at around 40-50wpm.

Any have any ideas on how to fix this? Any help would be greatly appreciated.

Thanks.

---

### Post by owenjm on 2011-10-17
Did you ever solve this problem?  I'm experiencing it also on a dv6-6135tx ... it's driving me nuts! ... only, for me it happens even when typing at ~50wpm (and I've had to correct multiple passages of typing when writing this post ...)

Does anyone have any ideas how to fix this, or even what might be causing it?  It seems really, really odd ...

---

### Post by boydell on 2012-05-06
I am guessing this was not solved, because I have looked everywhere for a solution. I also have a dv6, but I am not completely sure of the version. It is the one with the AMD A8-3520M.

I found a forum post once where someone with the problem saw entries in some error log, but now I can't remember where that post was and I don't know what log to look in.

Although I did do dmesg and I found a bunch of stuff like this:


[15282.088604] psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[15282.099301] psmouse serio1: TouchPad at isa0060/serio1/input0 - driver resynced.
[15282.228322] psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1

But that looks just like the trackpad. Could it actually be a more generic problem with the input stuff?

Here is some of what I have tried. Ubuntu 11.10, 12.04 beta, 12.04 final, 32 and 64 bit, Gnome and Unity. and lately fedora 16. All have the same problem, which of course means it is not a ubuntu specific problem, but I could use any help I can get.

Two situations on my computer that dont: Windows 7, and ubuntu 12.04 in virtualbox. (Although I dont know if I have used it on virtualbox long enough to know for sure).

Speed of typing seems to really not be a factor. The amount of time since the last reboot seems to be something. After using it a bunch today, waking more than once from suspend, it started happening after my latest install. I read from one person that talked about it only happening after coming back from suspend.

But all of that could be wrong. Maybe the problem really only crops up after I have installed a few things. I have to install the AMD Catalyst drivers. I also use wine. Of course I have java, and all the latest linux core stuff. That is about the only things that are the same between the ubuntu and fedora setups.

I found one post about a completely different computer having the same problem where the person helping suggested dropping to unity 2d to see if the problem was only in 3d. Now that I am in Fedora, I don't have that option, but I could try dropping out of gnome 3.

Other than that, I don't know anything I can do. I don't know how to troubleshoot a problem like this, where to look, what to try. Any help?

---

### Post by boydell on 2012-05-07
I found the fix.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/717970](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/717970)

go to post #26. Working great for me.

---

