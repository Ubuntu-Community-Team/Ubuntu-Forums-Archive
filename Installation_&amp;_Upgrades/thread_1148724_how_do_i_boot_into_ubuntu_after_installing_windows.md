---
title: "how do i boot into ubuntu after installing windows"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by thingy87654321 on 2009-05-04
i didnt have a xp install disc when i installed ubuntu, but today i got a xp pro disc, when i installed ubuntu, i put a partition for windows, si today i installed windows on that partition. but now i cant boot into ubuntu anymore, please help, or get me a compiled version of grub and install instructions. please help

---

### Post by xreaper on 2009-05-04
Hey! Do you have an ubuntu live cd handy?

---

### Post by xreaper on 2009-05-04
...If so, its fairly simple to get Ubuntu working again.

If its what I think it is... It is a problem with Window's bootloader overwriting GRUB.

To restore it, boot into the live cd and go into a terminal, and write the following commands:

sudo grub
*This will set it to grub mode*
 

find /boot/grub/stage1
 *This will locate your boot partition. If you already know the location, you can ignore this step.*
 

root (hdX,Y)
 *Replace the (hdX,Y) by your boot partition number.*


 setup (hdX)


 quit

---

### Post by thingy87654321 on 2009-05-04
yeah.. why?, i dont have to reinstall do i?

---

### Post by thingy87654321 on 2009-05-04
ok, i didnt see your second post, thank you

---

### Post by thingy87654321 on 2009-05-04
i mean the third post, and is there any way to do this without a cd, i am at work and my cd is at home, and i dont have any blank cds in my office?

---

### Post by thingy87654321 on 2009-05-04
what is a boot partition number?

---

### Post by xreaper on 2009-05-04
Okay, when you enter the certain commands that I gave you into the terminal, you get an output, eg:

Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

Type "root (hd0,3)".

Type "setup (hd0)". 
  
Type "quit".

---

### Post by xreaper on 2009-05-04
And the boot partition number is the number that is given to you when you enter the command "find /boot/grub/stage1"

---

### Post by networm1230 on 2009-05-04
look on your screen when your PC is booting look for your grub boot up screen and move your keys up or down to choose what OS you want to boot in to

install windows first than Linux. I have found that installing is much easer in this order.  (windows than Linux)

---

### Post by thingy87654321 on 2009-05-04
ok, thank you

---

### Post by networm1230 on 2009-05-04
for windows the minimum partition size 40GB or more. for Linux 20GB or more I have used partition editor  [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

hope this helps you

---

### Post by networm1230 on 2009-05-04
> **thingy87654321 said:**
> ok, thank you

vary good point

---

### Post by thingy87654321 on 2009-05-04
windows isnt showing up on the grub boot menu, how do i fix that little problem

---

### Post by xreaper on 2009-05-04
in the terminal type:
 
cd /boot/grub

then:

gedit menu.lst

then scroll down to the bottom of the page and add this line of code:
title		Windows NT/2000/XP (loader)
root (hd0,0)
makeactive
savedefault
chainloader +1
boot

---

### Post by xreaper on 2009-05-04
Did you manage to get windows working?

---

### Post by thingy87654321 on 2009-05-04
yes, thank you very much, but can you help me with this please? thanks in advance

[http://ubuntuforums.org/showthread.php?p=7215039#post7215039](http://ubuntuforums.org/showthread.php?p=7215039#post7215039)

---

