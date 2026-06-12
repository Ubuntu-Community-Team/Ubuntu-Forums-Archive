---
title: "&quot;Hardware Drivers&quot; gui won't activate madwifi driver -- 9.04 Jaunty"
date: 2009-05-02
forum: Hardware
---

### Post by pi3832 on 2009-05-02
@

---

### Post by pi3832 on 2009-05-03
@

---

### Post by MSIC1 on 2009-05-07
Having the same issue here on my Acer Aspire One. Will post back if i find a solution.

---

### Post by khaije1 on 2009-05-08
[disclaimer: this worked for me, but ymmv. I ran through it pretty quickly so there may be a better way to accomplish the same things]

summary:
it looks like the ath_pci modules are blacklisted even after the madwifi-tools package is installed.

I'm not sure how to fix jockey so it operates correctly in this case but i can tell you its not difficult to fix using the command line. Once I understood the problem it took about five minutes to remedy.


-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
explanation of the problem:

 - ath5k and the madwifi drivers dont always play nice together, so its pretty much a choice between one or the other.

 - ubuntu went with ath5k by default because it is free software. Madwifi is mostly free but still has some non-free dependencies.

 - part of getting ath5k to work means making sure that the madwifi driver doesnt load. the madwifi kernel driver/module/object is called ath_pci.ko 

 = therefore we are going to reverse the blacklist on ath_pci and add one to ath5k

 = we are going to add the madwifi-tools package, 'un-block' ath_pci , block ath5k, set ath_pci to load on boot, and then restart the networking service


-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
guidance:

1. add madwifi-tools...
```
sudo aptitude install madwifi-tools
```

2. un-blacklist ath_pci...
 - find the files that mention ath_pci
```
grep -i ath_pci /etc/modprobe.d/*
```
 - - on my system this was blacklist-ath_pci.conf and madwifi.conf
 - - anywhere you see a line that says 'blacklist ath_pci' change it to '#blacklist ath_pci' ```
sudo nano /etc/modprobe.d/blacklist-ath_pci.conf
```

3. blacklist ath5k...
 - do the opposite step #2 for the ath5k entries in the /etc/modprobe.d directory
 
4. set ath_pci to load on boot...
 - ```
sudo nano /etc/modules
```
 - - type 'ath_pci' (without the quotes) on new blank line in the file and save it.
 - ```
sudo modprobe ath_pci
``` to bring the module into the kernel now and test.

5. restart the networking service...
```
sudo /etc/init.d/networking restart
``` OR simply reboot


-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
conclusion:

your device should now be working though you'll still need to configure it according to your wlan's settings.

cheers,

---

### Post by pi3832 on 2009-05-09
@

---

### Post by markus42 on 2009-05-18
I discovered a simpler way of activating madwifi without editing configuration files.

Context: I run a Thinkpad T40p using Kubuntu 9.04 (Jaunty). The ath5 driver failed to connect to a WEP secured network. The networking plasmoid asked for the credentials again and again even though they were correct. I installed madwifi-tools as described above. Using the Ubuntu "Hardware Drivers" application (found in the programme menu), it was not possible to activate madwifi (clicking the button had no effect).

Strangely, this problem vanished when starting "jockey-kde" directly from a console. The application looked just like what you get with "Hardware Drivers" but the "Activate" button worked in this case. I restarted the machine to get all the drivers loaded properly (though one might have achieved this manually using "modprobe", too). WLAN now works properly.

---

### Post by markus42 on 2009-05-19
I noted that after suspending the computer (hibernate or sleep), the WLAN again fails, just like it did when using the ath5k_pci. A workaround for me was to unload and reload the ath_pci driver:

```
sudo modprobe -r ath_pci
sudo modprobe ath_pci
```

Maybe this could be automated by tweaking the suspend configuration.

---

### Post by YasirMX on 2009-07-21
> **khaije1 said:**
> [disclaimer: this worked for me, but ymmv. I ran through it pretty quickly so there may be a better way to accomplish the same things]

summary:
it looks like the ath_pci modules are blacklisted even after the madwifi-tools package is installed.

I'm not sure how to fix jockey so it operates correctly in this case but i can tell you its not difficult to fix using the command line. Once I understood the problem it took about five minutes to remedy.


-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
explanation of the problem:

 - ath5k and the madwifi drivers dont always play nice together, so its pretty much a choice between one or the other.

 - ubuntu went with ath5k by default because it is free software. Madwifi is mostly free but still has some non-free dependencies.

 - part of getting ath5k to work means making sure that the madwifi driver doesnt load. the madwifi kernel driver/module/object is called ath_pci.ko 

 = therefore we are going to reverse the blacklist on ath_pci and add one to ath5k

 = we are going to add the madwifi-tools package, 'un-block' ath_pci , block ath5k, set ath_pci to load on boot, and then restart the networking service


-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
guidance:

1. add madwifi-tools...
```
sudo aptitude install madwifi-tools
```2. un-blacklist ath_pci...
 - find the files that mention ath_pci
```
grep -i ath_pci /etc/modprobe.d/*
``` - - on my system this was blacklist-ath_pci.conf and madwifi.conf
 - - anywhere you see a line that says 'blacklist ath_pci' change it to '#blacklist ath_pci' ```
sudo nano /etc/modprobe.d/blacklist-ath_pci.conf
```3. blacklist ath5k...
 - do the opposite step #2 for the ath5k entries in the /etc/modprobe.d directory
 
4. set ath_pci to load on boot...
 - ```
sudo nano /etc/modules
``` - - type 'ath_pci' (without the quotes) on new blank line in the file and save it.
 - ```
sudo modprobe ath_pci
``` to bring the module into the kernel now and test.

5. restart the networking service...
```
sudo /etc/init.d/networking restart
``` OR simply reboot


-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
conclusion:

your device should now be working though you'll still need to configure it according to your wlan's settings.

cheers,

I blacklisted ath_pci and am using the original driver provided by linux and have been able to activate it. I was facing the prob "could not connect" and it kept prompting for WPA key. My problem was solved when I installed wi-cd and got rid of network manager.. Now, everything's fine :):guitar:

---

### Post by drpjkurian on 2009-08-02
Hi Khaijel

I am very thankful for your posting related to madwifi installation in Kubuntu jaunty. Since i am new to linux, I was not able to understand the steps 2 and three.
Will you please explain it to me.

Thank you in advance
Dr Kurian

---

