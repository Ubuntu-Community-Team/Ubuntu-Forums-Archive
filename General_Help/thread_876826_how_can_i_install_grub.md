---
title: "how can i install grub?"
date: 2008-08-01
forum: General Help
---

### Post by fatalus on 2008-08-01
i was trying to install ubuntu.everything was ok but then i got an error like grub-install (hd0) couldnt executed..so grub couldnt installed..i have windows vista also on my laptop..so i have to install grub but i dont know how can i do this..i looked at some topics about grub but i cant find the right solution for my problem..i hope u fix this :(

---

### Post by Archmage on 2008-08-01
I think the Virus-Protection for the bootblock has been turned on in your BIOS. You need to turn this off so that you can install grub into your harddrive.

---

### Post by fatalus on 2008-08-01
but i installed ubuntu before and there was no problem..i havent turned on virus-protection for bootlock..can it change itself?i think no :)

---

### Post by forger on 2008-08-01
so.. you installed vista and then you tried installing ubuntu again and now grub can't be installed?

---

### Post by fatalus on 2008-08-01
i had already vista but i tried pardus and then decided to turn back ubuntu..and while the installation grub couldnt installed..

---

### Post by fatalus on 2008-08-01
please somebody help me..is nobody know how to install grub?? :S

---

### Post by pastalavista on 2008-08-01
[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

---

### Post by faical117 on 2008-08-01
boot with the livecd and in terminal do :

1) [COLOR="RoyalBlue"]sudo grub[/COLOR]

2) [COLOR="RoyalBlue"]grub> find /boot/grub/stage1[/COLOR]  
(this will give you the partition to use in next step for example [COLOR="Red"](hd0,1)[/COLOR]  )

3) grub> [COLOR="RoyalBlue"]root[/COLOR] [COLOR="Red"](hd0,1)[/COLOR]

4) grub> [COLOR="RoyalBlue"]setup (hd0)[/COLOR]

5) grub> quit[COLOR="RoyalBlue"][/COLOR]

:)

---

### Post by fatalus on 2008-08-01
i tried to reinstall ubuntu with another CD but i got same error again..what should i do :S

---

### Post by fatalus on 2008-08-01
> **faical117 said:**
> boot with the livecd and in terminal do :

1) [COLOR="RoyalBlue"]sudo grub[/COLOR]

2) [COLOR="RoyalBlue"]grub> find /boot/grub/stage1[/COLOR]  
(this will give you the partition to use in next step for example [COLOR="Red"](hd0,1)[/COLOR]  )

3) grub> [COLOR="RoyalBlue"]root[/COLOR] [COLOR="Red"](hd0,1)[/COLOR]

4) grub> [COLOR="RoyalBlue"]setup (hd0)[/COLOR]

5) grub> quit[COLOR="RoyalBlue"][/COLOR]

:)


at the second step i got an error " Error 15: File not found ".i guess this grub installation procedure is for systems which grub has already been installed but it has a problem like windows installation after the linux..so grub cant appear..mine is a bit different because i dont have grub so it cant find the stage1 :/

---

### Post by faical117 on 2008-08-01
try to use EasyBCD with vista

---

### Post by fatalus on 2008-08-01
i have deleted all linux distros thanks for helps..:/

---

