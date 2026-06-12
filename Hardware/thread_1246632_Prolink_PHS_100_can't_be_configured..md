---
title: "Prolink PHS 100 can't be configured."
date: 2009-08-21
forum: Hardware
---

### Post by mastermind008 on 2009-08-21
[COLOR=Magenta][I]In this blog

**[http://nmlaxaman.blogspot.com/2009/04/prolink-phs100-hsdpa-workout-for-debian.html](http://nmlaxaman.blogspot.com/2009/04/prolink-phs100-hsdpa-workout-for-debian.html)**

Lakshman has done it with 'Intrepid lbex', but not with Jauty Jakalope.[/I][/COLOR]

my processor is intel dual core - 64 bit processor.
OS Ubuntu 9.04 Jaunty Jakalope(64 bit).

When I plugged in my Prolink PHS100 modem, all the mounted drives that are show on desktop were dissapeared and I couldn't open any of the Hard Drive Or Flash Drive folder.
when I executed
       $ lsusb
It shows the modem Id just with some characters(No any Vendor etc) 
something like,
       00:f000  - 
for bus 2

I followed all the related threads and installed many downloaded libraries to configure "wvdial"

then I had to use "mknod" and add /dev/ttyUSB0, /dev/ttyUSB1 and /dev/ttyUSB2
Then for "ls -al /dev/ttyUSB*" 
it gave a series as....     s<0>, s<1>,s<2>,s<3> USB0,USB1,USB2

then displayed that there's no any modem found.

when I run "sudo wvdial'
....................v1.6
---->Cannot open /dev/ttyUSB2 no such divice found 
---->Cannot open /dev/ttyUSB2 no such divice found
---->Cannot open /dev/ttyUSB2 no such divice found

then the modem indicator was turned to green but I couldn't make the internet connection, and had to reinstall windows to my Laptop.:confused:

I am a Ubuntu fan, and that's why I bought this modem as they had provided a manual in PDF format.but it doesn't work.

in brief

                                                                                                                     I tried to connect Prolink PHS 100 modem.
Then desktop icons are dissapeared.
I can't access any folder (places).


Then I uninstalled Ubuntu 9.04.


 [B][COLOR=Red]I tried again with Live CD boot.
the same thing happened and...


[COLOR=SeaGreen] Error is given as:[/COLOR]
"nautilus crashed with SIGSEGV in start_thread()"[/COLOR][/B]  

 how can I get solved this and get connected to internet via 'Prolink PHS100" modem?



Please help me!!!

---

### Post by mastermind008 on 2009-09-07
I could configured my PHS 100 modem nicely. I will post all the steps I followed to get it connected.
:popcorn:

---

### Post by suomaf on 2009-10-15
Hey Mastermind,

Any chance to post the steps that you got it connected? I seem to have to get the modem "initialised" in windows first to get to the magenta light .. unplug it and then plug it into ubuntu and wvdial.. then it will work.. if I had disconnected using the windows software.. it will not connect.

Any ideas?

Suo

---

### Post by suomaf on 2009-10-19
bump

---

