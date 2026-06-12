---
title: "[Solved]Low resolution Xubuntu 17 on Hp Pavillon 15 AB 113NL"
date: 2017-06-23
forum: Hardware
---

### Post by chefare2 on 2017-06-23
Hello everybody
I have a big and strange seamless problem ..
I installed it on my notebook with ati R7 M260/265 graphics card, Xubuntu 17, but to make it go to the grub I entered with nomodeset.
Now the system only starts with 800x600 resolution...but if you drop the nomodeset command, from grub, I have black screen..
The 4-10 kernel does not charge the drivers, but these are compatible with the ATI card..
If I use the command  xrandr --listproviders, nothing is found...also lshw -c display | grep driver...
Do you have solutions? :(
Thank you

---

### Post by chefare2 on 2017-06-24
Hi friends, do you have any advice?

---

### Post by gsahli on 2017-06-24
I would try the suggestions here:
[https://wiki.archlinux.org/index.php/AMDGPU](https://wiki.archlinux.org/index.php/AMDGPU)

On one machine, I had success by creating the simple xorg.conf shown (and get rid of nomodeset).

---

### Post by chefare2 on 2017-06-26
Hi
Thanks for the advice, but I have tried the solutions, but it dosn't work.. My hardware is bad for linux, not even wireless intel 3165 and bluetooth.. .
I also tried with 3.9 kernel...nothing!
Only win 10 works..
Just give it up
Thanks

---

### Post by chefare2 on 2017-06-28
Hello friends

I solved the problem of video resolution.
I think the problem is due to the new kernel or xorg or system boot file.. . But I'm not an expert :p
I did so:
1) kernel installed 3.16 with Xorg 7.7 
2) Fglrx proprietary drivers installed
3) Installed fglrx proprietary drivers and all amd (microcode-tool, etc..) packages.
4) Reconfigure xorg with command # aticonfig --initial
5) Reboot

I've tried all kernels up to 4.11 (with open or proprietary drivers), but nothing, black screen ever.
This is the only solution that works with this laptop model..
The only problems present now are:
Intel wifi card 3165 does not work, driver are in kernel 4...
Realtek bluethoot card not work..


Ciao ):P

---

