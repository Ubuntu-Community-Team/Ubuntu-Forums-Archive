---
title: "Interceptty and virtual com ports"
date: 2008-01-02
forum: Hardware &amp; Laptops
---

### Post by sanger440 on 2008-01-02
I have had some success running interceptty over my wireless network using linux on my laptops.  In my application, I run one laptop as the server with a car fuel injection computer hooked up to the com port 1(ttyS0). The other laptop is the client and it uses interceptty to connect over the wireless lan (TCIP) to the server laptop and remotely monitors the fuel injection computer on com 1.  Works very well.  The application I run on the client laptop is called megatunix.  Megatunix is configured to connect to a virtual-serial port on the client laptop and uses interceptty to actually connect to the physical com port 1 on the server laptop.  Here the scripts I run to set up interceptty:

**Server:**
#!/bin/sh 

PORT=3333 
SRV_IP=192.168.0.2 
PHYSICAL_PORT=/dev/ttyS0 
BAUD=9600 

interceptty -q  -s 'ispeed ${BAUD} ospeed ${BAUD}' \ 
${PHYSICAL_PORT} \ 
@${SRV_IP}:${PORT}

**Client:**
#!/bin/sh 

SRV_IP=192.168.0.2 
PORT=3333 
LOCAL_DEV=/tmp/virtual-serial 

interceptty -q @${SRV_IP}:${PORT} ${LOCAL_DEV}


So megatunix (Client PC) is configured to start up on the port /tmp/virtual-serial which is then sent by interceptty to the server IP which in turn uses com1 to communicate to the fuel injection computer (megasuirt) on the servers com1. Using this setup I can remotely monitor and tune the megasquirt fuel injection computer using a wireless lan.  Very cool.

However, I want to run a couple of other applications this way.  Megatune is windows application I am running on wine and can only be configured to run com1, com2, etc.  I want megatune on the client laptop to connect through interceptty as described above.  Problem is I cannot set megatune to use /tmp/virtual-server (or something similiar).

Question:  How can I use sybolic links or another method to trick my windows applications into logging on to a virtual-serial port which interceppty will forward to the server laptop?

I am running older P2 laptops with one serial/com port.  I have tried various symoblic links but to no avail.  However, I am not a very savvy linux user so my symbolic links may not have been done correctly.

Sanger.

---

### Post by dcolpitts on 2008-02-09
I'm in the same boat as you and have a similar application that also will not see non standard serial ports (ie /tmp/virtual-server) - did you ever find a solution to this?

---

