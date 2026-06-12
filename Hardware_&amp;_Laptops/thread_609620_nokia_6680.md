---
title: "nokia 6680"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by ne0hit on 2007-11-11
hello everybody,
how i can sync my nokia 6680 from usb with my ubuntu gutsy release?? i want to tranfers file from my pc to my cellphone, and from my cellphone to my pc... thanks you!

ne0h

---

### Post by daxumaming on 2007-11-11
I lost a few hairs trying to copy files via a USB connection. In the end, I got myself a USB Bluetooth Dongle instead. I have 6630 and I haven't found any apps and/or solutions that would allow me to do this.

---

### Post by ne0hit on 2007-11-11
ok, thank you for information. I'll buy a dongle bluetooth!

---

### Post by s4ncho on 2007-12-04
there's no problem with transfer files from/to 6680 (or other s60 symbian) phones on kubuntu. but problem is with sync (contact etc.)

my faq to use usb cable:
-add repo
```
deb http://www.stud.uni-karlsruhe.de/~ubq7/debian extra main
```
press "refresh" in synaptic or adept to read new repo

(or go directly to [http://www.stud.uni-karlsruhe.de/~ubq7/debian/](http://www.stud.uni-karlsruhe.de/~ubq7/debian/) & download packages & install them)

-next in adept or synaptic select to install:
```
libopenobex1 openobex-apps obexfs obexftp obextool tablelist 
```
press "apply

RUNNING:
- kubuntu(kde) create shortcut, go to 3rd tab (application) in "command" paste 
```
obextool --obexcmd "obexftp -u 1"
```
next "advanced options" & select "run as diffrent user" next ok, ok & run program
- in console
```

sudo obextool --obexcmd "obexftp -u 1"
```
----------------
certificates (not neccesary) 
```
gpg --recv-keys F6369E05
 gpg --export --armor F6369E05 --output - | apt-key add -
```
END

u can also use qobexftp form kde.org ([http://www.kde-apps.org/content/show.php/QObexftp?content=48364](http://www.kde-apps.org/content/show.php/QObexftp?content=48364)) insted obexftp which looks ugly but u need to have obexftp installed

---

### Post by coggz on 2008-02-28
Wow, this works really well for Nokia 6680. Thanks so much!
Luke

---

### Post by s4ncho on 2008-03-17
replace obextool with qobexftp (obextool needed to run)
it got better interface & allows to copy many file at ones

[http://www.kde-apps.org/content/show.php/QObexftp?content=48364](http://www.kde-apps.org/content/show.php/QObexftp?content=48364)

---

