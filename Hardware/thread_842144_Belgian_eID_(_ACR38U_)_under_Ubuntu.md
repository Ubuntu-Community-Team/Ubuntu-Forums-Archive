---
title: "Belgian eID ( ACR38U ) under Ubuntu"
date: 2008-06-27
forum: Hardware
---

### Post by newbie2 on 2008-06-27
this did ' the trick' for me , even on hardy :
> I removed every packages and was about to give up when I finally found the answer that made things work out of the box at
[http://doc.ubuntu-fr.org/materiel/acr38](http://doc.ubuntu-fr.org/materiel/acr38)

Packages to install :

sudo apt-get install libacr38u libacr38ucontrol0 beid-tools pcscd libpcsclite-dev beidgui libbeid2 libbeidlibopensc2

After installing these, I was able to read my card under beid.

Firefox :

In order to access websites working with the eID, you need to load the PKCS#11 module.

Edit > Preferences > Advanced > Encryption > Security Devices > Load

Module name : “Belgium Identity Card PKCS#11&#8243;
Module filename : “/usr/lib/libbeidpkcs11.so.2&#8243;

Restart Firefox when done.

The card reader MUST be plugged before starting Firefox if you intend to access a website requiring access to your eID.
[http://www.wains.be/index.php/2007/10/28/belgian-eid-under-ubuntu-710/](http://www.wains.be/index.php/2007/10/28/belgian-eid-under-ubuntu-710/)
:)

---

### Post by newbie2 on 2009-02-03
ubuntu gets 'a bit behind' other distro's it seems :
[http://rpmfind.net/linux/RPM/dag/redhat/el4/x86_64/eid-belgium-2.6.0-1.el4.rf.x86_64.html](http://rpmfind.net/linux/RPM/dag/redhat/el4/x86_64/eid-belgium-2.6.0-1.el4.rf.x86_64.html)

can someone make it 'ubuntu compatible' ... coz i use now itrepid 64 bit on my laptop, and when i log on a eID website with firefox , everything is ok , but when i unplug my cardreader(ACR38U) before i close firefox , firefox crashes(hangs)...:frown:

---

### Post by Tiftof on 2009-05-31
Just tried this on intrepid. Seem like libxerces27 needer for beidgui isn't available anymore in intrepid nor jaunty. Just downloading and using the old packet from hardy will solve this: [http://packages.ubuntu.com/nl/hardy/libxerces27](http://packages.ubuntu.com/nl/hardy/libxerces27)

And for adding pkcs11 module in firefox the module has been updated to /usr/lib/libbeidpkcs11.so.3

---

### Post by Jurgentje on 2009-11-06
Hi,

I also got myself an eID card reader for the Belgian eID.
Apparently, there's a second kind of card reader (type: ACR38-CFC-RZET14) that doesn't work with the ACR38U drivers. It's called ACR38 CCID.

For Debian based systems, there is a i386 (32-bits) .deb file in this package (there's three different packages in the file: one for fedora, one for opensuse and one for debian):

[http://www.acs.com.hk/drivers/eng/ACR38C_Package_Lnx_100_P.zip](http://www.acs.com.hk/drivers/eng/ACR38C_Package_Lnx_100_P.zip)

The debian file probably works fine under Ubuntu 9.10 i386 - but I'm running 64-bits version of Ubuntu here.

Next, I tried downloading the source file:

[http://www.acs.com.hk/drivers/eng/ACR38CCID_Driver_Lnx_100_P.tar.bz2](http://www.acs.com.hk/drivers/eng/ACR38CCID_Driver_Lnx_100_P.tar.bz2)

Here you have to do the compiling by hand, and I didn't succeed yet.

The people at ACS Hong Kong reply to support mails very quickly (I contacted them this summer with a previous issue and then also, they did respond within half an hour).
Because I had errors, I contacted them, and the advised to check if these programs were installed:
[LIST]
[*]libusb-dev (>= 0.1.6a-2.1)
[*]libpcsclite-dev (>= 1.3.3)
[*]flex
[*]autotools-dev
[*]pkg-config
[*]g++
[/LIST]

So I installed these (default Synaptic)... and ended up with these versions:
[LIST]
[*]libusb-dev (2:0.1.12-13)
[*]libpcsclite-dev (1.5.3-ubuntu1)
[*]flex (2.5.35-7ubuntu1)
[*]autotools-dev (20090427.1)
[*]pkg-config (0.22-1build1)
[*]g++ (4:4.4.1-1ubuntu2)
[/LIST]

Now I ran the commands again:

[LIST]
[*] sudo ./configure
[*] sudo make
[*]sudo make install
[/LIST]
Now I rebooted the computer... and the card read just fine :D
\\:D/Thanks to Mr Lincoln from ACS and their support team for the quick responses on this one!

---

