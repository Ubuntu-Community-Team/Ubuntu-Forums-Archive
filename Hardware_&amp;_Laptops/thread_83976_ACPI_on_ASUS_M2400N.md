---
title: "ACPI on ASUS M2400N"
date: 2005-10-30
forum: Hardware &amp; Laptops
---

### Post by Subtestube on 2005-10-30
Hi all, I'm fairly new to Linux, and I've just been trying to set up Ubuntu 5.10 on my notebook, but I've run into a few issues. I was able to install Ubuntu only with acpi=off, and of course that means that ACPI now doesn't function. I did try enabling it in an extra menu option in the Grub that I created, but that just caused the system to hang. Anyone who can direct me to instructions on how I might fix this, bearing in mind that I'm a bit of a Linux "noob", would be greatly appreciated.
I should state that sound doesn't work at the moment, because (I would guess) IRQs for it are assigned through ACPI. 

Just in case it helps, my specs on the notebook are as follows:

Pentium M 1.5Ghz (Banias)
i855 GM/GME Chipset
Intel Extreme Graphics (Shared, as if there was any other kind of Intel integrated graphics)
512 MB DDR RAM.
And various other components that I can't be bothered listing - if you need anything else to offer me assistance, please feel free to ask.

---

### Post by cdias on 2005-11-10
I had the same problem with my asus m2400n. An upgrade with the last bios should solve the problem. The acpi will install and the system will not hang. But the battery indicator on gnome works bad. The indicator always says that you are connected to battery. By the way, anyone have a solution for this?

---

### Post by new2linux9 on 2005-11-16
[QUOTE=cdias]I had the same problem with my asus m2400n. An upgrade with the last bios should solve the problem. The acpi will install and the system will not hang. But the battery indicator on gnome works bad. The indicator always says that you are connected to battery. By the way, anyone have a solution for this?[/QUOTE]
Hello, I was just wondering if you had found a solution to the battery indicator.  I am completely new to linux, and have the same problem with my ASUS M5200N.  Thank you.

---

### Post by bennibuntu on 2005-12-07
Hello

I have the same problem with my asus s1300n. installtions only works with acpi=off. that causes no sound and thats not acceptable.
I have installed the last bios (0206). I've read in a german forum, that i should fix my acpi (dsdt). but i can't do it myself.

the other interesting point is suse 10. this distri works correctly with my acpi. may you have an idea why?

cheers
benni

---

### Post by Gordone on 2008-01-29
Hi All,

Just in case anyone is still working with one of these dinosaurs. The BIOS needs to be updated before sound in Ubuntu will work properly (apparently, I'm still on the case), unfortunately it has to be done in Windows (or DOS).

So fire up the evil OS for the last time, and update the BIOS before formatting:) Here is the driver website:
[http://www.asus.com/products.aspx?l1=5&l2=26&l3=124&model=34&modelmenu=1](http://www.asus.com/products.aspx?l1=5&l2=26&l3=124&model=34&modelmenu=1)
ASUSTeK Computer Inc.

Cheers,
Gordon

---

### Post by Mr.Kuchinawa on 2008-05-14
I know this thread is old, but.. How do I update the BIOS in XP?

---

