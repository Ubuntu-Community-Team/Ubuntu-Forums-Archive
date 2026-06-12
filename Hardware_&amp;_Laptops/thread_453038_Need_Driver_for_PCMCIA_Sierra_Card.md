---
title: "Need Driver for PCMCIA Sierra Card"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by rnovak on 2007-05-23
Hi 

i need the driver for Sierra 750 Data Card AirCard GPRS

Anyone?


THX!! :)

---

### Post by teaker1s on 2007-05-24
firstly it may work with **ndiswrapper**

we can find the chipset if you post results of 

```
lsusb
```

```
lspci
```

---

### Post by rnovak on 2007-05-30
Sorry, can you explain im a linux Newbie

i got this from sirra but wasnt able to folloe trough

by the way, it is a Sierra AirCard 750

---

### Post by rnovak on 2007-05-30
root@rnovak-laptop:~# lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
root@rnovak-laptop:~# lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:05.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
01:0a.0 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
01:0a.1 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
01:0a.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
01:0a.3 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
01:0d.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
01:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
root@rnovak-laptop:~#

---

### Post by teaker1s on 2007-05-30
I'm no expert, but it looks as if the file system on the redhat guide is the same as ubuntu.
First issue we have is that we do not run as root on ubuntu-purely for safety. we can get round this by

```
gksudo nautilus
``` be aware to follow the guide to the letter-if in doubt do not delete anything,
select file system(click on left labled file system)
 you will allso need to make driver files executable-right click>properties>permissions
then tick write and execute:KS then cut and paste files into etc/pcima

tell me how you get on and I'll see if I can help

---

### Post by rnovak on 2007-05-30
i did it :) do you know of any SMS Gateway (with GUI)?

---

### Post by rnovak on 2007-05-31
I havent Managed to make it Work, all the installation was done but no success making it work






.

---

