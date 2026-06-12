---
title: "problem with my vga"
date: 2008-02-27
forum: Hardware &amp; Laptops
---

### Post by siavash_t on 2008-02-27
hi guys,
i am new to ubuntu and linux so sorry for the noob question

i have nvidia geforce fx 5200 installed in my pc . i downloaded the linux driver for it , typed the command written in nvidia site . an installation program launches but it says "you should be root to install te driver" 
my account name is something different from root but it has all the authorities needed for driver installation so what should i do ? please help
thnx

---

### Post by jeffus_il on 2008-02-27
Don't install the driver manually, use the restricted driver package (linux-restricted-modules)and the restricted driver application (restricted-manager)to enable it.

---

### Post by oldsoundguy on 2008-02-27
I have a 5200 on one older machine as it had no AGP slot.  I used Envy to install and have had no problems with it.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by .nedberg on 2008-02-27
> **jeffus_il said:**
> Don't install the driver manually, use the restricted driver package (linux-restricted-modules)and the restricted driver application (restricted-manager)to enable it.

+1

---

### Post by siavash_t on 2008-02-27
> **jeffus_il said:**
> Don't install the driver manually, use the restricted driver package (linux-restricted-modules)and the restricted driver application (restricted-manager)to enable it.

i did it but it seems that the driver isnt installed properly the effects of compiz-fusion dont work well

any idea about the login ?
what is my root password anyway? i didnt creat any root account just one account named "siavash"

---

### Post by jeffus_il on 2008-02-27
Have you installed xserver-xgl instead of the regular xserver?
You don't need a root password in Ubuntu, use ```
sudo <command>
``` instead, it's much safer ...

---

### Post by siavash_t on 2008-02-27
as i said i'm new to this os and even dont know what these things are !
i just followed the installation wizard . didnt install anything special

Edited: i just checked now it is x server and with "sudo" command the problem vanished :) thank you all

---

