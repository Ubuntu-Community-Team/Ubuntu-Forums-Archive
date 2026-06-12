---
title: "Alfa AWUS1900 wifi adaptor"
date: 2024-11-27
forum: Hardware
---

### Post by lash508 on 2024-11-27
Hi

I'm trying to install the Alfa Awus1900 wireless adapter on Ubuntu 24.04.1 LTS. I've downloaded the 
         Realtek rtl8814au driver       from github. I've unziped the driver and followed these commands:


# build & install
```
$ git clone [https://github.com/aircrack-ng/rtl8814au.git](https://github.com/aircrack-ng/rtl8814au.git)
$ cd rtl8814au
$ make
$ make install.

warning: the compiler differs from the one used to build the kernel
  The kernel was built by: x86_64-linux-gnu-gcc-13 (Ubuntu 13.2.0-23ubuntu4) 13.2.0
  You are using:           gcc-13 (Ubuntu 13.2.0-23ubuntu4) 13.2.0


Does anyone know what the solution is?

Thank you

---

### Post by Yellow Pasque on 2024-11-27
The warning can be ignored. You need to run make install with sudo:
```
sudo make install
```
You also need to make sure you sign the built module with mokutil (or disable SecureBoot in BIOS/EFI) so it loads.

---

### Post by Yellow Pasque on 2024-11-28
Actually, you are better off using:
```
make 
sudo make dkms_install
```
.. or else you will have to build/install rtl8814au module every time you get a kernel update.

---

### Post by lash508 on 2024-11-29
Hi

Thanks for your reply. I've disabled secure boot and it works now.

---

### Post by lash508 on 2024-11-30
> **Yellow Pasque said:**
> The warning can be ignored. You need to run make install with sudo:
```
sudo make install
```
You also need to make sure you sign the built module with mokutil (or disable SecureBoot in BIOS/EFI) so it loads.

How do I sign the module?

---

### Post by Yellow Pasque on 2024-11-30
> **lash508 said:**
> How do I sign the module?

With mokutil. Don't ask me for specifics. I personally think SecureBoot is more hassle than it's worth and don't use it.

---

