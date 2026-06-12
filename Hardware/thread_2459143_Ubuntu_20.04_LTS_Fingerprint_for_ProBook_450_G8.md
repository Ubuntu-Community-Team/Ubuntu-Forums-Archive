---
title: "Ubuntu 20.04 LTS: Fingerprint for ProBook 450 G8"
date: 2021-03-11
forum: Hardware
---

### Post by iamtodor on 2021-03-11
Hello guys,

I have the fingerprint area on my new laptop ProBook 450 G8, but the issue is I cannot use it.
I've checked few thread such as [https://askubuntu.com/questions/1244053/how-to-activate-fingerprint-on-ubuntu-20-04-for-login](https://askubuntu.com/questions/1244053/how-to-activate-fingerprint-on-ubuntu-20-04-for-login)

Here is the output from the lsusb command:
```

user@user-HP:~$ lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 04f3:0c5e Elan Microelectronics Corp. ELAN:ARM-M4
Bus 003 Device 002: ID 0408:5374 Quanta Computer, Inc. HP HD Camera
Bus 003 Device 004: ID 8087:0026 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Here is the output from what I've tried from the page [https://launchpad.net/~fingerprint/+archive/ubuntu/fprint](https://launchpad.net/~fingerprint/+archive/ubuntu/fprint)
```

user@user-HP:~$ sudo apt-get install libfprint0 fprint-demo libpam-fprintd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libfprint0
E: Unable to locate package fprint-demo

```

I've checked the thread on the official HP forum: [https://h30434.www3.hp.com/t5/Notebook-Software-and-How-To-Questions/Ubuntu-20-04-LTS-vs-HP-probook-440-g7-fingerprint-issue/td-p/7756390](https://h30434.www3.hp.com/t5/Notebook-Software-and-How-To-Questions/Ubuntu-20-04-LTS-vs-HP-probook-440-g7-fingerprint-issue/td-p/7756390)
I assume with new ProBook G8 I have the same issue - they just don't support fingerprint on OS other than Windows.

Here is the output of Hardware Probe: [https://linux-hardware.org/?probe=e26961f015](https://linux-hardware.org/?probe=e26961f015) if it worth to be mentioned.

Is there anything I can install to have the opportunity to use fingerprint with this laptop and ubuntu 20.04?

If I miss something, let me know I will try to provide as much information as I can as fast as I can

---

### Post by TheFu on 2021-03-11
Fingerprint devices are poorly supported because the vendors don't make Linux drivers for it.  Complain to the vendor. Complain to HP. Be vocal.  In the future, vote with your money.

I have an Asus laptop with a fingerprint reader. It isn't supported either.  For me, it is more of a curiosity than anything else, since I wouldn't use it for security reasons.  All sorts of problems with fingerprint readers when it comes to security.

---

