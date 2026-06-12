---
title: "Easy TV Capture - analog TV card and video capture"
date: 2009-09-25
forum: Hardware
---

### Post by draco_jem on 2009-09-25
Hello Folks!

I had some problem using my Easy TV Capture card but now IT WORKS!!

LINUX SYSTEM DETAILS: I'm using Ubuntu 9.04 with kernel 2.6.28-15-generic.
TV CARD DETAILS: The TV Card in an Easy TV Capture, the tuner is the PAL-BG version (as reported from the tuner cover).

CARD CONFIGURATION:

1) The kernel module: the right kernel module to use is saa7134 but you must supply the right options to the module:

card=1
tuner=10
i2c_scan=1

so you must load the module with the following command

        modprobe saa7134 i2c_scan=1 card=1 tuner=10

2) Audio: this TV card is not able to transfer audio signal via PCI bus, so using saa7134-alsa is useless.
SOLUTION: the TV card has 3 female jack connectors, the one pink coloured (near S-Video input) is the audio out, if you plug your headphones into this Jack you will hear the sound!!
Instead of connecting your headphones directly to the TV card you can use a male-male jack cable and connect one end to the TV-Card and the other end to a free audio input in your audio card, after thatremember to adjust your mixer settings (unmute the audio and rise the volume of the right audio input).

2) WATCH TV!! I use tvtime to watch TV (simple and powerful) but you can use other applications, for example MythTV.

Hope these informations are usefull to someone!

Have a nice day

Draco_Jem

PS: the card is supplied with a remote controller but I didn't have the time to try to configure it.

---

### Post by draco_jem on 2009-10-07
UPDATE: I found a better configuratione for the driver, the old configuration seems to support only MONO audio, this one should support STEREO audio.

To module manually type this:

        modprobe saa7134 card=3 tuner=10 i2c_scan=1

to automatically apply these options each time the module is loaded follow these steps (these steps are valid in Debian and Ubuntu but should work also for other distributions):

1) create the file /etc/modprobe.d/saa7134.conf

2) open the file and insert the following line

options saa7134 card=3 tuner=10 i2c_scan=1

3) save and close the file


Draco_Jem

P.S.: Althought with the new card number the TV card works better I suspect this is not the best or right configuration since tvtime still sees TWO composite input ports while the card only have ONE conmposite input port.

---

