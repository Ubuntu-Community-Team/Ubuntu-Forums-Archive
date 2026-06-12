---
title: "can't install firefox-3.0"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by hanzj on 2009-10-26
Hello,
Using Karmic Koala (Ubuntu 9.10). I did
 ```
firefox-3.0
```

and got

> The program 'firefox-3.0' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.0
firefox-3.0: command not found



I then did ```
sudo apt-get install firefox-3.0
``` and got

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox-3.0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Please advise.

---

### Post by fancypiper on 2009-10-26
Now launch it by clicking Applications->Internet->Firefox Web Browser

---

### Post by hanzj on 2009-10-26
it's not in there. it's not installed, apparently.

---

### Post by aysiu on 2009-10-26
> **hanzj said:**
> Hello,
Using Karmic Koala (Ubuntu 9.04). Karmic Koala is Ubuntu 9.10

Jaunty Jackalope is Ubuntu 9.04

Which are you using? *firefox-3.0* isn't available for Karmic.

---

### Post by fancypiper on 2009-10-26
Open a terminal and type:

firefox

Post any error messages you see

---

### Post by hanzj on 2009-10-26
fancypiper,
no error messages in "firefox" package aside from:

> LoadPlugin: failed to initialize shared library /opt/google/picasa/3.0/lib/npPicasa3.so [/opt/google/picasa/3.0/lib/npPicasa3.so: cannot open shared object file: Permission denied]
LoadPlugin: failed to initialize shared library /opt/google/picasa/3.0/lib/npPicasa3.so [/opt/google/picasa/3.0/lib/npPicasa3.so: cannot open shared object file: Permission denied]
LoadPlugin: failed to initialize shared library /opt/google/picasa/3.0/lib/npPicasa3.so [/opt/google/picasa/3.0/lib/npPicasa3.so: cannot open shared object file: Permission denied]


---

### Post by hanzj on 2009-10-26
aysiu.

oops. Sorry for the typo. I meant "9.10". 

You wrote that firefox-3.0 isn't available in Karmic Koala.

I realize that "firefox" is available in Karmic, which I believe is called Shiretoko. I don't like using "firefox" because I can't get Gears (aka Google Gears) to work. Pls advise.

---

### Post by fancypiper on 2009-10-26
I have 3.5.3

---

### Post by hanzj on 2009-10-26
fancypiper,
how do i get 3.5.3?
My "firefox" ("shiretoko") package shows "version 3.5.5pre"

---

### Post by fancypiper on 2009-10-26
Your version is newer than mine.

What happens with this command?

sudo apt-get install firefox

---

### Post by hanzj on 2009-10-26
This is what I get
> ~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Strange, huh? I think it's because when I saw the "packages are kept back from upgrading" I made aptitude install the later versions. Aaagh. I shouldn't have. How can I revert?

---

### Post by fancypiper on 2009-10-26
sudo apt-get remove firefox
or
sudo apt-get purge firefox
then
sudo apt-get install firefox

See man apt-get for the difference between purge and remove.

---

### Post by hanzj on 2009-10-26
fancypiper,
i did as you said, but the same version (version 3.5.5pre) still gets installed.

---

### Post by fancypiper on 2009-10-26
From man apt-get:
A specific version of a package can be selected for installation by following the
           package name with an equals and the version of the package to select. This will
           cause that version to be located and selected for install. Alternatively a specific
           distribution can be selected by following the package name with a slash and the
           version of the distribution or the Archive name (stable, testing, unstable).

So, remove or purge and
sudo apt-get install firefox =3.5.3

---

### Post by hanzj on 2009-10-26
Hello,> 
sudo apt-get install firefox=3.5.3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version '3.5.3' for 'firefox' was not found


---

### Post by hanzj on 2009-10-26
BTW,
I opened synaptic and saw firefox-3.6 (3.6b2pre; aka Namoroka). Too bad Gears doesn't work with it, either.

---

### Post by fancypiper on 2009-10-26
I'm out of ideas.

---

### Post by hanzj on 2009-10-26
does your version allow google gears?

---

### Post by fancypiper on 2009-10-26
The only google gears I could find for firefox is for Windows, not Linux.

---

### Post by hanzj on 2009-10-26
i found a gears xpi for linux, which worked just fine.

Example:
[http://groups.google.com/group/gears-users/msg/14d691d48e647f33](http://groups.google.com/group/gears-users/msg/14d691d48e647f33)

---

### Post by fancypiper on 2009-10-26
[GMail notifier and Dog Ears]("https://addons.mozilla.org/en-US/firefox/search?q=gears&appid=1&cat=0,0&tag=&atype=-1&pid=-1&lup=&sort=&lver=3.5&pp=20") is all I can find for Linux

---

### Post by aysiu on 2009-10-26
I thought I already said *firefox-3.0* is **not** available for Karmic.

*firefox* just installs *firefox-3.5*. There is no *firefox-3.0* to install.

More details here:
[http://packages.ubuntu.com/karmic/firefox-3.0](http://packages.ubuntu.com/karmic/firefox-3.0)

---

