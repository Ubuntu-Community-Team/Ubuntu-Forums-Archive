---
title: "Updated Xubuntu and now NO touchpad use"
date: 2014-03-11
forum: Hardware
---

### Post by skyblaze2 on 2014-03-11
I have  Medion netbook which was working perfectly fine until I updated earlier today and now I cannot use the touchpad (Synaptic)...I also cannot seem to get into the terminal yet the keyboard seems to be working ok. I am currently using Puppy linux through a flash drive and I am having NO problems using the touchpad. Xubuntu boots to a login screen yet the mouse is frozen...I can type and use TAB and SHIFT and it does take me to the appropriate desktop but I cannot do much...

I am certain this is just a config issue

I tried searching for xorg.conf file but its nowhere to be found  - Can the config file from Puppy be copied across to the appropiate place?

Any ideas on this? Sorry its lacking info I will do my best to provide it

---

### Post by mörgæs on 2014-03-11
Hi, welcome to the fora.
xorg.conf is not there by default, and adding one does not affect the touchpad.

---

### Post by skyblaze2 on 2014-03-12
thanks regarding the xorg.conf file - any idea how to rectify this as I cannot seem to access any thing from the xfce menu and alt f4 just brings up the dialog box to restart or shutdown

---

### Post by skyblaze2 on 2014-03-12
OK I have resolved this

I was just pressing various key combinations and Alt f2 brought up a Run command type of dialog. I entered xterm to get to a console/terminal. As Thunar was not working well I wanted to run MC...I did not have that installed so the system suggested using apt-get...I tried that and then it came up with some warning about packages and suggested a DPKG command to use. I did as it suggested...After re-booting there was NO problem with the touchpad and the system working as before

---

### Post by mörgæs on 2014-03-12
Good, please mark the thread 'solved'.

---

