---
title: "Need help with well a lot of stuff really..."
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by robertqadkins on 2009-07-01
Okay, i am new to linux. My first problem is that linux didn't detect my dial up modem when i installed ubuntu. Some help getting that set up would be great. Also I am trying to install wine from source. when I ./configure I get the error

configure: error: X development files not found. Wine will be built
without X support, which probably isn't what you want. You will need to install
development packages of Xlib/Xfree86 at the very least.
Use the --without-x option if you really want this.

Now before you suggest i use the apt, I have no way to connect to the internet in Ubuntu because of the whole modem issue.

Any advice would be great.

---

### Post by wojox on 2009-07-01
open a terminal and type

```
sudo wvdialconf
```

This should help with seeing what's up with modem.

---

### Post by sirhalos on 2009-07-01
Is it a External Modem? If so is it Serial or USB?

Is it Internal Modem? If so is it a WinModem/Softmodem or a regular Hardware Internal Modem?

---

### Post by robertqadkins on 2009-07-01
> **wojox said:**
> open a terminal and type

```
sudo wvdialconf
```This should help with seeing what's up with modem.


when i tried this it gave the the error 

command not found

---

### Post by robertqadkins on 2009-07-01
> **sirhalos said:**
> Is it a External Modem? If so is it Serial or USB?

Is it Internal Modem? If so is it a WinModem/Softmodem or a regular Hardware Internal Modem?


it is an internal modem, just not sure what the differences are. It is in a pci slot if that helps?

---

### Post by robertqadkins on 2009-07-01
any help at all anyone?

---

### Post by sirhalos on 2009-07-01
WinModem/Softmodem is just a small piece of hardware and the software does all the working of the device and tend to be rather cheap. WinModem is short for Windows Modem and for a long long time would only work in Windows machines. Softmodem stands for Software modem.

Normal internal modems have hardware that does everything for it.

For the best help we can provide please take the card out and try to find a model number and who the manufacture is for us. 

If it's a normal Hardware Internal modem that is an easy fix usually (it will think it's a serial modem).

If it's a WinModem/Softmodem it becomes much more difficult to help you and will be different for each brand and type.

---

