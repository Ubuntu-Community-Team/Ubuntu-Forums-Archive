---
title: "Remote controll PCTV Hybrid Pro PCI"
date: 2007-08-21
forum: Hardware &amp; Laptops
---

### Post by mulimans on 2007-08-21
I have problem with my TV-card 'PCTV Hybrid Pro PCI'.
Everything works fine, except the remote control.

I use Ubuntu 7.04.

I installed the linux-headers:

```

sudo apt-get install linux-headers-2.6.20-15
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
Reading state information... Klaar
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  linux-headers-2.6.20-15
0 pakketten opgewaardeerd, 1 nieuwe pakketten geïnstalleerd, 0 verwijderen en 0 niet opgewaardeerd.
Er moeten 0B/8110kB aan archieven opgehaald worden.
Na het uitpakken zal er 58,3MB extra schijfruimte gebruikt worden.
Selecteren van voorheen niet geselecteerd pakket linux-headers-2.6.20-15.
(Database inlezen ... 163180 bestanden en mappen geïnstalleerd.)
Uitpakken van linux-headers-2.6.20-15 (uit .../linux-headers-2.6.20-15_2.6.20-15.27_i386.deb) ...
Instellen van linux-headers-2.6.20-15 (2.6.20-15.27) ...

```


From: [http://www.lirc.org](http://www.lirc.org) 
i donwloaded  lirc-0.8.2.tar.gz
untared it
run './setup.sh'.
In 'Driver Configuration': I selected 'Pinnacle Systems PCTV (pro) reciever' in 'Other serial port devices' and the com-port '/dev//dev/ttyS0'.
Save configuration & run configure 

make
make install 

(no errors)

I installed lirc:

```

sudo apt-get install lirc
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
Reading state information... Klaar
Voorgestelde pakketten:
  lirc-modules-source lirc-x
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  lirc
0 pakketten opgewaardeerd, 1 nieuwe pakketten geïnstalleerd, 0 verwijderen en 0 niet opgewaardeerd.
Er moeten 0B/344kB aan archieven opgehaald worden.
Na het uitpakken zal er 1663kB extra schijfruimte gebruikt worden.
Voorconfigureren van pakketten...
Selecteren van voorheen niet geselecteerd pakket lirc.
(Database inlezen ... 158883 bestanden en mappen geïnstalleerd.)
Uitpakken van lirc (uit .../lirc_0.8.1+cvs20070310-0ubuntu2_i386.deb) ...
Instellen van lirc (0.8.1+cvs20070310-0ubuntu2) ...
moving /etc/lircmd.conf to /etc/lirc/
Starting lirc daemon: lircd.

```

I edited the file /etc/lirc/hardware.conf and changed the following lines:

LOAD_MODULES="false"
DRIVER="pinsys"
DEVICE="/dev/ttyS0"

Next I copied the content of '/usr/share/lirc/remotes/pinnacle_systems/lircd.conf.pctv' to '/etc/lirc/lircd.conf'

Next I did:

# sudo mv /usr/sbin/lircd /usr/sbin/lircd-original
# sudo mv /usr/sbin/lircmd /usr/sbin/lircmd-original
# sudo cp /usr/local/sbin/lircd /usr/sbin
# sudo cp /usr/local/sbin/lircmd /usr/sbin

Next I opend two terminals.
In the first i did: 

sudo lircd --nodaemon
I got the output
lircd: lircd(pctv) ready

and in the second terminal:
# irw

after that I got in the first:
lircd: accepted new client on /dev/lircd

But using the buttons on the remote control gives no output as it should.

Do anyone know what could be the reason?

Is it normal that on the remote control the led on the front keeps off either the led on the receiver witch is plugged into the card? I don't hope there is a defect in the remote control.

---

