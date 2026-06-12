---
title: "Cannot enable Bluetooth (Ubuntu 11.10)"
date: 2012-04-22
forum: Hardware
---

### Post by phildogg on 2012-04-22
Hello,
I am trying to enable bluetooth on my laptop, but when I right click on the bluetooth icon along the top panel, I don't have the option of switching it on. It states "Bluetooth is disabled by hardware switch".

I think "Fn + F5" is how to hardware enable it, but it doesn't seem to work. After some extensive Internet searching, I've had no joy.

Some details:
```

phil@phil-comp:~$ sudo dmidecode | grep Version
[sudo] password for phil: 
    Version: Intel(R) Core(TM) i3-2367M CPU @ 1.40GHz
    Version: 8QET54WW (1.15 )
    Version: ThinkPad X121e
    Version: Not Available
    Version: Not Available
    SBDS Version: V1.0
```
```
phil@phil-comp:~$ rfkill list
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
``````

phil@phil-comp:~$ lsmod
...
bluetooth             166112  10 bnep,rfcomm
...
```Any help would be much appreciated.
Thanks:D

---

### Post by ahallubuntu on 2012-04-22
Do the rest of your function keys work?  It's very common for them NOT to work by default in Ubuntu (brightness keys for example).  You may have to edit your Grub default file and update Grub.  Depends on the exact model laptop you have.  If your brightness keys don't work, fix them and you should be able to enable Bluetooth.

If brightness keys DO work - then you've got some other weird issue.  What's the exact make/model of your laptop?

---

### Post by phildogg on 2012-04-23
Some of the Fn keys work and some don't.
The brightness, suspend & volume ones work. The others don't.

I have my laptop details in the 1st post. It's a Thinkpad X121e

---

### Post by feistybill on 2012-07-05
> **phildogg said:**
> Some of the Fn keys work and some don't.
The brightness, suspend & volume ones work. The others don't.

I have my laptop details in the 1st post. It's a Thinkpad X121e

I have the same laptop and the same problem. Bluetooth and wifi disabled by default on startup. Did you find a solution?

---

### Post by bohemian9485 on 2012-07-05
Hi phildogg can you paste the output of command
```
lspci
```?

Just want to know if your wireless chipset is Realtek or Broadcom so we can go from there.

---

