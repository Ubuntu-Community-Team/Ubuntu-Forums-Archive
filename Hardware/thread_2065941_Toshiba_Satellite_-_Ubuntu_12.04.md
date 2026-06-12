---
title: "Toshiba Satellite - Ubuntu 12.04"
date: 2012-10-03
forum: Hardware
---

### Post by georgep1993 on 2012-10-03
Hello there, i've recently purchased a Toshiba Satellite C850D-107 for my university work to go alongside my desktop. I have got Windows on desktop and then decided to install Ubuntu onto here as a complete install with no windows installation left on here so that i can easily learn to program in java just on the laptop and keep it separate from the Windows machine. After installing it, it would start to crash quite easily, after some time i learnt that the processor spiked when i would connect to Wi-Fi so im guessing some kind of update is making it over work. If anyone has an knowledge on the subject some help would be greatly appreciated. (Btw the processor is 1.4ghz...)

---

### Post by 2F4U on 2012-10-03
So just to be clear about this point, is connecting the laptop to WiFi making the laptop crash and is this reproducible? Or is it also crashing otherwise? Or are you saying that connecting the laptop to WiFi causes the CPU to spike and the crashes are a seperate problem?

---

### Post by georgep1993 on 2012-10-08
sorry about very late reply but had a few problems with the desktop as well. Im under the impression that connecting to the Wi Fi is making ubuntu automatically start updating. this is making the processor spike and for the whole thing to simply freeze and will stay that way for hours unless just rebooted.

---

### Post by Bucky Ball on 2012-10-08
Very odd. But the wifi is actually connecting okay? Have you got a cable and does it do the same thing when connecting with that? As alluded to by 2F4U, is the machine working okay apart from the wifi? If you leave wifi alone you are not having any other problems?

If you have not yet updated you need to so I'd get a cable in there and do that, then try again with the wifi. It might help.

---

### Post by georgep1993 on 2012-10-08
Yeah machine works fine when not connected to the internet.. i have just wired it in and am watching what its doing now. do you know of any way i can see what is updating in the background? if there is something?

---

### Post by Bucky Ball on 2012-10-08
There shouldn't be anything updating in the background! At least not by default. Open the update manager and do an update and click details while you're updating and that will show all.

You can also open a terminal and:

```
sudo apt-get update
```

That will show you everything in the terminal.

---

