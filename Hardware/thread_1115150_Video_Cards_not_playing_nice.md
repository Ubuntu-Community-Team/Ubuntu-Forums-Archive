---
title: "Video Cards not playing nice"
date: 2009-04-03
forum: Hardware
---

### Post by jpnub on 2009-04-03
Hello
Thanks for taking a look at this for me. I am a recent convert to linux (well, almost...still dualbooting with windows 7)  and am not very experienced with  a command line and code. I love ubuntu and am happy I have switched but I bassically need a gui to function.
I currently have 3 monitors, and to run these I have two video cards. 1 video card is a  Nvidia 8500  PCI-E. This is what I am currently using to run Ubuntu 8.10, and it works fine with two monitors. All is good.
 

My other card is a  Nvidia 6200.  I  installed ubuntu, did a full update and restarted the machine. I then installed the restricted Nvidia drivers(177) and then when I restart I see the splash but after the orange bar loads on the splash screen a command line prompt asks me to log in.  So I then log in and can not go any farther. 
When I try:

[INDENT]Startx[/INDENT]

I get:

[INDENT]Server error: no screens found[/INDENT]

So basically, my nvidia 6200 does not work. Even with the new drivers. When I unplug the 6200 from it's PCI slot I boot up fine and the 8500 works.
I have used the 6200 and 8500 together with windows 7, and they function properly.
I have also set my default video device to pci-e in my bios, if that helps.(tried it the other way, same thing)


Happy to provide any more information if it will help. Thank you!```

```

---

### Post by norwoods on 2009-04-03
nvidia has an extensive README for each driver that explains multiple card installations.  google nvidia 177.xx  README where xx is your driver version.

---

