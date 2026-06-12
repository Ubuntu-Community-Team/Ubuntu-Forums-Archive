---
title: "raspberry pi Compute Module 4 with Raspberry pi 7 inch display not able to configure."
date: 2021-10-27
forum: Hardware
---

### Post by dharanipathi on 2021-10-27
[COLOR=#555555][FONT=Roboto]Hello,[/FONT][/COLOR]
[COLOR=#555555][FONT=Roboto]I have a CM4 and the IO board, I am trying to connect the official raspberry 7" display with touchscreen , using the RPI-Display adapter. I have followed these instructions ( [/FONT][/COLOR][https://www.raspberrypi.com/documentati ... splay-only]("https://www.raspberrypi.com/documentation/computers/compute-module.html#quickstart-guide-display-only")[COLOR=#555555][FONT=Roboto] ).[/FONT][/COLOR]

[COLOR=#555555][FONT=Roboto]i am using ubuntu os in my raspberry pi CM4.[/FONT][/COLOR]

[COLOR=#555555][FONT=Roboto]but the display not working,[/FONT][/COLOR]
[COLOR=#555555][FONT=Roboto]any suggestions[/FONT][/COLOR]

---

### Post by trub68 on 2022-02-20
Open the config.txt file on the SD and comment out dtoverlay=vc4-kms-v3d that has worked for me with at PI 4B and the 7" display. 



> **dharanipathi said:**
> [COLOR=#555555][FONT=Roboto]Hello,[/FONT][/COLOR]
[COLOR=#555555][FONT=Roboto]I have a CM4 and the IO board, I am trying to connect the official raspberry 7" display with touchscreen , using the RPI-Display adapter. I have followed these instructions ( [/FONT][/COLOR][https://www.raspberrypi.com/documentati ... splay-only]("https://www.raspberrypi.com/documentation/computers/compute-module.html#quickstart-guide-display-only")[COLOR=#555555][FONT=Roboto] ).[/FONT][/COLOR]

[COLOR=#555555][FONT=Roboto]i am using ubuntu os in my raspberry pi CM4.[/FONT][/COLOR]

[COLOR=#555555][FONT=Roboto]but the display not working,[/FONT][/COLOR]
[COLOR=#555555][FONT=Roboto]any suggestions[/FONT][/COLOR]

---

### Post by sirda on 2022-03-24
Commenting out dtoverlay=vc4-kms-v3d in config.txt does not work for me.

Ubuntu stopped working on the 7" touchscreen with version 21.04 and in 21.10 it is not working either.

It is sad.

---

