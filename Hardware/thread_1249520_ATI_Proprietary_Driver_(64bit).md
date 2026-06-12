---
title: "ATI Proprietary Driver (64bit)"
date: 2009-08-25
forum: Hardware
---

### Post by rfkrocktk on 2009-08-25
Now, before I begin, I **know** that since this is a proprietary driver, I won't get any support from the open source community on it. However, I needed some help with my xorg.conf file, and since X is open source, I believe that this is a good place to ask :)

Installing the latest ATI Proprietary Driver 9.8 (on Ubuntu Jaunty 9.04 64bit running ext4) goes fine, except for one thing. It wipes my xorg.conf file of basically everything. Before upgrading to the proprietary driver last night, I was using the open source ATI driver, which was working decently. Now, I'm basically not using a driver since my xorg.conf file is toast.

How can I configure my xorg.conf to use the open source driver again? Or, even better, since the proprietary driver DID install, how can I configure X to use it? Any and all help is extremely appreciated :)

---

### Post by Yellow Pasque on 2009-08-25
To generate a fresh xorg.conf (will overwrite your existing one):
```
sudo dpkg-reconfigure xserver-xorg
```
To configure it for the proprietary driver:
```
sudo aticonfig --initial -f
```

If you ever want to return to the open-source driver, make sure you purge the proprietary driver from your system: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver?action=show](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver?action=show)

---

### Post by rfkrocktk on 2009-08-26
Running "sudo aticonfig --initial -f" yields "aticonfig: No supported adapters detected"

I tried reconfiguring xorg, but I don't think it did anything, though I'll have to check on it.

---

### Post by Yellow Pasque on 2009-08-26
What kind of ATI card do you have? In Jaunty, only RadeonHD cards can use the proprietary drivers.

---

### Post by rfkrocktk on 2009-08-26
It's like a Radeon 200M laptop card. So I guess I'm out of luck then, right? 

Any way to return to the open source driver and get compiz working again?

---

### Post by Yellow Pasque on 2009-08-26
To return to pen-source driver: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver?action=show#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver?action=show#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

### Post by tommcd on 2009-08-27
To run the command:
```
sudo dpkg-reconfigure xserver-xorg
```
it is better if you run the command without the X server running. After running the commands to purge the ATI driver, boot to recovery mode, choose to drop to a command line system, then run the dpkg-reconfigure xserver-xorg command, then reboot.
You can also try booting to recovery mode and choose the option **xfix fix video**.

---

