---
title: "Cyber Power System, Inc. CP1500 AVR UPS"
date: 2009-05-01
forum: Hardware
---

### Post by 65 mustang on 2009-05-01
My UPS stopped working with 9.04.  Is anyone else having this problem?

Wrote a bug:
[https://bugs.launchpad.net/ubuntu/+bug/366511](https://bugs.launchpad.net/ubuntu/+bug/366511)

Is this UPS working on anyone else's 9.04 system?  :confused:

---

### Post by jturning on 2009-05-08
I don't use Gnome on my Slackware desktop, but I just got a Cyberpower UPS and they have a CLI package for controlling the UPS. The CLI package gives you a better status display on the unit, and you can configure the behavior. I've set mine up to power down when the battery hits 25%. Otherwise my desktop keeps running. The UPS will power down by time after the computer shuts down. If power is present it turns back on and my computer powers up on power through the BIOS. My desktop has some server functionality I depend on remotely.

[http://www.cyberpowersystems.com/products/management-software/ppl.html](http://www.cyberpowersystems.com/products/management-software/ppl.html)

```
root@bugz:/home/jturning# pwrstat -status

The UPS information shows as following:

        Properties:
                Model Name...................  CP 1300C
                Rating Voltage............... 120 V
                Rating Power................. 750 Watt

        Current UPS status:
                State ....................... Normal
                Power Supply by ............. Utility Power
                Utility Voltage ............. 118 V
                Output Voltage............... 118 V
                Battery Capacity ............ 100 %
                Load ........................ 13 %
                Remaining Runtime ........... 42 min.
                Line Interaction............. None
```Bugz

---

### Post by cebif on 2009-05-13
> **65 mustang said:**
> My UPS stopped working with 9.04.  Is anyone else having this problem?

Wrote a bug:
[https://bugs.launchpad.net/ubuntu/+bug/366511](https://bugs.launchpad.net/ubuntu/+bug/366511)

Is this UPS working on anyone else's 9.04 system?  :confused:

I have a similar problem a Richcomm KI1000LCD UPS. I was able to make it auto start on boot by editing the /etc/rc.local file in 8.10 intrepid but this doesn't work in 9.04.
Also in 8.10 and 9.04. I can start it manually with the command
that command starts both the ups_manager and ups_monitor software.
```
greg@greg-desktop:/etc/ups_manager$ sudo ./ups_manager start &
Starting UPS_Manager...: 
[2] 13206
greg@greg-desktop:/etc/ups_manager$ 
=========================UPS Power Manager start...============================
================Initialize is OK!  start read the data from com================


```
In the rc.local file the command is the same that works manually but that doesn't work with rc.local automatically on boot.

---

### Post by tehk on 2009-05-17
> **jturning said:**
> I don't use Gnome on my Slackware desktop, but I just got a Cyberpower UPS and they have a CLI package for controlling the UPS. The CLI package gives you a better status display on the unit, and you can configure the behavior. I've set mine up to power down when the battery hits 25%. Otherwise my desktop keeps running. The UPS will power down by time after the computer shuts down. If power is present it turns back on and my computer powers up on power through the BIOS. My desktop has some server functionality I depend on remotely.

[http://www.cyberpowersystems.com/products/management-software/ppl.html](http://www.cyberpowersystems.com/products/management-software/ppl.html)

```
root@bugz:/home/jturning# pwrstat -status

The UPS information shows as following:

        Properties:
                Model Name...................  CP 1300C
                Rating Voltage............... 120 V
                Rating Power................. 750 Watt

        Current UPS status:
                State ....................... Normal
                Power Supply by ............. Utility Power
                Utility Voltage ............. 118 V
                Output Voltage............... 118 V
                Battery Capacity ............ 100 %
                Load ........................ 13 %
                Remaining Runtime ........... 42 min.
                Line Interaction............. None
```Bugz

thanks, thats all i needed to decide whether or not to buy an APC or CyberPower UPS...

[SIZE="7"]CYBERPOWER IT IS![/SIZE]

---

### Post by JPorter on 2009-06-03
> **tehk said:**
> thanks, thats all i needed to decide whether or not to buy an APC or CyberPower UPS...

[SIZE="7"]CYBERPOWER IT IS![/SIZE]

You can run the CyberPower units very well without using their command line utility or script.

In Jaunty, just make sure you have the package[FONT="Courier New"] upsd [/FONT]installed, and in the power management panel (System -> Preferences -> Power Management) you will have a new "On UPS Power" tab.  Turn on the battery notification option in the General tab to have dynamic indication in the Gnome panel, similar to the battery icon for a laptop.

Hope this helps...

---

