---
title: "I need some help with accessing windows and some other things"
date: 2007-07-11
forum: Hardware &amp; Laptops
---

### Post by blakcode on 2007-07-11
Hello, I am using on a ASUS A7F laptop. I am using Ubuntu feisty. Anyway, I have been using it for a little while now and I need some help so I decided to post everything I need help with in this one post.

Firstly I need help with getting into my Windows Vista. Well I could do it at first with GRUB no problems but when messing around with resizing partitions (using paragon partition manager in windows) it messed something up. When I rebooted my computer (I was suspecting I might get an error 17) I got to the point of where the bootloader should be but instead nothing happened at all I just got a constant beep noise. So I loaded up my Ubuntu live CD and reinstalled GRUB :) it worked fine and I can get back into my Ubuntu partition fine. When I try to select my windows partition however the screen goes black and then my computer restarts. I think when I was messing with the partitions it might have either deleted something to do with my windows partition or maybe it changed that number (you know: hd0,x) Anyway I was hoping to get some help with this.  (and another thing, I have a button on the front of my computer for InstantFunPlus, anyway I could turn on my computer before and I would boot into vista and then  open media center straight up. I used to use this button whenever I accidentally deleted a bootloader. The button doesn't work now either :( thats why I suspect it might have something do with the windows startup files).

Secondly is a problem with getting the sound to work properly, when I first installed Ubuntu both the sound and display worked okay, but the resolution was off and the sound is flaky and doesn't have any bass sound. After trying a lot of things I finally got the display to display at my resolution (1440x900) and it turned out to be the simplest solution :) All I had to do was install the INTEL drivers. Well now that thats been done something weird happens when I watch videos or try to have those random effects going on my totem media player it automatically closes. Is there a way to fix this so I can watch videos and look at random effects? 

I still haven't managed to fix the sound either, do you guys know why I am not getting full sound. I think it might be because I am still using the default that came with Ubuntu and I haven't got any of my own sound drivers yet. I did have a look for sound drivers but I don't really know how to find them >.> (come on I need my music :guitar:)

Any help with these problems would be much appreciated :)

**-ßÎâ&#269;&#1220; &#986;&#1147;Ð&#441;**

---

### Post by EXCiD3 on 2007-07-12
After you reinstall grub the Windows grub entry might be configured wrong. Try this:
(assuming you use GNOME)
```

sudo gedit /boot/grub/menu.list
```
Add a Windows entry to the menu.lst file at the bottom:```

title		Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

Try reboot and try getting Vista to boot. Hopefully your Vista partition isnt messed up where this wont work.

The InstantFunPlus is just like the HP Quickplay that I have. After you install GRUB to the MBR this will no longer work, it will just give you GRUB. However during the installtion of Ubuntu it should have added an entry to menu.lst just like the one above that boots into that partition. I deleted mine as i saw little need for that 1GB of space which i rarely used.

As for your video and sound problems, i cant really help you there... :( sorry. My intel audio works fine out of the box. Which sound card do you have?And your video card is an Intel? I have no idea for that. Envy is a great script for installing the Nvidia or ATI drivers, but that wont help you...

Hope some of this helps!

**EXCiD3**

---

