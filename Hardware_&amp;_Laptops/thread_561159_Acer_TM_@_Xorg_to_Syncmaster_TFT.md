---
title: "Acer TM @ Xorg to Syncmaster TFT?"
date: 2007-09-27
forum: Hardware &amp; Laptops
---

### Post by in-dust-rial on 2007-09-27
Hi all,
i guess this is a commun problem for analog outputs from laptops.
i found some people haveing the same problem.
no solution, yet?

short description:
SyncMaster 225bw ( TFT from SAMSUNG) flickers. i.e. horizontal lines move up and down and change brightness.
so i can see the whole screen, but it seems like in behind there are moving lines up or down.

important to know:
on my windows it used to run without these problems, after installing suitable software.
( i don't use windows anymore, so i can not look up any settings)

outside the X-session ( for example on tty2 ) i can not see the flicker. Since on black and white the flicker can not be detected so well, maybe this is not a hint at all.



setup:
machine is a laptop: Acer TM 292 lmi ( analog output to the TFT ); readon mobility 9700; default sceen has a resolution different from the tft's. 
useing ubuntu: $ uname -a
Linux MYLAPTOP 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
( i also have some other kernels, but i guess its easiest to fix problem on generic)
in the Xorg.conf it is:

Section "Monitor"
        Identifier      "SyncMaster 225BW"
        Option          "DPMS"
        DisplaySize     474 296
        HorizSync       30.0 - 81.0
        VertRefresh     56.0 - 75.0
        Modeline        "1680x1050"     146.2 1680 1784 1960 2240 1050 1053 1059 1089
        EndSection

like i got it from the xorg.log
as discribed in this [  [http://www.wahlau.org/samsung_225bw_with_xorg_on_ubuntu_linux](http://www.wahlau.org/samsung_225bw_with_xorg_on_ubuntu_linux)  ]

I din't try to chance HorizSync  or VertRefresh, because i dont know how dangerous it is for my TFT.


what can i do?
what can i try?
i just want to have a stable "screen". without the feeling of the TFT exploding every minute.

IF i can give any helpful information or do specifications, please tell me so.

i am looking forward to your help.

thank you all a lot!

---

### Post by in-dust-rial on 2007-09-27
now i have a solution:


in case your screen flickers flicking is blurry blur sight whatever ( i tried to list keywords for search)

try to get your screen stable energie support.
when i was removing ALL other devices from the 10-slot-plug that supplies every maschine in my room with energie:

my TFT screen was the only thing getting energy out of the wall.

SUDDENTLY everything went fine.

display is stable, as long it gets enough energy or stable energy - i dont know


thank you again

---

