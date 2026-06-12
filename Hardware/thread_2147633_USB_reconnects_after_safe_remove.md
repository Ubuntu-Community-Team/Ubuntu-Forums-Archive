---
title: "USB reconnects after safe remove"
date: 2013-05-22
forum: Hardware
---

### Post by punathil on 2013-05-22
Hi All

I am using a HP Elitebook 8470p laptop and OS is Ubuntu 13.04 (x64). this laptop have 2 USB 3.0 ports. whenever i try to safe remove my Seagate USB3.0 1Tb HDD, it will get reconnected automaticaly. pls help me to get this fixed as i am unable to safe remove my external HDD

---

### Post by ohnonot on 2013-05-23
if you (or any app) doesn't start writing to the hd in the meantime, you can just pull it out. really.

---

### Post by punathil on 2013-05-27
Hi ohnonot,

But in Windows, when i select the device and safe remove, the HDD power will go off after safelanding HDD Heads. But if we remove HDD without safe remove.. i don't feel itz safe as still Platters will be rotating and Head may not be at landing place..

Viswan.

---

### Post by ohnonot on 2013-05-28
hello,
it seems i was half wrong - there is something called ["delayed write"]("http://www.ehow.com/how_5900160_fix-windows-delayed-write-error.html") on windows, which, afaik, does not exist in the linux world, thank god. this would make it necessary in the first place to add a button "safely eject drive" even for usb sticks.
also, i have an old (+5 years) external usb hd with external power source, that doesn't even have a switch, you can't do anything else but just pull the plug.
plus, i never had data failure although i'm treating all my external devices this way.
but i admit that i am unfamiliar with really new hardware.
anyhow, blah, blah, i got curious and did some web searches, sth you might have done yourself before posting.
here's what i got:
[http://askubuntu.com/questions/234523/when-can-i-safely-unplug-an-external-drive-on-12-10](http://askubuntu.com/questions/234523/when-can-i-safely-unplug-an-external-drive-on-12-10)
[http://askubuntu.com/questions/56270/how-can-i-spin-down-external-hard-drive](http://askubuntu.com/questions/56270/how-can-i-spin-down-external-hard-drive)
and even a little app to do it:
[https://github.com/fenrrir/bdin](https://github.com/fenrrir/bdin)
would any of those answer your question?

---

