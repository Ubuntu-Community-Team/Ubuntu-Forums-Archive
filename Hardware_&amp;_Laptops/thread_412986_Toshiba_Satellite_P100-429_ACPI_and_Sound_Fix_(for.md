---
title: "Toshiba Satellite P100-429 ACPI and Sound Fix (for Bios 3.30)"
date: 2007-04-18
forum: Hardware &amp; Laptops
---

### Post by rax_m on 2007-04-18
Hi all, 

I finally managed to fix my Toshiba P100-429 with a custom DSDT. 

Please follow this guide: 
[http://ubuntuforums.org/showthread.php?t=349491&highlight=toshiba+p100+dsdt](http://ubuntuforums.org/showthread.php?t=349491&highlight=toshiba+p100+dsdt)

But use the custom DSDT that I have built for this laptop. 

So far ACPI and sound and Hibernation seems to be working. I will post the new DSDT on acpi.sourceforge.net.
I commented out some of the lines in the code which seemed to be windows specific to fool the ACPI to think Linux is Windows. Hopefully that shouldn't cause any issues. 
I also had the help of a spanish (i think) website that showed me how to fix the compilation errors  that I had. 
[http://sle.homelinux.net/olive/?p=67#more-67](http://sle.homelinux.net/olive/?p=67#more-67) 
Unfortunately I don't speak Spanish so kind of deciphered the text along with my errors .. fingers crossed. 

Hope this helps someone else :) 

Rax

---

### Post by samopal on 2007-04-19
any idea how to fix it for P100-324? :confused:

---

### Post by rax_m on 2007-04-19
Hi, 

It took me a little bit of searching and reading before I finally figured it out. 

Check this link: [http://acpi.sourceforge.net/dsdt/index.php](http://acpi.sourceforge.net/dsdt/index.php)

Theres some info on DSDT's and link to a couple of HOWTO's. I used these as a basis for starting off. 
I also had to install Intels ASL compiler on my laptop (which had some dependencies like bison). 
I didn't have to do any of the dsdt patches or any of the other things recommended. 

So basically I followed these steps  (if I remember correctly.. some of the other links can give you the details). 

1. Install Intel ASL compiler ( you may to additionally install bison and flex thru synaptic) 
2. cat /proc/acpi/dsdt > dsdt.dat (root power needed here) this gives you the compiled DSDT
3. Decompile the DSDT using: iasl -d dsdt.dat 
    This gives you two files dsdt.asl and dsdt.hex
4. Try and compile the dsdt.asl file : iasl -tc dsdt.asl
    This will generate some errors and warnings which you'll have to fix with the help of some of the other guides and a text editor. 
5. Once you've got a fully working compilation than you can install as per the link I provided in my post. BTW I think some of the installation instructions in the prev post are Edgy specific. 

** Make sure you backup your system as recommended first tho' !! 

Let me know if anything is unclear. 

Rax

---

### Post by gene6482 on 2007-04-19
does gnome-power-manager work for you after the recompile?
for some reason acpid isn't working for me after i recompiled my p105-s6197s dsdt

---

### Post by rax_m on 2007-04-19
If I go to the power management application in Preferences -> Power management, the tool is launched and I can change my settings there. They seem to work after I have the changed them too. 

R

---

### Post by loliverouge on 2007-04-19
> **rax_m said:**
> Hi all, 

I finally managed to fix my Toshiba P100-429 with a custom DSDT. 

Please follow this guide: 
[http://ubuntuforums.org/showthread.php?t=349491&highlight=toshiba+p100+dsdt](http://ubuntuforums.org/showthread.php?t=349491&highlight=toshiba+p100+dsdt)

But use the custom DSDT that I have built for this laptop. 

So far ACPI and sound and Hibernation seems to be working. I will post the new DSDT on acpi.sourceforge.net.
I commented out some of the lines in the code which seemed to be windows specific to fool the ACPI to think Linux is Windows. Hopefully that shouldn't cause any issues. 
I also had the help of a spanish (i think) website that showed me how to fix the compilation errors  that I had. 
[http://sle.homelinux.net/olive/?p=67#more-67](http://sle.homelinux.net/olive/?p=67#more-67) 
Unfortunately I don't speak Spanish so kind of deciphered the text along with my errors .. fingers crossed. 

Hope this helps someone else :) 

Rax

Hello,

"http://sle.homelinux.net/olive" is my website and i'm french :lolflag: but thank you to refer me :popcorn: 

Bye ;-)

---

### Post by rax_m on 2007-04-20
A while after I'd posted and I was looking at your site again I realised that it was French!! :redface: 

Sorry for my mistake! And thanks for the help on your site it was really useful :KS . I tried to post a msg to your site but it didn't work at the time so i gave up.

---

### Post by loliverouge on 2007-04-25
No problem :guitar: , you're welcome

Thank's again :popcorn: 

see you soon...

---

