---
title: "Invert Touchpad 2-finger scrolling on asus synaptics touchpad 10.10"
date: 2011-01-10
forum: Hardware
---

### Post by AdmiralNotorious on 2011-01-10
Hello all.

the issue i am having is that i have been using my brother's macbook and got used to his inverted scrolling. its just better in my opinion.

Is there any way to invert the scrolling on the touch-pad (fingers go down, page goes up) in ubuntu on my asus u50a in Xorg.conf or something? or is there some other config file i should alter? is it even possible?

PS. Is simulated inertial scrolling possible at all? loved that about the macbook too.

---

### Post by pi/roman on 2011-01-11
Get the name or number of your device with "xinput list". Then test with "xinput test #device" where #device is the name or number of your device. Look what number it is reporting upon scroll.  If it is 4 and 5 then use xinput set-button-map #device 1 2 3 5 4. To make it permanent add an xorg option: Option ZAxisMapping "5 4".

---

### Post by AdmiralNotorious on 2011-01-11
thanx!!!!!!!!!!!

worked like a charm. and a response within 2 hours of posting. THIS is why i love ubuntu, because of great people like u guys

---

### Post by AdmiralNotorious on 2011-01-11
didnt feel like screwing with xorg so i made the command a startup application

---

### Post by felipemartim on 2011-07-28
Really cool! Thanks.

---

### Post by M1ck3y on 2012-02-02
Thanks so much! This is just what I was looking for. I too feel way more comfortable with the inverted controls.

---

### Post by 9954colinr on 2012-02-22
Could someone explain in n00b language where I should put the xorg option mentioned by pi/roman.  Executing the xinput command worked great but it would be equally great if it happened automatically.

---

### Post by alkemyst on 2012-06-20
Edit: I was proposing this solution:
> Hi,
having a command executed at startup (like "xinput set-button-map etc etc...") is easy. You start gnome-session-properties (aka "Startup Applications" from the menu), then you click "Add", you put a reasonable name in the "Name" field (like "Natural scrolling") and your command in the "Command" field (in my case: "xinput set-button-map 14 1 2 3 5 4").
Save
Close
But it does not work! 

Sorry :D

---

### Post by it_self on 2013-01-10
Need to do the same. Thanks for the post!

---

