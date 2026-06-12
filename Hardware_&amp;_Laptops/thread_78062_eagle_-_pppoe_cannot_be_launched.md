---
title: "eagle - pppoe cannot be launched"
date: 2005-10-17
forum: Hardware &amp; Laptops
---

### Post by martimgf on 2005-10-17
hi,

i am a new linux user and i am using ubuntu linux.

i have a adsl usb model (arescom - nds1060usb) and the driver that it uses is eagle ([www.eagle-usb.org)](www.eagle-usb.org)).

in the ubuntu i can install it in a automatic way, but when i try to use it i have this message "pppoe cannot be launched. exiting...".

what can i do? i am a new linux user, and i don't know what to do.

thank everybody and sorry about the english.

bye.

---

### Post by huygens on 2006-03-25
[QUOTE=martimgf]hi,
in the ubuntu i can install it in a automatic way, but when i try to use it i have this message "pppoe cannot be launched. exiting...".
[/QUOTE]

Hello,

I have the same problem using Kubuntu 5.10 (I know ;)  , I am also using Ubuntu Dapper on another computer though!)
My ADSL modem is a Sagem F@st 800 USB and I have been trying the eagle-usb driver of Kubuntu and also the one supplied by Sagem on their web site. However, they both look for the PPPoE executable (filename: pppoe) which does not exist.
I did not find any package containing this pppoe executable. Could anyone help?

Thanks a lot.

Huygens

PS: This is mad that I need to go on my Windows OS just to access Internet ](*,)

---

### Post by freedom on 2006-05-26
first update sources if you didn't do recently
then type
```
sudo aptitude install pppoe
```
after that you sould have pppoe executable

---

