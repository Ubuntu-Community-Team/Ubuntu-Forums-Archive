---
title: "Twinhan Vision Plus 102G DVB-S Problem"
date: 2006-06-02
forum: Hardware &amp; Laptops
---

### Post by rubrboots on 2006-06-02
Hello I have a Twinhan Vision Plus 102G DVB-S, when the card is installed the computer will hang on startup. As soon as I take the card out everything works well. I have read an old post how it was fixed in Hoary and it allowed me to boot but I get errors. Those instructions are below

```
Still the way to avoid the audio conflict is getting dvb-bt8xx to load BEFORE snd_bt8xx by default somehow it happens the other way round.

1)
sudo gedit /etc/hotplug/blacklist
Add these lines:
snd_bt87x
bttv
dvb_bt8xx
bt878

2)
sudo gedit /etc/modules
add these lines:
bttv
dvb-bt8xx
dst
snd_bt87x
```

Now I could not find /etc/hotplug/blacklist in dapper so I added the line to /etc/modprobe.d/blacklist , but this gives me errors in the terminal, something about being ignored due to improper syntax. 

Am I adding the code to the wrong file? Or has the syntax changed in dapper? Or is there another way I can get this card working and bootable?

---

### Post by hackbox on 2006-06-03
make it look like that:

1)
sudo gedit /etc/modprobe.d/blacklist
Add these lines:
blacklist snd_bt87x
blacklist bttv
blacklist dvb_bt8xx
blacklist bt878

2)
sudo gedit /etc/modules
add these lines:
bttv
dvb-bt8xx
dst
snd_bt87x

---

### Post by rubrboots on 2006-06-04
Thanks for the info hackbox. Unfortunately the fix did not work. If anyone has any ideas of how to get a twinhan 102g card working in ubuntu I would love to hear them.

thanks

---

### Post by rubrboots on 2006-06-05
Solved. Thanks for all the suggestions guys. I seems that I had 2 different problems here. When installing linux with a twinhan card you must install the os without the twinhan card installed. Then add the line bttv i2c_hw=1 card=0x71 which I think properly identifies the card. You may also have second problem, an incompatible motherboard. Originally I was using a cheap soyo board, the line bttv i2c_hw=1 card=0x71 would allow me to boot, but the computer was very unstable. Eventually I installed ubuntu dappper on a different computer (MSI mobo), added the above line, inserted the twinhan card, and everything worked perfectly:D 

If you are using ubuntu dapper add the below to your /etc/modprobe.d/options file

```

options dvb_core dvb_shutdown_timeout=0
options bttv i2c_hw=1 card=0x71

```

And add the below to your /etc/modules file

```

bt878
dst
dvb-bt8xx

```

I am sure this will work for other distros as well but the file that needs to be edited may be different.

---

### Post by captevo on 2008-01-09
I got this error:

[   33.555852] dvb-bt8xx: A frontend driver was not found for device 109e/0878 subsystem 1822/0001

any idea?
Thanks in advance.

---

