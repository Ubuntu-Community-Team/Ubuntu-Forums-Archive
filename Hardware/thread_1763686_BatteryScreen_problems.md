---
title: "Battery/Screen problems?"
date: 2011-05-20
forum: Hardware
---

### Post by Sqmaster1234 on 2011-05-20
Hey
I've been having some issues with Ubuntu on my netbok (Toshiba mini nb255) for a while now, and they've only gotten worse with updates.
I installed Ubuntu 10.10 a while back without a hitch. It ran fine for a while, but then I started to get some error messages on the login screen (I'll include them in an edit after I post this and reboot).
After that, I had battery issues. The battery in this computer worked fine and had great life under Windows 7, and even better life under Ubuntu. But after a while of 10.10, whenever I unplugged the laptop, I would get a popup telling me that the laptop was running on critical power. Usually I could click "close" and it wouldn't make a difference. But now it forces hibernation whenever I get the message (I just got it a few minutes ago after pulling it off of the charger, 100% battery). I have no idea what could be causing this, and it only started a few weeks ago.
Lastly, I finally made the upgrade to 11.04, and to my dismay, more problems came with it.
Whenever I boot, whether it be a cold boot or a hibernation, only about 1/4 of the screen is usable. The right-most section of the screen shows whatever is happening, and the left 3/4 shows nothing but black with some purple static at the top of the square (picture coming up). The mouse can move into the black portion and I can see it (?). However, when I put the laptop into standby and resume, it's back to normal.
Sorry if I'm overwhelming with all these problems; they just sorta came at me all at once.
If worst comes to worst, I could re-install (there's not too much to reinstall) but I would rather not.
Any help regarding any of these issues would be greatly appreciated!

---

### Post by SteveDee on 2011-05-21
If you haven't already done so, you need to check whether the problems are hardware or software related. The easy way to do this is to boot the system with a LiveCD.

Its a good idea to keep a live CD or bootable USB stick with an operating system that you know works properly on your machine. For example this could be an earlier release of 'buntu, or Puppy Linux or whatever you are happy with (in your case you seemed initially happy with 10.10, so that's the one to use).

I hope this helps.

---

### Post by Sqmaster1234 on 2011-05-22
Yeah that was gonna be my first test :P
I'm pretty sure it's software, as it ran fine for a while before these issues developed. Let me get on the LiveUSB and I'll see what's up. Thanks for the reply!

---

### Post by Saladin1 on 2011-05-24
I have the same screen problem with my satellite L500, it was in 10.10 and still in 11.04 till now, is there a vga card driver install or something like that? did you find a solution so far?

---

### Post by ander111 on 2011-06-07
It's odd that you're having such problems. I'm running 11.04 on my NB255 and it's great. (Well, I am having a [small problem]("http://ubuntuforums.org/showthread.php?p=10911085#post10911085") with wireless, but that's usually easy enough to fix.) 11.04 has fixed some significant problems (screen brightness, audio, etc.) that kept me from using previous versions on my netbook.

Maybe you would've done better with a clean 11.04 install rather than going through the upgrades. It's easy enough to find out&#8212;just try running 11.04 from a [live USB]("http://www.pendrivelinux.com/").

---

### Post by SteveDee on 2011-06-07
> **ander111 said:**
> It's odd that you're having such problems. I'm running 11.04 on my NB255 and it's great.....

Its a bit of a lottery.

For me 10.10 has been the most straightforward recent install for my Dell laptop and Compaq desktops. I had big problems with 10.04, and with 11.04 I can upgrade the Compaqs but not clean install any machines...I'm sure these problems could be overcome, but I just can't be bothered, as 10.10 is so stable.

---

### Post by ander111 on 2011-06-07
> **SteveDee said:**
> For me 10.10 has been the most straightforward recent install for my Dell laptop and Compaq desktops. I had big problems with 10.04, and with 11.04 I can upgrade the Compaqs but not clean install any machines...I'm sure these problems could be overcome, but I just can't be bothered, as 10.10 is so stable.
I'm glad that's worked out for you.

However, we are talking portables here (not to mention, the same *model* of portable), and they tend to have their own types of problems.  ;?)

Actually (and not to flame one distro in favour of another), I thought I'd mention this: 

Tonight I tried [Linux Mint 11]("http://blog.linuxmint.com/?p=1760") on my NB255 from a live USB. And wow, *everything* works—screen brightness, audio, wireless... It's fantastic. 

And as far as I know, LM is based on Ubuntu. So I guess they've done some extra tweaking. In any case, if you're still looking for a distro that'll run well on your NB255, LM 11 is a good one to try.

---

