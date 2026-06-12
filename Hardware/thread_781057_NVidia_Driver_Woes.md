---
title: "NVidia Driver Woes"
date: 2008-05-03
forum: Hardware
---

### Post by jhmb on 2008-05-03
Hi,

I am trying to install Ubuntu 8.04, on an HP Pavillion Laptop. I have tried installing the Nvidia drivers several times without success =- it always starts up in low resolution mode.

I looked at /var/log/xorg.conf, and it complained about there being no nvidia module. I checked dmesg and it says:

[   51.012910] NVRM: API mismatch: the client has the version 169.12, but
[   51.012913] NVRM: this kernel module has the version 71.86.04.  Please
[   51.012914] NVRM: make sure that this kernel module and all NVIDIA driver
[   51.012915] NVRM: components have the same version.

Is there anyway to resolove this?

First I tried enabling the restricted drivers using the System/Admin/HardwareDriver dialog. Although this said the drivers were installed, when I rebooted I was back to low resolution.

Then I tried downloading the drivers directly from NVidia and installing them. I did get this to work once, and finally I had full 1440x900 resolution. But when I rebooted, it went back to low resolution mode :(

Then I tried EnvyNG. This claimed to install the drivers, but after rebooting, I was still in low resolution again.

I am running amd64, with the update to date version according to 
sudo apt-get update && sudo apt-get dist-upgrade

Any help appreciated because I would like to escape Vista.

Thanks,
Magnus.

---

### Post by netsurfau on 2008-05-04
G'day Magnus,

I've been having similar issues with my desktop at home.
First, I've been warned to avoid Envy (was in another thread)

Try disabling the nVidia driver in the "Restricted Drivers" under System/Administration.  Doing this stopped the Low Resolution screen coming up every time I booted up &, I can run 1600x1024 on my Asus LCD Widescreen monitor.
So far, the only prob I've had is that Google Earth wont run.  If that's the only problem I have, I'll wait till the Kernal version (which is causing the conflict) is updated.

---

### Post by Zorael on 2008-05-04
Whenever toiling with nvidia drivers (and likely other drivers as well), you should **completely remove** the packages in Synaptic - also called **purge** in Adept Manager, aptitude and apt-get - before reinstalling them to get the newer version.

```
$ sudo aptitude purge nvidia-glx-new nvidia-settings
$ sudo aptitude update
$ sudo aptitude clean
$ sudo aptitude install nvidia-glx-new nvidia-settings
```
Obviously, replace nvidia-glx-new with nvidia-glx or nvidia-glx-legacy if the -new one doesn't support your card.

---

### Post by netsurfau on 2008-05-27
This has gone way beyond a F**KING joke!!
I cannot believe the number of posts where, upgrading to Hardy has caused numerous issues.  Hardy has caused me more problems since it's release, than I've had the whole time I've been using Ubuntu.
(Rant over)

New it was too good to last.  Booted sys on Sat morning and back to  Low Resolution mode.  Nothing I tried would get me back.
In frustration I tried installing Hardy as a fresh, clean install on a new partition.  Result, wonderful graphics but, a number of other issues with FF (3b5 & 2.0.0.14), Thunderbird, nine times out of ten, crashes straight after d/loading new emails.  As well as, when adding icons to Top Panel, the links are missing to activate the selected apps.

Going back to Gutsy is looking like the only way to resolve all my issues.

BTW: Does anyone know how Evolution compares to T/Bird?

---

### Post by netsurfau on 2008-05-28
bump

---

### Post by hotweiss on 2008-05-28
I had a similar problem when trying to upgrade to the 173.08 drivers. The only solution was to reinstall and then use Envy.

---

