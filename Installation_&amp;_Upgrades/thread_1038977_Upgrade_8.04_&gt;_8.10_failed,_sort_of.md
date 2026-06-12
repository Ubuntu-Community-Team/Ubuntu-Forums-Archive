---
title: "Upgrade 8.04 &gt; 8.10 failed, sort of"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by Halsnalle on 2009-01-14
I just upgraded 8.04 to 8.10 on my MacBook Pro, but something went wrong in the process. 

* The upgrade program complained towards the end that everything had not installed correctly, but when I check my installed version it seems that I do have 8.10 installed after all. 

However:

* Network functions seem not to be working. Pinging my home server seems to give no answer and I can't even start Network Configuration. 

* Firefox is not starting. 

* Given that my computer seems not to be able to connect to the network, it's not surprising that I get an error message when I run "sudo apt-get update" that it fails to fetch the needed files and lookup the repositories. 

* When I run "sudo apt-get dist-upgrade" I get an error message that there some error related to the following:

xulrunner-1.9
firefox-3.0
firefox-3.0-branding
xulrunner-1.9-gnome-support
firefox-3.0-gnome-support
yelp
startupmanager
sun-java6-plugin
ubufox
ubuntu-desktop

...which might explain why Firefox isn't working.

Any suggestions how to fix it?

---

### Post by Tim Sharitt on 2009-01-14
The packages may not have been configured properly. Try
```
sudo dpkg --configure -a
```

---

### Post by Halsnalle on 2009-01-14
> **Tim Sharitt said:**
> The packages may not have been configured properly. Try
```
sudo dpkg --configure -a
```

Thanks! When I tried that, I get the same error as with upgrade/update. There are errors in handling and dependency problems that prevent the updating/configuring of the files listed above.

---

### Post by kranny on 2009-01-14
Can you post the errors?

---

### Post by Halsnalle on 2009-01-18
> **kranny said:**
> Can you post the errors?

