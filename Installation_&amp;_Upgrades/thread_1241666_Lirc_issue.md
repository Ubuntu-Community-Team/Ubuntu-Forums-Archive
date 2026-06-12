---
title: "Lirc issue"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by Tdummy on 2009-08-16
Hi everyone,

I have a lirc issue, where I'm absolute clueless. I'm using Ubuntu 9.04 with Soundgraph device 15c2:0036. Lirc was compiled from the CVS sources. So far, no problem at all, the modules are loaded and I have the devices /dev/lirc0 and /dev/ldc0. With mode2 --raw -d /dev/lirc0 I see the input from teh remote, also irw is running, if I start it without any parameter. 

> 2a9115b700002401 00 Pause iMON-PAD
2b9715b700002401 00 Stop iMON-PAD
2a8115b700002401 00 Play iMON-PAD                      

But if I'm using irw with the device like irw /dev/lirc0 I'm getting the error message 

> connect: Connection refusedI assume that this is also the reason why I cannot get it to work for example with xbmc. 

Maybe someone could help me with that. 

Thanks in advance.

---

### Post by Tdummy on 2009-08-16
Found a hint in the lirc documentation, which solved my problem. I had to define a output device. :lolflag:

---

### Post by pablo79 on 2009-08-18
Hi Tdummy,
  could you explain me what do you make? I'm in your situation.

Thank you,
   Pablo

---

### Post by Tdummy on 2009-08-18
Hello Pablo,

I have right now no access to my pc, but maybe this short description will already help you. Otherwise please let me know.

If you have the device /dev/lirc0, try to start your lirc with the following line:

> lircd --driver=default --device=/dev/lirc0 --output=/dev/lircd --pidfile=/var/run/lircd.pid --connect=localhost:8765 			 		

After this you should have a /dev/lircd device and are now able to start irw with

> irw /dev/lircd

As far as I understood, by default this device is normally located under /var/run/lircd.

If you need further details, as already mentioned, please let me now.

I'M not sure, if this is the perfect way, but it works fine for me.

---

### Post by pablo79 on 2009-08-18
Thank you Tdummy,
    I've tried your suggestion but nothing change form me. I'm able to run irw /dev/lircd also with starting the lircd normally, but in both case, I don't have any result with irw.
When my system starts, it creates immediately lirc0 and lircd so I think that I don't need the instruction you posted me, am I right?

The strange, for me, is that the remote works as a mouse but nothing else.

I don't have any idea on how to proceed ](*,). Do you have some help for me?

Thank you again,
  Pablo

---

### Post by Tdummy on 2009-08-18
Are you sure that you have the correct lirc.conf for your remote?

Did you try to use mode2 to make sure that the input from the remote is working?

After this, maybe try irrecord to create your own config file.

Just try the following and proceed as shown on the display.

> irrecord  -d /dev/lircd example.conf

---

### Post by pablo79 on 2009-08-18
Yes, I've tried the mode2 and it works. If I try irrecord, it works only with /dev/lirc0 and not with /derv/lircd.

I think the files is ok because the codes returned by mode2 are compatible with the ones contained in the lircd.conf

I will try your suggstion to create my own lircd.conf (probably tomorrow, now it's a bit late :))

Thank you for your support,
   Pablo

---

### Post by pablo79 on 2009-08-19
You are right, I need to create a new lircd.conf because my code is different from one in the standard iMON-PAD.
With
```
sudo irrecord -n -d /dev/lirc0 example.conf
```

I've registered all the keys and I include this file in my lircd.conf

When I try irw after a reboot nothing is changed :confused:

-any idea?

Pablo

---

