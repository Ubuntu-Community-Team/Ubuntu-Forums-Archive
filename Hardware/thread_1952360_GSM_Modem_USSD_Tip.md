---
title: "GSM Modem USSD Tip"
date: 2012-04-04
forum: Hardware
---

### Post by red-lichtie on 2012-04-04
For my provider the USSD code/message "*100#" retrieves the balance from my provider and they don't have a web method of booking vouchers (Pay As You Go) on to my balance.

I have an Acer Aspire 3810TG with an integrated 3G Modem (Huawei EM770W, 12d1:1404), I didn't want the hassle of a dongle. :)

I didn't want to use my phone and do a bit of SIM juggling to top it up so I went looking for a solution the works with Ubuntu.

I tried all sorts of ways to access the USSD functionality of my UMTS card and had limited success with gammu and gsm-ussd.

The reason the success was limited, was because my 1st port was sometimes ttyUSB0, and other times it would be ttyUSB1. To use USSD I have to address the 3rd device ttyUSB2 (or ttyUSB3).

I finally found a way that works for me and should work for just about every 3G modem attached to a DBUS system: dbus-send !

I haven't seen anyother posts describing access to this function so I thought I would share it with you all:

```
dbus-send --system --print-reply --dest=org.freedesktop.ModemManager /org/freedesktop/ModemManager/Modems/0 org.freedesktop.ModemManager.Modem.Gsm.Ussd.Initiate string:*100#
```

Hope this helps someone.

---

### Post by xiq on 2012-04-05
> **red-lichtie said:**
> 
```
dbus-send --system --print-reply --dest=org.freedesktop.ModemManager /org/freedesktop/ModemManager/Modems/0 org.freedesktop.ModemManager.Modem.Gsm.Ussd.Initiate string:*100#
```


Hey Red,

When I try this I get this error:
```

$ dbus-send --system --print-reply --dest=org.freedesktop.ModemManager /org/freedesktop/ModemManager/Modems/0 org.freedesktop.ModemManager.Modem.Gsm.Ussd.Initiate string:*100#
Error org.freedesktop.ModemManager.Modem.General: Failed to encode USSD command '*100#'

```

Any ideas what the right "format" should be?

pix

---

### Post by matiasjrossi on 2012-04-05
> **xiq said:**
> Hey Red,

When I try this I get this error:
```

$ dbus-send --system --print-reply --dest=org.freedesktop.ModemManager /org/freedesktop/ModemManager/Modems/0 org.freedesktop.ModemManager.Modem.Gsm.Ussd.Initiate string:*100#
Error org.freedesktop.ModemManager.Modem.General: Failed to encode USSD command '*100#'

```

Any ideas what the right "format" should be?

pix

I get the same response when the modem is not registered in the GSM network. Try enabling "Mobile broadband" in the NetworkManager indicator.

However if I run this same command with the modem registered, it fails like this:

Error org.freedesktop.ModemManager.Modem.General: USSD session terminated without reply.

And my modem gets disconnected from the USB bus. I suspect this might be a bug in the firmware from the manufacturer. It is known to be flaky.

Maybe you can give it a spin and see if it works for you...

---

### Post by s1.ranjan on 2012-05-24
great work, this have helped me a lot the process what you mentioned only worked for me when I am offline it does not work when I am online I am using Huawei E1732 modem, now I am looking out for some script so that I can just run the script and get the result

---

### Post by red-lichtie on 2012-08-03
I've made it a couple of scripts to make this stuff easier to use:

Identify the modem (the number increases every suspend/resume).

**ussdIdent**
```
#!/bin/bash
modem=`dbus-send --system --print-reply --dest=org.freedesktop.ModemManager /org/freedesktop/ModemManager org.freedesktop.ModemManager.EnumerateDevices|grep "object path"`
modem=`echo $modem | sed 's/.*object path "//' | sed 's/"//'`
echo $modem
```

Send a message to the provider, "*100#" queries my current balance on my pay as you go card.

**ussdQuery**
```
#!/bin/bash
modem=`ussdIdent`
if  [ "x" = "x$1" ]
then
qry="*100#"
else
qry=$1
fi
echo "Sending $qry to $modem ..."
resp=`dbus-send --system --print-reply --dest=org.freedesktop.ModemManager $modem  org.freedesktop.ModemManager.Modem.Gsm.Ussd.Initiate string:$qry`
resp=`echo $resp | sed 's/.* string "//' | sed 's/"//'`
echo $resp
```

If the send fails this will cancel any outstanding requests.

**ussdCancel**
```
#!/bin/bash
modem=`ussdIdent`
resp=`dbus-send --system --print-reply --dest=org.freedesktop.ModemManager ${modem}  org.freedesktop.ModemManager.Modem.Gsm.Ussd.Cancel`
echo $resp
```

Send a "top up" code. My provider uses "*101*TopUpCode#" for this.

**ussdTopup**
```
#!/bin/bash
modem=`ussdIdent`
if  [ "x" = "x$1" ]
then
echo Need to give me a top up code!
exit -1
fi
qry="*101*$1#"
echo "Sending $qry to $modem ..."
resp=`dbus-send --system --print-reply --dest=org.freedesktop.ModemManager $modem  org.freedesktop.ModemManager.Modem.Gsm.Ussd.Initiate string:$qry`
resp=`echo $resp | sed 's/.* string "//' | sed 's/"//'`
echo $resp
```

---

