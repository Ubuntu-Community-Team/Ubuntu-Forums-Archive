---
title: "Disable bluetooth at startup with gnome-bluetooth"
date: 2009-12-28
forum: Hardware
---

### Post by Axx83 on 2009-12-28
Hi. I'm using Ubuntu 9.10 Karmic and since the bluetooth in my notebook works perfectly with the gnome-bluetooth applet, especially turning it on and off, I'd like to issue at startup the command that the applet issue every time it's used. Currently the system turns bluetooth on at each restart not remembering its last status and I see no other way around then my eventual solution.

Thanks

---

### Post by Axx83 on 2009-12-29
Guys, any help ?

---

### Post by darius.k on 2009-12-29
I was looking for a solution for this as well. I didn't find one.
It's annoying to have to turn off bluetooth every time you boot and don't use it. And if your forget it sucks on your laptop batteries.

Maybe open a bug for this at launchpad?

---

### Post by Axx83 on 2009-12-29
Sure it might be a very good idea, but I guess there's already more than one open on this subject

---

### Post by carimbonon on 2010-03-23
I could not find any graphical method so I had to do it this way:
First ALWAYS backup configuration files ! !
```
sudo cp /etc/bluetooth/main.conf /etc/bluetooth/main.conf.OLD
```once backed up edit main.conf file
```
sudo nano /etc/bluetooth/main.conf
```Inside main.conf look for entry:
```
InitiallyPowered = true
```and change the value to *false*

Save with Ctrl+X and restart GDM to see the effect : 
```
/etc/init.d/gdm restart
```**[COLOR=Red]*Remember to save any file in use before restarting the graphical session*[/COLOR]**

I have read[COLOR=Blue] [this tutorial]("https://help.ubuntu.com/community/BluetoothSetup")[/COLOR] but seems a little bit out of date.

---

### Post by Axx83 on 2010-03-24
Thanks carimbonon ! That works perfectly ;-)

---

### Post by lostthetrail on 2010-06-19
Thank you for the great solution, but...

gnome-bluetooth doesn't seem to recognize that I have changed this value and always shows that I have bluetooth enabled. Anyone find a way to solve this problem that will have the applet reporting correctly as well?

---

### Post by wagalaweia on 2011-07-28
According to [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/381913](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/381913) there is the problem that the entries *InitiallyPowered* and *RememberPowered* seem to be ignored (or perhaps overwritten by some other settings). However, there is mentioned a workaround, which works in ubuntu 11.04 and very likely elsewhere, too:

Calling from the commandline...
```
rfkill block bluetooth
```...disables bluetooth in the same way, as a click on 'decativate' does. You can then manually enable/disable it later.

So, it is a good idea to just add the above command to your **.profile** file in your home-directory, then the bluetooth manager gets loaded, but deactivated on each startup.

---

### Post by lvanderree on 2011-10-15
Thanks, rfkill block bluetooth seems to do the trick!

---

### Post by Lupius on 2011-11-21
So how do you manually start up bluetooth after disabling it?

---

### Post by Axx83 on 2011-11-22
By clicking on the bluetooth icon, upper right of the screen

---

### Post by Lupius on 2011-11-24
I disabled my bluetooth so hard that there's no bluetooth icon there anymore, and I can't remember what I did to make it go away...

---

### Post by lvanderree on 2011-11-28
> **Lupius said:**
> I disabled my bluetooth so hard that there's no bluetooth icon there anymore, and I can't remember what I did to make it go away...

Hard to say, only thing I can think of right now, with no information at all is that you might have disabled the entire bluetooth module in /etc/modprobe.d/blacklist.conf ?

I have these modules loaded:

```

$ modprobe -l | grep -i blue

```

```
kernel/drivers/platform/x86/toshiba_bluetooth.ko
kernel/drivers/bluetooth/hci_vhci.ko
kernel/drivers/bluetooth/hci_uart.ko
kernel/drivers/bluetooth/bcm203x.ko
kernel/drivers/bluetooth/bpa10x.ko
kernel/drivers/bluetooth/bfusb.ko
kernel/drivers/bluetooth/dtl1_cs.ko
kernel/drivers/bluetooth/bt3c_cs.ko
kernel/drivers/bluetooth/bluecard_cs.ko
kernel/drivers/bluetooth/btuart_cs.ko
kernel/drivers/bluetooth/btusb.ko
kernel/drivers/bluetooth/btsdio.ko
kernel/drivers/bluetooth/ath3k.ko
kernel/drivers/bluetooth/btmrvl.ko
kernel/drivers/bluetooth/btmrvl_sdio.ko
kernel/drivers/bluetooth/btwilink.ko
kernel/net/bluetooth/bluetooth.ko
kernel/net/bluetooth/rfcomm/rfcomm.ko
kernel/net/bluetooth/bnep/bnep.ko
kernel/net/bluetooth/cmtp/cmtp.ko
kernel/net/bluetooth/hidp/hidp.ko

```

But you should always be able to find the bluetooth icon in the system settings 

something else you can check is, if the bluetooth service is running:

```
$ service bluetooth status

``` 

```
* bluetooth is running

```

if it is not running, and you have bluetooth modules, you should probably be able to simply start the service, or check your log /var/log/syslog or dmesg and find errors.

---

### Post by ceoxtc on 2011-12-04
> **Lupius said:**
> So how do you manually start up bluetooth after disabling it?

*$  rfkill unblock bluetooth*

(Or just right-click on the applet in the tray and turn it on.)

---

