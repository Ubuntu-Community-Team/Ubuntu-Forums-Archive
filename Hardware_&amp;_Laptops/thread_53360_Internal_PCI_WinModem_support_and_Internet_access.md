---
title: "Internal PCI WinModem support and Internet access"
date: 2005-07-31
forum: Hardware &amp; Laptops
---

### Post by Banner65 on 2005-07-31
Hi.

Could someone advise me if Unbuntu Linux has Internal PCI WinModem support, and if so, could you advise me on which Internal PCI WinModem to use, please?

Secondly, could someone advise me on how to configure and use a dialup (WinModem) Internet connection, please?

Thank you.

David.

---

### Post by dmsynck on 2005-07-31
[QUOTE=Banner65]Hi.

Could someone advise me if Unbuntu Linux has Internal PCI WinModem support, and if so, could you advise me on which Internal PCI WinModem to use, please?

Secondly, could someone advise me on how to configure and use a dialup (WinModem) Internet connection, please?

Thank you.

David.[/QUOTE]
 Hello,

I could be wrong in my thinking, but I was under the impression that most linuxes don't support WinModems. Most all the install instructions and HOWTO's that I have read specifically state not to try and use a WinModem because they require software that cannot be duplicated by the open-source community due to lack of API's, documentation, etc. Hope this might answer your question.

---

### Post by az on 2005-07-31
Many or most winmodems have linux support

Use Scanmodem to identify the chiopset so that you can install the correct driver:

[https://wiki.ubuntu.com/forum/hardware/modem](https://wiki.ubuntu.com/forum/hardware/modem)


And then find the driver here:

[https://wiki.ubuntu.com/forum/hardware](https://wiki.ubuntu.com/forum/hardware)

---

### Post by dmsynck on 2005-07-31
[QUOTE=azz]Many or most winmodems have linux support

Use Scanmodem to identify the chiopset so that you can install the correct driver:

[https://wiki.ubuntu.com/forum/hardware/modem](https://wiki.ubuntu.com/forum/hardware/modem)


And then find the driver here:

[https://wiki.ubuntu.com/forum/hardware](https://wiki.ubuntu.com/forum/hardware)[/QUOTE]
 Ok, I guess that I am wrong on the WinModem issue. Sorry if I caused any confusion.

---

### Post by tdjokic on 2005-07-31
This site is very good too [http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/) 
Edit: I didn't say anything new: [https://wiki.ubuntu.com/forum/hardware/modem](https://wiki.ubuntu.com/forum/hardware/modem)  has this "my" site in it! :-)

---

### Post by Ptero-4 on 2005-07-31
[QUOTE=tdjokic]This site is very good too [http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/) 
Edit: I didn't say anything new: [https://wiki.ubuntu.com/forum/hardware/modem](https://wiki.ubuntu.com/forum/hardware/modem)  has this "my" site in it! :-)[/QUOTE]
 Be carefull with which PC and WinModem you got. Some PC's (those made in 2002 and later) come with winmodems that have a hardware based lock. If you boot from a non-MS operating system (e.x: Linux) the modem (even with it's drivers properly installed) will (depending on the modem make and model) ignore all dialout commands or begin dialing but simulate a "no carrier" (the phone is offline), or "negotiation with the peer failed" (your username or password is incorrect) error, which makes your dialout software hang the phone. I know 'cause my sistem owns an HP Pavilion PC with an Agere/Lucent Winmodem and I installed Ubuntu on that PC. I downloaded the ubuntu-restricted-modules as instructed in the ubuntu's Lucent install How-to guide and installed them following the guide's instructions to the letter, and rebooted (yes you need to reboot because to make the modem work you have to pass an option to the kernel and that is done at system bootup). Then I used pon to dial. The modem began to make it's familiar sound but it didn't connect. Upon looking at the pon log using plog I could see that the modem was hanging with that error that only happens with a bad password (I triple-checked the ISP login info and it's correct). By looking at some sites (I'm using my eMac to get to the internet) I read about this lock in the winmodems and the fact that it's used to prevent you from using the internet from any operating system that has been disapproved by Microsoft.

---

### Post by az on 2005-07-31
"I read about this lock in the winmodems and the fact that it's used to prevent you from using the internet from any operating system that has been disapproved by"

Never heard of it.  Please post a link.

It may be that you used the wrong driver or that the driver is for an older version of the particular chipset.  That is a problem with binary drivers.

Anyway, only a small percentage of winmodems can run with completely open source drivers.  The prebuilt binary drivers are made by the manufacturers.  This lock thing does not make sense.

---

### Post by Ptero-4 on 2005-08-04
[QUOTE=azz]"I read about this lock in the winmodems and the fact that it's used to prevent you from using the internet from any operating system that has been disapproved by"

Never heard of it.  Please post a link.

It may be that you used the wrong driver or that the driver is for an older version of the particular chipset.  That is a problem with binary drivers.

Anyway, only a small percentage of winmodems can run with completely open source drivers.  The prebuilt binary drivers are made by the manufacturers.  This lock thing does not make sense.[/QUOTE]
 I can't recall right now the site it was in but was linked in one of those news sites that allows you to see the news for free but hides the archived articles and only allows access to the archives to those who pay the suscription (WallStreet Journal and CNN do this) so probably by now it's already archived. I thought that you had heard of this 'cause the article said that this was an M$ lock and mentioned how it was bad for the OSS people. Also as for the modem, it's an Agere/Lucent one it's classified as a Lucent WinModem (rev 02) and IIRC I have seen other people having bad issues with that modem (My scanmodem output is similar to the one in several topics mentioning this modem) and I use Ubuntu Hoary with the drivers in the restricted-modules package. I installed them using this wiki: [https://wiki.ubuntu.com/forum/hardware/lucent](https://wiki.ubuntu.com/forum/hardware/lucent)

As for the lock not making sense. I read from the article that it was a M$ "DRM" thing. I thought that since. 1) M$ wants to crush Linux. 2) M$ have been approved by the US gov to do anything in the name of "combating piracy". 3) The US gov is stupid in this computer matters. 4) Dialup is still popular since broadband is still not accesible everywhere and broadband ISP are far more likelly to be hostille against Linux (and even OSX, MacOS). and 5) Using the web is one of the top reasons for using a computer and one of the top factors when choosing an OS. This kind of lock would make a lot of sense, specially to those greedy M$ guys.

---

