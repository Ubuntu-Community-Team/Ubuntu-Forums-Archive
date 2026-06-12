---
title: "grub 2 doesnt let me boot ubuntu"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by jarrah-95 on 2009-08-05
when i boot my laptop it has the grub 1 menu and at the top it says that i am using debain (not ubuntu like i am) and when i try to load grub 2 or "debian" (witch is ubuntu)it says error 11: unrecognised device string 
im using windows on the same laptop so at least i can boot into that is there anything i can do to get ubuntu back
thanks

---

### Post by jarrah-95 on 2009-08-06
i managed to fix it by booting from a live cd and using chroot to get into my normal ubuntu root and then coppied the backup of grub menu.lst to the real file

---

### Post by stlsaint on 2009-08-06
ha...by u fixing your own error i learned something!!! thanks!!!

---

### Post by jarrah-95 on 2009-08-07
thats good to hear but it wasent my error it was an error in grub2s installer

---

### Post by Habboblob on 2009-10-16
> **jarrah-95 said:**
> thats good to hear but it wasent my error it was an error in grub2s installer

Looks like you didn't know what you were doing.
If you installed grub 2 as an upgrade of the grub that comes with ubuntu, yes you will receive an error.

You should research before you do something, as I did, and Grub 2 worked perfectly for me.
All I had to do was install it, and when it came up with this error:
[img]http://images.howtoforge.com/images/grub2_ubuntu_9.04/3.png[/img]
press the a key to continue.

You should then come to this:
[img]http://images.howtoforge.com/images/grub2_ubuntu_9.04/4.png[/img]
select chainload and press e.

Select root and then press e
[img]http://images.howtoforge.com/images/grub2_ubuntu_9.04/5.png[/img]

Now re-name the string of root:
[img]http://images.howtoforge.com/images/grub2_ubuntu_9.04/6.png[/img]

too uuid and press enter:
[img]http://images.howtoforge.com/images/grub2_ubuntu_9.04/7.png[/img]

Select the uuid entry and press b to boot:
[img]http://images.howtoforge.com/images/grub2_ubuntu_9.04/8.png[/img]

Now grub should boot safely without any errors, straight to this screen:
[img]http://images.howtoforge.com/images/grub2_ubuntu_9.04/9.png[/img]

Do not blame a program for being bad when it is purely your fault. Set it up correctly for it to work, but don't blame it for not working if it has worked for tons of others.

---

