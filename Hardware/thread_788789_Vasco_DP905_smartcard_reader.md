---
title: "Vasco DP905 smartcard reader"
date: 2008-05-10
forum: Hardware
---

### Post by Domie on 2008-05-10
To do my banking with the internet and to fill in my taxes ([www.taxonweb.be](www.taxonweb.be)), I have a Vasco digipass 905 smartcard reader.

I followed the installation of the necessary software on this blog:

[http://www.stroobant.be/eid-taxonweb-linux-1-windows-0](http://www.stroobant.be/eid-taxonweb-linux-1-windows-0)

```
$ sudo apt-get install libacr38u libacr38ucontrol-dev pcscd
$ sudo apt-get install beid*
```

Afterwarts, I used in firefox...:

```
/usr/share/beid/beid-pkcs11-register.html
```

result: beidgui says "no smartcard inserted". No problem, probably wrong driver... Looking further.

[http://pcsclite.alioth.debian.org/ccid.html](http://pcsclite.alioth.debian.org/ccid.html)
 This site says the CCID driver should be working with Vasco DP905. I installed the driver (./configure - make - sudo make install - got no errors ) but still I can't read my electronical ID

Any ideas on this one? Is there some additional output info required, if so, I'll post it with pleasure?

---

### Post by Domie on 2008-05-12
I also tried

[https://help.ubuntu.com/community/CommonAccessCard](https://help.ubuntu.com/community/CommonAccessCard)

if you wonder

---

### Post by Domie on 2008-05-15
bump

---

### Post by VHans on 2008-05-20
I'm trying to do the same thing. No luck until now.

Hans

---

### Post by Domie on 2008-05-25
I've got a response of Vasco:

Here is the support you requested.

Linux support is based on PC/SC lite. I expect DP905 to be listed as a
tested reader (today listed as "Should work but untested by me") on
[http://pcsclite.alioth.debian.org/ccid.html](http://pcsclite.alioth.debian.org/ccid.html) . No need therefore for a
specific Vasco driver.

But it doesn't work and nobody knows how it does work...

---

### Post by VHans on 2008-05-26
Thanks for the update. It doesn't look very promising though.

Hans

---

### Post by newbie2 on 2008-06-26
[http://www.digipassforeid.be/install_ubuntu.html](http://www.digipassforeid.be/install_ubuntu.html)

---

### Post by stijngysemans on 2008-07-21
> **newbie2 said:**
> [http://www.digipassforeid.be/install_ubuntu.html](http://www.digipassforeid.be/install_ubuntu.html)

this seems to get the driver working. thanks.

---

### Post by VHans on 2008-07-21
> **stijngysemans said:**
> this seems to get the driver working. thanks.

Indeed, the driver works. Now about the software: did somebody try loading KBC's software on Linux?

---

### Post by Cycler on 2008-08-10
> **VHans said:**
> Indeed, the driver works. Now about the software: did somebody try loading KBC's software on Linux?

Yes I did.
I used Wine and got the software installed but I don't get the cardreader working with Wine 1.0. :(

---

### Post by Werner Debrie on 2008-08-11
Cycler,

How did you manage to install the MSI file of KBC (OS checks)?
Did you get any errors that explain why it doesn't work?

Werner

---

### Post by Cycler on 2009-01-09
> **Werner Debrie said:**
> Cycler,

How did you manage to install the MSI file of KBC (OS checks)?
Did you get any errors that explain why it doesn't work?

Werner

At the moment it's not possible to use Wine for this. The Winscard.dll privided within WINE does not contain all te windows winscard functions at this moment.

I got the software installed after installing wine, the vasco DP905 and Starmoney (it installs IE6 and some other components)

More information for overruling the systemcheck, see the documentation of Isabel:
[http://www.isabel.be/contrib6/documents/en-US/MSI_Isabel_Sec_Comp_Customer.pdf](http://www.isabel.be/contrib6/documents/en-US/MSI_Isabel_Sec_Comp_Customer.pdf)

---

### Post by engine on 2009-01-24
The link posted by newbie2 was just what I needed - now I can see who I am <g>

Thanks!

---

