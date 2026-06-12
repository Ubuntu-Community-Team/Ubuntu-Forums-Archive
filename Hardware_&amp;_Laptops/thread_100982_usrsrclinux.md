---
title: "/usr/src/linux"
date: 2005-12-08
forum: Hardware &amp; Laptops
---

### Post by lost2 on 2005-12-08
Hi all,

I am trying to compile a USB modem driver on edubuntu 5.10 but got '/usr/src/linux: no such file or directory. Stop.' error.
/usr/src exists but it's empty.

Any help ?

Thanks.

---

### Post by Sutekh on 2005-12-08
I think to do this (compile drivers) you will need the kernel headers, for the kernel that you are using.

To download your kernel headers you will need to determine your kernel version; at a command line type
```

uname -r

```
You will get something like **2.6.12-10-386**. You would need to then download the headers using
```

sudo apt-get install linux-headers-**2.6.12-10-386**

```
Of course if your kernel version is different, just adjust that code.

You could also do this in Synaptic just search for "headers" and select to install the correct version.

---

### Post by lost2 on 2005-12-08
Thank you sutekh.

... but how do I 'apt-get install linux-headers-2.6.12-10-386' if I do not have any modem working on ubuntu ??
Is there any other way to download kernel headers ? Can I download via Windows, save it and after boot from ubuntu cp it to /usr/src ??

---

### Post by Sutekh on 2005-12-08
[QUOTE=lost2]Thank you sutekh.

... but how do I 'apt-get install linux-headers-2.6.12-10-386' if I do not have any modem working on ubuntu ??
[/QUOTE]
Doh I'm such an idiot.  The kernel headers should be on the installation CD.  Synaptic can be directed to use a CD-ROM as a repository, so you could try that first. 

If not there is a website that has all the ubuntu packages listed. [http://packages.ubuntu.com/]("http://packages.ubuntu.com/"), you can search for the one you need here.

---

### Post by lost2 on 2005-12-08
Thank you. Tomorrow I will try instalation CD first, because now it's 02:14 AM.
I hope to get this issue solved ;)

---

### Post by lost2 on 2005-12-09
Hi Sutekh,

Here I am posting. This time on Ubuntu !!  :smile: 
just to say that I did not compile my USB driver but, instead, I bought a new one !
It's a Huawei MT882 eth/usb adsl modem router.
This time was easy (just config it and ... voila !)
Now, I can think about going wireless too !

Thanks anyway.
Bye

BTW: I am from Portugal. What about you ?

---