### Post by teaker1s on 2007-05-31
I don't know of any sms gateway's-your service provider should tell you(same as sim)
```
 gksudo synaptic
```
search "ppp" you may need a ppp program to dial out, then look in system>administration>networking
I appologise if my writing is brief, have had accident with my hand and damaged tendon-making it difficult:(

---

### Post by rnovak on 2007-06-01
Nothing working yet.....


all i want is to receive SMS

---

### Post by linxuser14 on 2007-06-20
Hi,
 I also have an AirCard 750. I'm running Kubuntu 6.06 LTS. I've made connect, but it won't continue.

I'm thinking now that the operating system is somehow losing recognition of my card. In my attempts

to make it work I've somehow caused it to stay on even when the OS loses the connection for some

reason. I have to reinsert the card and manually exit KPPP (pppd), wait for the led light to blink

green, and then restart KPPP (pppd). I don't think I use SMS. Not sure what that is. 

If you've come across something that helps with aircard, I'd greatly appreciate any comments 

about it. Following is a cut and paste from my post in Absolute Beginner Talk Foruim. Hope something

in it can help.

linxuser14

>The following is best I can remember, how i gained temporary

access to internet with my Sierra Wireless AirCard 750

Via [http://www.sierrawireless.com/SupportDownload/downloads/AirCard7x0.zip](http://www.sierrawireless.com/SupportDownload/downloads/AirCard7x0.zip)

Downloaded and unzip AirCard7x0.zip

ac750

ac750chat

SW_7xx_SER.dat

Edited with Kate

Added to /etc/pcmcia/config under Modems and other serial devices

card "Sierra Wireless AC710/AC750 GPRS Network Adapter R1"
manfid 0x0192, 0x0710
cis "cis/SW_7xx_SER.dat"
bind "serial_cs"

Copied the file SW_7xx_SER.dat to /etc/pcmcia/cis/

Restarted computer

Inserted AirCard. It didn't make two beeps indicating it was detected.

KSystemlog shows it was detected with only two lines

	kernel	[17180031.284000] pccard: PCMCIA card inserted into slot 0
	kernel	[17180031.292000] pcmcia: registering new device pcmcia0.0

Copied files ac750 and ac750chat into /etc/ppp/peers

Editied file /etc/ppp/peers/ac750chat second line to

OK AT+cgdcont=1,"IP","INTERNET2.VOICESTREAM.COM"

/usr/share/doc/kppp/README.Debian says to

uncomment "noauth" in /etc/ppp/peers/kppp-options

KSystemlog now shows

	kernel	[17180283.576000] pccard: card ejected from slot 0
	kernel	[17180289.916000] pccard: PCMCIA card inserted into slot 0
	kernel	[17180289.916000] pcmcia: registering new device pcmcia0.0
	kernel	[17180289.944000] 0.0: ttyS0 at I/O 0x3f8 (irq = 3) is a 16550A

KPPP says it errored or couldn't find /lib/firmware/SW_7xx_SER.cis

So I copied SW_7xx_SER.dat to /lib/firmware/SW_7xx_SER.dat

and copied SW_7xx_SER.dat to /lib/firmware/SW_7xx_SER.cis

My KPPP connect program is configured as follows

-> Accounts
             -> Connection name: T-Mobile
             -> Phone number:    *99#
             -> Authentication:  PAP
                                   -> Store password is checked
----------------------------------------------------------------------

-> Modems
             -> Device
                       -> Modem name:        AirCard 710/750
                       -> Modem device:      /dev/ttyS0
                       -> Flow control:      Hardware [CRTSCTS]
                       -> Line termination:  CR
                       -> Connection speed:  921600
-> Use lock file is un-checked
-> Modem timeout: is set at 60 sec

-> Modems
             -> Modem
                    -> Wait for dial tone is un-checked
                    -> only one addition to edit modem commands is

            -> Initialization string 2: at+cgdcont= 1,"IP","INTERNET2.VOICESTREAM.COM"

Both Login ID and Passord I've double single quote

This is the KSystemlog output for the connect. as you see it terminated at 2 minutes

	kernel	[17182113.032000] pccard: card ejected from slot 0
	kernel	[17182119.556000] pccard: PCMCIA card inserted into slot 0
	kernel	[17182119.556000] pcmcia: registering new device pcmcia0.0
	kernel	[17182119.600000] 0.0: ttyS0 at I/O 0x3f8 (irq = 3) is a 16550A
	pppd[5539]	Connect: ppp0 <--> /dev/ttyS0
	pppd[5539]	pppd 2.4.4b1 started by ds2, uid 1000
	pppd[5539]	Using interface ppp0
	kernel	[17182185.284000] PPP BSD Compression module registered
	kernel	[17182185.356000] PPP Deflate Compression module registered
	pppd[5539]	appear to have received our own echo-reply!
	pppd[5539]	PAP authentication succeeded
	pppd[5539]	Remote message: TTP Com PPP - Password Verified OK
	pppd[5539]	Cannot determine ethernet address for proxy ARP
	pppd[5539]	local  IP address 10.172.93.90
	pppd[5539]	primary   DNS address 66.94.9.120
	pppd[5539]	remote IP address 169.254.85.170
	pppd[5539]	secondary DNS address 66.94.25.120
	pppd[5539]	appear to have received our own echo-reply!
	pppd[5539]	appear to have received our own echo-reply!
	pppd[5539]	appear to have received our own echo-reply!
	pppd[5539]	Connection terminated.
	pppd[5539]	Connect time 2.0 minutes.
	pppd[5539]	Exit.
	pppd[5539]	No response to 4 echo-requests
	pppd[5539]	Sent 57010 bytes, received 216199 bytes.
	pppd[5539]	Serial link appears to be disconnected.

Here is the first of an endless stream of attempt by pppd (KPPP) to reconnect.

	pppd[5714]	Connect: ppp0 <--> /dev/ttyS0
	pppd[5714]	pppd 2.4.4b1 started by ds2, uid 1000
	pppd[5714]	Using interface ppp0
	pppd[5714]	Connection terminated.
	pppd[5714]	Exit.
	pppd[5714]	Hangup (SIGHUP)
	pppd[5714]	Modem hangup

I added this via Windows Connect. When I first posted this I did it thru

Kubuntu via my WIFI connection.

The continueing attempts by KPPP to connect via aircard are unchanged.

I can only connect via Windows to check this forum. Anyone see what I'm doing

wrong. I know Kubuntu can establish a connection cause it did for 2 minutes.

I just don't know what to try next. This 2 minute connect was after having installed

Kubuntu 3 months ago and several times since. Any suggestions are welcome

Thanks

linxuser

P.S. An additional attempt

I got an idea to look for things to edit in files of /etc/ppp and /etc/pcmcia etc....

opened one file /etc/ppp/config i think, uncommented things like passive, something

to do with LTP or something like noLTP not ending pppd after an event. I don't recall

it all. unfortunately its on the Kubuntu partition of my hard drive so its not available to me

from this my Windows partition. But this connection via aircard is stable. Anyway after

editing these changes KPPP connected and remained connected for 10 minutes. When

it no longer communicated I had to manually disconnect, presumably cause of the passive

thing or something. KPPP when restarted couldn't find my aircard, so I reinserted it and

waited for the led to flash green, meaning it had a connection available. Then KPPP was

able to recognize the aircard, intialize and connect for an additional 5 minutes. More tries

proved unsuccessful. Thing is when I rebooted into windows the aircard's led light remained

steady red. After 2 attempts at reinstalling Window's software for it, it came back. I've

decided that maybe Kubuntu issued something to the aircard and I don't know what. 

Since the aircard works in windows I'm thinking maybe I should give up trying to get it

to work in Kubuntu. Don't want to mess it up and end up with no internet. Anyway this is

all I have on it.



p.s p.s. 

if you think this posting should be under another forum, please let me know, and 

thank you to everyone for working on this OS. I don't understand alot about it but I like

being able to work with open source system. I think its the coolest idea around.

Later, All
>

---

