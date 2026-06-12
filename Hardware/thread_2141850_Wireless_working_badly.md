---
title: "Wireless working badly"
date: 2013-05-03
forum: Hardware
---

### Post by frohfroh on 2013-05-03
Good night,
I am not 100% sure about this one. The wireless worked fine in 12.10, but it is "weak" in 13.04. Basically it does does not work as far from the wireless modem as before, it takes a long time to connect and it is slow. The only way to use is to stay one meter away from the modem.
The same notebook works fine with another operating system and other computers also, so I guess it is not the Internet connection or the wireless network. 
Could anybody please help me? I'll have to give up on ubuntu otherwise

---

### Post by ahallubuntu on 2013-05-03
~

---

### Post by kurt18947 on 2013-05-04
I agree with ahallubuntu.  Why not go back to 12.04?  That's supported 'til 2017 and the next LTS will be 14.04.  But I'm curious, what adapter do you have?  If internal, in a terminal type "lspci", if external "lsusb".  A somewhat common problem has to do with encryption and disabling hardware encryption helps.

---

### Post by frohfroh on 2013-05-04
Actually, I did not really upgraded to 13.04. I formated the partition and installed it when my 12.10 just stopped working completely after "important security updates"... 

from lspci I get 

0d:00.0 Network controller: Ralink corp. RT5390 [802.11 b/g/n 1T1R G-band PCI Express Single Chip]


is that what you were looking for?
I am not sure about hardware encryption... Is it hard disk encryption? I definitely did not enable it during Ubuntu installation.

---

### Post by kurt18947 on 2013-05-04
> **frohfroh said:**
> Actually, I did not really upgraded to 13.04. I formated the partition and installed it when my 12.10 just stopped working completely after "important security updates"... 

from lspci I get 

0d:00.0 Network controller: Ralink corp. RT5390 [802.11 b/g/n 1T1R G-band PCI Express Single Chip]


is that what you were looking for?
I am not sure about hardware encryption... Is it hard disk encryption? I definitely did not enable it during Ubuntu installation.

Yes.  I have a USB adapter using a Ralink RT53**7**0 chip.  And yeah, it's weak.  Same USB port same location same orientation, an AR9271 based adapter or a RealTek 8192SU adapter will show 135 - 150 Mb./sec.  The Ralink RT5370 will show 52 Mb./sec.  Link quality and signal level are lower with the RT5370 but not as much as the Mb./sec. spread would lead me to expect.  I'm  guessing the native RT53** driver just isn't that efficient.  I only have the one Ralink adapter and I got it for cheep on Ebay so that may enter into it as well.  It's plug 'n' play, the connection is reliable, doesn't drop but just not as fast as other adapters I have.

As far as hardware encryption, that refers to the hardware/software/firmware in the adapter/driver that encrypts and decrypts the network stream, be it WPA,WPA2, WEP or whatever.  Some adapters have problems using the built-in hardware and work better/more reliably when performing the encryption/decryption in software rather than in hardware.  At least that's how I understand it.

---

