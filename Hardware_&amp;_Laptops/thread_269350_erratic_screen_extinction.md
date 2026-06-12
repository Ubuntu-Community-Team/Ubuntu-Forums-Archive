---
title: "erratic screen extinction"
date: 2006-10-01
forum: Hardware &amp; Laptops
---

### Post by oduhart on 2006-10-01
I have just installed Ubuntu Dapper on my old laptop PC: a PIII with 320 Mo  RAM and a HD 10 Go . Compared to Windows and another distrib that I would not quote there is not  possible comparison! But a small trick disturbs me: my screen LCD persists in dying out all  every 5 minutes and only a pressure on a keyboard makes it relight , a movement of the mouse does not have any effect. I had a similar experience with my preceding install of Linux (Mandriva 2006) and that had disappeared when I had chosen at the boot time,  the option  “linux-nonfb” that GRUB proposed  me without I. But I don't really understand the reason of this behavior (thus I suspect it is related to the frame buffer). Anyone have an idea of the reason of this periodic extinction which obliges me to keep  a finger on the key ctrl of my PC? and if so is there a solution to cure my Ubuntu? 
Of cours I tested all the energy manager and screen saver options which ddoes nnot make nothing which make me think that the problem is way more complicated.

thanks in advance,

Olivier.

---

### Post by oduhart on 2006-10-01
rien

---

### Post by mpires on 2006-10-01
Is it a toshiba satellite pro 4600? Does it happen on windows either?

---

### Post by oduhart on 2006-10-02
to mpires : almost ... it is a toshiba satellite pro 4300 series (4340 exactly). 
but I did not notice this problem whith Windows.

---

### Post by Propwash on 2006-10-09
I have a Toshiba Satellite 4090XDVD and the same thing happens.  I installed Ubuntu 5.10 and everything worked fine.  After upgrading to 6.06 the screen blanks out every 3 minutes about.  Touching either a key or the trackpoint brings it back.  Using the xset command and turning off blanking (tset s noblank) doesn't fix it.

Update:  There is a post by Hexion in the Desktop Envirnoment forum that might help.  Also check your "Display" option in Power Management in your laptop bios ( for Tosiba laptops: turn off the system then press and hold the Esc key for three seconds after turning it on).  The entry should be "disabled" as Dapper doesn't override the setting as 5.10 or Windows does.

---

### Post by oduhart on 2006-10-09
thanks Propwash,

might be a problem with dapper,only have to hope that it will
be solved with edgy eft thought it is not that so disturbing.
Thanks for your testimony anyway.

Olivier

---

