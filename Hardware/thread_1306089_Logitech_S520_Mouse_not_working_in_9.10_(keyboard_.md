---
title: "Logitech S520 Mouse not working in 9.10 (keyboard works fine from same usb receiver)"
date: 2009-10-30
forum: Hardware
---

### Post by Takenover83 on 2009-10-30
It is kinda strange. Both the Keyboard and Mouse worked fine in 9.04. I have done a clean install of 9.10 and now just my keyboard works. Both use the same usb receiver, which is why I find it strange. I plugged in a stand alone Logitech USB Mouse and it works fine. How do I go about troubleshooting this?

The error exist in Ubuntu and Xubuntu 9.10, as I have tested both.

---

### Post by Takenover83 on 2009-10-30
Hmmm, guess I am the only one :(

---

### Post by cob05 on 2009-11-10
> **Takenover83 said:**
> Hmmm, guess I am the only one :(

Nope, you're not alone!  :)

As I write this I am having to navigate with keyboard only.  You don't realize how essential the mouse is until you can't use it!

I am having the same issue.  The keyboard and mouse worked perfectly under 8.10, then I upgraded to 9.04 and they also worked perfectly, but now under 9.10 - not so much...

The keyboard works fine, but the mouse refuses to do anything.  I've checked/replaced the batteries, tried different USB ports for the receiver, tried doing a reconnect, etc... but nothing has worked.

Any help on this issue would be appreciated, I miss my mouse!  :(

---

### Post by imaca on 2009-11-11
Hi,
I'm using S520 in 9.10 and mouse is working fine.
Are you sure it's not a hardware (battery, press connect etc) problem ?

---

### Post by cob05 on 2009-11-11
> **imaca said:**
> Hi,
I'm using S520 in 9.10 and mouse is working fine.
Are you sure it's not a hardware (battery, press connect etc) problem ?
 
I'm pretty sure. I've tried all of those things and more, but since you say it is working for you then there is hope! :)
 
I did some more research and found that: 
 
**ls /dev/input/mouse*** lists mouse0 and mouse1 as input devices
 
**cat /dev/input/mouse0** shows nothing when moving the mouse
 
**cat /dev/input/mouse1** shows strange characters when I move the mouse
 
So... I think that my 9.10 is using mouse0 when it _should_ be using mouse1 as the input. I tired to look at the /etc/X11/xorg.conf file but it was blank. I then tried to add an input section from an example I found online and changing it to use mouse1, but no dice. I may have missed something though.
 
I'm still working on the issue, but my limited knowledge of Linux is making progress slow.
 
imaca, is there anyway that you can look at your xorg.conf file and see what you have listed there for the mouse input, if anything?
 
I might be on the right track, or I might be way off. Still looking for help on this one.

---

### Post by never gonna give you up on 2009-11-11
Made an account just so you know I am intently watching this and that you are not alone with this issue.

---

### Post by cob05 on 2009-11-11
> **never gonna give you up said:**
> Made an account just so you know I am intently watching this and that you are not alone with this issue.
 
Welcome!  Hopefully we can get this figured out and fixed for all of us.

---

### Post by cob05 on 2009-11-13
Still working on this.  No luck yet, but I feel like I'm getting closer to getting some results.

---

### Post by cob05 on 2009-11-18
When running: 
 
**cat /proc/bus/input/devices**
 
I'm getting the mouse listed as a keyboard it looks like. I'm sure it has something to do with the single USB reciever and how it is handled in 9.10. Not sure how to correct this. All of my tinkering with xorg.conf has had no effect.
 
I've gotten distracted by other issues, but I'll keep working on this when I have time.

---

### Post by big_patty on 2009-11-23
I am also running into a very similar problem with a keyboard mouse combo.  Let me know if I can help you out in any way with information regarding the problem.

---

### Post by skiplin43 on 2009-11-30
I am having the same problem

---

### Post by marvel65 on 2009-12-21
Afer upgrade to Xubuntu 9.10 both external en internal pointer don't work on my Toshiba satellite S1690CDT.

---

### Post by majormajor on 2009-12-24
heya,
i've just got this cordless desktop as present. 
plugged it into my Karmic Koala machine, connected it as printed on the back of the board and everything is working like a charm.
did you guys use the right connecting order? (first the mouse then the keyboard?)
the funniest thing that i can switch the numlock led on my still connected ps2 keyboard with the logitech one :)

merry xmas!

---

### Post by billyboy1995 on 2010-01-05
I just got one today. I have had no problems with it. I am running 9.10 with latest updates.

sorry i can't help

---

### Post by blkideas on 2010-02-02
Hi all,
I don't know if you guys found the problem to this issue, but I have a similar problem. I just got a MSI U100 netbook, and I had plugged in an optical MSI mouse. It was working fine, until I had to disconnect it to move the netbook. Now I plug in the mouse and it lights up, but it is not working. I'm new to ubuntu so I'm not sure how to go from here. (And by new I mean I got my netbook yesterday and installed ubuntu at night so I'm have barely used ubuntu for a day hahahaha!) 

blkideas

---

### Post by aglc2005 on 2010-02-18
I purchased this recently. Has there been any luck with this? I am having issues with the keyboard not working actually.

---

### Post by vortex-5 on 2010-02-24
I am also having this problem I wonder if there's any progress on a solution. I might see if I can downgrade to 9.04 now.

---

