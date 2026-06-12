---
title: "intel 945gm graphic drivers for Ubuntu Hardy"
date: 2008-09-20
forum: Hardware
---

### Post by burhangondal on 2008-09-20
hey guys i m new to linux...but i really understood ubuntu that how it works and stuff but not that i m a super experienced person in linux so i m better with newbie lol....

i have installed everything and everything working fine with no problem but i dont have any default drivers for things i have in my laptop for example video card drivers, wireless, etc etc.....i m ok with everything but all i want to know is that how do u install intel 945gm video drivers if u want to install by ur self new drivers same with wireless....like if i go to intel website and download whatever they have for linux then how would i install them? thanks :)

intel 945gm dual core toshiba laptop...

---

### Post by burhangondal on 2008-09-28
no one?:confused::(

---

### Post by EnGorDiaz on 2008-09-28
the 945 range of graphic sub controllers have nearly no support at all thats because its nearly to bypass a Directx issue

---

### Post by EnGorDiaz on 2008-09-28
but this shoul work :P


sudo apt-get install xserver-xorg-video-intel

restart your comp uninstall any other graphics rivers by oing 

sudo apt-get autoremove

---

### Post by EnGorDiaz on 2008-09-28
if you screw it up you shoul 


sudo dpkg-reconfigure xserver-xorg-video-intel

---

### Post by eawu40 on 2008-10-21
> **EnGorDiaz said:**
> if you screw it up you shoul 


sudo dpkg-reconfigure xserver-xorg-video-intel


how sure are you dis is going to work,.. now i have windows(right noe)... and  i installed ubuntu many times before but i had to switch back to windows because the game wont run as good as xp.. ( have 945 also..) is it my graphics or the wine?

---

