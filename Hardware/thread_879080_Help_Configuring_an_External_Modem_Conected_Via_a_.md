---
title: "Help Configuring an External Modem Conected Via a a USB/Serial Converter"
date: 2008-08-03
forum: Hardware
---

### Post by l1qgu on 2008-08-03
I have a USR 325686D external modem.  I have no serial port on my computer so I have used a USB serial adapter to connect it.  The adapter appears to be working properly as it appears in Device Manager as USBSer! on /dev/ttyUSB0  I have the following entries in /etc/modules:

usbserial vendor=0x4348 product=0x5523
modprobe usb-storage
modprobe usbserial

When I plug in the device dmessage shows the following:

  636.248000] usb 4-2: new full speed USB device using uhci_hcd and address 3
[  636.412000] usb 4-2: configuration #1 chosen from 1 choice
[  636.424000] usbserial_generic 4-2:1.0: generic converter detected
[  636.424000] usb 4-2: generic converter now attached to ttyUSB0

Device Manager does not show the modem, but under the converter there is an entry called UCHI Host Controller.  I don't know if that is important.

When I try to configure the modem it can not be autodetected.  If I use gnome-ppp and enter /dev/ttyUSB0 as the device name I can get the "RD" and "SD" lights to blink, but this is what the log shows:

--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATX3
ATX3
--> Sending: ATQ0
ATQ0
--> Re-Sending: ATX3
ATX3
--> Modem not responding.

I have also tried using pppconfig, but I can't even get the lights to blink that way.  I'm thinking now that maybe I need to do something special with setserial but I'm way over my head with that.  Any help on this would be great, thanks.

---

### Post by phidia on 2008-08-03
There is a somewhat related thread [here]("http://ubuntuforums.org/showthread.php?t=617623") that might help some? From what I've seen in search some usb to serial adapter have problems in linux so that's the use of the linked thread. 
If you know enough AT&T commands or are willing to learn you could install minicom and see more of what's happening. Minicom allows you to issue commands directly to the modem.

---

### Post by ModelM on 2008-08-03
Your USB/serial adapter seems to be working. If the log file is accurate what is happening is the modem is receiving commands, and even echoing them back, but not responding to the commands.

Make sure your DTE rate is no greater than 115200, lower speeds such as 57600 will work, but do not use any speed above 115200.

Your init string for this USR modem should be: ATZ4 - this is the USR reset string enabling hardware handshaking.

Until you get it running, it may be easier to diagnose by using wvdial because wvdial allows you to see *everytihing* sent to the modem and *every* modem response. Using wvdial, nothing is hidden.

Here's a /etc/wvdial.conf file which should work for you. Just copy this to /etc/wvdial.conf, edit the phone #, username, password, open a terminal, and type:

sudo wvdial

after entering the root password, you should be able to see everything going on...
```

[Dialer Defaults]
    New PPPD = yes
    Stupid Mode = 0
    Modem Type = Analog Modem
    ISDN = 0
    Auto DNS = yes
    Auto Reconnect = 0
    Modem = /dev/ttyUSB0
    Baud = 115200
    Init1 = ATZ4
    Phone = 555 588 3200
Username = whoisthis
Password = guessit 



```

---

### Post by l1qgu on 2008-08-05
Sorry to take so long to reply back to my own thread.  I don't have an internet connection at home so I had to wait for a work day.  I'm going to try that config file and post the results tonight.  Also, I did get the modem to initilize by setting the init dip switch to "override" rather than "normal."  I will post that output tonight as well.

---

### Post by ModelM on 2008-08-05
You bring up a good point regarding the DIP switches. I always forget about them because I never use them, I use software commands to configure.

Now that you've brought it up, though...

*picks up modem*

This one is a USR 5686D & my dip switches are set:

1 = DTR override = up (override is off)
2 = verbal/numeric result codes = up (verbal)
3 = suppress/display result codes = down (display)
4 = echo/no echo of commands = up (echo)
5 = auto answer on/off = down (off)
6 = carrier detect override = up (off)
7 = load NVRAM/Factory defaults = up (NVRAM)
8 = dumb/smart mode = down (smart)

