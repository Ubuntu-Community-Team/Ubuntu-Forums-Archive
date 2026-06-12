---
title: "Mouse goes bezerk"
date: 2006-02-17
forum: Hardware &amp; Laptops
---

### Post by hartz on 2006-02-17
Hi,

Sometimes my mouse pointer goes bezerk.  It then pushes buttons, opens the trashcan (repeatedly), and is totally uncontrollable.

The only solution when this happens it to reboot (Ctrl-ALT-F1, login, sudo reboot).  CTRL-ALT-BKSPC does not fix it.  Killing and restarting X doesn't help either.

This sometimes happens twice in a single day.  Other times a week goes by and it behaves properly.

Today I installed XFCE at work and on my home computer.  On my home computer (Where the mouse goes bezerk), I notice that when I change a theme in XFCE, the mouse pointer jumps to the upper-right corner.

Which brings me to my 3rd mouse-related complaint:  It takes so long to move the mouse from one place to another (1600x1200).  If I make the mouse faster, I keep on overshooting.... Maybe I need a smaller screen :-(

---

### Post by localzuk on 2006-02-17
Does it do the bezerk problem in more than one desktop environment? ie. in gnome as well as xfce?

My guess would be a dodgy mouse personally - have you tried a different one?

---

### Post by hartz on 2006-02-17
I have not used xfce long enough yet, only a few hours now, and it has not happened, like I said, it sometimes don't happen for a whole week.

It could be the mouse, but I really hope not.  It never misbeahaved in Windows.  On the day I uninstalled WIndows and started using Linux, I started having this problem.  This was an expensive mouse (When I bought it, at least)

I will try another mouse if this one acts up again... I have a cheapie here somewhere...

---

### Post by sjnovick on 2006-02-17
I cannot install Ubuntu on my old laptop because, every once in a while, my mouse goes absolutely crazy, clicking everything.

I have read some posts that for low RAM systems, when the CPU use is high, the mouse tends to go berserk.  Is this also the case for you?

---

### Post by hartz on 2006-02-18
[QUOTE=sjnovick]I cannot install Ubuntu on my old laptop because, every once in a while, my mouse goes absolutely crazy, clicking everything.

I have read some posts that for low RAM systems, when the CPU use is high, the mouse tends to go berserk.  Is this also the case for you?[/QUOTE]


Hi there.  No, I have lots of RAM, but my symptoms sounds like yours, the pointer jumps arround the screen when you move the mouse and cannot be controlled.  

**But this is HAPPENING RIGHT NOW!**  I managed to ALT-TAB and CTRL-TAB and then navigate firefox to this page by keyboard.  I have an install in Synaptic which is waiting for some response, but I will have to reboot to regain my mouse action.

How do I use the keyboard to switch to another workspace in XFCE?  Or any Desktop / Window manager for that matter, it might be similar.  Even if I could just get the focus on the XFCE panel that would probably help.

I would realy like to go see what is synaptic doing before I reboot!

---

### Post by Rizado on 2006-02-18
What drivers are you using? If you use mousedev, try evdev. (If you have a USB mouse) Don't know if it'll help but it's worth a try.

---

### Post by hartz on 2006-02-19
Well, just for completeness' sake, I've found that I can switch to another workspace by using Ctrl-F1, Ctrl-F2, etc. So I was able to get to the workspace where Synaptic was running.  This doesn't work in Enlightenment though :-(

---

### Post by Kokosnuss on 2006-02-19
[QUOTE=sjnovick]I cannot install Ubuntu on my old laptop because, every once in a while, my mouse goes absolutely crazy, clicking everything[/QUOTE]

I used to have the same problem with my Dell Inspiron 8100. It first occured in hoary and hasn't been fixed in breezy. I don't know how it is in dapper, but I'm going to try it in the next days...

**But there's an easy workaround:**
Just disable "Intel SpeedStep" in BIOS. It is a feature that clocks down the CPU when the laptop is powered by a battery. Didn't have any problems after that...

---

### Post by sjnovick on 2006-03-14
"But there's an easy workaround:
Just disable "Intel SpeedStep" in BIOS. It is a feature that clocks down the CPU when the laptop is powered by a battery. Didn't have any problems after that..."

There is a big flashing warning in my BIOS that turning off the "Intel SpeedStep" could lead to overheating.  Is this a real problem?

I'm going to try out Dapper on the old laptop when it's released.  I'll update my post to let people know if the mouse problem continues.

---

### Post by hegex on 2006-03-18
Hi! 
My mouse (logitech MX610) goes nuts too (or drives me nuts). Some times when i click once it counts it double. Everything works great in M$ XP (hate to mention). The problem wasnt there yet, it started suddenly about month ago. First i tought the problem was somewhere in receiver but if my mouse works fine in xp, so it should work in ubuntu too :-s

---

### Post by Stranger678 on 2006-04-10
I fixed this same problem on my Dell inspiron 8100 by uninstalling powernowd.

---

### Post by Twilight Lamentation on 2006-04-10
I have the exact same problem. I originally thought that my (3 year old, cheapie) mouse was on its death throes, because it'd been just scrolling when I clicked in WinXP, and then did the same thing in Ubuntu. Then it started going even more haywire (i.e. opening and closing windows, etc. with any movement at all, instead of just scrolling with a click), so I figured that it was time to buy a new mouse. But then I had the exact same thing happen with just my touchpad, when the mouse wasn't even plugged in (the touchpad had always worked fine up til then; when my mouse started acting up, I'd just switch to the touchpad for a few minutes and then the mouse would be ok). Anyone know what's going on?

Is there any disadvantage to disabling Speedstep other than draining the battery faster?

>  	I fixed this same problem on my Dell inspiron 8100 by uninstalling powernowd.
What's powernowd do?

I've got an Inspiron 8200 actually, which makes me hopeful that your fix will also fix my problem. But I'm hesitant to uninstall something without know what I'm getting into...

---

### Post by Sef on 2006-04-11
I found this post in Hoary which has a solution and explains what powernowd is.

[http://www.ubuntuforums.org/showthread.php?t=21501]("http://www.ubuntuforums.org/showthread.php?t=21501")

---

### Post by sjnovick on 2006-07-19
Hi again.

My mouse went completely bezerk in Ubuntu 5.10.  The mouse would scroll and click by itself uncontrollably for several seconds, wreaking all sorts of havoc on the desktop.

The mouse problem is a little bit better in Dapper.  Now, every once in a while, my mouse moves into the corner of the screen.  Control of the mouse can be regained immediately.

I do not wish to turn off powernod on my laptop.  I have tried Kanotix on the laptop and, with it, I have no mouse troubles with powernod ON.  Thus, Kanotix is what I run on the laptop.

---

