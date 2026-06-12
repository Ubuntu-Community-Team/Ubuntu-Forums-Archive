---
title: "Screen resolution changing...Again"
date: 2008-08-17
forum: General Help
---

### Post by Jdm111 on 2008-08-17
I made a thread about a week ago saying that my screen resolution changed to 960x600, I didn't get any help so i had to reinstall.It was fine for a while, Until today. Its changed to 960x600 and it should be 1024x768.
Please, Please help.

---

### Post by overdrank on 2008-08-17
> **Jdm111 said:**
> I made a thread about a week ago saying that my screen resolution changed to 960x600, I didn't get any help so i had to reinstall.It was fine for a while, Until today. Its changed to 960x600 and it should be 1024x768.
Please, Please help.

Hi and if you are using Hardy, you can try and boot into recovery mode which is usually the second choice at the grub and use the xfix option. If this doesn't work then you can try and use the alt, F2 keys and use the command ```
gksu displayconfig-gtk
``` and adjust there.

---

### Post by Jdm111 on 2008-08-17
Neither of them worked.

---

### Post by overdrank on 2008-08-17
> **Jdm111 said:**
> Neither of them worked.

Ok could you post the output of this command ```
cat /etc/X11/xorg.conf
``` and you may use the code tags to make for easier reading and conserve space.

---

### Post by Jdm111 on 2008-08-17
> **overdrank said:**
> Ok could you post the output of this command ```
cat /etc/X11/xorg.conf
``` and you may use the code tags to make for easier reading and conserve space.
Dont bother. wasted time and managed to sort it out. Now my friend hates

 me

---

### Post by overdrank on 2008-08-17
> **Jdm111 said:**
> Dont bother. wasted time and managed to sort it out. Now my friend hates

 me

Ok would you mind posting how you solved it so others may be helped. :)

---

