---
title: "Delete partition"
date: 2008-07-19
forum: General Help
---

### Post by 500sd on 2008-07-19
Alright so a while ago i had windows xp and ubuntu as a dual boot. Than I updated my xp to vista, and ever since then I wanted to delete the linux partition. But the problem is, i don't know how to :D
So anybody care to educate me?

---

### Post by mikewhatever on 2008-07-19
You can use Gparted Live CD.

---

### Post by Helios1276 on 2008-07-19
google Parted Magic and download the .iso and burn it to a cd, it comes with a nice gui too so it's easy to use. It'll be a handy tool to keep for the future too.That will let you manage/resize or delete partitions.

---

### Post by 500sd on 2008-07-19
Ok so all i need to do is just simple delete it? nothing will happen to my other patition?

---

### Post by Helios1276 on 2008-07-19
Not unless you delete the wrong partition ;)

---

### Post by 500sd on 2008-07-19
ok thanks i deleted it
but i still have these wierd flashes of messages but it only takes off like 1 second of my booting. i think it says something about grub?

---

### Post by OscarPapa on 2008-07-19
You need to re-install the XP bootloader most likely. It is on the XP cd, I think it is called "restorembr" or something to that effect. Shame you removed Linux though.

---

### Post by 500sd on 2008-07-19
The xp bootloader? not the vista? 

and how would i do this?

---

### Post by OscarPapa on 2008-07-19
Sorry, thought you said you had XP :oops:

I am not sure how it is done in Vista, but I would not suspect the process being too difficult, if anything google or microsoft.com would probably explain how to remove the grub boot loader and restore the one provided by Microsoft.

---

### Post by 500sd on 2008-07-19
well i did have xp but i upgraded to vista as i said in my original post

---

### Post by Helios1276 on 2008-07-19
What messages are you getting? You can work with Grub from a live cd if needs be .

---

### Post by 500sd on 2008-07-19
its ok i fixed it
i downloaded this program called easybcd and it fixed the mbr. 
everything is perfect now :) thanks guys

---

