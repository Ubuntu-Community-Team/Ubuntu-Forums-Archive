---
title: "Audio Drive Problem"
date: 2008-06-25
forum: Hardware
---

### Post by yaqatari on 2008-06-25
[SIZE="4"][COLOR="Blue"]Hi I am a noob with Ubuntu and linux in general
 have just installed Ubuntu 8.04 , everything is working fine except the sound card , I have a GIGABYTE GA-P35-D3SL and I can't find any compatible drive for it 

please help[/COLOR][/SIZE]

---

### Post by MasterSander on 2008-06-25
That's the name of your mother board, can you tell us what type your sound card is?

---

### Post by yaqatari on 2008-06-25
[SIZE="4"][COLOR="Blue"]The card is : Realtek ALC883 , high definition audio, 2/4/5.1/7.1-chanel , suport for S/PDIF In/Out , suport for CD In
thats every thin written about it in the manual

thank you for you for carring[/COLOR][/SIZE]

---

### Post by yaqatari on 2008-06-25
he card is : Realtek ALC888 , high definition audio, 2/4/5.1/7.1-chanel , suport for S/PDIF In/Out , suport for CD In
thats every thin written about it in the manual

thank you for you for carring

---

### Post by Nepherte on 2008-06-25
Try this: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by yaqatari on 2008-06-26
I tried to follow the steps shown in the link and my system crashed  all I find now when I login is a terminal like black screen like in DOS

---

### Post by Odrodzona-Sarmacja on 2008-06-27
I guess you managed to crash your gdm :D
Boot up with in recover mode (it is in boot up grub's menu) and when you get there to repair menu choose "fix x-server". It should give you back your desktop ;) And then good luck with your sound adventures! :)

---

### Post by yaqatari on 2008-06-27
thank you two for carring 

I couldn't find this "grub's menu" but I gound something similar ot it and chose " try to fix x-server" and it didn't work, is still have only the terminal like screen

---

### Post by yaqatari on 2008-07-02
thank yuo all guys
I have reinstalled ubuntu and this time I chose ALC888 in the volume control and then I installed alsa mixer there I found a bar called "PCM" I rased it and then the sound went on

---

