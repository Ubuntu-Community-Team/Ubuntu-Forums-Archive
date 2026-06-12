---
title: "Saitek Cyborg Mouse and Keyboard Drivers"
date: 2009-08-26
forum: Hardware
---

### Post by Kirboosy on 2009-08-26
Hello I am new to Ubuntu. I have previous experience with Fedora 9 and 11. I still would call myself a newbie to Linux in general. 
My question is I have a Saitek Cyborg Mouse and Keyboard but the drivers are written in Windows. In Windows I have full functionality but in Ubuntu I cant use all the special features available. Is there any software that would allow me to emulate the windows drivers? I search google but I came up empty handed.

If it helps any I'm running Ubuntu 9.10 Gnome...
Thanks
Drew

---

### Post by Kirboosy on 2010-01-18
[SIZE="4"]Anybody?[/SIZE]

---

### Post by Kirboosy on 2010-02-25
I tried looking up how to map mouse keys but I can't figure out how to capture the input coming off the mouse

---

### Post by Baspar on 2010-05-04
Can you explain more what would you like to do with the mouse?
For the keyboard, it's media keys are recognized by xbindkeys, but the macro keys doesn't work.
I send mail to Saitek, but I've no reply.

---

### Post by Kirboosy on 2010-09-25
I want my programmable Macro keys to work. I also tried emailing saitek long ago before I ever posted on Ubuntu forums but they seem to have just ignored me because of my OS being Linux...

On my mouse I have a Hat switch and Thumb button. I tried capturing the outputs of the mouse to try and write my own driver but I was unsuccessful.  Here is the mouse to give you an idea of what I'm working with. It can be in 4 way mode or 8 way mode in Windows.

[http://www.amazon.com/gp/product/images/B000VLMRVS/ref=dp_image_0?ie=UTF8&n=172282&s=electronics](http://www.amazon.com/gp/product/images/B000VLMRVS/ref=dp_image_0?ie=UTF8&n=172282&s=electronics)

I know the media keys on my keyboard work I would just like the volume meter and my side macro keys to work as well...
[http://www.google.com/imgres?imgurl=http://www.brapris.no/images/saitek_cyborg_keyboard_sv_fi_-1800790506_0_Big.jpg&imgrefurl=http://www.overclock.net/computer-peripherals/440611-razer-lachesis-saitek-cyborg-keyboard.html&usg=__pFVCB12B-67u76BXofs6-d4PYBM=&h=383&w=591&sz=150&hl=en&start=0&zoom=1&tbnid=r5eHS_XgxP4YwM:&tbnh=111&tbnw=236&prev=/images%3Fq%3DSaitek%2BCyborg%2Bkeyboard%26um%3D1%26hl%3Den%26sa%3DN%26biw%3D1440%26bih%3D711%26tbs%3Disch:1&um=1&itbs=1&iact=rc&dur=381&ei=aR6eTPvPGsOBlAeb2JHGCQ&oei=aR6eTPvPGsOBlAeb2JHGCQ&esq=1&page=1&ndsp=23&ved=1t:429,r:7,s:0&tx=79&ty=26](http://www.google.com/imgres?imgurl=http://www.brapris.no/images/saitek_cyborg_keyboard_sv_fi_-1800790506_0_Big.jpg&imgrefurl=http://www.overclock.net/computer-peripherals/440611-razer-lachesis-saitek-cyborg-keyboard.html&usg=__pFVCB12B-67u76BXofs6-d4PYBM=&h=383&w=591&sz=150&hl=en&start=0&zoom=1&tbnid=r5eHS_XgxP4YwM:&tbnh=111&tbnw=236&prev=/images%3Fq%3DSaitek%2BCyborg%2Bkeyboard%26um%3D1%26hl%3Den%26sa%3DN%26biw%3D1440%26bih%3D711%26tbs%3Disch:1&um=1&itbs=1&iact=rc&dur=381&ei=aR6eTPvPGsOBlAeb2JHGCQ&oei=aR6eTPvPGsOBlAeb2JHGCQ&esq=1&page=1&ndsp=23&ved=1t:429,r:7,s:0&tx=79&ty=26)

Thanks for the help. :)

---

### Post by Baspar on 2010-11-12
I'm in the same case as you.
I've try "sudo od -x /dev/input/by-id/usb-Chicony_Saitek_Cyborg_Keyboard-event-if01" wich is the file for media keys, and  "sudo od -x /dev/input/by-id/usb-Chicony_Saitek_Cyborg_Keyboard-event-kbd" wich is the file for all other keys.. But no one recognize macro keys.
I think it's more complex than any other key..

I've send mails to Saitek too, but no responses..

For the mouse, I suggest you to look at btnx, originally a software for Logitech Mouse, but who recognize all mouses an allow you to create profiles.

---

### Post by Xqua on 2012-01-25
Well for everyone, If you sniff the USB packets between the keyboard and the computer (I didn't tried the mouse yet) You'll notice that all the key sends outputs (even the Macro keys) So you should be able to write your own python driver ! 
The probleme should just be to listen to the interface ! 


I reversed engineered the AlienFX and wrote the pyAlienFX drivers for it, you can check out the code to help you start maybe !

If I have time I would write it myself but so far I didn't so ...

But I would be happy to share my knowledge of how to make a usb driver in python !

---

