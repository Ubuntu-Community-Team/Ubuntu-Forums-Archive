---
title: "longer time out and sound for my modem"
date: 2005-08-13
forum: Hardware &amp; Laptops
---

### Post by edemark on 2005-08-13
Hi all 

I am using a hsf linmodem in my hp/compaq nx9010 and it works fine. However i have no sound (i just get used to listen the modem connecting since my first 2400k modem and i miss it). My other problem that i was unable to find how to give longer time out (by default is set up to 60s but sometimes it is just too short for being able to connect) i would really need some 75-80 seconds.

thanks in advance
mark

---

### Post by s_p_a_r_k_y on 2005-08-13
System->Adminstration->Networking
click on your modem, properties. You should be able to change the volume there by default set to off. Not sure about the timeout option

---

### Post by edemark on 2005-08-13
I have tried that but still no sound. I have tried with gnome-ppp but no luck as well as i have tried changing the atdt command but still no luck. The funny thing is that when i installed the modem it had sound but since the first reboot no more sound

thanks anyway 
mark

---

### Post by s_p_a_r_k_y on 2005-08-13
maybe they are trying to get direct control over the sound cardinstead of using ESD. whenever I have sound problems I kill esd (actually I don't run esd EVER anymore). ```
 pkill -9 esd 
``` and try then?

---

### Post by aveline on 2005-08-13
[QUOTE=s_p_a_r_k_y]maybe they are trying to get direct control over the sound cardinstead of using ESD. whenever I have sound problems I kill esd (actually I don't run esd EVER anymore). ```
 pkill -9 esd 
``` and try then?[/QUOTE]
 If you're using WVDial theres a way in its config to set the timeout #'s.  I recommend wvdial very highly b/c of its simplicity & although most people new to linux hate hand editing files *I'm not new to linux & hate it anyway :)*, even I could do it with WVdial, regardless of hte fact i'd never tried to setup a modem on linux before in my life.  That should give you some testament to its ease of use. :P

aveline

---

### Post by edemark on 2005-08-13
thanks to you all.
first to sparky i do not use esd either. Bec i like gaming and i sometimes need to run vvin in linux (qemu is really good) so some month ago i just get rid of esd and get to alsa. Second to aveline i am now going to check out wvdial config file. though i now use gnome ppp it uses wvdial but if was necesary i do not mind using hand editing though i hate it also after some five years of linux it should not be a problem. Thanks to both of you and with hopes that wvdial config editing will work. (to be honest this part is more important that the sound as this second is just an ear candy though i love it)

thanks again and will give a feed back on this time out after logging out

pd still no idea on the sound issue

mark

---

### Post by edemark on 2005-08-14
So still on the same issue 

I just could not figure out how to change time out. I made a search in mc for wvdial and i checked all files shown in the list. I also tried options in /etc/ppp/ but no luck. I really had hopes in trying options as (if i am correct) in slackware that was the place to change time out.

so if you have any ideas pls 

thanks 

pd still no idea on the sound

---

