---
title: "Modem not working with 2.6 kernel"
date: 2005-08-18
forum: Hardware &amp; Laptops
---

### Post by jkidlark on 2005-08-18
Hello from a linux newbie,

Require help getting Unbuntu 5.04 to recognize internal ISA modem.
Details follow:

I have an:
internal CommCenter ISA modem
with a Rockwell controller chip
RCVDL 56ACF/SP
R6761-21
ROCKWELL 97
9832 B62848-3
MEXICO

The scanModem maintainer at linmodems.org has confirmed it is a hardware modem:

<<you have a full hardware one. It needs no special driver, which is why "RH9 detected it without a hitch">>

The modem is detected immediately with rh9 (2.4.2 kernel) and I've been using rh9 and kppp to connect to the internet.
However, I've never had any success detecting the modem with any distributions(MDK,RH,SuSe) using the 2.6 kernel including Ubuntu 5.04.

Ubuntu is the first distribution that has given me the desire to want to solve this problem.

I'm suspecting(remember newbie talking here) that alsa is interferring with modem detection.
My soundcard is an ensoniq 5880.
On direction from [http://linuxmafia.com.faz/Debian/alsa.html](http://linuxmafia.com.faz/Debian/alsa.html), 
I edited etc/hotplug/blacklist in an attempt to stop soundcard being detected as a modem(?) by adding:

snd-ens1371 

The scanModem maintainer advised me to "remove the modules supporting audio" and run wvdialconf.
I don't know how to remove the audio modules (require help here) but I did run wvdialconf


# wvdialconf /dev/wvdial.conf
Scanning your serial ports for a modem.
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Port Scan<*1>: S2   S3   S4   S5   S6   S7   S8   S9
Port Scan<*1>: S10  S11  S12  S13  S14  S15  S16  S17
Port Scan<*1>: S18  S19  S20  S21  S22  S23  S24  S25
Port Scan<*1>: S26  S27  S28  S29  S30  S31  S32  S33
Port Scan<*1>: S34  S35  S36  S37  S38  S39  S40  S41
Port Scan<*1>: S42  S43  S44  S45  S46  S47  S48  S49
Port Scan<*1>: S50  S51  S52  S53
Sorry, no modem was detected! 
Is it in use by another program?
Did you configure it properly with setserial?

I haven't ran setserial. I'm unclear on how to do this.

I then physically pulled audio card from the machine,reinstalled Ubuntu, and ran wvdialconf with same negative results as above.

QUESTIONS:
1) Can someone provide direction to help me get my modem detected with Ubuntu 5.04?
2) How do I remove the "modules supporting audio" in Ubuntu 5.04?
3) How do I install,compile,configure and run setserial in Ubuntu 5.04?

Your consideration is appreciated.

---

### Post by az on 2005-08-18
Even if autodetection fails, try the different devices like


/dev/ttyS0

/dev/ttyS1

/dev/ttyS2

/dev/ttyS3



try dialing out with them.  Note the capital S.

---

### Post by jkidlark on 2005-08-22
Nadda...

But I did compare my /var/log/dmsg files for redhat 9 and KubuntuLive ( I got tired of reinstalling RH9 and Ubuntu5.04 - I don't think I have enough real estate on my harddrive for both).
The excerpts from the  /var/log/dmsg file for RH9 are as follows:
.....
Activating ISA DMA hang workarounds.
isapnp: Scanning for PnP cards...
isapnp: Card '56 Speakerphone srm'
isapnp: 1 Plug & Play card detected total

and....

Serial driver version 5.05c (2001-07-08) with MANY_PORTS MULTIPORT SHARE_IRQ SERIAL_PCI ISAPNP enabled
ttyS0 at 0x03f8 (irq = 4) is a 16550A
ttyS1 at 0x02f8 (irq = 3) is a 16550A
ttyS2 at port 0x03e8 (irq = 4) is a 16550A

<<interesting to note that my BIOS printout puts the '56 Speakerphone srm' on IRQ 5>>

Excerpts from the /var/log/dmsg file for Unbuntu5.04 are as follows:

.....
Activating ISA DMA hang workarounds.
isapnp: Scanning for PnP cards...
isapnp: Card '56 Speakerphone srm'
isapnp: 1 Plug & Play card detected total

<<GOOD NEWS HERE - UBUNTU DOES DETECT THE '56 Speakerphone srm'>>

and 

Serial: 8250/16550  driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at 0x03f8 (irq = 4) is a 16550A
ttyS1 at 0x02f8 (irq = 3) is a 16550A
ttyS0 at 0x03f8 (irq = 4) is a 16550A
ttyS1 at 0x02f8 (irq = 3) is a 16550A

<<NOTHING MENTIONED ABOUT ttyS2>>

It looks like I might have to use setserial to set ttyS2 to irq 4
Unfortunately, I can't seem to installl setserial in KubuntuLive.
Looks like I may have to reinstall Ubuntu5.04 and run setserial
or is it possible to use a different 6249/16550 driver than $Revision 1.90

---

