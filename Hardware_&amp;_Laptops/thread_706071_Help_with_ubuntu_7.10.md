---
title: "Help with ubuntu 7.10"
date: 2008-02-24
forum: Hardware &amp; Laptops
---

### Post by gnrfan228 on 2008-02-24
Alright, so I just installed ubuntu 7.10 on my laptop (HP ze4500 intel edition)  it booted from the CD just fine and installed just fine. But when I went to restart the laptop (yes I removed the install cd first) it says starting up and then the screen goes black. I tried going into the esc options and booting from recovery mode and it goes through a whole lot of text and at the end it says "root@daniel-laptop~#" and then leaves space for me to type a command. Help please? :confused:

---

### Post by cdtech on 2008-02-24
at the command line type:
```
sudo dpkg-reconfigure xserver-xorg
```
This will configure X for your hardware.

---

### Post by Yellow Pasque on 2008-02-24
Perhaps it's having difficulty with the splash screen. Try going in to the boot options and using the 'nosplash' boot argument.

Also, do you know what type of video chip you have? Run this if unsure:
```
lspci | grep VGA
```

---

### Post by gnrfan228 on 2008-02-24
Alright, I'm pretty sure it's the splash thing I'm having trouble with. My laptop's res is 1024x768

Where do I type in the nosplash argument thing? (first time linux user, been a windows n00b my whole life)

---

### Post by cdtech on 2008-02-24
> **gnrfan228 said:**
> Alright, I'm pretty sure it's the splash thing I'm having trouble with. My laptop's res is 1024x768

Where do I type in the nosplash argument thing? (first time linux user, been a windows n00b my whole life)

You have to go into the menu.lst and change "splash" to "nosplash.":
```
sudo pico /boot/grub/menu.lst
```
Did you try:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by gnrfan228 on 2008-02-24
grr I've tried everything you guys have suggested and I still get the ~10 minute boot time.

---

### Post by konungursvia on 2008-02-24
On such an old laptop, a long boot time may be unavoidable. You could try Debian, which is faster on lean old machines.

---

### Post by Yellow Pasque on 2008-02-24
Boot into recovery mode. When you get to the terminal root prompt (#), enter:
vim /boot/grub/menu.lst
Press 'i' to put vim into insert mode. Now it's just like a normal text editor (Notepad). Add nosplash to the list after the root=  line for whatever kernls you want to use.mmuivki=whilthe timoorpgihjyTSDS

---

### Post by metalf8801 on 2008-02-24
Xubuntu or Fluxbuntu would be faster

---

### Post by cdtech on 2008-02-25
> **konungursvia said:**
> On such an old laptop, a long boot time may be unavoidable. You could try Debian, which is faster on lean old machines.

True.....

---

