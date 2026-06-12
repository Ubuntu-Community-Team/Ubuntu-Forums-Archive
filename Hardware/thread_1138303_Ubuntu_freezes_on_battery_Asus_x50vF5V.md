---
title: "Ubuntu freezes on battery Asus x50v/F5V"
date: 2009-04-26
forum: Hardware
---

### Post by painkiller1980 on 2009-04-26
Hello
I had a problem with my Asus x50v.
It was freezing on Ubuntu when I plugged off the wire cord, when it had to use battery.
I just flashed/upgraded my BIOS.
The BIOS version was 212, and I upgraded to 216 (from Asus website: DOWNLOADS> NOTEBOOK> F5> F5V). Because I have also Vista installed on my laptop too, I used WinFlash, but offcourse there is other way to do this if you don't have Vista on it.
Now it's working good.
Good luck!
ps.: excuse me for my not so good english.

---

### Post by memyself on 2009-05-06
Hy - got the same problem with my x50v !! Since Ubuntu 7.04.

Freezes on startup when in batterie-mode, freezes when plug out ac connection!

What I did was:  open the_ "/boot/grub/menu.lst"_  and add _"nolapic"_  !

open terminal, type: sudo gedit  /boot/grub/menu.lst 

This didn't really fix it, but it works. Prob is, that with this option only one core is running, but i can use the laptop.;)

should look like this:
...
title        
Ubuntu 8.10, kernel 2.6.27-11-generic
uuid        d5d33eb7-8569-4996-9b69-7e91f64c5838
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=d5d33eb7-8569-4996-9b69-7e91f64c5838 ro quiet splash_*** nolapic***_
initrd        /boot/initrd.img-2.6.27-11-generic
quiet
....

Hope I could help u !

---

### Post by rez182 on 2011-04-01
its happening to me, i cant use my Ubuntu 10.10 in battery mode in my Asus K40IE. updated my BIOS to 215 (Latest) but still does not work. any idea how to solve it?

---

