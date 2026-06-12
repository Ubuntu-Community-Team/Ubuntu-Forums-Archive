---
title: "NUM keys don't react on Hardy"
date: 2008-04-29
forum: Hardware
---

### Post by randomAccess on 2008-04-29
After fresh install of Hardy, I edited gdm's Default file as many times before in order to turn NUM LOCK on. 
However, now only Enter key works, while '+' key selects the word. Other keys don't work! :confused:

I also use keytouch in order to enable my Logitech EX110 keyboard. But in Gutsy it didn't mess up my keyboard.

---

### Post by randomAccess on 2008-05-01
Both, mouse and keyboard, are connected via adapter (2 ps2 into 1 usb port) so this may be the problem. 

Is really none having any idea?

---

### Post by randomAccess on 2008-06-03
just to say that I've solved it by deleting /home conf files in gconf folder

---

### Post by vkennedy85 on 2008-07-28
I've got the same Keyboard, and I can't find any home conf files in the gconf folder.  I only  have a couple of folders inside of the gconf folders, and none of them contain anything resembling the file you mentioned.

If you could help me out I'd appreciate it.

---

### Post by randomAccess on 2008-07-28
You didn't tell me why you want to delete these files!

However, these are my steps. I first created another account, logged into it, started nautilus as root, a deleted everything in the folder /home/my_user_name/.gconf/. In this way I lost all my gnome settings. When I logged back to my account, everything was set to default thus resetting the keyboard as well.

---

