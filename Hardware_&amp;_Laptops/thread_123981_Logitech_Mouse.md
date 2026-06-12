---
title: "Logitech Mouse"
date: 2006-01-31
forum: Hardware &amp; Laptops
---

### Post by thepocketdrummer on 2006-01-31
I have a Logitech MX700 mouse, but I can't center click and scroll or use the side buttons to go back and forward.

Does anyone know how I can make the mouse do that?

---

### Post by gingermark on 2006-01-31
I found the following here: [http://kerneltrap.org/node/3637](http://kerneltrap.org/node/3637)

"I have the same mouse, and it works ok here, with the following configuration:

xorg.conf:

Section "InputDevice"
Identifier "Logitech MX 700"
Driver "mouse"
Option "Protocol" "ExplorerPS/2"
Option "Device" "/dev/input/mice"
Option "ZAxisMapping" "6 7"
Option "Emulate3Buttons" "no"
EndSection

then i run this cmd on startup:

xmodmap -e "pointer = 1 2 3 6 7 4 5" 

that makes the wheel and the side buttons work nicely."

So I guess the first step would be to edit your xorg.conf file (make a backup first). Not too sure how to run that command on startup though (short of doing it manually every time), but I'm sure someone else can point you to the correct file to edit.

---

### Post by darknightuk on 2006-01-31
sorry 4 jumpin in here but..@gingermark what exactly does your side mouse buttons now do because the best i've been able to get them to do despite following every tutorial n how 2 etc is for them to do left n right in firefox etc?:-k

---

### Post by thepocketdrummer on 2006-02-03
is there a way to make the side buttons go back and forward in firefox (or any browser for that matter?)

---

### Post by darknightuk on 2006-02-03
yep but thats all i've been able to get the bloody things to do! wut have u tried?

---

### Post by tajreed on 2006-02-03
Check out the Wiki on this issue.

---

