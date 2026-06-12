---
title: "Toshiba Satellite Pro M60 support"
date: 2008-01-07
forum: Hardware &amp; Laptops
---

### Post by xurizaemon on 2008-01-07
I have a Toshiba Satellite Pro M60 here which I'm testing with Gutsy. It appears to have out of the box support for everything, but require a little configuration to make it all work perfect.

Hoping this can be merged into the [Toshiba Laptop Testing pages]("https://wiki.ubuntu.com/LaptopTestingTeam/Toshiba") once the information is fully collected.

What is this thing?
 * Pentium M 2GHz
 * Stock 80GB Toshiba HD
 * 512MB RAM (wtf? I thought it had more until now. bugger!)
 * Built-in wireless, bluetooth
 * 17" display (1440x900 native)
 * nvidia video card

I'll get more specific about each of these as I squeeze more info out of the beast.

**Suspend / Hibernate**

Suspend / hibernate was having issues with the stock config (feisty install upgraded to gutsy); the screen would come back with only the mouse cursor visible, or a cursor and single square of garbage. Seems to behave OK now with a few tweaks. Here are my relevant settings:

/etc/default/acpi-support:
```
ACPI_SLEEP=true
ACPI_HIBERNATE=true
ACPI_SLEEP_MODE=mem
MODULES=""
MODULES_WHITELIST=""
SAVE_VBE_STATE=false
VBESTATE=/var/lib/acpi-support/vbestate
POST_VIDEO=true
USE_DPMS=true
DOUBLE_CONSOLE_SWITCH=true
HIBERNATE_MODE=shutdown
LOCK_SCREEN=true
STOP_SERVICES="mysql "
RESTART_IRDA=false
ENABLE_LAPTOP_MODE=true

```

also added /etc/acpi/resume.d/99-local.sh (may not be required?)
```
#!/bin/sh

xset dpms 0 0 1800

```

Wireless comes back up when suspended. Haven't tested hibernate yet (I'll follow that up).

**Wireless**

Wireless works OK, but it does this weird thing where it wants you to open the wireless settings and change 'em after each boot. I am not sure if it's not remembering the password, or just being ornery. Switching to/from "Roaming" mode usually works.

**Video**

Using the restricted drivers from nvidia for compiz effects and other dancing baloney. Lovely. Not a monster video card, but works fine anyway.

**Bluetooth**

**Trackpad**

The ALPS trackpad doesn't work for me yet with the stock config (am using a USB mouse so far) but I will try out the tips on [this page]("http://ubuntu.wordpress.com/2005/11/15/fixing-my-alps-touchpad-with-the-synaptics-driver/") and [this forum post]("http://ubuntuforums.org/showthread.php?t=78904") to configure it RSN.

**Questions?**

Hit me with any questions and I'll add more tests as we go.

Hope this helps someone else ...

**References**

 * [Ubuntu Laptop Testing / Toshiba]("https://wiki.ubuntu.com/LaptopTestingTeam/Toshiba")
 * [Tosh Sat M60 / Slackware]("http://www.freemodding.it/modules/newbb/viewtopic.php?topic_id=1532&forum=34") (italian, via [linux-on-laptops.org/toshiba.html]("http://www.linux-on-laptops.com/toshiba.html"))
 * [ALPS touchpad config]("http://ubuntu.wordpress.com/2005/11/15/fixing-my-alps-touchpad-with-the-synaptics-driver/")
 * [ALPS touchpad config]("http://ubuntuforums.org/showthread.php?t=78904")
 * [Ubuntu on Toshiba M45]("http://www.cantrip.org/toshiba-m45.html")
 * [Ubuntu on Toshiba Tecra M5]("http://blogs.warwick.ac.uk/chrismay/entry/ubuntu_edgy_on/")

---

### Post by kwacka on 2008-01-07
Check the "linux for laptops" site:

[http://www.linux-on-laptops.com/toshiba.html](http://www.linux-on-laptops.com/toshiba.html)

If it doesn't have your model it will have something similar.

---

### Post by xurizaemon on 2008-01-07
Thanks, kwacka. Have already done a fair bit of reading on these, but I should have thought to include the various links I've used. Will edit the original post to add these references.

Cheers

---

### Post by DeLiK on 2008-02-25
I am using the same laptop as you are and i'm having some problems with bluetooth...

I don't know how to explain better. All i know is that bluetooth is randomly detected (or it seems like it)

---

