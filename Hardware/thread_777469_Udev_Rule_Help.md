---
title: "Udev Rule Help"
date: 2008-05-01
forum: Hardware
---

### Post by bcardarella on 2008-05-01
I have a Franklin Wireless CDU-680 mobile broadband USB stick. When it is hotplugged it defaults to a storage device (as it should) that contains the device drivers and such. To get the modem operational I have to manually run a script to change the mode of the device, then run another script to have wvdial connect the modem via ppp. I wrote a single script to do both, with a 5 second sleep in between to allow the device to change properly.

My script works, so I figured it would be nice if this script could be run automatically when the modem is hotplugged. I wrote a custom udev rule that I named:

9999-cmotech-modem.rules

I used udevinfo to identify the device. The rule works, the problem seems to be that my script is being run before the device is mounted to the system. I was under the impression that the numbers that start the file denote the load order of the rules. So I thought maybe the rules were being run in parallel so I put a 15 second sleep at the beginning of my script but it just seems when I hotplug the modem the script sleeps for 15 seconds, tries to change the mode of the device that doens't exist yet, sleeps for another 5 seconds, attempt to dial out with a device that doesn't exist, then the device is mounted to the file system.

Is there something I'm doing wrong? Is there some other way to force my script to be run after the device is mounted?

---

### Post by xe1ufo on 2008-07-18
I would LOVE to know what you are doing! My Franklin is only a storage device in Linux so far.

---

### Post by lswb on 2008-07-18
Could you post your udev rule and the script it is calling?

---

### Post by Vivaldi Gloria on 2008-07-19
> **bcardarella said:**
> Is there something I'm doing wrong? Is there some other way to force my script to be run after the device is mounted?

Files should be named xx-descriptive-name.rules, so may be there is a problem with your name 9999.

If it still fails then consider adding your script to /etc/rc.local as follows:

```
cd /path_of_your_script &
./script &
exit 0
```

Also please post your script here so that other people (including xe1ufo  above) can use it.

---

### Post by bcardarella on 2008-07-19
Unfortunately I don't have access to the files anymore. I set the CDU-680 on one of our employee's machines who works remotely. I will attempt to get the files on Monday and post the results here.

---

