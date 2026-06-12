---
title: "No Sound After Installation"
date: 2007-10-02
forum: Hardware &amp; Laptops
---

### Post by jonel on 2007-10-02
Newbie. Desperate for Help in getting sound working on my Toshiba Satellite P100 Laptop model PSPA3C - SD402E. I've gone through the forum threads and found what i needed. I had to download Intel's ACPI  
compiler and use it to compile the DSDT.dsl file in /usr/src/DSDT directory. I did that. And i also corrected the errors in the file as instructed.Now for some reason when i make changes to the file i can't save the file with the corrected info. The save option is grayed out. By  looking at the directory permissions i found that root is the owner and no modifications can be made. I need someone to give me detailed instructions on how to save the DSDT,dsl file. I know i have to be in root console (maybe?) but i don't know how to save a file from a console yet.

---

### Post by gene6482 on 2007-10-05
you can either edit it in the terminal using sudo nano dsdt.dsl, or you can use gksudo and then whatever text editor you use (it's letting you be root inside of gnome)

---

