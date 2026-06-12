---
title: "How to install the correct kernel source file?"
date: 2008-08-23
forum: General Help
---

### Post by xiaoyong on 2008-08-23
When I execute 
```
sudo apt-get install build-essential linux-headers'uname-r linux-source-'uname-r
```,

I got the message,
```
E: Couldn't find package linux-headersuname-r linux-source-uname-r

```

Is there something wrong?

---

### Post by Rocket2DMn on 2008-08-23
Yes, you don't use the apostrophe to run a command within a command, you use the backtick, it's the same key as ~.
```
`
```
So
```
sudo apt-get install build-essential linux-headers-`uname -r` linux-source-`uname -r`
```

---

### Post by tommcd on 2008-08-23
Or if you are in doubt about the exact name of a  package (you have to type it exactly if installing from terminal, as Rocket2DMn illustrated) just search for it in synaptic. For example, you could have searched for linux-headers in synaptic and it would have come up. Just pick the correct one for the kernel you are using, since the ones for older kernels are there as well.

---

### Post by crayon.stylo on 2010-11-29
Hello,
I downloaded Kernel linux source 2.6.36.1 and tried to install by using terminal.But it is something wrong when it installed.
It was said Access denied permission and unable locate package....
And then i tried another way that is directly to download via terminal but it didn't work too....
I wanna use internet by dial up connection.That's why i need kernel sources.My USB Modem is AZTECH UM3100.....

I am new user of ubuntu 10.10
Please help me....

---

### Post by tommcd on 2010-11-29
> **crayon.stylo said:**
> 
I downloaded Kernel linux source 2.6.36.1 and tried to install by using terminal.But it is something wrong when it installed.
It was said Access denied permission and unable locate package....
Where did you download the kernel from? You can get Ubuntu kernel packages as easy to install .deb packages here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
> **crayon.stylo said:**
> 
I wanna use internet by dial up connection.That's why i need kernel sources.My USB Modem is AZTECH UM3100.....

Do you have reason to believe that the 2.6.36.1 kernel will have the driver for your usb modem? Perhaps there is a driver for it that you could download and install instead of having to upgrade the kernel. If you have a link to the proper driver for the modem, post it here and hopefully we can help you get it installed.

And welcome to the Ubuntu forums!

---

