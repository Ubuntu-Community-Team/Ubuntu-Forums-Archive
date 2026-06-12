---
title: "Keyboard repeeeeeeeeeeeeeeats keys"
date: 2005-10-04
forum: Hardware &amp; Laptops
---

### Post by alfotis on 2005-10-04
Hi all,

I am facing a very annoying problem with ubuntu 5.04 for i386. My keyboard repeeeeeeeeeeeeeeeeeeats keys when i type, so while i'm writing, i suddenly see a whole line filled with the letter i just pressed and keeps growing until I press the backspace key. Also, sometimes some keys like Ctrl and Alt stick too. 

I am pretty sure this is a software problem because this didn't existed in 5.04 amd64 distro or any other distro i have tried.

My system is an Acer 1522WLMi, AMD64 3000+, 512 RAM, 60GB HDD, CD/DVD-RW, 802.11g and b compatible. Ubuntu 5.04 i386 with all the security fixes, kernel 2.6.5-386 (ubuntu update).

During system startup I load ndiswrapper, irda and nvidia modules. 

Can anyone help me?

---

### Post by JimmyJazz on 2005-10-04
I have had similar problems in the past, however it seems they cleared up on their own

---

### Post by brentoboy on 2005-10-04
I had this same problem you are describing a few months ago running mepis.

I fixed it back then by disableing releated keys altogether - which is inconvenient, but better then thiiiiiiiiiiiiiiiiiiis  :)

try system > prefs> keyboard 
and disable repeat keys (or just change the threshhold settings).

---

### Post by Kitty on 2005-10-04
I had the same problem.

I solved it by adding this line 
psmouse rate=40
in /etc/modules (sudo gedit /etc/modules)

The problem came from synaptics touchpad driver.

---

### Post by JimmyJazz on 2005-10-04
wow thanks Kitty

---

### Post by alfotis on 2005-10-07
Unfortunately that didn't work.

Besides that, my mouse pointer goes craaaaaaaazy!!! (oops...)

---

### Post by tseliot on 2005-10-08
[QUOTE=alfotis]Unfortunately that didn't work.

Besides that, my mouse pointer goes craaaaaaaazy!!! (oops...)[/QUOTE]
Your computer might be affected by the Double Clock Speed BUG.

Please, check my guide (I had the same problem). If the method for Ubuntu 32bit doesn't work for you I suggest you to try to install Ubuntu 64bit and try the 2nd method (for 64bit only).

[http://ubuntuforums.org/showthread.php?t=53094]("http://ubuntuforums.org/showthread.php?t=53094")

---

