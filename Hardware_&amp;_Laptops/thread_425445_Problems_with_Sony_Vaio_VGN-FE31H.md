---
title: "Problems with Sony Vaio VGN-FE31H"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by s1nnless on 2007-04-27
Hi. It's my 1st time using ubuntu and i had some issues with Intel 3945G Wi-Fi and my nVidia Geforce Go 7400. I use Ubuntu 7.04 x86 version. I can't install their drivers. I downloaded them in nvidia.com and Intel.com, but i can't get the instalation to start. Can Someone help me?

PS: other thing, does any mp3 software player, like winamp or foobar, exist for linux?

---

### Post by s1nnless on 2007-04-29
Please, can someone help me?

---

### Post by Nizarus on 2007-06-12
Hello I have the same laptop and wireless works out of the box with feisty. For the graphic card I used the restricted manger to install th appropriate driver and it works fine.

---

### Post by JakZ on 2007-06-28
I got this laptop too and everytime I try to install the Nvidia drivers (did it with the nvidia install from the website, with the repository and with the automated Envy ) and every time I install them, activate them in X , reboot and then I get the message the kernel from the linux and the kernel from the nvidia differ in number and X crashes (it actually crashes first and then displays the message) 

Can anybody please help in this issue? getting pretty desperate here and I DON'T want to go to Windows Vista :(

---

### Post by toocrazy on 2007-07-13
I too have this laptop and no problems at all
Could you post your xorg.conf file

---

### Post by Smeg Head on 2007-07-13
Hmmm thats very odd. I have a vaio FE28B, which has nigh on identical hardware to the FE31H, at least with graphics and wireless :) Yeah, i have the same wireless and graphics hardware and it worked out of the box on feisty. Hell the wireless would have worked off the lived CD if it wernt for WPA. All i had to do for the graphics was enable it in the restricted driver manager. Dont worry tho, one of the dudes around here will have a solution for you, and whatever you do dont go to vista!!!!!

---

### Post by JakZ on 2007-07-16
Hello :) I wouldn't want to go Vista. I finally came up with a solution :

I had to unload the graphic kernel drivers and fysically delete all related files, i did an apt then again and it works perfectly now !


Thanks for the support anyway! ubuntu all the way :guitar:

---

