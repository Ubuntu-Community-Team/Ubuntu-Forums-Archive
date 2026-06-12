---
title: "Can someone help?"
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by thegreenblob on 2007-02-03
Can someone explain to me like I was a 4 year old on how to get my ATI RADEON XPRESS 200M IGP video card to work right? I tried several tutorials with no luck :/

All I wanna do is play open arena... but keeps saying I don't have 3d acceleration...

My laptop is a HP Pavilion ZE2315us... And just wanna get it to work!

Thanks.

---

### Post by bsalt on 2007-02-03
hm... (trying to remember what i know)

1) Go to Ati's driver page:
[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

2) Choose linux_x86 if you don't have 64-bit installed (type "uname -r" without the quotes in the terminal). If it has "amd64" or something like it at the end, you have 64-bit installed. If you do have the 64-bit version installed, choose linux_x86-64
 
3) Then choose Integrated/Motherboard

4) Then Radeon Xpress 200

5) Download the one at the top of the list and save it to your desktop.

6) After the download finishes, type this in a terminal:

```
cd Desktop
sudo sh ati*
```


Let me know if this helps

---

### Post by thegreenblob on 2007-02-03
Nope. didn't work :( . It says theres no hardware acceleration still and could not open opengl subsystem. So... any more help? Did I do something wrong in the installation?

---

### Post by Mike'sHardLinux on 2007-02-03
Did you notice if the command actually executed?

When I download bash scripts (*.sh), I always have to make them executable first.
```

chmod +x name_of_script.sh

```

---

### Post by thegreenblob on 2007-02-03
uhh... not sure what that id cause all it did was go to the next line, lol. But, I just noticed there was something called "ATI Control" in my applications menu... but when I click it it says something like it cannot be found or something? :confused: I am so confused here...

---

### Post by thegreenblob on 2007-02-04
Anyone?

---

### Post by thegreenblob on 2007-02-04
Come on! There must be someone that knows whats wrong :confused:

---

### Post by bsalt on 2007-02-05
Well, I'm going to build and install the game for my computer - I have an onboard Intel video card. I'll see if I get something like that error you get.

I will say, however, that 3d support for ATI cards is *extremely* limited for Linux/UNIX. Everybody seems to push for Nvidia cards when they are given an option. But as you are not, I am just trying to explain why this is receiving limited replies. 

Make another post asking how to setup and enable 3d acceleration for ATI cards. See if that helps.

I'll let you know what happens with the game on my end. If I get something like that as well - and I already have 3d acceleration enabled on my Intel GMA, then it's a game problem and not an Ubuntu prob.

---

### Post by imspecial on 2007-02-06
just wondering, how did you manage to get 3D acceleration enabled on your intel card? did you compile the mesa drivers or use an actual intel supported driver?

---

### Post by bsalt on 2007-02-06
Well, 3d acceleration actually worked "out of the box". But to be sure, I typed "sudo modprobe i810" - a command that checked that module i810 - the driver for almost all Intel graphics cards (even mine, a GMA 950). Did you do a basic search on Google on how to get 3d up and running for ATI cards with just Linux?

---

