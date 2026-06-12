---
title: "Bluetooth Problems - Toshiba Satellite"
date: 2006-09-19
forum: Hardware &amp; Laptops
---

### Post by agentno4 on 2006-09-19
I have a Toshiba Satellite P105-S9312, which has built in bluetooth.  I am trying to get my Kensington bluetooth mouse to connect.  I am running a dual-boot of Ubuntu & Windows XP.  If I just start up log into Ubuntu:

```
$hcitool dev
Devices:
$

```

However, if I log into windows, turn on bluetooth radio, reboot, then log into Ubuntu:

```
$hcitool dev
Devices:
        hci0    xx:xx:xx:xx:xx:xx
$  

```

So, apparently Ubuntu is not turning on the bluetooth radio.  I read in one of the threads here that some people can turn on bluetooth on Toshibas with ```
$toshset -bluetooth on
```

Unfortunately, when I try that I get:
```
$sudo toshset -bluetooth on

required kernel toshiba support not enabled
``` 

I assume this is because my laptop has the Pheonix bios rather than the Toshiba bios, thus toshset will not run on my system. (at least I can't get it to.)  Does anybody know of another way to turn on bluetooth on a Toshiba without using toshset? Or maybe a way to get toshset to work? 

I would really like to be able to use my mouse without having to log into Windows first, since that is kind of a pain in the ***.  Any help would be greatly appreciated.

---

### Post by agentno4 on 2006-09-30
somebody?

---

### Post by /carlito on 2006-09-30
Is there no option in your bios to always enable bluetooth?

---

### Post by agentno4 on 2006-10-31
No, there is no option in the bios to always turn on the BT radio.

---

### Post by didobuntu on 2006-10-31
if the toshset is not in the repos, that means that it is integrated in the Bluetooth by default. 

click on the reset button of you Bluetooth device then quickly type the command "sudo hidd --search"

follox this [howto]("https://help.ubuntu.com/community/BluetoothSetup"), it worked for me.

---

### Post by Azriphale on 2007-06-16
For toshiba laptops with a phoenix BIOS, there is a kernel module that will enable you to use bluetooth. Instructions here:
[http://ubuntuforums.org/showthread.php?t=316358&highlight=toshiba+phoenix+bluetooth](http://ubuntuforums.org/showthread.php?t=316358&highlight=toshiba+phoenix+bluetooth)

---

### Post by Pronco on 2007-07-06
Hello,

How do I determine the Toshiba BOIS whether its Phoenix or Toshiba BOIS ?

Thank you.

---

