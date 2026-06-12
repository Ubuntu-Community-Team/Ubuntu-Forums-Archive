---
title: "Assistance Installing Nvidia GeForce 7600 Driver"
date: 2006-11-16
forum: Hardware &amp; Laptops
---

### Post by puffidredz on 2006-11-16
I just installed Ubuntu Dapper and when I go to System, Preferences, Screen Resolution, the highest resolution I have is 1024x768. I have an AMD64 box so I downloaded Linux AMD64/EM64T: 1.0-9629 file from the Nvidia site, ran the file using command "sudo sh NVIDIA-Linux-x86_64-1.0-9629-pkg2.run", entered my password and in terminal it says,  "Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86_64 1.0-9629......". The installation launches and then I get error:

"NVIDIA Software Installer for Unix/Linux: ERROR: Unable to find the system utility `ld`; please make sure you have the package 'binutils' installed.  If you do have binutils installed, then please check that `ld` is in your PATH."

I am not all that familiar with Linux but it seems like I'm doing something wrong. I have the file downloaded to my username home folder /Downloads. Can someone please help me as to what I should do to install these drivers? 

Thank you in advance
Puffidredz

---

### Post by tubasoldier on 2006-11-16
```
sudo apt-get install binutils
```

and then try it again.

---

### Post by claydoh on 2006-11-16
have you tried the nvidia-glx package available to Ubuntu?
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by puffidredz on 2006-11-17
> **tubasoldier said:**
> ```
sudo apt-get install binutils
```

and then try it again.

Did that and now I get error:

ERROR: You appear to be running an X server; please exit X before
         installing.  For further details, please see the section INSTALLING
         THE NVIDIA DRIVER in the README available on the Linux driver
         download page at [www.nvidia.com](www.nvidia.com).

I don't know how to exit X. How do I do that?

---

### Post by NotIt on 2006-11-17
Press ctrl-alt-F1 to get to a terminal and type:
```
sudo /etc/init.d/gdm stop
```

---

### Post by puffidredz on 2006-11-18
> **NotIt said:**
> Press ctrl-alt-F1 to get to a terminal and type:
```
sudo /etc/init.d/gdm stop
```

I tried this and I got as far as one screen in the installation and I got an error that I needed to install "gcc". Where can I download this sw for Ubuntu?

---

### Post by bikeboy on 2006-11-19
Hope I'm not too late to help you.

```
sudo apt-get install build-essential
```

---

