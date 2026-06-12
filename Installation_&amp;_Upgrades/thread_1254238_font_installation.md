---
title: "font installation"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by saneej on 2009-08-31
How to install fonts???????? (.ttf)

---

### Post by sloggerkhan on 2009-08-31
if it does not exist, make a folder called .fonts in your home directory. Put fonts there.

As an alternative, you can install fonts for all users with sudo permissions by putting them in /usr/share/fonts.

Likewise, you may want to look at a font manager if you have lots of fonts. such as fontmatrix of fonty python.

---

### Post by oboedad55 on 2009-08-31
> **sloggerkhan said:**
> if it does not exist, make a folder called .fonts in your home directory. Put fonts there.

As an alternative, you can install fonts for all users with sudo permissions by putting them in /usr/share/fonts.

Likewise, you may want to look at a font manager if you have lots of fonts. such as fontmatrix of fonty python.

If you're looking for basic .ttf fonts, go to a terminal and type: 
sudo apt-get install msttcorefonts

This will give you courier new, etc. that you usually need for OpenOffice.

---

### Post by saneej on 2009-08-31
I'm not able to paste inside truetype folder. y?

---

### Post by sloggerkhan on 2009-08-31
like I said, if you put them in /usr/share/fonts, you need admin (sudo) permissions.

Likewise, things with a . infront of them are hidden. You can show them with ctrl-h.

---

### Post by sahabcse on 2009-08-31
Login to the root account and try

or run in terminal

#sudo nautilus

---

### Post by ibutho on 2009-08-31
> **saneej said:**
> I'm not able to paste inside truetype folder. y?

Because you need root (admin) permissions. Do Alt-F2 and enter "gksu nautilus" and that will run a file manager with admin privileges and you can then copy and paste stuff with root privileges.

---

### Post by saneej on 2009-08-31
Done. Thanx a lot. But still I'm having problem loading particular site containing the  font I've installed. Is it necessry 2 restart,log off session n cm back.

---

### Post by ibutho on 2009-08-31
> **saneej said:**
> Done. Thanx a lot. But still I'm having problem loading particular site containing the  font I've installed. Is it necessry 2 restart,log off session n cm back.
Try logging out and back in again and see if the new font is recognised.

---

