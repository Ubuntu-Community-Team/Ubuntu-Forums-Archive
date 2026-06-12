---
title: "How to get my Focusrite Saffire firewire soundcard to work in 8.04"
date: 2008-05-02
forum: Hardware
---

### Post by jonspencerbx on 2008-05-02
Hello,

I'm havin a hard time getting my focusrite saffire to do anything at all. As far as I can see, the card isn't recognized at all. I have ardour, freebob and jack installed. Any ideas? Or pointers where to start?

M.

---

### Post by brigux on 2008-05-02
result of: 
```
jackd -d freebob
```
?

---

### Post by jonspencerbx on 2008-05-02
Hi Brigx,

Looks like my firewire chip is not working?

```
mike@mike-ubuntu:~$ jackd -d freebob
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
Freebob using Firewire port 0, node -1
Ieee1394Service::initialize: Could not get 1394 handle: Permission denied
Is ieee1394 and raw1394 driver loaded?
Fatal (devicemanager.cpp)[68] initialize: Could not initialize Ieee1349Service object
Fatal (freebob.cpp)[69] freebob_new_handle: Could not initialize device manager
LibFreeBoB ERR: cannot create libfreebob handle
FreeBoB ERR: FREEBOB: Error creating virtual device
cannot load driver module freebob
Segmentation fault
```

This is what lspci -v has to say about the firewire chip:
```
0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 0121
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at f3300000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [dc] Power Management version 2
```

Thanks for looking into this,

Mike

---

### Post by jonspencerbx on 2008-05-02
Ok, I get the unit to switch on. instead of jackd -d freebob I used ```
sudo jackd -d freebob
```
Now I need to get sound from it. Nothing realy happens other than the unit turning on. Nothinh has changed in the mixer panel or anything. And there is no mention of the card when using lspci -v (don know if firewire devices should be listed there).

Regards,

M.

Edit: here is the output of sudo jackd -d freebob
```
mike@mike-ubuntu:~$ sudo jackd -d freebob
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
Freebob using Firewire port 0, node -1
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.
```

---

### Post by brigux on 2008-05-02
mm.. You might like that:

[http://ubuntuforums.org/archive/index.php/t-425316.html](http://ubuntuforums.org/archive/index.php/t-425316.html)

---

### Post by jonspencerbx on 2008-05-02
Ok, I did this:
```
You will have to change the udev rules. 
The file to modify is usually : /etc/udev/permissions.rules. 
look for the line : 
KERNEL=="raw1394",                              GROUP="audio" 
and change GROUP="disk" to "audio" 

reload udev : 
# /etc/init.d/udev restart 
reload raw1394 device : 
# rmmod raw1394 && modprobe raw1394
```
And I don't have to sudo anymore when using ```
jackd -d freebob
```

I also installed JACK Control, and I am unable to fire up the saffire with it. So, with the jackd -d freebob command I am able to fire up the saffire, but that's about it. I can't find the device anywhere in the mixer panels or in the JACK Control settings. Any ideas?

M.

---

### Post by jonspencerbx on 2008-05-02
Ok, I got Jack Control to fire up my saffire. But still no audio.

Here is a screenshot of my Jack Control settings:

[IMG]http://quickimg.com/uploads/ce483774c848b1541ded993ae754d319.png[/IMG]

---

