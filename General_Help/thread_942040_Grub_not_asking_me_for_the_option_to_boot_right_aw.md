---
title: "Grub not asking me for the option to boot right away"
date: 2008-10-08
forum: General Help
---

### Post by Gondee on 2008-10-08
This is most likely a simple fix, but it seemed i could not get the right key words, so here it is. 

I have windows and Ubuntu dual booted. But recently Grub just does the 3 second thing then goes strait to Windows. How do i make it so that i don't have to press Esc to boot to Ubuntu, and it just gives me the options.

---

### Post by unutbu on 2008-10-08
```
gksu gedit /boot/grub/menu.lst

```
Change
```

hiddenmenu
```

to```


#hiddenmenu
```

---

### Post by Gondee on 2008-10-08
Thanks abunch man =)

---

### Post by drs305 on 2008-10-08
Gondee,

You can also edit menu.lst with StartUp-Manager, a gui tool that will let you set up menu display times, default OS, colors, number of kernels to display, etc. And you don't have to edit the menu.lst.

Install StartUp-Manager with:
```
sudo apt-get startupmanager
```

Run: System, Administration, StartUp-Manager

Use the link to a detailed tutorial in my signature line for more info.

---

