---
title: "Ubuntu CD doen't boot on HP Compaq nx9000"
date: 2013-07-19
forum: Hardware
---

### Post by PAleksandrov on 2013-07-19
Lubuntu alternate CD 13.04 i386 doesn't boot on HP Compaq nx9000. The language selection menu displays and when I press keys nothing happens (so I can't select a language and continue booting). Lubuntu desktop CD 12.10, Lubuntu alternate CD 12.10, Kubuntu DVD behaves in the same way. When I used Lubuntu desktop CD, the number of seconds before auto boot were displayed and normally changed (30s - 29s - ...). But when I press a key, the timer stops. If I boot with a key (for example, Ctrl) pressed, the menu doesn't show. If I am not mistaken, Mandriva 2011 DVD doesn't boot too. Old Linux distro (Mandriva 10.0) behaves normally.

---

### Post by tristantonks-b on 2013-08-15
Hi Guys,

I have been battling with this for half an hour too Burning the dvd from a Mac.

The solution for me was as follows;

[LIST=1]
[*]Download a new copy of Ubuntu (32bit).
[*]DONT Mount the iso.
[LIST=1]
[*]In Mac...
[*]Right-click the iso file,
[*]Select Burn "Ubuntu....." to disc,
[*]--Select the LOWEST write speed--
[*]Don't interrupt the write by doing anything else with your drives or write program.
[/LIST]
[/LIST]
All done - loaded happily to HP :P
I have had no problems loading various Linux OS's to machines with the exception of the HP flavours - no idea why but they ALWAYS cause me grief.

Next step for me is the inevitable Broadcomm issue :(

---

### Post by tristantonks-b on 2013-08-15
Incidentally you can 'Strip' your Ubuntu install down to the Lubuntu version or a [ChromeOS]("http://www.chromium.org/chromium-os") - it's more time consuming than loading the Lubuntu direct from disc but then I've never managed to actually do that. Another alternative that you can use to build UP from is SLAX which I always find loads (Except on HP's).

---

