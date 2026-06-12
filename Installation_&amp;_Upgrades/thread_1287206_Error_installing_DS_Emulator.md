---
title: "Error installing DS Emulator"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by thisisthenewguy on 2009-10-09
tired using the add/remove section to install the ds emulator, got this error:

E: Method http has died unexpectedly!
E: Method /usr/lib/apt/methods/http did not start correctly
E: Unable to lock the download directory

please help

---

### Post by rreese6 on 2009-10-09
Maybe this site might help you>

[http://desmume.org/]("http://desmume.org/")

---

### Post by thisisthenewguy on 2009-10-09
> **rreese6 said:**
> Maybe this site might help you>

[http://desmume.org/](http://desmume.org/)

tried that, same error

---

### Post by 10Digits on 2009-10-10
Try wine......

If you can get your hands on a DS emulator for windows , you can use that emulator to do whatever gaming you might want to.

Wine runs it smoothly,I used this method so that my bro can play pokemon on his PC....


So, Try it....

---

### Post by thisisthenewguy on 2009-10-10
> **10Digits said:**
> Try wine......

If you can get your hands on a DS emulator for windows , you can use that emulator to do whatever gaming you might want to.

Wine runs it smoothly,I used this method so that my bro can play pokemon on his PC....


So, Try it....

okay this is now a turn for the worst, nothing will install i keep getting the same error no matter what program i try. please help

---

### Post by rreese6 on 2009-10-11
Sorry I totally missed this the first read..
You don't have an error with DS emu, you have an APT error.

Find the apt package on the install cd or download it from packages.ubuntu.com and reinstall it with dpkg

one you have the file do save to your desktop
then open Terminal and type the following:
```
cd ~/Desktop
sudo dpkg -r apt
sudo dpkg -i apt<TAB><ENTER>
```

<TAB> = Tab key
<ENTER> = Enter Key

---

