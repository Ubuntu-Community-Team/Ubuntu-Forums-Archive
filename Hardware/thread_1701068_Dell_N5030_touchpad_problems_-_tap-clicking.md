---
title: "Dell N5030 touchpad problems - tap-clicking"
date: 2011-03-06
forum: Hardware
---

### Post by blm14 on 2011-03-06
So I am running ubuntu maverick with liquorix kernel. If I use the ubuntu standard kernel then when I run gpointing-device-settings I see this

[img]http://img835.imageshack.us/img835/6974/45192280.png[/img]

With liquorix kernel I see this:

[img]http://img215.imageshack.us/img215/3029/93831380.gif[/img]

I have no "touchpad" section in preferences-mouse. 

Here is what I want to do. DISABLE &*#&%ing tap-to-click. I love this laptop and I love ubuntu but that tap-click thing is KILLING me. 

Some information:

```

ben@maybeinnovations:/etc/apt$ uname -a
Linux maybeinnovations 2.6.37-2.dmz.2-liquorix-amd64 #1 ZEN SMP PREEMPT Tue Mar 1 19:42:15 CST 2011 x86_64 GNU/Linux
ben@maybeinnovations:/etc/apt$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 ALPS GlidePoint                  	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_0.3M           	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=12	[slave  keyboard (3)]

```

here is the output of lshal:
[http://pastebin.com/7Fcqrr1c](http://pastebin.com/7Fcqrr1c)

I tried creating an xorg.conf to see if that allowed me to add some entries to solve the problem but Xorg -configure only put a generic ps2 mouse entry, BOO!!

contents of xorg.conf:
[http://pastebin.com/t8CkNAAs](http://pastebin.com/t8CkNAAs)

I JUST WANT TAP CLICK GONE. I will do anything, ANYTHING to turn this )(*$^)*$ feature off. Please, ANYONE help. Hacks, workarounds, ANYTHING. I don't care about getting a working driver (although it would be nice) I just want this tap clicking gone.

TIA

---

### Post by blm14 on 2011-03-13
Bump

---

### Post by blm14 on 2011-03-26
Upgraded to 11.04 alpha to see if newer kernel would help. No dice. 

Anyone?

---

### Post by blm14 on 2011-04-18
11.04 too unstable. Went back to 10.10. Still no working touchpad. Anyone!?

---

### Post by mariothomas on 2011-05-09
go to your application pannel and right click 
then click add to panel.

click on custom application launcher.

then click on add.

in the name section put "Turn off Touch Pad"
in the command section copy paste this :

xinput set-int-prop 'PS/2 Generic Mouse' 'Device Enabled' 8 0;

then 

click on custom application launcher.

then click on add.

in the name section put "Turn on Touch Pad"
in the command section copy paste this :

xinput set-int-prop 'PS/2 Generic Mouse' 'Device Enabled' 8 1;


finnally clik on the icons to turn on/off the pad

if u want to dible only the tap and keep the mouse (dunno why would someone do that but..) check out the other properties in xinput to see what can you configure

---

### Post by Chachalaco on 2011-08-09
Thank you very very much!!!!
This worked for me.
I have to use an icon instead of the special (built in) button, but it will really make my typing easier. 
No more cursor jumps because of tap clicking!
Thank you. Thank you.

---

