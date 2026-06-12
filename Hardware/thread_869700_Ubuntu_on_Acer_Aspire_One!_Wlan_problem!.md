---
title: "Ubuntu on Acer Aspire One! Wlan problem!"
date: 2008-07-25
forum: Hardware
---

### Post by bedofdread on 2008-07-25
Hallo!
I just got my Acer Aspire One(1.6 Atom, 512 MB) and installed Ubuntu on it! It works fine, sometimes its a little slow but its OK.
I have problem to find drivers to the wlan card. Have anybody got a solution to this? Any other recommendation what i should do with ubuntu to get it optimized for my netbook?

Best Regards!
John Herrlin

---

### Post by didko on 2008-08-02
Hi there,

First you need to install build-essentials, after that download and untar this madwifi driver [http://fox.deyan.org/madwifi-ng-r2756+ar5007.tar.gz](http://fox.deyan.org/madwifi-ng-r2756+ar5007.tar.gz)

$make
$sudo make install
$sudo modprobe ath_pci

restart 

That's it.

---

### Post by Tux Aubrey on 2008-08-02
As per dido's post - worked fine for me.  If you don't get it straight away, try the wifi switch once (front right of the machine).  The light doesn't work with Ubuntu and you don't know whether the card is turned on or off.

When you are happy with the wireless, you can then add ath_pci to your start-up modules with: 

> sudo echo ath_pci >> /etc/modules


Check out [wanderingstar's AcerOne page on the Ubuntu Community wiki]("https://help.ubuntu.com/community/AspireOne") too.

I love my one.

---

### Post by kid543 on 2008-08-14
I have followed this process and still unable to get my wlan to work. Is there a work around for the button? I have tried turning it on and off, but there was no change. When doing ifconfig i don't see the wlan interface.


thanks

---

### Post by Crazy Jesus on 2008-08-18
Try this:

[http://adamdotnet.net/2008/08/18/acer-one-wifi-fix/](http://adamdotnet.net/2008/08/18/acer-one-wifi-fix/)


The Atheros card should have native support in the next Ubuntu release with the 2.6.25 kernel, but for now the madwifi drivers with HAL should work well enough.

---

