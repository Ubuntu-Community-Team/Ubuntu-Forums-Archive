---
title: "Firewire soundcard doesn't work"
date: 2010-07-08
forum: Hardware
---

### Post by soerennoergaard on 2010-07-08
Hi
I recently bought a new external soundcard, an ESI Quatafire 610, which runs through firewire. It is supposed to be fully Linux compatible. 
 On Windows (Vista 32 bit) I can run it just fine after installing the drivers, but when I connect it in Ubuntu (64 bit 10.4) nothing seems to happen.
 From reading some other posts on this subject I understand, that it should work through Jack, but by default not as a soundcard directly, but when I try to run jack set to use the Firewire driver, it crashes and shows the following:

```
21:42:11.609 Patchbay deactivated.
21:42:11.816 Statistics reset.
21:42:11.851 ALSA connection graph change.
21:42:12.087 ALSA connection change.
21:42:27.872 Startup script...
21:42:27.873 artsshell -q terminate
sh: artsshell: not found
21:42:28.276 Startup script terminated with exit status=32512.
21:42:28.276 JACK is starting...
21:42:28.276 /usr/bin/jackd -dfirewire -r44100 -p128 -n3
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
21:42:28.281 JACK was started with PID=2256.
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    3042618
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
libffado 2.0.0 built Mar 31 2010 16:21:44
firewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
no message buffer overruns
21:42:28.459 JACK was stopped successfully.
21:42:28.460 Post-shutdown script...
21:42:28.460 killall jackd
jackd: no process found
21:42:28.868 Post-shutdown script terminated with exit status=256.
21:42:30.458 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

 I had problems when I used jack with my internal soundcard, but those problems were solved by following instructions from the message box. I just don't understand the message this time. Can anyone help me? It seems it doesn't support 64 bit Windows, but should that affect the Linux drivers?

-Søren

---

### Post by cchhrriiss121212 on 2010-07-08
You need a new kernel:
> With the new Firewire stack in Ubuntu Kernel, at the moment, it is not possible to run FFADO sound cards nor use Firewire for DV capture with -generic and -lowlatency kernels. Please see instructions on this page to install -rt kernel on this page, wich has old working stack. Until the new firewire stack works well with FFADO et DV capture, this section needs a complete rewrite.
Taken from this guide:
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)
You should also follow these steps:
[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

---

### Post by soerennoergaard on 2010-07-08
Maybe that's the problem. I'll just try it, it looks as if it would work.. I keep my fingers crossed! Thank you for your reply! :)

---

### Post by soerennoergaard on 2010-07-08
YES! THANK YOU! Now it works! Installed the rt kernel and enabled the raw1934.

---

### Post by mörgæs on 2010-07-08
Fint. Husk at mærke tråden 'solved'.

---

