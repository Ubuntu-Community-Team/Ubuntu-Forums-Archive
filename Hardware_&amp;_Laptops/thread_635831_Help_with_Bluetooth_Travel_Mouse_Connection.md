---
title: "Help with Bluetooth Travel Mouse Connection"
date: 2007-12-09
forum: Hardware &amp; Laptops
---

### Post by Richard.F on 2007-12-09
Hi, I recently moved to Ubuntu from Windows for the obvious reasons... :)

I was wanting to connect my Logitech Bluetooth Travel Mouse to my Bluetooth-enabled laptop. After a clean installation of Ubuntu, I right-clicked the Bluetooth icon in the top-right corner of the desktop and pressed "Browse Device...". After a few second my mouse appeared and so did my phone (which I don't want to connect). I tried to connect to the mouse but when I did this appeared: "'obex://[00:07:61:4b:2b:fe]' is not a valid location. Please check the spelling and try again.". Yes, that address there is my Bluetooth Address for the mouse.

Now, I'm not very smart with the whole Linux commands but I do realise you have to type most configurations into a terminal? Am I doing something wrong here? Any help on this issue would be greatly appreciated!

Thanks,

Richard F

Edit: The laptop's Bluetooth was still on whilst trying to connect to the mouse and the mouse's discoverable mode was activated whilst trying to connect too. Oh and I'm using Ubuntu 7.10 Gusty Gibbon.

---

### Post by aum11 on 2007-12-12
I had a very similar problem and solved it by the following:

right click on the bluetooth icon
preferences
services
input service
add

choose the mouse device after it is found by the "add"( you may need to hold the pairing button at this time)

Good luck!

---

