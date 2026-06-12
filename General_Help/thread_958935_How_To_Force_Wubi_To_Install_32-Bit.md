---
title: "How To Force Wubi To Install 32-Bit"
date: 2008-10-25
forum: General Help
---

### Post by Naro on 2008-10-25
I read the little description given in the FAQ, but could someone explain in more detail how to do it?  I've downloaded the Wubi installer and the 32 bit ISO version of Ubuntu, but I'm not sure what to do from there.

---

### Post by andrew_wilson on 2008-10-26
To get Wubi to install the 32-bit version of the Ubuntu iso, just put the iso in the same place as the Wubi .exe (e.g., put both on D:\).

The installer will automatically detect the iso (you have to use the same version iso as the installer, e.g. 8.04.1).  You'll know that the instaler is using the 32-bit iso you downloaded earlier because the installer will go through pretty quickly and not attempt to download the iso from the Internet.  If it does not detect the iso, you will see a dialog box that says it is retrieving a file from the Internet.

---

### Post by ago on 2008-10-26
[https://wiki.ubuntu.com/WubiGuide#Can%20I%20force%20Wubi%20to%20download%20and%20install%20a%2032%20bit%20version%20of%20Ubuntu?](https://wiki.ubuntu.com/WubiGuide#Can%20I%20force%20Wubi%20to%20download%20and%20install%20a%2032%20bit%20version%20of%20Ubuntu?)

---

### Post by Naro on 2008-10-26
> **andrew_wilson said:**
> To get Wubi to install the 32-bit version of the Ubuntu iso, just put the iso in the same place as the Wubi .exe (e.g., put both on D:\).

The installer will automatically detect the iso (you have to use the same version iso as the installer, e.g. 8.04.1).  You'll know that the instaler is using the 32-bit iso you downloaded earlier because the installer will go through pretty quickly and not attempt to download the iso from the Internet.  If it does not detect the iso, you will see a dialog box that says it is retrieving a file from the Internet.

So if both the ISO and Wubi installer are on my desktop it should automatically recognize it?

---

### Post by ago on 2008-10-26
yes, make sure you do not have several ISOs on the same folder.

---