Depending on your USB/Serial adapter, you may indeed need to override DTR using switch #1. It's also important to check switch #8 - dumb mode could cause the behavior you have described.

---

### Post by l1qgu on 2008-08-05
Alright, I tried your wvdial.conf file with DTR on override, and the modem dialed no problem.  I guess "ATZ4" rather than ATZ made all the difference because the other settings appear to be the same.

Thanks a bunch

---

### Post by l1qgu on 2008-08-06
Looks like I spoke too soon.  I assumed that because the modem was dialing that all would be well.  It turns out that the modem dials, the modem on the other end picks up, and they make all those happy modem noises, then... nothing.  After a little wait, wvdial says "no carrier."

Also, I tried to autodetect.  It talks to the modem on ttyUSB0 and decides that a save spped would be 2400, then after checking TTYS$ it reports that no modem could be detected.  I'll post these logs tonight, but I don't know if there is really anything usefull in them.

---

### Post by ModelM on 2008-08-06
Make sure that ATZ4 is the only init string being sent to the modem as wvdial can have several (Init1, Init2, etc) and then let's see how well it hears.

Have the modem dial your own phone # & we'll see if it hears & properly interprets the busy signal.

Yes, I'd like to see those results if you have them, as well as your wvdial.conf file.

---

### Post by l1qgu on 2008-08-06
Here is my wvdial.conf:
[INDENT][Dialer Defaults]
    New PPPD = yes
    Stupid Mode = 0
    Modem Type = Analog Modem
    ISDN = 0
    Auto DNS = yes
    Auto Reconnect = 0
    Modem = /dev/ttyUSB0
    Baud = 57600
    Init1 = ATZ4
    Phone = 454 5776
Username = user
Password = pass[/INDENT]

Here is the output when attempting to dial my own number:
[INDENT]--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ4
ATZ4
OK
--> Modem initialized.
--> Sending: ATDT454 5776
--> Waiting for carrier.
ATDT454 5776
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT454 5776
--> Waiting for carrier.
ATDT454 5776
--> Timed out while dialing.  Trying again.
--> Sending: ATDT454 5776
--> Waiting for carrier.
ATDT454 5776
--> Timed out while dialing.  Trying again.
--> Sending: ATDT454 5776
--> Waiting for carrier.
[/INDENT]


