---
title: "Mouse Pointer very jittery"
date: 2009-10-28
forum: Hardware
---

### Post by whiskeylover on 2009-10-28
Jittery/shakey... I don't know exactly what word to use. English isn't my first language.

But when I keep my finger still on the touchpad, the mouse pointer seems to keep moving rapidly within a tiny square area. 

I know that the touchpad must be sending thousands of tiny signals per second to the OS. But Windows, on the same laptop, shows a perfectly still mouse pointer, when the finger is still. I'm assuming the touchpad driver on Ubuntu isn't doing a good job with filtering out the noise.

This isn't a huge issue, but when I'm, say, moving a window, and stop dragging, the mouse pointer keeps on moving erratically in a small area, and hence, the window keeps wobbling constantly till I stop dragging. Same with dragging icons, selecting text etc. 

It also makes it very difficult to point the pointer on a small area on the screen, like when trying to grab the bottom right corner of a window to re-size it. The mouse pointer refuses to stay still. It gets annoying. 

Especially annoying are right click context menus. Sometimes, as soon as I right click, the mouse pointer has moved over the menu because of the jitter, and it ends up clicking the first menu item. :???:

Its a brand new Dell Inspiron 17, with a Dell touchpad. Works perfectly well on windows. Doesn't work too well on Ubuntu 9.10 beta.

Any help would be appreciated.

---

### Post by whiskeylover on 2009-10-28
*cough*

---

### Post by twent4 on 2011-01-11
Heya, did you ever get this figured out? Got the same thing on mint9.

---

### Post by wankel786 on 2011-01-16
Same issue, any solution?

---

### Post by vinodkhare on 2011-04-21
I have the same problem on an HP Touchsmart TX2 with Ubuntu 11.04 beta2. Had the same problem previously with Ubuntu 10.10 too. Despite keeping the finger steady on the trackpad the mouse pointer jumps around seemingly randomly in a very small area.

---

### Post by r4wb3r7 on 2011-04-26
Ditto. I'm using v11.04 a ThinkPad T42p, but this problem has existed on all of my other notebooks with various versions of Ubuntu. Basically, I've never been able to solve this problem. Hopefully someone can help.

---

### Post by davethewave83 on 2011-09-22
no ideas anyone? I have this same issue but with a normal mouse. In windows it's perfectly still and smooth, in Ubuntu it behaves like someone who has ALS.

---

### Post by maul9999 on 2011-09-22
> **whiskeylover said:**
> Jittery/shakey... I don't know exactly what word to use. English isn't my first language.

But when I keep my finger still on the touchpad, the mouse pointer seems to keep moving rapidly within a tiny square area. 

I know that the touchpad must be sending thousands of tiny signals per second to the OS. But Windows, on the same laptop, shows a perfectly still mouse pointer, when the finger is still. I'm assuming the touchpad driver on Ubuntu isn't doing a good job with filtering out the noise.

This isn't a huge issue, but when I'm, say, moving a window, and stop dragging, the mouse pointer keeps on moving erratically in a small area, and hence, the window keeps wobbling constantly till I stop dragging. Same with dragging icons, selecting text etc. 

It also makes it very difficult to point the pointer on a small area on the screen, like when trying to grab the bottom right corner of a window to re-size it. The mouse pointer refuses to stay still. It gets annoying. 

Especially annoying are right click context menus. Sometimes, as soon as I right click, the mouse pointer has moved over the menu because of the jitter, and it ends up clicking the first menu item. :???:

Its a brand new Dell Inspiron 17, with a Dell touchpad. Works perfectly well on windows. Doesn't work too well on Ubuntu 9.10 beta.

Any help would be appreciated.

You will want to go to mouse and keyboard setting.  Try to fix some setting. turn it slowest if you can.  If you still have problem. try open package manager then search for mouse and delete it.

---

### Post by Herby Pepper on 2011-10-14
I have that problem too. 
Ubuntu 11.10 with E17, on hp mini 2133 pointer is ok , but on external monitor pointer is blurry (like inch by inch shack square).
I try different distributions: Debian, Ubuntu 11.04, Easy Peasy, Bodhi - with all of them I had that problem. Although I try Lubuntu and pointer on external monitor was ok. 
The problem is I don't want Lubuntu just because pointer works fine:/  

maul9999
I don't have any mouse installed in package manager

---

### Post by dannyboytward on 2012-05-28
I had this problem on my Thinkpad X220i after upgrading from 11.10 to 12.04, and I just found a solution.

You can change touchpad settings with the "synclient" command.  After some experimentation, I found that raising the horizontal and vertical "Hysteresis" from 8 up to 64 fixed my problem.  I used the command

 synclient HorizHysteresis=64 && synclient VertHysteresis=64

and added this command to my startup programs.  Presumably there is a conf file somewhere where I could change these settings permanently.  But for now this works.

---

### Post by Herby Pepper on 2012-09-17
I get it fixed on Lubuntu 12.04 on Hp2133 and post it here:
[http://ubuntuforums.org/showthread.php?t=2042366](http://ubuntuforums.org/showthread.php?t=2042366)

---

