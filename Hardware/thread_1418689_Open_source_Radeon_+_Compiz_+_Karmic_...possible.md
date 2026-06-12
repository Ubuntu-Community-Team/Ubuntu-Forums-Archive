---
title: "Open source Radeon + Compiz + Karmic ...possible?"
date: 2010-02-28
forum: Hardware
---

### Post by marius311 on 2010-02-28
I think fglrx is causing some suspend/resume issues so I'd like to try the open source drivers. Will the combination of the radeon driver + Karmic + Compiz work? It seems to be working out-of-the-box on Lucid alpha 3 with great performance, but on Karmic I can only get Metacity, not Compiz working. Has anyone done this successfully or is this something I'll have to wait until Lucid for?

---

### Post by nickylee on 2010-03-01
I had it working with the Xorg Edgers PPA ([link]("https://launchpad.net/~xorg-edgers")) but it's not really do-able on the default Karmic afaik.  I didn't run into too many problems with Edgers, but then your mileage may vary.

Hope that helps.

---

### Post by Yellow Pasque on 2010-03-01
The open-source drivers often have problems with suspend/resume as well, but if you want to try them, follow these two subsections:
[https://help.ubuntu.com/community/RadeonHD#Preparation](https://help.ubuntu.com/community/RadeonHD#Preparation)
[https://help.ubuntu.com/community/RadeonHD#For%20Group%202%20Cards](https://help.ubuntu.com/community/RadeonHD#For%20Group%202%20Cards)

You can try both radeon and radeonhd drivers (switch between them in /etc/X11/xorg.conf)

---

### Post by marius311 on 2010-03-02
Thanks for the links... I'll definitely give this a try!

---

### Post by Fenris_rising on 2010-03-02
Hi

Don't know if it helps but I have dual screens + compiz on Karmic running without proprietary drivers with an x300 radeon card.

It's perfect!! YMMV

regards

Fenris

---

### Post by nickylee on 2010-03-02
Yeah I must say I've been thoroughly impressed with the state of the open source Radeon drivers, all things considered.  I'm using them on Lucid Alpha 3 now and I don't have much complaint except for video tearing, but I hear that's due to some work being done within Mesa that breaks past patches for the problem.

---

### Post by pme 72 on 2010-03-04
Works with an integrated Xpress200 although I am unable to resume from suspend. Also works with an X1550 and suspend works too. No Compiz with an HD4550 though unless I enable the proprietary driver.

---

