---
title: "Fail to install"
date: 2005-12-02
forum: General Help
---

### Post by be_me on 2005-12-02
I have a Pentium III 500Mhz with 398mb Ram. I decided to install on it Ubuntu, everything go ok untill 33% of the installation than it stop and never continue.
I am installing with the cds that I received in the post and tried with the minimun hardware possible, motherboard, processor and graphic and it is the same. Someone with the same problem?:( :(

---

### Post by Miguel on 2005-12-02
Hi be_me,

I am sorry to tell you that it is likely that the shipped CD you use is broken. If you have access to another shipped CD, you could try this. If you have or know someone that has a fast internet connection, you can also try to download the Ubuntu 5.10 ISO image.

Anyway, do you get any error message? When does the installer fail? Did it get to the first reboot?

EDIT: I'll be out for the weekend

---

### Post by be_me on 2005-12-02
The cd is good. I tried with other cd and did not work too. It do not appear nothing just stop in the 33%:( it happens the same with Kubuntu.
It is strange

---

### Post by vaquerox on 2005-12-02
hi ppl.

Im a complete noob in linux. It's my first time installing linux.

I was installing ubuntu and after screen when the file aer loaded appear something like that:

                                          UBUNTU

                             xxxxxx                     ok
                             xxxxxx                     ok
                             xxxxxx                     ok
                             xxxxxx                     [COLOR="Red"]failed[/COLOR]


and then start to install and appear an error and the installation don't continue. then ask for my login and my password but nothing happens and I type the right login and password but nothing.

Can anybody help me?

---

### Post by linbetwin on 2005-12-02
[quote=vaquerox]hi ppl.

Im a complete noob in linux. It's my first time installing linux.

I was installing ubuntu and after screen when the file aer loaded appear something like that:

                                          UBUNTU

                             xxxxxx                     ok
                             xxxxxx                     ok
                             xxxxxx                     ok
                             xxxxxx                     [COLOR=Red]failed[/COLOR]


and then start to install and appear an error and the installation don't continue. then ask for my login and my password but nothing happens and I type the right login and password but nothing.

Can anybody help me?[/quote]

Can you tell us what module failed?

---

### Post by vaquerox on 2005-12-02
I really dont know because the name of the module is too fast for my sight...im in my job right now but in 2 hours i'll check and i'll tell you.

---

### Post by cgjones on 2005-12-02
As for the 33% problem, I used the pci=noacpi option. When you boot to the install disk, at the boot: prompt, type linux pci=noacpi. This was the only thing I did differently from the first failed install attempt, and it seemed to work fine. This was on an older machine that didn't have an acpi enabled bios.

---

### Post by be_me on 2005-12-02
Tpmorrow I will try it. I hope that works thank you for your help:smile:

---

### Post by vaquerox on 2005-12-02
thanx for your intention to help me but I already have ubuntu installed and running, but now i need help for install my ethernet card, It's an encore fast ethernet  network adapter ENL832-TX-ICNT, I already have the drivers but I don't know how to install it.

---

### Post by be_me on 2005-12-03
I try the comand but the computer continues to stop during the instalation this time was not at 33% but at 32:( :( 
What else can I  try?

---

### Post by cgjones on 2005-12-03
I don't see why this would matter, but what filesystem are you using? I manually set up the drive when I installed and I chose ReiserFS. Also, check the settings in your BIOS. See if there is anything about ACPI. I've seen this problem elsewhere on the forum and no one seems to have a definite fix for it.

---

### Post by Miguel on 2005-12-05
Hi again be_me,

Could you try installing ubuntu with the "noapic" (or similar, see the Fx pages before installing) option? By the way, what are your hardware specs?

---

