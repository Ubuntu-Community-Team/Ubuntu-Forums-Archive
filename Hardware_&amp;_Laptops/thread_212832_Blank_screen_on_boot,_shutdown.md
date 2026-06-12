---
title: "Blank screen on boot, shutdown"
date: 2006-07-10
forum: Hardware &amp; Laptops
---

### Post by Ficus on 2006-07-10
Using an Acer Aspire 5004WLMi, I have strange problem.  When I boot Dapper, the screen goes blank.  It boots, and GDM come up a few minutes later.  I also get the blank screen when I shutdown.  However, when I boot into safe mode, the text boot works.  I tried changing some stuff around with the uplash, but nothing happens still.  If it would help to completely disable it, I can't find anything that tells me how to do that (or at least, nothing clear)  I also get the blank screen when I use Ctrl+Alt+F1-6 to swtich to a terminal.  The terminals obviously works, but they don't show anything.  I keep thinking it's a problem with the widescreen moniter on here.

---

### Post by stephen53 on 2006-07-10
Do you use the nvidia video driver ? I had this problem and the virtual  consoles  were blank too. Apparently the newest Nvidia graphic drivers will not display in the default kernel low res video mode. To change this behavior in the /boot/grub/menu.lst file add this to the end of the kernel line. vga=791 which gives 1024 x 768 res. in the video setting. Different values give different color and screen resolution , that setting sets the color to 16 bits. This is working fine on my machine. What follows is my first default grub setting after editing.

title Ubuntu, kernel 2.6.15-23-686
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-23-686 root=/dev/sda1 ro quiet splash vga=791
initrd /boot/initrd.img-2.6.15-23-686
savedefault
boot

some notes I used.
This is notes on vesa frame buffer settings. Got from Linus Annoyances For Geeks. Today's date is 6/26/2006. 

Frame Buffer know-how is at [http://www.tldp.org/HOWTO/Framebuffer-HOWTo.html](http://www.tldp.org/HOWTO/Framebuffer-HOWTo.html)  .

Table 5-3. VESA video modes

Bits	640x480	800x600	1024x76  1280x1024  1600x1200

8	769	771	773	 775         796

16	785	788	791      794         798

32	786	789	792	 795         799

I have used this on the menu.lst , for grub on the kernel line , used 

vga=791 , to pass this vesa parameter to the kernel.

(This edit has to be done as root or sudo . copy your menu.1st to a back up file before you edit. 
on command line 
cp boot/grub/menu.lst  boot/grub/menu.lst.backup
hope that this helps.)

---

### Post by Ficus on 2006-07-10
Thanks

I don't have a an Nvidia card, I have a SIS card...  that kinda sucks, heh.  Either way, it did work, although I would prefer not to have that stretched-out screen that happens with widescreen, but eh.

---

### Post by usererror on 2006-07-11
i have the exact same problem on my ATI X600 Dual DVI Video Card.  Would that 'fix' above work for me too?  I haven't tried getting the dual video to work yet.

---

### Post by KevinM on 2006-10-30
I have the exact issue with a Dell 2005FPW using DVI.  I'll have to read up on this vga parameter.

---

### Post by fireboxtester on 2007-08-01
> **stephen53 said:**
> Do you use the nvidia video driver ? I had this problem and the virtual  consoles  were blank too. Apparently the newest Nvidia graphic drivers will not display in the default kernel low res video mode. To change this behavior in the /boot/grub/menu.lst file add this to the end of the kernel line. vga=791 which gives 1024 x 768 res. in the video setting. Different values give different color and screen resolution , that setting sets the color to 16 bits. This is working fine on my machine. What follows is my first default grub setting after editing.

title Ubuntu, kernel 2.6.15-23-686
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-23-686 root=/dev/sda1 ro quiet splash vga=791
initrd /boot/initrd.img-2.6.15-23-686
savedefault
boot

some notes I used.
This is notes on vesa frame buffer settings. Got from Linus Annoyances For Geeks. Today's date is 6/26/2006. 

Frame Buffer know-how is at [http://www.tldp.org/HOWTO/Framebuffer-HOWTo.html](http://www.tldp.org/HOWTO/Framebuffer-HOWTo.html)  .

Table 5-3. VESA video modes

Bits	640x480	800x600	1024x76  1280x1024  1600x1200

8	769	771	773	 775         796

16	785	788	791      794         798

32	786	789	792	 795         799

I have used this on the menu.lst , for grub on the kernel line , used 

vga=791 , to pass this vesa parameter to the kernel.

(This edit has to be done as root or sudo . copy your menu.1st to a back up file before you edit. 
on command line 
cp boot/grub/menu.lst  boot/grub/menu.lst.backup
hope that this helps.)

I'm having this exact same problem and I want to try your fix.  However my monitor uses 1920x1200 and I want 32 bit graphics.  Would I not use vga=791 for that?

OR OR, does this not affect the xorg display only consoles and at shutdown?  Please help a poor feller.

---

### Post by Cappy on 2007-08-01
Just use boot parm "nosplash". "vga=791" will only fix the problem on bootup, not shutdown.

---

### Post by fireboxtester on 2007-08-01
how would nosplash fix the problem on shutdown?

---

### Post by fireboxtester on 2007-08-01
That fixed it for me.  Though I'm not sure if the nosplash or the vga=.. fixed it.  Oh well, I don't need a splash I guess.

Here's what the part of my menu.lst file that I changed looks like now:

```
title		Ubuntu, kernel 2.6.15-28-686
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-686 root=/dev/sda2 ro quiet nosplash vga=791
initrd		/boot/initrd.img-2.6.15-28-686
savedefault
boot
```

---

