---
title: "Modem driver installed, but won't dial out"
date: 2006-01-02
forum: Hardware &amp; Laptops
---

### Post by trav1085 on 2006-01-02
I finally found a driver for my Conexant D480 MDC V.9x Modem from linuxant.com and it installed right, I also used scanModem to find my modem, it said it found my Modem but with the driver installed it won't dial, I have used "$ sudo pppconfig" to make a account, then "$ sudo pon telus" to connect. There is nothing.

I went to System>>Administration>>Networks and went to modem properties, typed in my account and phone number then set it to auto detect, it detected a modem on /dev/modem/, and after activating it, I close it and go back to the Networks option and then it is deactivated.

But I know my modem is on COM3, /dev/ttySS2.

I remember when I had RedHat Linux 7 installed on my old 486 and my modem was detected durring installation, but it wasn't a winmodem though...

---

### Post by towsonu2003 on 2006-01-13
try using wvdial to dial out. at least you'll see the errors...

---

### Post by behi on 2006-01-21
I have one Dell D600.but i loss my driver for model D480.please send this driver to my email [email]add.behrooz_z_20@yahoo.com[/email]
thanks alot

---

### Post by mesocool on 2006-06-10
[QUOTE=trav1085]I finally found a driver for my Conexant D480 MDC V.9x Modem from linuxant.com and it installed right, I also used scanModem to find my modem, it said it found my Modem but with the driver installed it won't dial, I have used "$ sudo pppconfig" to make a account, then "$ sudo pon telus" to connect. There is nothing.

I went to System>>Administration>>Networks and went to modem properties, typed in my account and phone number then set it to auto detect, it detected a modem on /dev/modem/, and after activating it, I close it and go back to the Networks option and then it is deactivated.

But I know my modem is on COM3, /dev/ttySS2.

I remember when I had RedHat Linux 7 installed on my old 486 and my modem was detected durring installation, but it wasn't a winmodem though...[/QUOTE]

I got the modem with the same problem, it doesn't dial at all..
Anyone got solution? ](*,)

---

