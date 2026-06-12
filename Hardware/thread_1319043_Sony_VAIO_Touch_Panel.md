---
title: "Sony VAIO Touch Panel"
date: 2009-11-08
forum: Hardware
---

### Post by ashsalama on 2009-11-08
PLZ guys I need help on this
my laptop is Sony VAIO CS26G, I Need two things if its possible
1- driver for the touch panel including "CAPTURE" bottom which opens cam program.
2- Fn key works only with volume control, I want to know how to enable the rest of controls like brightness screen zoom
Thanks advanced

---

### Post by ashsalama on 2009-11-09
I'm sorry because I'm asking again but it is important to me to know if there is a solution

---

### Post by levis lover on 2009-11-09
**see if this works..**

I found a working solution (should have searched better the last time!): it is on ubuntuforums. In short:

1) install the package "nvclock": sudo apt-get install nvclock
2) create following scripts:

/etc/acpi/events/sony-brightness-up
/etc/acpi/events/sony-brightness-down
/etc/acpi/events/sony-brightness-dim
/etc/acpi/events/sony-brightness-ac
/etc/acpi/sonybright.sh

3) make them all executable: sudo chmod +x nameofscript
4) fill the scripts with following content:

**sony-brightness-up:**

# /etc/acpi/events/sony-brightness-up
event=sony/hotkey SNC 00000001 00000011
action=/etc/acpi/sonybright.sh up

**sony-brightness-down:**

# /etc/acpi/events/sony-brightness-down
event=sony/hotkey SNC 00000001 00000010
action=/etc/acpi/sonybright.sh down

**sony-brightness-dim**

# /etc/acpi/events/sony-brightness-dim
event=ac_adapter ADP1 00000081 00000000
action=/etc/acpi/sonybright.sh dim

**/etc/acpi/events/sony-brightness-ac**

# /etc/acpi/events/sony-brightness-ac
event=ac_adapter ADP1 00000081 00000001
action=/etc/acpi/sonybright.sh bright

**/etc/acpi/sonybright.sh**

#!/bin/bash
if [ "x$1" = "xdown" ]; then
# xbacklight -steps 10 -dec 10 2>/tmp/sonybright.log
nvclock -S -15
elif [ "x$1" = "xup" ]; then
# xbacklight -steps 10 -inc 10 2>/tmp/sonybright.log
nvclock -S +15
elif [ "x$1" = "xdim" ]; then
# xbacklight -steps 10 -inc 10 2>/tmp/sonybright.log
nvclock -S 15
elif [ "x$1" = "xbright" ]; then
# xbacklight -steps 10 -inc 10 2>/tmp/sonybright.log
nvclock -S 100
else
echo >&2 Unknown argument $1
fi


5) restart acpid: sudo /etc/init.d/acpid restart 

**source : mad_spooky**

---

### Post by ashsalama on 2009-11-10
Thanks levis lover, its working very well.
may I ask you another question?
what about the other function? I mean for example my Scroll lock work only by Fn key so I need to do the same for it.
I know I'm asking to many questions but if you give me a 'how to' or explanation for the commands and arguments used in the brightness commands, maybe I can create the rest of Fn works
also please if there is any chance to get touch panel works

---

### Post by levis lover on 2009-11-11
man i asked the same question on another forum and MAD_SPOOKY relied this..
when i saw this thread i searched the forum and copy pasted it here.. thats it.. i am also a noob..

---

### Post by levis lover on 2009-11-11
also is your webcam working?

---

### Post by ashsalama on 2009-11-12
> **levis lover said:**
> also is your webcam working?

thanks levis lover you already helped me very well I will do more search about touch panel and if I get good news I will let you know.

about my webcam its working with cheese program without any additional configuration.

):P

---