### Post by pbanerjee on 2011-12-07
> **lvanderree said:**
> Hard to say, only thing I can think of right now, with no information at all is that you might have disabled the entire bluetooth module in /etc/modprobe.d/blacklist.conf ?

I have these modules loaded:

```

$ modprobe -l | grep -i blue

``````
kernel/drivers/platform/x86/toshiba_bluetooth.ko
kernel/drivers/bluetooth/hci_vhci.ko
kernel/drivers/bluetooth/hci_uart.ko
kernel/drivers/bluetooth/bcm203x.ko
kernel/drivers/bluetooth/bpa10x.ko
kernel/drivers/bluetooth/bfusb.ko
kernel/drivers/bluetooth/dtl1_cs.ko
kernel/drivers/bluetooth/bt3c_cs.ko
kernel/drivers/bluetooth/bluecard_cs.ko
kernel/drivers/bluetooth/btuart_cs.ko
kernel/drivers/bluetooth/btusb.ko
kernel/drivers/bluetooth/btsdio.ko
kernel/drivers/bluetooth/ath3k.ko
kernel/drivers/bluetooth/btmrvl.ko
kernel/drivers/bluetooth/btmrvl_sdio.ko
kernel/drivers/bluetooth/btwilink.ko
kernel/net/bluetooth/bluetooth.ko
kernel/net/bluetooth/rfcomm/rfcomm.ko
kernel/net/bluetooth/bnep/bnep.ko
kernel/net/bluetooth/cmtp/cmtp.ko
kernel/net/bluetooth/hidp/hidp.ko

```But you should always be able to find the bluetooth icon in the system settings 

something else you can check is, if the bluetooth service is running:

```
$ service bluetooth status

``````
* bluetooth is running

```if it is not running, and you have bluetooth modules, you should probably be able to simply start the service, or check your log /var/log/syslog or dmesg and find errors.

I have Lucid Lynx 10.04 running Toshiba laptop with built in bluetooth v3.
When I run modprob as suggested by you, I don't get the first line of the output that you got.. the Toshiba driver for bluetooth. Below is what I get:
---------------------------------------------------------------------
pbanerjee@pbanerjee-laptop:~$ modprobe -l | grep -i blue
kernel/drivers/bluetooth/hci_vhci.ko
kernel/drivers/bluetooth/hci_uart.ko
kernel/drivers/bluetooth/bcm203x.ko
kernel/drivers/bluetooth/bpa10x.ko
kernel/drivers/bluetooth/bfusb.ko
kernel/drivers/bluetooth/dtl1_cs.ko
kernel/drivers/bluetooth/bt3c_cs.ko
kernel/drivers/bluetooth/bluecard_cs.ko
kernel/drivers/bluetooth/btuart_cs.ko
kernel/drivers/bluetooth/btusb.ko
kernel/drivers/bluetooth/btsdio.ko
kernel/drivers/bluetooth/btmrvl.ko
kernel/drivers/bluetooth/btmrvl_sdio.ko
kernel/net/bluetooth/bluetooth.ko
kernel/net/bluetooth/l2cap.ko
kernel/net/bluetooth/sco.ko
kernel/net/bluetooth/rfcomm/rfcomm.ko
kernel/net/bluetooth/bnep/bnep.ko
kernel/net/bluetooth/cmtp/cmtp.ko
kernel/net/bluetooth/hidp/hidp.ko
pbanerjee@pbanerjee-laptop:~$ 
---------------------------------------------------------------------

Any idea why I don't see the bluetooth module for Toshiba ? 
Thanks in advance.

---

### Post by spielball on 2011-12-22
I use Ubuntu 11.10

And the following does the trick for me to disable bluetooth by default on startup/boot, but still keeping the icon in the top panel:

Open your /etc/rc.local file:

```
sudo gedit /etc/rc.local
```Add the following line _before_ all other commands:

```
rfkill block bluetooth
```Then you have something like this:
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

rfkill block bluetooth
exit 0

```Save the file.

After reboot, your bluetooth should be disabled. But you can still re-enable it when needed by using the icon in the top bar.

---

### Post by SpindizZzy on 2012-01-10
Well, spielball, i tried your solution and the upper right corner icon DOES indeed indicate that bluetooth is off, but when i open a terminal right after bootup and check 'service bluetooth status' i get :

* bluetooth is running  :confused:

So i guess the graphical interface 'thinks' that BT is down, but processes are still running... Is this possible ? 


EDIT: I looked here: [http://ubuntuforums.org/showthread.php?t=1768170](http://ubuntuforums.org/showthread.php?t=1768170) , and Howefield's solution (post # 7) removes the graphical BT-icon. That, along with this [http://ubuntuforums.org/showthread.php?t=1897021&highlight=disable+bluetooth+startup](http://ubuntuforums.org/showthread.php?t=1897021&highlight=disable+bluetooth+startup) (post # 3) did the trick for me. When i boot now and check status in terminal, i get 
* bluetooth is not running 

Next question: how to enable it when i need it ?

---

### Post by Syock on 2012-08-31
> **SpindizZzy said:**
> 
* bluetooth is running  :confused:

So i guess the graphical interface 'thinks' that BT is down, but processes are still running... Is this possible ? 

"bluetooth is running" refers to the bluetooth service, which stars the daemon (the program running in background). Even if you disable bluetooth via the applet, it should still be running. If you set BLUETOOTH_ENABLED=0, the bluetooth service won't start at all, on you won't be able to turn on bluetooth via the applet, unless you start the daemon by yourself (and if you try to start the service, it will mention about BLUETOOTH_ENABLED=0 and refuse to start)

---

