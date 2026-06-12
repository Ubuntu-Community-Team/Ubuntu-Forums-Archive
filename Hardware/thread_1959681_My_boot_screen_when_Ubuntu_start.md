---
title: "My boot screen when Ubuntu start"
date: 2012-04-16
forum: Hardware
---

### Post by sensenku on 2012-04-16
Hi, When I installed Ubuntu 11.10 from beginning till this time my Ubuntu start logo screen is black and white. I attached a file. How can I fix this?

---

### Post by kc1di on 2012-04-16
> **sensenku said:**
> Hi, When I installed Ubuntu 11.10 from beginning till this time my Ubuntu start logo screen is black and white. I attached a file. How can I fix this?

you can try this. 

open your favorite text editor I use gedit
```
sudo gedit 
```
open /etc/default/grub 

look for the following line of code:
```
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
```

Remove the # symbol in front of 
```
GRUB_GFXMODE=640X480 
```

Then change the ```
 640x480 to say 1024x768
```
So it should now look like this ```
GRUB_GFXMODE=1024x768
```
Save the file

in a terminal type:
```
sudo update-grub
```
Reboot see if that works for you. you can change the resolution to fit your screen closely but can only use those the grub recognizes.  for a list of accepted grub resolutions by typing 
```
vbeinfo
``` at the grub command.
Good Luck

---

