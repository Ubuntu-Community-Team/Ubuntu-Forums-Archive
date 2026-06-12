---
title: "Ubuntu on Dell Inspiron 6400 - 1680*1050"
date: 2006-05-27
forum: Hardware &amp; Laptops
---

### Post by mohnish82 on 2006-05-27
Hi,

I was amazed to find that special Ubuntu exists for some HP desktop models. Great guys:) 

But, the problem is I didn't knew it before and therefore purchased Dell Inspiron 6400.

Does there exist a special Ubuntu edition for Dell Inspiron?

If not what steps should be taken to get most of the hardware working, esp. screen resolution of 1680*1050 and 3D capabilities?

Thanks in advance.

regards,
Mohnish

---

### Post by brsseb on 2006-05-27
To get the custom resolution, edit the file:

/etc/init.d/915resolution

(or was it /etc/default/915resoulution...?)

In the file, but something like 3c after the "=" for the mode field, X is 1680 and Y is 1050, and the last one is 24 bits. Now save and reboot. Hopefully this should work. 

Yiu might also wanna edit your /etc/X/xorg.conf and add  "1680x1050" as a resolution to the Screen-section. Hope it works

---

### Post by irias on 2006-05-31
[QUOTE=mohnish82]Hi,

I was amazed to find that special Ubuntu exists for some HP desktop models. Great guys:) 

But, the problem is I didn't knew it before and therefore purchased Dell Inspiron 6400.

Does there exist a special Ubuntu edition for Dell Inspiron?

If not what steps should be taken to get most of the hardware working, esp. screen resolution of 1680*1050 and 3D capabilities?

Thanks in advance.

regards,
Mohnish[/QUOTE]
Grettings, I have a DELL INSPIRON 6400, i'm usin Ubuntu 6.06 and all is rigth (only the modem is not tested).

---

### Post by mohnish82 on 2006-06-03
[QUOTE=irias]Grettings, I have a DELL INSPIRON 6400, i'm usin Ubuntu 6.06 and all is rigth (only the modem is not tested).[/QUOTE]

What problems did you face? And, of course, how did you fix them:) 

Regards,
Mohnish
======

---

### Post by nischg on 2006-06-07
I am on a Dell 6400 now with Dapper on it. I've managed to solve almost every issue but two things are holding me from saying bye to Win XP. They are described in this post [http://www.ubuntuforums.org/showthread.php?t=190167]("http://www.ubuntuforums.org/showthread.php?t=190167") 

I thought that we could create a guide or how-to for this laptop and Ubuntu with all our problems and solutions so far so we can help each other out. I do not know if a thread on this great forum would be the best or we could make a wiki or something. If someone else is interested in this please contact me. I do have little time but I am willing to do everything I can to help others with an Inspiron. I can offer 24/7 hosting for anything on this subject.

Thanks

---

