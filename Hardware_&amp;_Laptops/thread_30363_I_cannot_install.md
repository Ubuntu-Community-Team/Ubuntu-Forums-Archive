---
title: "I cannot install"
date: 2005-04-28
forum: Hardware &amp; Laptops
---

### Post by LinxNew on 2005-04-28
Hi,

I've dowloaded 5.04 and burned it on a cd.
I start boot menu from cd, press enter and then I have a black screen.

I've a laptop Toshiba. 
It's the first time that I have this type of problem.

Can someone help me to start the first installation ?  :roll:  ](*,)

---

### Post by LinxNew on 2005-04-28
Some other information:

after a press enter at boot promt, I can see that Ubuntu try to load. I see a flash about acpi and then no more response from my laptop.

So, I try to write at boot promt 'linux acpi=off' , 'expert', 'expert acpi=off', but there is no difference.

What can I do ?

---

### Post by Sami on 2005-04-28
I have installed ubuntu 5.04 on a Compaq nx8220 and had a similar problem. After choosing the install mode (i just pressed enter) i had a blackscreen. After that i pressed short the little button which is pressed down when you close the screen of your notebook. After that everthing was working fine.

---

### Post by LinxNew on 2005-04-28
Thanks for the tips Sami, but doesn't work for me.  ](*,)

---

### Post by alastair on 2005-04-28
Hard to say. Maybe try :

linux noapic acpi=off
or
linux noapic

Maybe google for your specific laptop model and see if others have problems.

---

### Post by LinxNew on 2005-04-28
I tried acpi=off and other solution, but nothing.

So finally I find the really solution :  set vga=791

But now, when Utumbu try to detect automatically my laptop hardware it's block at 98%, when 'starting pc card services...' :mad:  :confused: 

What can I do now ?

---

