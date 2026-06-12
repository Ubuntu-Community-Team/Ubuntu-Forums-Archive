---
title: "Lenovo VGA driver for Ubuntu ?"
date: 2010-10-07
forum: Hardware
---

### Post by binu305 on 2010-10-07
I have installed ubuntu 10 desktop version on my Lenovo Notebook. It has already windows XP. And both operating system working finely. But the problem is when i boot from ubuntu my desktop is not at all have a good look and feel. I tried different desktop theme. My question is do i want to install any display driver in my notepad ?. If yes where can i find it ? and how can i install it ?  I dont have much knowledge in ubuntu/linux OS.
My notebook is Lenovo N100 series.

---

### Post by coffeecat on 2010-10-07
> **binu305 said:**
> But the problem is when i boot from ubuntu my desktop is not at all have a good look and feel.

Can you expand on what you mean? Are the fonts not properly rendered? Do you get tearing when you try to move a window? Is the monitor resolution wrong? Or is it just the colour scheme you don't like?

> **binu305 said:**
> My question is do i want to install any display driver in my notepad ?

That really depends. We need to know more about your hardware. What model Lenovo notebook is it? Open a terminal (Applications > Accessories) and post the output of this command:

```
lspci | grep -i vga
```That will tell us what video chipset you have, whether it's a "problem" one, and whether a different driver would help.

---

### Post by binu305 on 2010-10-07
> **coffeecat said:**
> Can you expand on what you mean? Are the fonts not properly rendered? Do you get tearing when you try to move a window? Is the monitor resolution wrong? Or is it just the colour scheme you don't like?



That really depends. We need to know more about your hardware. What model Lenovo notebook is it? Open a terminal (Applications > Accessories) and post the output of this command:

```
lspci | grep -i vga
```That will tell us what video chipset you have, whether it's a "problem" one, and whether a different driver would help.

This is my terminal out put

laptop:~$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by binu305 on 2010-10-07
Actually my problem is desktop looking dull. Other than this everything working perfect.

I have only one week experience with Ubuntu/Linux. Doesn't Ubuntu provide a graphics like MS Windows system ?

---

