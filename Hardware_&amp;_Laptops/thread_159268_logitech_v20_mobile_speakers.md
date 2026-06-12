---
title: "logitech v20 mobile speakers"
date: 2006-04-12
forum: Hardware &amp; Laptops
---

### Post by groggyboy on 2006-04-12
so i'm purchasing considering the [logitech v20 laptop speakers]("http://www.logitech.com/index.cfm/products/details/US/EN,CRID=2173,CONTENTID=10908").  they run off usb, so i suspect they require a software frontend.  does anyone know if there is linux software available, or where i should look to find out?

cheers, groggyboy

---

### Post by groggyboy on 2006-04-14
<bump>

anyone?

---

### Post by groggyboy on 2006-05-12
well, I guess I'll answer this myself then:

yes, they do work - with a little tweaking.

I plugged them in, and Ubuntu Dapper immeadiately recognized them as "Logitech USB Speakers".  However, they didn't produce any audio until I rebooted Ubuntu.  They use ALSA, so I had to configure Gnome Volume Control (and all my other audio programs like amarok and terminatorX) to use ALSA.  Under Gnome Volume Control I also had to make sure the Logitech Speakers were selected under the File menu.

As for the buttons on the speakers: the volume controls change the on-screen indicator, but not the actual speaker volume!  To adjust volume, I have to open Gnome Volume Control.  The play/stop/back/forward buttons do nothing.  I know the buttons are being recognized by the system, because if I run "xev" in a terminal, it indicates that keys are being pressed.  It seems that further tweaking is required - but at least the speakers work!

I remember reading on the forums about several ways of getting multimedia keyboard keys to work.  Maybe something like that will work here.

cheers,
groggyboy

---

### Post by haiku99 on 2006-09-10
I got  all my Logitech V20 speaker buttons working with the help of various posts on multimedia keys as you suggested and posted a howto at:
[http://ubuntuforums.org/showthread.php?p=1482074](http://ubuntuforums.org/showthread.php?p=1482074)

---

### Post by mrphd on 2006-12-27
I'm thinking of getting the Logitech V20 speakers. Would you recommend them, and do you know of any other decent USB-powered speakers?

Thanks!

---

### Post by haiku99 on 2006-12-27
I would recommend them highly, love mine....they are so light that they can move around at high volume, but this is not a big deal, and a reasonoble tradeoff for me since I carry them in my laptop case.  I wrote a more detailed review at amazon.com, as have others.  From what I've read the Altec Lansing USB speakers are good too, but I have not tried them personally..

---

### Post by groggyboy on 2007-01-04
using USB speakers has become even easier with Edgy (GNOME) - the first time you plug them in, and every time afterwards, a little dialog pops up reminding you to adjust your Sound settings - no reboot required.  However, getting them to work in KDE is a royal pain.  I guess we have to wait for KDE4's upcoming sound backend, Phonon.

---

### Post by mrphd on 2007-01-08
I just bought myself a pair today and I'm quite impressed with them so far, although I haven't got the multimedia keys configured in Edgy yet. They are quite expensive in the UK. Most places sell them for about £50, but I managed to get them for £33 from Maplin (special promotion + 5% student discount).

---

