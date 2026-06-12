---
title: "Logitech K350 Keyboard Issues"
date: 2015-07-07
forum: Hardware
---

### Post by john409 on 2015-07-07
I had a logitech keyboard and it started acting up. Missing keystrokes primarily. So I went and got a new Logitech K350 and it is doing the same thing. Primarily when I am copy and pasting and entering data into LibreOffice Calc. It is not doing anything as I type this, but has been pretty frustrating in LibraOffice Calc.

Is this a Ubuntu issue? The rest of my hardware is listed in my signature line.

Is there a fix?

thanks,

John

---

### Post by john409 on 2015-07-10
Bump?

---

### Post by Vladlenin5000 on 2015-07-10
How does it work in a live session?

---

### Post by john409 on 2015-07-10
What would you consider a "live session?"

It is glitchy a bit even when I am typing a command into the Terminal

It pauses, as if it the computer is tied up doing something else, but when I look at the CPU/Memory processes, there is almost nothing going on. It stalls, then starts typing again, sometimes with a few of the keystrokes I had already entered, sometimes not.

I don't think it is the keyboard, this is the second one (and brand new) of the same brand I am using after seeing the problem.

---

### Post by Vladlenin5000 on 2015-07-10
A live session is the one you boot from the installation media, DVD or USB, when you choose "Try Ubuntu".
The purpose of this is, obviously, to rule out any hardware issues. Testing in another PC would be great also.

---

### Post by john409 on 2015-07-10
Oh... Ok... I will switch over to my Dual Boot Window 8.1 and work for awhile and see if the problem shows up. I'll let you know. The problem is intermittent, so I will work over there all evening.

---

### Post by john409 on 2015-07-10
Seems like it works just fine in Windows. Is it possible that I am reaching some sort of limit in the clipboard from copy and pasting?

Does anybody know how to clear the clipboard?

---

### Post by Vladlenin5000 on 2015-07-10
That's a possibility, among several others... Honestly, I don't know where to start. And I don't know about the clipboard either.

---

### Post by john409 on 2015-07-12
I think I have ruled out clipboard issues, from a cold boot, only working in terminal the keyboard glitches. It is as if the keystrokes are getting entered late or not at all. Sometimes it works just fine, then suddenly it wont accept a simple keystroke. Then when it starts working again it enters several of the recent keystrokes I had just entered. Sometimes all of them, sometimes just the last few.

It is a wireless keyboard if that makes a difference.

---

### Post by kurt18947 on 2015-07-12
I have a logitech K550 'wave' keyboard. I sometimes see the delayed keystrokes if typing text very soon after resuming from suspend. After the machine has 'been awake' for a couple minutes no more delays. The logitech keyboard this one replaced - K320 - would exhibit 'stuck key' behavior even though there was not a key physically stuck. That problem was quite intermittent.

---

### Post by john409 on 2015-07-12
It does not seem to matter if I have a full restart or wake from hibernating. And the problem persists beyond the first few minutes of activity.

It seems almost as if another process is interrupting me. But I don't see one that takes a lot of resources running.

---

### Post by kurt18947 on 2015-07-12
Do you have a copy of Windows? If so you might try downloading Logitech unifying software and try re-pairing the receiver, keyboard and mouse (if any). Run that software in Windows then reboot into Ubuntu. It may not help you but it did seem to help my keyboard performance in Ubuntu.

---

### Post by Vladlenin5000 on 2015-07-12
> **kurt18947 said:**
> Do you have a copy of Windows? If so you might try downloading Logitech unifying software and try re-pairing the receiver, keyboard and mouse (if any). Run that software in Windows then reboot into Ubuntu. It may not help you but it did seem to help my keyboard performance in Ubuntu.

+1 to this suggestion. Nothing to loose by trying...

---

### Post by john409 on 2015-07-12
Actually, I got to thinking about it and figured it out.

When I originally set up this new machine someone mentioned that there might be USB3 issues, but was not sure. I was not really thinking about it when I plugged the wireless USB into the back of the computer, but today pulled it out and looked, sure enough, it was plugged into a USB3 port. I moved it over to a USB2 port and have been working away for a bit now without an issue.

So now I just need to figure out what is wrong with my USB3 and if there is a fix...but that is for another thread. Thanks guys/gals for trying to help.

---

### Post by kurt18947 on 2015-07-12
I'm glad you were able to solve the mystery.  It sounds like USB3 support at least in the linux world is sort of like UEFI, a work in progress. Have you tried USB3 device(s) in that port? Did it/they behave as expected?

---

### Post by john409 on 2015-07-12
Lol...I don't actually have any USB3 devices! So no, no way to test the USB3 systems yet. For now they are just charging ports for my phone. 

I used the keyboard all evening without a single hiccup though, so I am pretty sure that solved it.

---

