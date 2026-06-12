---
title: "GRUB Won't Boot Without CD Drive"
date: 2007-12-07
forum: Hardware &amp; Laptops
---

### Post by computergee on 2007-12-07
I just got a battery for my Gateway Solo 9500, but it goes in the place of the cd-rom drive. The problem is GRUB doesn't like to start without the cd-rom drive in place, it just sticks on "GRUB Loading stage1.5." and won't go any farther. Anyone know what's going on?

---

### Post by muskratmx on 2007-12-07
Grub should give you an error message number.

The look in the grub manual and you should be able to see the problem.

The grub manual can be found at [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html) .
There is a complete listing of the error numbers with explanations in chapter 14.

---

### Post by vac on 2007-12-07
If you may post the menu.lst from /boot/grub/menu,lst, it may usefull.

---

### Post by computergee on 2007-12-07
After much testing, I don't think it's GRUB, I've used LILO and it still won't go without the cd drive plugged in, I think it's something in my BIOS. I updated it and still no dice. I don't receive any error from grub, nor did I LILO.

---

### Post by muskratmx on 2007-12-09
That sure seems to be a strange disign, having a laptop which uses the cd bay for a battier  How would one use cd on the go?

---

### Post by staticvoid on 2007-12-09
I had a dell that had two slots that could fit either two batteries or two Cd's or one of each.

cool stuff :P

check the boot order for your BIOS if you think it is your BIOS

---

### Post by computergee on 2007-12-11
The battery I have is designed to be a secondary battery, but I can't afford a primary one, so that's all I'm using. I'm almost sure it's a BIOS problem now. I've installed Ubuntu completely from hard drive, so it would be aware of any cd-rom drive existing and the same happens.

---

