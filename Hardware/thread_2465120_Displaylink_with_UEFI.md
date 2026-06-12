---
title: "Displaylink with UEFI"
date: 2021-07-22
forum: Hardware
---

### Post by ahpitre on 2021-07-22
I just installed Ubuntu 20.1 LTS on a Lenovo IdeaPad 5 laptop. I use a Pluggable micro USB docking station which  connects my 2 4K monitors. When I installed Ubuntu I disabled UEFI secure boot, this allowed proper installation of DisplayLink Ubuntu driver. Computer can now use 3 monitors (built-in plus the 2 external monitors connected to USB dock). Issue is that the Displaylink driver is unsigned, when I enable UEFI secure boot on BIOS then Displaylink driver doesn't load (because it's not signed), leaving me w/o my 2 external monitors. I wouldn't like use my computer w/o UEFI Secure boot as it's more prone to viruses (I dual boot between Ubuntu and Windows 10). This issue seems to be ongoing for several years (the makers of Display link have never provided a Linux signed driver). Any recommendations are welcomed.

---

### Post by CatKiller on 2021-07-23
> **ahpitre said:**
> Issue is that the Displaylink driver is unsigned, when I enable UEFI secure boot on BIOS then Displaylink driver doesn't load (because it's not signed), leaving me w/o my 2 external monitors.
The solution is to sign the driver modules yourself, and then to tell your UEFI that you trust your own signature. The signature is called a "Machine-Owner's Key," and the process is called "enrolling a MOK." It's not super hard, just a bit fiddly; I did it once to try it out. You should be able to find instructions easily enough.

---

### Post by cryptearth on 2021-07-23
Solution already suggested. In fact - when you do something like installing nvidia graphics drivers the "installer" does it for you: you get a prompt to set a password (at least 8 digits) and when you reboot MOKmanager is started to let you "enroll" this key.
Re-doing this by hand should not by that hard:
- generate your own keypair
- sign the driver with it
- add the public key to mokmanager to enroll it on next boot
First and third I can even tell you from top of my head - as for second: I'm sure there're several tutorials how to sign your driver with a key.

---

### Post by ahpitre on 2021-07-23
I followed all steps, rebooted, entered password for MOK signing, rebooted, but nothing happened, Ubuntu is still using the unsigned version which only works in Non-UEFI mode.

---

### Post by cryptearth on 2021-07-23
Well, you have to install the signed driver in places where the unsigned files are installed.
I suspect you built the driver - signed it - but then installed the unsigned one instead of the signed version - just a guess.

---

### Post by ahpitre on 2021-07-23
How can I verify which version is installed? How can I remove the unsigned version? When you restart you get the MOK menu, there are 2 option MOK and MOK from file, which one should I choose?

---

### Post by cryptearth on 2021-07-23
When you get he MOK screen you select the option to enroll the key added to the enroll list and confirm it.
If you don't get an option for enrollment you not correctly added the new key to the enroll list.

---

### Post by ahpitre on 2021-07-26
Thanks to all for your valuable input. This is how I was able to finally solve this :
1. Reinstall Ubuntu (again). Use the option to install 3rd party display and other adapters, this is key.
2. Connect to WiFi. Continue installation.
3. At the end of installation enter the MOK password and confirm it.
4. Reboot to MOK entry screen, select Enter MOK, enter password, reboot.
5. Now, install Display Link (there are several steps first including updating Ubuntu (running sudo apt... ), install DKMS, install other libraries.
6. Install DisplayLink driver (download from Display Link website, also available in some Ubuntu sites/forums). Note, this driver is not signed, and there is no need to sign it (where I always failed as signing the driver made it not install as the checksum changed).
7. Reboot, this allows Linux to recognize the DisplaLink driver even though it's unsigned.
8. Enjoy! This surely was tedious and took me multiple attempts at installing LINUX including many versions (Ubuntu, Arch, Elementary, etc.). So far, this is the only install that has worked for me.

---

