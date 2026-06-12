---
title: "Problem with Compaq Boot"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by c-smith35 on 2008-01-08
I am a Noob with Linux, but have to say I am very impressed

I have a Compaq Presario 2526E and have recently installed 7.10

The only problem I have is upon turning the computer on, my screen seems to go funny, and slowly shifts from a black screen to a grey pixely screen, instead of showing an ubuntu startup screen to show what is happening. The same thing happens when shutting down the computer, although when shutting down I also get 2 horizontal lines accross the screen. The strange pixelation effect looks similar to what happens when you press on the screen. 

I think it is trying to show the boot/shutdown screens (on 7.3 it displayed 'Ubuntu' with a progress bar underneath, similar to what happens when starting Windows XP), but without being able to see anything, it's impossible for me to tell

I previously, and briefly had 7.3 installed and didn't have this problem, but I am in the middle of making the 'big switch' and so keep changing back to XP to try and decide which I prefer.

Any ideas?

---

### Post by luisromangz on 2008-01-08
You should check the vga parameter of the kernel option you boot. That can be found in /boot/grub/menu.lst

Try setting vga=normal.

But be careful, that file is not meant to be broken, search on the Internet about the vga option and the grub config file if you don't feel like editing that file easily.

---

### Post by c-smith35 on 2008-01-09
thank you for getting back to me luisromangz,
I have opened up the menu.lst file, but cannot find anything to do with vga
There is a lot of writing with hashes at the beginning ( I assume this is a way of noting out the code)
The only unhashed code in this file is:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5083869e-0896-4261-ba6c-28f8cb1a7157 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5083869e-0896-4261-ba6c-28f8cb1a7157 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

I think the quietsplash may mean something but I'm only clutching at straws. As a complete newby, how do I change this code?

---

