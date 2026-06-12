---
title: "Asus P5e-VM HDMI no audio through HDMI"
date: 2013-08-15
forum: Hardware
---

### Post by bucket81 on 2013-08-15
Hello all 

I am very new to Linx and Ubuntu, I am setting up a media PC with some old hardware and XBMC. I have installed ubuntu-12.04.2-desktop-amd64 installed avalible updates and also played with the sound settings. It sees that I have an HDMI and lets me test it but I get no sound. I did search and came back with some pretty old solutions nothing for the current version. Any ideas? 

Oh and I booted up windows with the HDMI and get sound so its doesn't seam to be hardware.

---

### Post by Yellow Pasque on 2013-08-16
If it's an ATI/AMD radeon, use workaround 1 here: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735)

If not, give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by bucket81 on 2013-08-16
No its Intel. Some of the directions on that page didnt work but I figured it out. 

[http://www.alsa-project.org/db/?f=0868702e03ce70bb392ae5d7c0ca06d0553d4cc1](http://www.alsa-project.org/db/?f=0868702e03ce70bb392ae5d7c0ca06d0553d4cc1)

---

### Post by Yellow Pasque on 2013-08-16
First thing I'd try is the latest driver:
```
cd ~/
wget https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+files/oem-audio-hda-daily-lts-quantal-dkms_0.201308151917%7Eprecise1_all.deb
sudo dpkg -i oem-audio-hda-daily-lts-quantal-dkms_0.201308151917~precise1_all.deb
```

---

### Post by bucket81 on 2013-08-16
> **Temüjin said:**
> First thing I'd try is the latest driver:
```
cd ~/
wget https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+files/oem-audio-hda-daily-lts-quantal-dkms_0.201308151917%7Eprecise1_all.deb
sudo dpkg -i oem-audio-hda-daily-lts-quantal-dkms_0.201308151917~precise1_all.deb
```

Do I just plug that into terminal?(my noob is showing) And will that only do my audio I would like all the drivers up to date. I checked with Asus before posting and there are no drives for Linux.

And thanks for the help!

---

### Post by bucket81 on 2013-08-16
Im getting an error... 

(Reading database ... 170116 files and directories currently installed.)
Preparing to replace oem-audio-hda-daily-lts-quantal-dkms 0.201308151917~precise1 (using oem-audio-hda-daily-lts-quantal-dkms_0.201308151917~precise1_all.deb) ...
Unpacking replacement oem-audio-hda-daily-lts-quantal-dkms ...
dpkg: dependency problems prevent configuration of oem-audio-hda-daily-lts-quantal-dkms:
 oem-audio-hda-daily-lts-quantal-dkms depends on dkms (>= 1.95); however:
  Package dkms is not installed.
dpkg: error processing oem-audio-hda-daily-lts-quantal-dkms (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 oem-audio-hda-daily-lts-quantal-dkms

I then rebooted and saw a do not enter singh at the top of my screen, it say there has been a package that has not been install. Theres 2

Dynamic Kernel Module Support Framework 
and 
tool for simulating superuser privileges

If I try to install these I get 
The package system is broken 
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

details
The following packages have unmet dependencies:

oem-audio-hda-daily-lts-quantal-dkms: Depends: dkms (>= 1.95) but it is not installed

^^ That looks like my problem. Any solutions?

---

### Post by Yellow Pasque on 2013-08-16
> **bucket81 said:**
> Im getting an error... 

(Reading database ... 170116 files and directories currently installed.)
Preparing to replace oem-audio-hda-daily-lts-quantal-dkms 0.201308151917~precise1 (using oem-audio-hda-daily-lts-quantal-dkms_0.201308151917~precise1_all.deb) ...
Unpacking replacement oem-audio-hda-daily-lts-quantal-dkms ...
dpkg: dependency problems prevent configuration of oem-audio-hda-daily-lts-quantal-dkms:
 oem-audio-hda-daily-lts-quantal-dkms depends on dkms (>= 1.95); however:
  Package dkms is not installed.
dpkg: error processing oem-audio-hda-daily-lts-quantal-dkms (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 oem-audio-hda-daily-lts-quantal-dkms

I then rebooted and saw a do not enter singh at the top of my screen, it say there has been a package that has not been install. Theres 2

Dynamic Kernel Module Support Framework 
and 
tool for simulating superuser privileges

If I try to install these I get 
The package system is broken 
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

details
The following packages have unmet dependencies:

oem-audio-hda-daily-lts-quantal-dkms: Depends: dkms (>= 1.95) but it is not installed

^^ That looks like my problem. Any solutions?

My fault for assuming you had dkms installed. :\
```
sudo apt-get install dkms
```

---

### Post by bucket81 on 2013-08-16
That did it!! 
So what exactly did I do?

---

### Post by Yellow Pasque on 2013-08-16
It installed the package, or do you actually have sound now?

---

