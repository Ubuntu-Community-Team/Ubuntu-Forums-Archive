---
title: "How to configure a Canon LBP 3010"
date: 2019-03-01
forum: Hardware
---

### Post by benmam on 2019-03-01
I am a newbie in Ubuntu. My problem is that I have a printer Canon  LBP 3010. I tried everything to install it, but no use. The printer is  indicated by the system, but can't find its driver. I tried a script for  some LBP canon printer, but I can't print through a message said  printing completed. I think the issue with CUPS because I often get cups  -server-bad-request. I got tired.
  My question is what am I able to configure my printer as a network printer. If yes how is the method in details?

---

### Post by brian_p on 2019-03-01
Download a Canon package from

[https://www.canon.co.uk/support/consumer_products/products/printers/laser/i-sensys_lbp3010.html?type=drivers&language=&os=linux](https://www.canon.co.uk/support/consumer_products/products/printers/laser/i-sensys_lbp3010.html?type=drivers&language=&os=linux)

Extract the files in the package with

```
tar zvxf linux-capt-.........tar.gz
```

Change to the Debian directory in the extracted directory:

```
cd cd linux-capt-............../64-bit_Driver/Debian/
```

You will see two files beginning with cndrvcups- and ending with .deb. Install them with

```
dpkg -i cndrvcups-common.......amd64.deb
```
```
dpkg -i cndrvcups-capt.......amd64.deb
```

Set up the printer as described in parts 10, 11 or 13 at

[https://wiki.debian.org/PrintQueuesCUPS](https://wiki.debian.org/PrintQueuesCUPS)

---

### Post by benmam on 2019-03-02
hello, every body. thankyou for your reply. i am afriad the method above didnt work. idon t know why.

---

### Post by brian_p on 2019-03-02
At what point did the installing procedure fail? There are four commands given; did any of them not work?

---

### Post by brian_p on 2019-03-02
To make this clear: at which point did "didnt work" not work? During the installation or afterwards?

---

### Post by benmam on 2019-03-02
i mean by it didnt work that when trying test page print. the message appears print completed , printer actually no print

---

### Post by brian_p on 2019-03-02
So - the software was correctly installed. You just need to set it up. Lots of detail at

[https://wiki.debian.org/PrintQueuesCUPS](https://wiki.debian.org/PrintQueuesCUPS)

---

