---
title: "Cellphone and dialup?"
date: 2005-08-23
forum: Hardware &amp; Laptops
---

### Post by AndersAA on 2005-08-23
Does anyone have this working?

Plugging the cellphone into the laptop I see it's connected ok at /dev/ttyUSB0, but trying to connect with gnome's tool it doesn't seem it's getting anywhere.

```

Aug 23 23:52:11 localhost pppd[9417]: pppd 2.4.2 started by root, uid 0
Aug 23 23:52:12 localhost chat[9418]: timeout set to 60 seconds
Aug 23 23:52:12 localhost chat[9418]: abort on (ERROR)
Aug 23 23:52:12 localhost chat[9418]: abort on (BUSY)
Aug 23 23:52:12 localhost chat[9418]: abort on (VOICE)
Aug 23 23:52:12 localhost chat[9418]: abort on (NO CARRIER)
Aug 23 23:52:12 localhost chat[9418]: abort on (NO DIALTONE)
Aug 23 23:52:12 localhost chat[9418]: abort on (NO DIAL TONE)
Aug 23 23:52:12 localhost chat[9418]: abort on (NO ANSWER)
Aug 23 23:52:12 localhost chat[9418]: send (ATZ^M)
Aug 23 23:52:12 localhost chat[9418]: send (AT&FH0L3^M)
Aug 23 23:52:12 localhost chat[9418]: expect (OK)
Aug 23 23:53:12 localhost chat[9418]: alarm
Aug 23 23:53:12 localhost chat[9418]: send (AT^M)
Aug 23 23:53:12 localhost chat[9418]: expect (OK)
Aug 23 23:54:12 localhost chat[9418]: alarm
Aug 23 23:54:12 localhost chat[9418]: Failed
Aug 23 23:54:13 localhost pppd[9417]: Exit.

```

---

### Post by adityanag on 2005-08-28
I am using a Nokia 3120 with the USB data cable to connect and it works fine. I used wvdial to set it up. 

1. I plugged in the cable and phone. dmesg showed me that the phone was detected and assigned the USB-ACM driver. Since your phone is detected as well, you shouldn't have any problems either.

2. run "sudo wvdialconf" This will setup your modem and create a file called /etc/wvdial.conf. 

3. Edit /etc/wvdial.conf, and enter your ISP's phone number, your username and password.

4. Try connecting using the command wvdial

5. If you are lucky, it'll connect, and you should be able to use the net. In my case, I had to edit wvidal.conf to include some specific Init commands. i got these by going through the windows .inf file for my Nokia. If you are trying a Nokia, it may work for you too. Otherwise, I guess you'll have to Google for your phone's specific Init commands.

Here's what my wvdial.conf looks like

[Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 230400
Init1 = ATZ
Init2 = AT+crm=1  #extra Nokia Init  
Init3 = AT+cso=33 #-ditto-
Init4 = AT V1 E0 #-ditto-
ISDN = 0
Modem Type = USB Modem
 Phone = #777
 Username = whatever
 Password = whatever

I hope that helped you..

---

### Post by AndersAA on 2005-08-28
well it isn't picked up by usb-acm, what does your dmesg output look like when connecting it?

---

### Post by adityanag on 2005-08-28
drivers/usb/class/cdc-acm.c: This device cannot do calls on its own. It is no modem.
cdc_acm 2-1:1.0: ttyACM0: USB ACM device
usbcore: registered new driver cdc_acm
drivers/usb/class/cdc-acm.c: v0.23:USB Abstract Control Model driver for USB modems and ISDN adapters


That's what I get. However, in your first post you said that your phone is getting detected as /dev/ttyUSB0. This means that your phone probably doesn't need to use the USb-ACM driver. 

Did you try running wvdialconf? and i forgot to mention that the command is "sudo wvdialconf /etc/wvdial.conf" I think it should just work. here's the output i get when i run it.

 sudo wvdialconf temp
Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Port Scan<*1>: S1   S2   S3   S4   S5   S6   S7   S8
Port Scan<*1>: S9   S10  S11  S12  S13  S14  S15  S16
Port Scan<*1>: S17  S18  S19  S20  S21  S22  S23  S24
Port Scan<*1>: S25  S26  S27  S28  S29  S30  S31  S32
Port Scan<*1>: S33  S34  S35  S36  S37  S38  S39  S40
Port Scan<*1>: S41  S42  S43  S44  S45  S46  S47
ttyACM0<*1>: ATQ0 V1 E1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 Z -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- ERROR
ttyACM0<*1>: Modem Identifier: ATI -- ERROR
ttyACM0<*1>: Speed 4800: AT -- OK
ttyACM0<*1>: Speed 9600: AT -- OK
ttyACM0<*1>: Speed 19200: AT -- OK
ttyACM0<*1>: Speed 38400: AT -- OK
ttyACM0<*1>: Speed 57600: AT -- OK
ttyACM0<*1>: Speed 115200: AT -- OK
ttyACM0<*1>: Speed 230400: AT -- OK
ttyACM0<*1>: Speed 460800: AT -- \uffff\uffff
ttyACM0<*1>: Speed 460800: AT -- \uffff\uffff
ttyACM0<*1>: Speed 460800: AT -- \uffff\uffff
ttyACM0<*1>: Max speed is 230400; that should be safe.
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK

Found an USB modem on /dev/ttyACM0.
Modem configuration written to temp.
ttyACM0<Info>: Speed 230400; init "ATQ0 V1 E1 S0=0 &C1 &D2"

Wvdial ought to find your phone on /dev/ttyUSB0 and set it up. try it and get back to me if it worked.

---

### Post by chunk on 2005-08-28
I just used pppconfig to set mine up on /dev/ttyACM0

Anyway, can you guys suspend to ram after using your cellphone-internet? Sometimes suspend doesn't work for me after using it, or it works, but only after a long delay (several minutes). Does anyone have a solution?

---

### Post by adityanag on 2005-08-28
I didn't have any problems. It sleeps fine and hibernate also works. I am using an IBM T43 1875-e5u

---

### Post by AndersAA on 2005-08-29
[QUOTE=chunk]I just used pppconfig to set mine up on /dev/ttyACM0

Anyway, can you guys suspend to ram after using your cellphone-internet? Sometimes suspend doesn't work for me after using it, or it works, but only after a long delay (several minutes). Does anyone have a solution?[/QUOTE]
 well I never got my cellphone online in the first place :p

---

### Post by chunk on 2005-08-29
[QUOTE=AndersAA]well I never got my cellphone online in the first place :p[/QUOTE]

Still having problems? Are you sure you have all the right connection info? Have you tried pppconfig?

---

### Post by AndersAA on 2005-08-29
I plug the phone in and can connect to it using /dev/ttyUSB0 (as per dmesg msg), but I never get any "output" on the phone, nor do I get a dial tone.

---

### Post by chunk on 2005-08-30
[QUOTE=AndersAA]I plug the phone in and can connect to it using /dev/ttyUSB0 (as per dmesg msg), but I never get any "output" on the phone, nor do I get a dial tone.[/QUOTE]

What cellular service provider are you using and what model of phone? Are you trying to dialup to your cellular service provider's internet service (if they provide one) or are you trying to dialup to a separate ISP?

My only experience is using a motorola phone to dialup to verizon's cellular internet service. However, different phones and cellular service providers require different kinds of initializations. Perhaps you should check [http://howardforums.com](http://howardforums.com) for information on how to go online with your service provider and phone model (regardless of operating system), then use this information to make your configuration file using pppconfig or wvdialconf.

Also, if anyone has run into the same problem of being unable to suspend to ram after using cellular internet in ubuntu then please post here. I'm sure I just need to remove a driver or shutdown a service (in acpi-support), but I'm not sure which and I haven't gotten a chance to look at logs. I will post back when I get a chance to look at the logs, but if someone else already knows the answer then that would be easier for me. :)

---

### Post by estebancs on 2007-09-11
I found out that it's kinda easy to use cell phones treating them as usb modems when connected with an usb cable... Unfortunately I don't have an usb cable, I use an USB to IRDA adapter that works great in windows but I dont know how to configure it in ubuntu, there's any way I can use it in ubuntu, how I configure wvdial to recognize my phone from my IRDA connection?

---

