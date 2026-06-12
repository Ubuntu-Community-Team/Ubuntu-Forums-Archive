---
title: "HP Laserjet drivers"
date: 2023-02-16
forum: Hardware
---

### Post by manin1952 on 2023-02-16
Hello,

I tryito install HP Laserjet 1020 drivers.
I downloaded HPLIP from [https://developers.hp.com/hp-linux-imaging-and-printing/gethplip](https://developers.hp.com/hp-linux-imaging-and-printing/gethplip)

I tried to install it, but during the process I get :

```
rror: Package install command failed with error code 100note: Some packages may not get installed on python3 due to distro incompatibilites


note: Please check for more information at http://hplipopensource.com/node/369
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? y
Running 'sudo apt-get install --assume-yes libjpeg-dev'
Please wait, this may take several minutes...
error: Package install command failed with error code 100



```

I try to install the package, but...

```
sudo apt-get install --assume-yes libtool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libjpeg-dev : Depends: libjpeg8-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.



```

Googling the above message unfortunately did not help me!!!

---

### Post by Autodave on 2023-02-16
Usually no need to download a driver from a website online.  HPLIP is available in the Software Center!

---

### Post by manin1952 on 2023-02-18
> **Autodave said:**
> Usually no need to download a driver from a website online.  HPLIP is available in the Software Center!

I installed drivers and the application, but it does not work.
Before I installed the hplip, the system recognised the printer, but it does not print.
In fact it did not to anything. The same now.
If the printer was broken, I would get an error message, right?
[IMG]https://drive.google.com/file/d/120o7tV4bnJfIIMvqiVMAPAq5xd6uTmF2/view?usp=sharing[/IMG]

---

### Post by Autodave on 2023-02-18
What exactly did you install?

---

### Post by manin1952 on 2023-02-18
ipp-usb
hplip-printer-app

---

### Post by manin1952 on 2023-02-18
ipp-usb
hplip-printer-app

---

### Post by mIk3_08 on 2023-02-18
Please run the command below in your terminal. Regards and cheer.
```
lsb_release -a
```

---

### Post by manin1952 on 2023-02-19
manin@manos-PC:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.5 LTS
Release:    20.04
Codename:    focal

---

### Post by brian_p on 2023-02-20
> **manin1952 said:**
> ipp-usb
hplip-printer-app

OK. Let's have some more solid information. What is

[LIST]
[*]The printer model?
[*]The connection method?
[*]Where did you get hplip-printer-app from and why?
[*]Where did you get ipp-usb from?
[/LIST]

---

### Post by manin1952 on 2023-02-25
> **brian_p said:**
> OK. Let's have some more solid information. What is

[LIST]
[*]The printer model?
[*]The connection method?
[*]Where did you get hplip-printer-app from and why?
[*]Where did you get ipp-usb from?
[/LIST]


HP Laserjet 1020
USB
I downloaded hplip-printer-app and ipp-usb from Ubuntu software because I read it in this link
[https://developers.hp.com/hp-linux-imaging-and-printing/gethplip](https://developers.hp.com/hp-linux-imaging-and-printing/gethplip)

---

