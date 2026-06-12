---
title: "Probel with the keyboard : The &quot;e&quot; button does not work"
date: 2010-01-21
forum: Hardware
---

### Post by naspar on 2010-01-21
hello all,

i have a laptop Lenovo SL500 with ubuntu karmic installed.

i dont know why, but suddenly my keyboard does not work anymmore. If i open the terminal and try to push the "e" button , the system does not write the "e" but just copy what i have copied in the clipboard previously.

does someone knows why my laptop has a weird behavior when i open a terminal and try to press the "e" letter ?

Is there any way to restore the default gnome setting ? i tried with dpkg-reconfigure but it doesn have any positive effetcs.

Thanks a lot

N

---

### Post by pi/roman on 2010-01-21
If you copy and paste this in a terminal:
showkey -a

and the press the e key you should get 101 145 65 or if you have caps on 69 105 45 for the decimal octal and hex ascii codes and try a b c and d just to make sure they should be in order.

---

### Post by naspar on 2010-01-22
hi and thanks for answering.

very strange .. pushing "e" does not appears any hex or decimal code. Instead it works proper with the rest of the buttons.
So seems the button "e" is not connected to the keyboard one i boot the laptop, but if i capy some content in the clipboard .. the button "e" then contains this content working as "paste" button .. is it strange ? :)


karmic@ubuntu:~$ showkey -a

Press any keys - Ctrl-D will terminate this program

a 	 97 0141 0x61
b 	 98 0142 0x62
c 	 99 0143 0x63
d 	100 0144 0x64

---

### Post by naspar on 2010-01-22
for now i temporary fixed opening the terminal option :

"Edit -> Keyboard Shotcuts" and weirdly in the "edit" section i found the "e" values in the "Paste" section .. dont know actually how it was changed

---