Here we go (unfortunately, some of it's in Swedish):
```

johan@johan-laptop:~$ sudo dpkg --configure -a
[sudo] password for johan: 
St&#8730;§ller in xulrunner-1.9 (1.9.0.5+nobinonly-0ubuntu0.8.10.1) ...
/usr/lib/xulrunner-1.9.0.5/xulrunner-bin: error while loading shared libraries: libplds4.so.0d: cannot open shared object file: No such file or directory
dpkg: fel vid hantering av xulrunner-1.9 (--configure):
 underprocess post-installation script gav felkod 127
dpkg: beroendeproblem f&#8730;&#8706;rhindrar konfigurering av yelp:
 yelp beror p&#8730;• xulrunner-1.9 (>= 1.9~rc1), men:
  Paketet xulrunner-1.9 har inte konfigurerats &#8730;§nnu.
dpkg: fel vid hantering av yelp (--configure):
 beroendeproblem - l&#8730;§mnar okonfigurerad
dpkg: beroendeproblem f&#8730;&#8706;rhindrar konfigurering av ubuntu-desktop:
 ubuntu-desktop beror p&#8730;• yelp, men:
  Paketet yelp har inte konfigurerats &#8730;§nnu.
dpkg: fel vid hantering av ubuntu-desktop (--configure):
 beroendeproblem - l&#8730;§mnar okonfigurerad
dpkg: beroendeproblem f&#8730;&#8706;rhindrar konfigurering av xulrunner-1.9-gnome-support:
 xulrunner-1.9-gnome-support beror p&#8730;• xulrunner-1.9 (= 1.9.0.5+nobinonly-0ubuntu0.8.10.1), men:
  Paketet xulrunner-1.9 har inte konfigurerats &#8730;§nnu.
dpkg: fel vid hantering av xulrunner-1.9-gnome-support (--configure):
 beroendeproblem - l&#8730;§mnar okonfigurerad
dpkg: beroendeproblem f&#8730;&#8706;rhindrar konfigurering av firefox-3.0:
 firefox-3.0 beror p&#8730;• xulrunner-1.9 (>= 1.9.0.1), men:
  Paketet xulrunner-1.9 har inte konfigurerats &#8730;§nnu.
dpkg: fel vid hantering av firefox-3.0 (--configure):
 beroendeproblem - l&#8730;§mnar okonfigurerad
dpkg: beroendeproblem f&#8730;&#8706;rhindrar konfigurering av startupmanager:
 startupmanager beror p&#8730;• yelp, men:
  Paketet yelp har inte konfigurerats &#8730;§nnu.
dpkg: fel vid hantering av startupmanager (--configure):
 beroendeproblem - l&#8730;§mnar okonfigurerad
dpkg: beroendeproblem f&#8730;&#8706;rhindrar konfigurering av firefox-3.0-gnome-support:
 firefox-3.0-gnome-support beror p&#8730;• firefox-3.0 (= 3.0.5+nobinonly-0ubuntu0.8.10.1), men:
  Paketet firefox-3.0 har inte konfigurerats &#8730;§nnu.
 firefox-3.0-gnome-support beror p&#8730;• xulrunner-1.9-gnome-support (>= 1.9~b4~), men:
  Paketet xulrunner-1.9-gnome-support har inte konfigurerats &#8730;§nnu.
dpkg: fel vid hantering av firefox-3.0-gnome-support (--configure):
 beroendeproblem - l&#8730;§mnar okonfigurerad
dpkg: beroendeproblem f&#8730;&#8706;rhindrar konfigurering av firefox-gnome-support:
 firefox-gnome-support beror p&#8730;• firefox-3.0-gnome-support, men:
  Paketet firefox-3.0-gnome-support har inte konfigurerats &#8730;§nnu.
dpkg: fel vid hantering av firefox-gnome-support (--configure):
 beroendeproblem - l&#8730;§mnar okonfigurerad
dpkg: beroendeproblem f&#8730;&#8706;rhindrar konfigurering av firefox-3.0-branding:
 firefox-3.0-branding beror p&#8730;• firefox-3.0 (= 3.0.5+nobinonly-0ubuntu0.8.10.1), men:
  Paketet firefox-3.0 har inte konfigurerats &#8730;§nnu.
dpkg: fel vid hantering av firefox-3.0-branding (--configure):
 beroendeproblem - l&#8730;§mnar okonfigurerad
dpkg: beroendeproblem f&#8730;&#8706;rhindrar konfigurering av firefox:
 firefox beror p&#8730;• firefox-3.0, men:
  Paketet firefox-3.0 har inte konfigurerats &#8730;§nnu.
 firefox beror p&#8730;• firefox-3.0-branding, men:
  Paketet firefox-3.0-branding har inte konfigurerats &#8730;§nnu.
dpkg: fel vid hantering av firefox (--configure):
 beroendeproblem - l&#8730;§mnar okonfigurerad
dpkg: beroendeproblem f&#8730;&#8706;rhindrar konfigurering av sun-java6-plugin:
 sun-java6-plugin beror p&#8730;• firefox | firefox-2 | iceweasel | mozilla-firefox | iceape-browser | mozilla-browser | epiphany-gecko | epiphany-webkit | epiphany-browser | galeon | midbrowser | xulrunner, men:
  Paketet firefox har inte konfigurerats &#8730;§nnu.
  Paketet firefox-2 &#8730;§r ej installerat.
  Paketet iceweasel &#8730;§r ej installerat.
  Paketet mozilla-firefox &#8730;§r ej installerat.
  Paketet iceape-browser &#8730;§r ej installerat.
  Paketet mozilla-browser &#8730;§r ej installerat.
  Paketet epiphany-gecko &#8730;§r ej installerat.
  Paketet epiphany-webkit &#8730;§r ej installerat.
  Paketet epiphany-browser &#8730;§r ej installerat.
  Paketet galeon &#8730;§r ej installerat.
  Paketet midbrowser &#8730;§r ej installerat.
  Paketet xulrunner &#8730;§r ej installerat.
dpkg: fel vid hantering av sun-java6-plugin (--configure):
 beroendeproblem - l&#8730;§mnar okonfigurerad
dpkg: beroendeproblem f&#8730;&#8706;rhindrar konfigurering av ubufox:
 ubufox beror p&#8730;• firefox | abrowser | firefox-3.0 | firefox-2, men:
  Paketet firefox har inte konfigurerats &#8730;§nnu.
  Paketet abrowser &#8730;§r ej installerat.
  Paketet firefox-3.0 har inte konfigurerats &#8730;§nnu.
  Paketet firefox-2 &#8730;§r ej installerat.
dpkg: fel vid hantering av ubufox (--configure):
 beroendeproblem - l&#8730;§mnar okonfigurerad
Fel uppstod vid hantering:
 xulrunner-1.9
 yelp
 ubuntu-desktop
 xulrunner-1.9-gnome-support
 firefox-3.0
 startupmanager
 firefox-3.0-gnome-support
 firefox-gnome-support
 firefox-3.0-branding
 firefox
 sun-java6-plugin
 ubufox

```

---

### Post by Pumalite on 2009-01-18
Boot into Recovery Mode, choose 'Shell'; run:
```
dpkg --configure -a
apt-get -f install
apt-get update
apt-get dist-upgrade
uname -a
```

---

### Post by Halsnalle on 2009-01-18
Okay, when I boot into recovery mode and then choose "root: Drop to root shell prompt" and run the commands you suggest, I get basically the same error as above ("Errors were encountered while processing: xulrunner-1.9 ... ubufox").

---

### Post by Halsnalle on 2009-01-18
Hm, tried advice in [this thread]("http://ubuntuforums.org/showthread.php?t=957268") and purged Firefox. Now I only get errors for the following:

 xulrunner-1.9
 yelp
 ubuntu-desktop
 xulrunner-1.9-gnome-support
 startupmanager

But they still won't configure/install correctly, I still don't have network access, and, of course, I now don't have Firefox... ;)

---

### Post by MaindotC on 2009-02-19
I have the same problem per updates that were released a week ago:
```

Errors were encountered while process:
 xulrunner-1.9
 firefox-3.0
 xulrunner-1.9-gnome-support
E:  Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Pumalite on 2009-02-19
At you at kernel -8?
If not, do my commands again

---

### Post by Pumalite on 2009-02-19
```
uname -a
```

---

### Post by MaindotC on 2009-02-19
Sorry I had to go work my worthless job at the convenience store because the night guy called in sick - back now.  I didn't upgrade to 8.10; I'm just having the problem w/ the three packages updating.  I'm using 2.6.24-22.

---

