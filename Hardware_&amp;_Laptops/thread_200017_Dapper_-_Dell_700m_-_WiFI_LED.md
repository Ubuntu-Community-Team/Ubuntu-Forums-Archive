---
title: "Dapper - Dell 700m - WiFI LED"
date: 2006-06-19
forum: Hardware &amp; Laptops
---

### Post by jweila01 on 2006-06-19
Dapper on my Dell 700m is almost perfect except for the WiFi LED on the panel just below the display. Has anyone gotten the LED to function?

---

### Post by jml on 2006-06-19
Since the LED function on many laptops now is controlled by a software call.  Its not uncommon for the LED to remain dark.  The wireless connection should be ok, however.  On some laptops, (my hp nx6110 as an example) the LED only flashes briefly when data is either being recieved or transmitted,

Joe

---

### Post by jweila01 on 2006-06-19
Thanks JML.

You're right - the wireless works fine - I'd just like to find a way to get the LED to light. Then I could say Dapper is 100%.

---

### Post by hashstat on 2006-06-20
I don't know what wifi card your laptop uses, but the Intel Pro Wireless 2200BG has a special file you can write to to activate the led: */sys/bus/pci/drivers/ipw2200/0000:03:03.0/led*.  Write a 1 to activate the led and a 0 to deactivate.  More info is available in the readme: [http://ipw2200.sourceforge.net/README.ipw2200](http://ipw2200.sourceforge.net/README.ipw2200).

---

### Post by jweila01 on 2006-06-22
Hashstat:

Thanks for the link - I'll investigate when I have time.

JNW

---

### Post by evilhomer on 2006-07-09
works great!  thanks

just a note in case anyone doesn't see, the numbers in the path were different for me

---

### Post by reacocard on 2006-07-09
it won't let me write to the file, even using root gedit. is there something special i need to do to get access to the file?

EDIT: nevermind, abiword worked

ANOTHER EDIT: is there something similar for my mute button? it's also supposed to light when in use. i have an hp pavilion dv4000

---

### Post by evilhomer on 2006-07-21
hmm, i noticed vi gave me some strange messages when editing, but i ignored them.  turns out the setting won't stick on reboot.  also, the file doesn't have the write attribute, yet it seems to get overwritten each time (including when I did it)

any way to make this stay on, even after a reboot?

---

### Post by mrvw0169 on 2006-07-22
Cool... try adding:```
echo 1 > /sys/bus/pci/drivers/ipw2200/0000\:02\:01.0/led
``` to your /etc/rc.local before the exit 0 line... replace the path with the appropriate one, like 0000\:03\:03 (safer to just type and use tab completion in the shell and copy/paste)... or editing /etc/modprobe.conf or /etc/modprobe.d/options to have: options ipw2200 led=1...

Don't know if this will work, since I can't reboot right now (middle of projects)... The LED status light is sucky though still since it's delayed toggle, sometimes it doesn't even toggle correctly

---

### Post by bigken on 2006-07-22
wey hey work a treat for me on my inspiron 9200 Pro/Wireless 2915ABG Mini PCI ;)

---

### Post by setdosa on 2006-08-24
Thanks for wonderful tip. I have the LED glowing now on my Dell 700m. I made the modprobe.d/options change as you suggested and it starts up with the LED on now. 

Is there a way to link the key press to this option. What I mean is if I press say the fn key and the Wifi key, the LED should toggle. 

Appreciate the help,
Arun

---

### Post by setdosa on 2006-08-24
> **mrvw0169 said:**
> Cool... try adding:```
echo 1 > /sys/bus/pci/drivers/ipw2200/0000\:02\:01.0/led
``` to your /etc/rc.local before the exit 0 line... replace the path with the appropriate one, like 0000\:03\:03 (safer to just type and use tab completion in the shell and copy/paste)... or editing /etc/modprobe.conf or /etc/modprobe.d/options to have: options ipw2200 led=1...

Don't know if this will work, since I can't reboot right now (middle of projects)... The LED status light is sucky though still since it's delayed toggle, sometimes it doesn't even toggle correctly
Thanks for wonderful tip. I have the LED glowing now on my Dell 700m. I made the modprobe.d/options change as you suggested and it starts up with the LED on now. 

Is there a way to link the key press to this option. What I mean is if I press say the fn key and the Wifi key, the LED should toggle. 

Appreciate the help,
Arun

---

### Post by ianmillington on 2006-08-29
> **hashstat said:**
> I don't know what wifi card your laptop uses, but the Intel Pro Wireless 2200BG has a special file you can write to to activate the led: */sys/bus/pci/drivers/ipw2200/0000:03:03.0/led*.  Write a 1 to activate the led and a 0 to deactivate.  More info is available in the readme: [http://ipw2200.sourceforge.net/README.ipw2200](http://ipw2200.sourceforge.net/README.ipw2200).
Hi

Dell Inspiron 630m.

On doing the fix referred to, the wireless LED does indeed light up. However:-

On toggling Fn+F2 and switching off the wireless, the LED remains lit and

On reboot the system has reset itself!

Any clues on making it stick?

---

### Post by CELI-Nux on 2006-08-29
Confirms that this also works with an HP/Compaq nc8000. My "led" file path was: /sys/bus/pci/drivers/ipw2200/0000:02:04.0 and quite easyly found.

Personal preferences: This option should be "1" (on) by default.

Thanks for this post :-)

---

### Post by CELI-Nux on 2006-09-01
Just noticed that this modification only works once (not permanently).  So everytime I reboot, I have to reset this value to "1".  I could use a script to do just that but isn't there another way of achieving this goal?

Regards to all.

---

### Post by mrvw0169 on 2006-09-11
Add 
> ```
echo 1 > /sys/bus/pci/drivers/ipw2200/0000\:02\:01.0/led
```to your /etc/rc.local before the exit 0 line... replace the path with the appropriate one, like 0000\:03\:03 (safer to just type and use tab completion in the shell and copy/paste)...

That will do it every startup... I haven't figured out anything else yet and it *does* turn off when you hit Fn+F2 (but only on the first try or some random shot)... Only way is to fix the code in the driver probably...

Also, I found that modifying /etc/modprobe.d/options doesn't work for me (but I'm running Edgy Eft -- maybe upstart is loading the module first before checking the options?)...

---

### Post by bigken on 2006-09-11
Hi I added this line to rc.local and it works ;)
echo 1 > /sys/bus/pci/drivers/ipw2200/0000:02:03.0/led
Dell inspiron 9200

also worked on edgy eft knot2

---

### Post by Dinerty on 2006-10-05
Absolute brilliant guide, thanks all

---

### Post by basketcase on 2006-10-13
Works on Dell Inspiron 6000 with ipw2200 wifi card.  

The only thing left that didn't work with 6.06 on this notebook!  

Thanks!

---

### Post by arthursc on 2006-11-08
Can someone help with this as I am a new linux user and my wifi LED doesn't work either. 

I need to real hand holding here please.

Regards
Colin](*,)

---

### Post by basketcase on 2006-11-08
> **arthursc said:**
> Can someone help with this as I am a new linux user and my wifi LED doesn't work either. 

I need to real hand holding here please.

Regards
Colin](*,)
What specifically are you having problems with?

---

### Post by arthursc on 2006-11-08
I have rc.local open but not sure where to add the line required

---

