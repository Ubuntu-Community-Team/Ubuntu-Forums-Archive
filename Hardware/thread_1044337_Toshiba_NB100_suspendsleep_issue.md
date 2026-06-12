---
title: "Toshiba NB100 suspend/sleep issue"
date: 2009-01-19
forum: Hardware
---

### Post by jamaisvu on 2009-01-19
[IMG]http://james.dowden.googlepages.com/Screenshot-Power.png[/IMG]

As you can probably see from the above screenshot, when I've got my netbook plugged in (for use as a radio), I don't want it to decide to go to sleep/suspend (and thereby cut the sound).

Now -- you guessed it -- despite setting the GNOME power management dialog as above, there's clearly some low-level setting making it go to sleep/suspend anyway.

Does anyone know what file I need to hack to kill this annoying behavior? (It's the default Hardy UNR install, FWIW.) I presume it's one of the Toshiba customizations or something to do with the Netbook Remix, as I've not had this problem with any previous Ubuntu or Kubuntu installation.

---

### Post by jamaisvu on 2009-01-20
[FONT=Franklin Gothic Medium][SIZE=4]Anyone?[/SIZE][/FONT]

---

### Post by sandman652001 on 2009-01-22
same problem no solution yet

---

### Post by atlas95 on 2009-01-22
Hi,

I have NB100 too but at home, i will search for you when back home, have you tried the inibit gnome applet ?

Another thing, please could you post you /etc/default/acpi-support files ?
I have change bad thing inside and i would like to have the default ;)

Regards,

---

### Post by vmalep on 2009-02-03
Hi,

I experienced the same problem and I modified the parameters of the screensaver in order to regard the computer as idle only after 2 hours (the maximum). I also unchecked the box under this last option in order not activate the screensaver when the computer is idle.

Hope it helps,
Pierre

---

