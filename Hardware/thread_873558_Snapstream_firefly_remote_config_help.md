---
title: "Snapstream firefly remote config help"
date: 2008-07-29
forum: Hardware
---

### Post by hotrod6657 on 2008-07-29
I'm running ubuntu 8.04 and i decided to play around with my snapstream firefly remote and see if i could get it working.

Long story short, i can't... haha

Here's what i've done.  I tried from the terminal entering:  sudo apt-get install lirc

That installed the program and launched a set up ... i think (there might have been another step there, i can't remember)

I selected my snapstream remote and said custom for the transmitter part when it asked, because i couldn't find anything that matched mine on the list.  Nothing really happened and i didn't get any response from the remote when i typed iwr into the terminal.

So, i did some more looking and found a GUI for the same function.  I installed the gnome-lirc-properties and tried that GUI.  

Now, from there it detects my remote if i ask it to for the first part, and i say that i'm using the provided remote.

The final part, the test doesn't do anything.  No matter what keys i press i don't get a response.  I'm not sure if i'm missing something simple or what, but does anyone know where i should go from there?

The fact that it detects my remote makes me hopeful that it can work, but i don't know how.

hotrod

---

### Post by hotrod6657 on 2008-08-06
bump?  It would be a shame to not get this working.  It's the only thing left on my system that isn't doing what I want it to.  I'm proud to say that I've gone more than a week now without booting in the windows.  It would just be nice to get that remote working.

Is there another program i might try?  The fact that it has options for firefly makes me thing i have a fighting chance, i just don't know what to do.

hotrod

---

### Post by jacksbackw on 2009-01-05
Hey there, did you ever get this to work?  I have a FireFly remote that I want to use in Ubuntu in conjunction with XBMC.

Thanks,
Jacksback

---

### Post by thejipster on 2009-01-22
I kinda got it working.  The only thing is that sometimes it takes two presses to get it recognized and when that happens IRW shows that I pressed the button twice.  
For example, if I press a button and hold it, it doesn't do anything.  I release the button and press it again, it starts getting recognized by irw.  This behavior is intermittent.  

I am not sure how to fix.

Here is my hardware.conf
root@ubuntu:/etc/lirc# more hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Snapstream X10 RF"
REMOTE_MODULES="lirc_dev lirc_atiusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="atiusb/lircd.conf.atiusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
root@ubuntu:/etc/lirc#




I got the lircd.conf from 
[http://lircconfig.commandir.com/configure/?add=selectremote](http://lircconfig.commandir.com/configure/?add=selectremote)

Just select Firefly.



Let me know if you can get it working.   This double press thing is quite annoying right now.

---

### Post by cross157 on 2009-02-13
I'm bumping this because I have the same issue. Snapstream Firefly remote setup in Ubuntu 8.10. It's working BUT I have to press each button twice for it to work.

Using irw, each button press is registered but in MythTV the action doesn't happen unless I press the same button twice.

Here's my hardware.conf:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Snapstream X10 RF"
REMOTE_MODULES="lirc_atiusb"
REMOTE_DRIVER="default"
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD=true

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

# Remote settings required by gnome-lirc-properties
REMOTE_MODEL="R1000"
REMOTE_VENDOR="Snapstream Firefly"

# Receiver settings required by gnome-lirc-properties
RECEIVER_MODEL="Firefly PC Remote"
RECEIVER_VENDOR="SnapStream Media"
```

Here's my lircd.conf:
```


begin remote

  name            Snapstream_Firefly
  bits            40
  eps             30
  aeps            100
  one             0 	0
  zero            0 	0
  gap             219964

  begin codes
       MAXI            0x00000014012C0000
       CLOSE           0x0000001457820000
       1               0x00000014E20D0000
       2               0x00000014638E0000
       3               0x00000014E40F0000
       4               0x0000001465900000
       5               0x00000014E6110000
       6               0x0000001467920000
       7               0x00000014E8130000
       8               0x0000001469940000
       9               0x00000014EA150000
       0               0x000000146C970000
       BACK            0x00000014EB160000
       ENT             0x000000146D980000
       VOL+            0x00000014DE090000
       VOL-            0x00000014DD080000
       MUTE            0x00000014DF0A0000
       FIREFLY         0x00000014D5000000
       CH+             0x00000014E00B0000
       CH-             0x00000014E10C0000
       INFO            0x00000014032E0000
       OPTION          0x00000014042F0000
       UP              0x00000014EF1A0000
       LEFT            0x00000014F21D0000
       DOWN            0x00000014F7220000
       RIGHT           0x00000014F41F0000
       OK              0x00000014F31E0000
       MENU            0x00000014F11C0000
       EXIT            0x00000014F5200000
       REC             0x000000147CA70000
       PLAY            0x000000147AA50000
       STOP            0x000000147DA80000
       REW             0x0000001479A40000
       FWD             0x000000147BA60000
       PREV            0x0000001480AB0000
       PAUSE           0x000000147EA90000
       NEXT            0x000000147FAA0000
       MUSIC           0x000000145B860000
       PHOTOS          0x000000145A850000
       DVD             0x0000001459840000
       TV              0x0000001458830000
       VIDEO           0x000000145C870000
       HELP            0x0000001456810000
       MOUSE           0x0000001482AD0000
       A               0x000000146E990000
       B               0x00000014709B0000
       C               0x0000001476A10000
       D               0x0000001478A30000
                 
  end codes

end remote
```

---

### Post by thejipster on 2009-02-14
I got it working.  I also have 8.10, so this should work for you.

root@ubuntu:/etc/lirc# more hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Snapstream X10 RF"
REMOTE_MODULES="lirc_atiusb"
REMOTE_DRIVER="default"
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD=true

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

# Remote settings required by gnome-lirc-properties
REMOTE_MODEL="R1000"
REMOTE_VENDOR="Snapstream Firefly"

# Receiver settings required by gnome-lirc-properties
RECEIVER_MODEL="Firefly PC Remote"
RECEIVER_VENDOR="SnapStream Media"




-------------

root@ubuntu:/etc/lirc# more lircd.conf.atiusb
begin remote

name Snapstream_Firefly
bits 40
eps 30
aeps 100

one 0 0
zero 0 0
gap 219964
toggle_bit 0


begin codes
MAXI 0x0000001481AC0000
MAXI 0x00000014012C0000
CLOSE 0x00000014D7020000
CLOSE 0x0000001457820000
1 0x00000014628D0000
1 0x00000014E20D0000
2 0x00000014E30E0000
2 0x00000014638E0000
3 0x00000014648F0000
3 0x00000014E40F0000
4 0x00000014E5100000
4 0x0000001465900000
5 0x0000001466910000
5 0x00000014E6110000
6 0x00000014E7120000
6 0x0000001467920000
7 0x0000001468930000
7 0x00000014E8130000
8 0x00000014E9140000
8 0x0000001469940000
9 0x000000146A950000
9 0x00000014EA150000
0 0x00000014EC170000
0 0x000000146C970000
BACK 0x000000146B960000
BACK 0x00000014EB160000
ENT 0x00000014ED180000
ENT 0x000000146D980000
VOL+ 0x000000145E890000
VOL+ 0x00000014DE090000
VOL- 0x000000145D880000
VOL- 0x00000014DD080000
MUTE 0x000000145F8A0000
MUTE 0x00000014DF0A0000
FIREFLY 0x0000001455800000
FIREFLY 0x00000014D5000000
CH+ 0x00000014608B0000
CH+ 0x00000014E00B0000
CH- 0x00000014618C0000
CH- 0x00000014E10C0000
INFO 0x0000001483AE0000
INFO 0x00000014032E0000
OPTION 0x0000001484AF0000
OPTION 0x00000014042F0000
UP 0x000000146F9A0000
UP 0x00000014EF1A0000
LEFT 0x00000014729D0000
LEFT 0x00000014F21D0000
DOWN 0x0000001477A20000
DOWN 0x00000014F7220000
RIGHT 0x00000014749F0000
RIGHT 0x00000014F41F0000
OK 0x00000014739E0000
OK 0x00000014F31E0000
MENU 0x00000014719C0000
MENU 0x00000014F11C0000
EXIT 0x0000001475A00000
EXIT 0x00000014F5200000
REC 0x00000014FC270000
REC 0x000000147CA70000
PLAY 0x00000014FA250000
PLAY 0x000000147AA50000
STOP 0x00000014FD280000
STOP 0x000000147DA80000
REW 0x00000014F9240000
REW 0x0000001479A40000
FWD 0x00000014FB260000
FWD 0x000000147BA60000
PREV 0x00000014002B0000
PREV 0x0000001480AB0000
PAUSE 0x00000014FE290000
PAUSE 0x000000147EA90000
NEXT 0x00000014FF2A0000
NEXT 0x000000147FAA0000
MUSIC 0x00000014DB060000
MUSIC 0x000000145B860000
PHOTOS 0x00000014DA050000
PHOTOS 0x000000145A850000
DVD 0x00000014D9040000
DVD 0x0000001459840000
TV 0x00000014D8030000
TV 0x0000001458830000
VIDEO 0x00000014DC070000
VIDEO 0x000000145C870000
HELP 0x00000014D6010000
HELP 0x0000001456810000
MOUSE 0x00000014022D0000
MOUSE 0x0000001482AD0000
A 0x00000014EE190000
A 0x000000146E990000
B 0x00000014F01B0000
B 0x00000014709B0000
C 0x00000014F6210000
C 0x0000001476A10000
D 0x00000014F8230000
D 0x0000001478A30000

end codes

end remote
root@ubuntu:/etc/lirc#

---

