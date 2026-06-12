---
title: "Laptop Touchpad has been accidently disabled"
date: 2011-02-27
forum: Hardware
---

### Post by LePeache on 2011-02-27
Hello,

I have ubuntu installed on my HP Pavillion, and everything has been working great since I installed. Having said that, my son (toddler) has done something while my back was turned. I found  him sitting next to the laptop and ever since, the touchpad doesn't work. The cursor appears but neither left or right buttons, the scroll and actual touchpad works. If I plug in a USB mouse, the mouse I can control the cursor. At the moment I have a Bamboo tablet plugged in as my wife decided she need her USB mouse back ....

I believe my son has found a function key of sorts but no matter how much I try, I cannot find it. I have googled with no luck and hope someone here may be able to point me in the right direction.

Cheers
Leon.

---

### Post by LePeache on 2011-03-02
fixed it, found anwser via another thread

"Create a file called
/etc/modprobe.d/touchpad.conf

You can do this by typing
sudo gedit /etc/modprobe.d/touchpad.conf
in your terminal (Applications --> Accessories --> Terminal). It will ask for your password

when the file opens put in it
options psmouse proto=imps
Save the file and restart"

Cheers

---

