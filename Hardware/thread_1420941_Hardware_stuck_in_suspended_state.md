---
title: "Hardware stuck in suspended state?"
date: 2010-03-03
forum: Hardware
---

### Post by galdren on 2010-03-03
Hey guys, so I kindda screwed up my ubuntu install which was finally nearing a "perfection" stage. Hope you guys can help me :(

How it happened:
i had windows running on my second workspace with virtualbox. It had to reboot so I was switching back to my primary workspace using the compiz desktop cube.

Virtualbox resetting the VM with me rotating my desktop cube was too much and the display got stuck in the cube. I could see a shiny rendering of my desktops but wasn't able to click or do anything.

So I closed X with ctrl + alt + f3 and shutdown the system with the power button. But apparantly ubuntu was in the middle of something when the power went off. Because now I'm having trouble at boot.

The situation now:
when I boot up I get some errors about 
-the machine not being able to connect to some samba shares and mount them (error code 101 from cifs)
-something about the usb drive being suspended (error code 71)


So I'm guessing the OS was trying to suspend the hardware and something must have gotten corrupted.

Do you have any idea what kind of files I should look for and how to fix them? Please help me out guys...feeling kindda sad that ubuntu fails because of some rediculous graphical bug


runnig 9.10-19 x64 on an AMD laptop: sony vaio cw 1s1e. 

intel core 2 duo 2,16 ghz
nvidia 230m gpu

---

### Post by galdren on 2010-03-03
well managed to get back into a working linux: apparently the 9.10-14 kernel isn't broken.

but the 9.10-19 is still bugged. the errors of cifs have disappeared since the log in to 14 but it's still crashing on boot because of the USB. Any help would be appreciated but there's no emergency anymore :)

---

