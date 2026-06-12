---
title: "Slower/Faster mouse sensitivity"
date: 2010-12-23
forum: Hardware
---

### Post by runeh76 on 2010-12-23
My mouse (Logitech USB Laser Mouse) was way too fast, so i did this:


Open Terminal and put this command to find ur mouse-name:

xinput list


Make new file to Home folder, name it to "file.sh". (User/file.sh)
Right-click file.sh and choose properties.
Select permissions and put cross to box (Allow file execution like a program)

Open ur "file.sh" with text-editor.
Put this in the "file.sh":

xinput --set-prop "UR MOUSE-NAME" "Device Accel Constant Deceleration" 2

(U can play with number 2 to make more or less sensitivity)

Make it executable after boot:
Go to startup programs (System/Settings/Startup programs).
Click Create new and browse ur file.sh
Name it what ever u want.

Thats it. 
And now if u want fine-tuning ur mouse. Do it from (System/Settings/Mouse)

Mods can move this thread another location, if its in the wrong place.

---

