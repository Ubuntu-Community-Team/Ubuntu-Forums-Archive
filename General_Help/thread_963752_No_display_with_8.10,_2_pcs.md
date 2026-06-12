---
title: "No display with 8.10, 2 pcs"
date: 2008-10-30
forum: General Help
---

### Post by madwab on 2008-10-30
I'm pretty much a newbie (I've installed many Linux variations over many years but each has had one or more issues that kept me from delving very far). BUT, I know something is wrong here. I installed 8.04 recently from a bootable 'tryme' disk, and everything was fine. (Except support for my Linksys WUSB54GS, but that's another story.) Today I got the equivalent disk for 8.10. It validated OK, but when booting from CD, although it sounds fine there is no display after the initial loading screen. I assumed it might be a fault with booting directly from CD so tried installing, but got the same thing: I can hear the welcome sound, but my monitor just repeats 'entering power save mode' - tho' as the light remains green, it never gets there. The install partition has near 700mb on it but isn't bootable.

I've since tried booting from CD on another box with v. different h/w, and I get exactly the same symptom. Searches for 'no display' and 8.10 show other threads but they seem to be unrelated. Anyone else heard of this or know what might be up?
:confused:

---

### Post by overdrank on 2008-10-30
> **madwab said:**
> I'm pretty much a newbie (I've installed many Linux variations over many years but each has had one or more issues that kept me from delving very far). BUT, I know something is wrong here. I installed 8.04 recently from a bootable 'tryme' disk, and everything was fine. (Except support for my Linksys WUSB54GS, but that's another story.) Today I got the equivalent disk for 8.10. It validated OK, but when booting from CD, although it sounds fine there is no display after the initial loading screen. I assumed it might be a fault with booting directly from CD so tried installing, but got the same thing: I can hear the welcome sound, but my monitor just repeats 'entering power save mode' - tho' as the light remains green, it never gets there. The install partition has near 700mb on it but isn't bootable.

I've since tried booting from CD on another box with v. different h/w, and I get exactly the same symptom. Searches for 'no display' and 8.10 show other threads but they seem to be unrelated. Anyone else heard of this or know what might be up?
:confused:

Hi and welcome, what is the model of the graphics card? If you have installed it can you boot into recovery mode which is usually the second choice from the grub and reach the desktop there?

---

### Post by madwab on 2008-10-30
Thanks for replying. Nope, I haven't installed it, I just *tried* to install it; there are no grub options to select. The data on the install partition is just what the install process copied there (tho' it never asked me what partition to use). The screen blanks before any install options are presented.

Graphics cards are a Radeon HD 2600 and Geforce 9300 GE. In each case the last thing I see is the Ubunto logo with the orange bar beneath. I'm currently trying a CD boot on my laptop, and it... wait for it... Works. So it isn't a disk problem. However I don't want to install it there.

...?

---

### Post by madwab on 2008-11-01
Ho hum, yet another 'Linux is still for hard-core techies, back to Windows for me' user.

The daft thing is, by many standards I am a hard-core techy. I've worked and played with computers for 36 years. I spent many years writing applications and systems mainframe software. I've coded channel command words to communicate at the lowest level between a mainframe and its attached storage. But I don't wan to to do that in my spare time, I want a system that works. I've installed EVERY flavour of Windows since 3.1, many, many times, with almost no problems. I've NEVER succeeded in installing a Linux system - and I've tried many variations - without the result requiring hard-core attention to get some critical component working. In these forums its pretty clear there are folk who want to keep it that way, to feel, I guess, that they're in a technical elite. For the rest, those who want to convince the world that Linux is good, a system that blank screens on 2 out of 3 PCs, and for which no help is forthcoming, isn't fit for purpose at any price, even free.

Rant over, I'll try again in a year or so.

---

### Post by madwab on 2008-11-03
I'm gobsmacked.

I stand by what I said. However, I decided to try the disk in another box out of curiosity, and it worked again. Well, it should. What is amazing is that the box was downstairs with just a Linksys WUSB54GS wireless adaptor to connect. There's a pretty huge amount of space in various forums, including this one, dedicated to getting this adaptor working in various editions of Ubuntu, including 8.04. I spent near 2 days on it and got no more than an unreliable and unrepeatable connection, and that's more than many.

I booted the 8.10 CD, saw a network icon, saw a wireless tab, filled in my ssid and security details, and... bingo, connected!!! :)

So for anyone searching for how to get a WUSB54GS (v2 in my case) adaptor working with Ubuntu, the answer might be very simple: move to 8.10.

I say 'might be', because I can't be the only person getting a blank screen from 8.10. :(

---

### Post by Ice Dragon on 2008-11-03
Your not, im also having that exact same problem. I couldent install 8.10 due to this. 8.04 installed perfectly however, strange.

I have an ATI 2400 HD dual display. I tried with one monitor, with two monitors, doesnt matter.

Finally I took out the ATI video card and used the onboard video, that worked, I installed 8.10. That is not acceptable however, and im on that computer now on the forums trying to find a solution, which there doesnt appear to be one.

---

### Post by madwab on 2008-11-03
Well that's not good for you, but at least it confirms that this isn't an isolated case.

Worse tho' unrelated: when I installed 8.04, the boot loader booted my XP and Vista systems no problem. This one doesn't, and after a bit of tinkering with a partition manager, all 3 systems are now n/a. Priot to that I also noticed that when changing screen resolution the display was partly corrupted and didn't get corrected until a reboot.

My graphics cards (working) are Radeon 7500 and nvidia 3650 mobile. Failing ones are a Radeon 1950 Pro and a Radeon HD 2600. Both failing machines are connected to the same native 1920x1200 monitor - I'm tempted to connect one of them to a different monitor and try again...

---

