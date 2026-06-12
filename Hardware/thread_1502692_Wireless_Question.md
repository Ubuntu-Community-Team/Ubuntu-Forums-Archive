---
title: "Wireless Question"
date: 2010-06-05
forum: Hardware
---

### Post by RavenStandsAlone on 2010-06-05
I have a Dell Netbook Inspiron 910 (Mini). This unit came pre-installed with Ubuntu 8.0.x. I downloaded the .iso for Ubuntu 10 and did a thumbdrive install. Seems to run real nice and had no problen connecting to the Interwebs on "Auto eth0."

The hardware for the wireless 802.11 is Broadcom. Hardware drivers says: "License: Proprietary THese package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware." (Puctuation and apparent typos are theirs.)

Below that it says that "This driver is activated and currently in use."

Here is the problem. I am not able to connect except with the ethernet. The Wireless Networks is greyed out and it says disconnected in even fainter grey letters below that.

Also, my bluetooth Icon says bluetooth on in greyed out and gives me the active option to turn bluetooth off but there is a red x on the icon on the task area.

Any suggestions as to how to get the wireless to find my wifi and what is up with the bluetooth?

EDIT: I went to system and looked at Bluetooth Prefernces and it says bluetooth is disabled and has a large button that says "Turn On Bluetooth" I clicked on it and it greyed out and is just sitting there now waiting for me to close the dialogue. Still says Blutooth is disabled.

Thanks,

Raven

:guitar:

---

### Post by irv on 2010-06-05
> **RavenStandsAlone said:**
> I have a Dell Netbook Inspiron 910 (Mini). This unit came pre-installed with Ubuntu 8.0.x. I downloaded the .iso for Ubuntu 10 and did a thumbdrive install. Seems to run real nice and had no problen connecting to the Interwebs on "Auto eth0."

The hardware for the wireless 802.11 is Broadcom. Hardware drivers says: "License: Proprietary THese package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware." (Puctuation and apparent typos are theirs.)

Below that it says that "This driver is activated and currently in use."

Here is the problem. I am not able to connect except with the ethernet. The Wireless Networks is greyed out and it says disconnected in even fainter grey letters below that.

Also, my bluetooth Icon says bluetooth on in greyed out and gives me the active option to turn bluetooth off but there is a red x on the icon on the task area.

Any suggestions as to how to get the wireless to find my wifi and what is up with the bluetooth?

Thanks

:guitar:
First do you have a hardware switch on you Inspiron netbook? I have one on my Inspiron 1521 laptop. If you do make sure it is set to on.
Next. I use a STA wireless driver, and I had to install it by going to System > Administration > Hardware Driver and Install the third party driver from there. I had to plug in the wire network until this was done then I could unplug it and the wireless worked.

---

### Post by RavenStandsAlone on 2010-06-05
> **irv said:**
> First do you have a hardware switch on you Inspiron netbook? I have one on my Inspiron 1521 laptop. If you do make sure it is set to on.
Next. I use a STA wireless driver, and I had to install it by going to System > Administration > Hardware Driver and Install the third party driver from there. I had to plug in the wire network until this was done then I could unplug it and the wireless worked.

This is what I got when I went to System Administration Hardware drivers: 

"License: Proprietary THese package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware." (Puctuation and apparent typos are theirs.)

Below that it says that "This driver is activated and currently in use."

---

### Post by gunfyter on 2010-06-05
Connected to your wired internet connection

Try

SYSTEM>ADMINISTRATION>HARDWARE DRIVERS 

and see if there is 

BroadCom B43 wireless driver.

If there is there should be a "Green Light" to the left of it indicating it is active and currently in use.

I am saying this because mine says NO PROPRIETARY DRIVERS ARE IN USE ON THIS SYSTEM.  Which is contrary to what you say yours says.     I have an HP L2000 but I think it has the same wireless card as yours....  I would think you could use the same non-proprietary driver.

---

### Post by RavenStandsAlone on 2010-06-05
> **gunfyter said:**
> Connected to your wired internet connection

Try

SYSTEM>ADMINISTRATION>HARDWARE DRIVERS 

and see if there is 

BroadCom B43 wireless driver.

If there is there should be a "Green Light" to the left of it indicating it is active and currently in use.

I am saying this because mine says NO PROPRIETARY DRIVERS ARE IN USE ON THIS SYSTEM.  Which is contrary to what you say yours says.     I have an HP L2000 but I think it has the same wireless card as yours....  I would think you could use the same non-proprietary driver.

It says mine is currently the proprietary STA driver. I will uninstall it and install the B43 and see if that flies.

---