Here is the output when attempting to autodetect the modem using the gnome-ppp frontend (i don't know the command to autodetect from the terminal):
[indent]
WVCONF: /root/.wvdial.conf
GNOME PPP: STDOUT: Editing `/dev/null'.
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: Scanning your serial ports for a modem.
GNOME PPP: STDOUT: 
GNOME PPP: STDERR: Modem Port Scan<*1>: S0   S1   S2   S3   
GNOME PPP: STDERR: WvModem<*1>: Cannot get information for serial port.
GNOME PPP: STDERR: ttyUSB0<*1>: ATQ0 V1 E1 -- OK
GNOME PPP: STDERR: ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
GNOME PPP: STDERR: ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
GNOME PPP: STDERR: ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
GNOME PPP: STDERR: ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
GNOME PPP: STDERR: ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: ttyUSB0<*1>: Modem Identifier: ATI -- ATI
GNOME PPP: STDERR: ttyUSB0<*1>: Speed 4800: AT -- AT
GNOME PPP: STDERR: ttyUSB0<*1>: Modem Identifier: ATI -- ATI
GNOME PPP: STDERR: ttyUSB0<*1>: nothing.
GNOME PPP: STDERR: ttyUSB0<*1>: Max speed is 2400; that should be safe.
GNOME PPP: STDERR: ttyUSB0<*1>: Max speed is 2400; that should be safe.
GNOME PPP: STDERR: ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- ATQ0 V1 E1 S0=0 &C1 &D2
GNOME PPP: STDOUT: 
GNOME PPP: STDERR: ttyUSB0<*1>: and failed too at 115200, giving up.
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: Sorry, no modem was detected!  Is it in use by another program?
GNOME PPP: STDOUT: Did you configure it properly with setserial?
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: If you still have problems, send mail to <wvdial-list@lists.nit.ca>.
[/indent]

There is another new development with this thing.  It was telling me there was no dial tone, so I unplugged it, plugged it back in and checked the phone and it did hear the tone.  Now, however it doesn't seem to matter what I do, it tells me there is no dial tone (though I ca talk on the phone which is plugged into the modem).  I am beginning to suspect that there is a physical problem with the modem.  Anyway, here is the output from that:
[indent]

--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ4
ATZ4
OK
--> Modem initialized.
--> Sending: ATDT460 0200
--> Waiting for carrier.
ATDT460 0200
NO DIAL TONE
--> No dial tone.
--> Disconnecting at Wed Aug  6 17:12:51 2008


[/indent]

---

### Post by ModelM on 2008-08-06
I have a lot of modems here - I think 7 off the top of my head (there's a story behind that, but we'll skip it). One of them is a USR Sportster about 10 years old. It works great - unless...

If the first dialing attempt fails for any reason all subsequent dialing attempts will fail also, sometimes with the modem not even going off hook even though it thinks it has. It's easy with wvdial to test this by waiting for the dial string to be sent to & echoed from the modem, then picking up the phone. If you hear a dialtone, the modem isn't dialing no matter what it tells you.

The only way to recover from a failed dialing attempt with this modem is to turn it off & back on. If the first dial is successful (it usually is, of course) the modem performs very well, thus it is still here.

You might want to keep this in mind when you're working with yours.

Your wvdial.conf looks ideal. The output from wvdial looks very familiar. That's how this modem behaves - first dialing attempt unsucessful (for any reason) and the next attempt times out.

---

### Post by l1qgu on 2008-08-06
This modem is 8 years old, so that makes it about the same age as yours.  I have finally managed to get online with it, but I'm using a borrowed windows conputer.  Configuring this thing was suprisingly difficult on windows too, and I can only get it up to 28.8 which is a bit odd.  I'm going to play some more on my own computer now and we'll see.

---

### Post by l1qgu on 2008-08-06
After quite a bit of playing I have found that it takes an average of 4 dialing attempts to get this modem to connect in windows, and I get the best results if I match the adapter's speed to the modem port speed.  I'm wondering now if it would make any sence to try the same thing in Ubuntu, and if so what is the file that i have to edit?

---

### Post by ModelM on 2008-08-07
I don't understand what "match the adapter's speed to the modem port speed" means. I would expect your adapter to behave like a serial port & have only one speed - the DTE speed.

You're doing everything right, as far as I can tell. Is there any way you can lay your hands on another RS232 modem for a test? I'm beginning to think yours might be flaky.

---

### Post by l1qgu on 2008-08-07
I had thought the same about the speed, but in the windows device manager, the modem and the adapter appear as two seperate entries.  The adapter is unter the "ports, com and lpt" section, and has all the normal settings you would expect for a communications port (parity, max bitrate, flow control, stop bits, etc).  The modem also has all these same settings and if the adapter's speed is set below the modem's speed it does not work very well at all.  I'm not supprised that Linux doesn't do it that way as the windows way is obviously quite silly.

  I think I do have another modem.  It's a Zoltrix 28.8 external that I paid $450 for (it was a long time ago) and thought I would never get to use again.  It'll be the weekend before I can lay my hands on it though so I think I'll just wait until then before I spend any more time on this.

---

### Post by ModelM on 2008-08-08
There's one more thing you might try. You can go to the USR Support website, walk your way through the menus to find your modem & check for a firmware update. If yours is a 5686D there is an update available.

I flashed the one I have here some months back. The folks at USR have the flash utility available in a package which works quite smoothly under Linux - no Windows required.

The USR Support website can be found here...

[http://www.usr.com/support/s-main-menu.asp](http://www.usr.com/support/s-main-menu.asp)

---

