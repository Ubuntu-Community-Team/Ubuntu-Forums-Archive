---
title: "Edirol FA-66 firewire with ubuntu 13.10 not working"
date: 2013-11-21
forum: Hardware
---

### Post by elibabila on 2013-11-21
Hi,
I'm trying to get my edirol fa-66 working with no luck. I've install libffado & jackd, tried some settings but nothing seems to work...I just want to be able to playback.

Here's the output I'm receiving, thanks for any help

eb@MARS:~$ jackd -R -P70 -dfirewire -r48000 -p128 -n2 -D
jackdmp 1.9.10
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2013 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 70
libffado 2.1.9999- built Feb  1 2013 04:49:43
firewire ERR: FFADO: Error creating virtual device
Cannot attach audio driver
JackServer::Open failed with -1
no message buffer overruns
Failed to open server

---

