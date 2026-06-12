---
title: "Mousepad stopped working after update/upgrade Maverick"
date: 2011-01-15
forum: Hardware
---

### Post by sevenenemy on 2011-01-15
i did a sudo apt-get update and upgrade and my Synaptics mousepad ceased to work on the desktop. it works during login but dies when i login.

---

### Post by Brando753 on 2011-01-16
Hi there, I had this same issue on my laptop. I find it pops up every now and then try this in the terminal.

gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true

Let me know if this works or not. 

P.S. if you are unable to go to Application -> Accessories -> terminal Then hit Ctrl + Alt + F1 Log in and type in the command then hit Ctrl + Alt + f7 to go back :D

Best of luck to you,

Brando753

---

### Post by sevenenemy on 2011-01-16
that fixed it thanks Brando753

---

### Post by Brando753 on 2011-01-16
No problem Sevenenemy, If you could however mark this post as solved it would be a great help to others. 

Best Regards,

Brando753

---

### Post by sevenenemy on 2011-01-20
in case you are a noobuntu and you are using a laptop with a "function" key try also checking your F-keys for a graphic that looks like a touchpad. for my acer it is F7, Function Key+(your F Key with the touchpad graphic) should also do the trick.

---

### Post by Gagandeep_1985 on 2011-01-22
hay brando753

i'v recently got a sony vaio. i'v not installed ubuntu but i tried it form cd. n the mouse pad is not working. m afraid to installed it. do i install it n thn try to fix it..??

please suggest me.....
thanks
gagandeep_1985

---

### Post by sevenenemy on 2011-01-22
this thread is marked as solved so im not sure you are going to find any help here, please try a new thread.

---

