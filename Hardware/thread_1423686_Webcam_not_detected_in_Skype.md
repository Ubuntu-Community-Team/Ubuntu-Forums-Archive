---
title: "Webcam not detected in Skype"
date: 2010-03-07
forum: Hardware
---

### Post by delfabc on 2010-03-07
Hi all,

I've connected a "Microdia TwinkleCam USB camera" (used lsusb to check the system detected it) and have verified it's working with the software Cheese.

Problem is, when I go into 'Skype > Options > Video Devices' the 'Select Webcam' button is empty and when I click it the webcam isn't listed.

I've tried rebooting my comp, but have had no luck.

Ideas please? Thanks.

I'm using Ubuntu 9.10 and have done a software update.

---

### Post by Aruna Hewapathirane-&#3461;&#3515;&#3536;&#3499; on 2010-03-07
> **delfabc said:**
> Hi all,

I've connected a "Microdia TwinkleCam USB camera" (used lsusb to check the system detected it) and have verified it's working with the software Cheese.

Problem is, when I go into 'Skype > Options > Video Devices' the 'Select Webcam' button is empty and when I click it the webcam isn't listed.

I've tried rebooting my comp, but have had no luck.

Ideas please? Thanks.

I'm using Ubuntu 9.10 and have done a software update.

try this in a terminal : LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype "$@"

---

### Post by delfabc on 2010-03-07
> **Aruna Hewapathirane-&#3461 said:**
> try this in a terminal : LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype "$@"

Thanks. I tried what you suggested, but it gave me the following message:
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

I opened Skype, and now the device "SN9C1xx PC Camera (/dev/video0) is listed, but when I test it, it still doesn't work.

Any other ideas?

---

### Post by Rumpty on 2010-03-07
Make sure there is no software that might use the camera, apart from Skype, running

---

### Post by delfabc on 2010-03-07
> **Rumpty said:**
> Make sure there is no software that might use the camera, apart from Skype, running

Thx Rumpty. Checked. No other software is running. I tried doing a fresh reboot and just kick off Skype as my first app, but no go.

Ideas?

---

### Post by Aruna Hewapathirane-&#3461;&#3515;&#3536;&#3499; on 2010-03-10
> **delfabc said:**
> Thanks. I tried what you suggested, but it gave me the following message:
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

I opened Skype, and now the device "SN9C1xx PC Camera (/dev/video0) is listed, but when I test it, it still doesn't work.

Any other ideas?

Install Virtual box, install your preferred operating system ( xp,vista, whatever..) then install skype. Should work.

---

### Post by Aruna Hewapathirane-&#3461;&#3515;&#3536;&#3499; on 2010-03-10
> **delfabc said:**
> Thanks. I tried what you suggested, but it gave me the following message:
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

I opened Skype, and now the device "SN9C1xx PC Camera (/dev/video0) is listed, but when I test it, it still doesn't work.

Any other ideas?

Try installing the 32bit libraries ```
sudo apt-get install lib32v4l-0
``` then ```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype
```

---

### Post by delfabc on 2010-03-14
> **Aruna Hewapathirane-&#3461 said:**
> Try installing the 32bit libraries ```
sudo apt-get install lib32v4l-0
``` then ```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype
```

Thanks. Tried that and got this:

carlo@carlo-desktop:~$ sudo apt-get install lib32v4l-0
[sudo] password for carlo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lib32v4l-0 is already the newest version.
lib32v4l-0 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
carlo@carlo-desktop:~$ LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skypecarlo@carlo-desktop:~$ ^C
carlo@carlo-desktop:~$ 

Then Skype opened but 'No device [was] found'. So no change.

---

### Post by Aruna Hewapathirane-&#3461;&#3515;&#3536;&#3499; on 2010-03-16
> **delfabc said:**
> Thanks. Tried that and got this:

carlo@carlo-desktop:~$ sudo apt-get install lib32v4l-0
[sudo] password for carlo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lib32v4l-0 is already the newest version.
lib32v4l-0 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
carlo@carlo-desktop:~$ LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skypecarlo@carlo-desktop:~$ ^C
carlo@carlo-desktop:~$ 

Then Skype opened but 'No device [was] found'. So no change.

okay... let's do this: 
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype "$@"

```The ""$@" at the end IS **important** - please cut and paste _**exactly**_ as shown above in to a terminal. Once skype loads go to options->video->test... wait a little while and you should see things start to work. Good luck.

---

### Post by delfabc on 2010-03-17
> **Aruna Hewapathirane-&#3461 said:**
> okay... let's do this: 
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype "$@"

```The ""$@" at the end IS **important** - please cut and paste _**exactly**_ as shown above in to a terminal. Once skype loads go to options->video->test... wait a little while and you should see things start to work. Good luck.

Hi,

Thanks but the following happened:

carlo@carlo-desktop:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype "$@"
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

It then opened Skype, and there is no device located under webcams.

What could it be?

Cheers,
Carlo

---

