---
title: "Turn my laptops into a &quot;server&quot;"
date: 2011-08-08
forum: Hardware
---

### Post by alokhan on 2011-08-08
Hi,

I have a old Alienware (**Area-51® m5550** ) laptops which i want to turn into a home server. 
The first issue is, it has a ACPI bug which increase the boot time by 15 seconds ... which is very annoying.
But the second issue is that my graphic card is not working correctly, I think it is because of over heating (the laptops is horrible about that, it's always very hot even if you don't do anything). I took apart my laptops but of course it wont start without the graphic card. Is there a way to make the laptop start without it ? because it over heat and it is useless for a server and i am afraid that one day it will totally burn and make  damage to the motherboard or so.

For the acpi problem I try this tutorial [http://www.lesswatts.org/projects/acpi/faq.php](http://www.lesswatts.org/projects/acpi/faq.php) but of course i am stuck so if anyone could help me i would appreciate it.

Regards 

Alokhan

---

### Post by elliotbeken on 2011-08-08
If you are using it as a home server why dont you use the ubuntu server edition ? this would keep the GPU cool as it will be under low usage. 

also if the server is always on like a server should be why is the boot time a problem ?

---

### Post by alokhan on 2011-08-08
Well i also want to use it over ssh to compile software so i am not gonna let it turn on all the time that's why the boot time is important, and also because i don't like seeing bug during boot :P. But I am currently editing my DSDT :) 

About the graphic card, yes i could install unbuntu server this is true but i would like to know what makes removing the graphic card impossible ? the bios ?

---

### Post by navr91 on 2011-08-08
I think it depends on whether your computer has an integrated graphics card in the motherboard. If your motherboard doesn't have integrated graphics then your computer won't be able to boot, as in it won't even POST, which means it will fail even before loading the BIOS and obviously the OS.

Does your motherboard have integrated graphics?

---

### Post by alokhan on 2011-08-09
> **navr91 said:**
> I think it depends on whether your computer has an integrated graphics card in the motherboard. If your motherboard doesn't have integrated graphics then your computer won't be able to boot, as in it won't even POST, which means it will fail even before loading the BIOS and obviously the OS.

Does your motherboard have integrated graphics?

Unfortunately, no :(

---

### Post by navr91 on 2011-08-09
My suggestion would be to find a cheap, basic graphics card. What ports/slots does your laptop have?

---

