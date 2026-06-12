---
title: "How to Ati Mobility HD 2xxx +7.11  +Compiz"
date: 2007-11-25
forum: Hardware &amp; Laptops
---

### Post by Illubaba on 2007-11-25
Yo Leute!

Ich habe es geschafft die Mobility Radeon HD2600 +compiz unter Ubuntu/gutsy zum laufen zu bringen. Ich weiss, dass dies viele noch nicht geschafft haben resp. das es dazu noch keine Guide gibt die wirklich was bringt. Also hier meine kleine Guide für all die Leute die dasselbe Problem haben wie ich hatte :) gl & hf. Ich übernehme keinerlei Garantie oder Haftung für die funktionsweise :P


1.alle fglrx treiber installieren. sudo apt-get install
fglrx-driver
	fglrx-driver-dev
	fglrx-control
	xorg-driver-fglrx
	xorg-driver-fglrx-dev

2.xserver-xgl installieren. sudo apt-get install xserver-xgl.
3.envy downloaden - [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
4.benötigte packages für envy installieren
dpatch
linux-headers-generic [7] 
build-essential 
debconf 
dh-make 
fakeroot 
gcc-3.3 
libstdc++5 
module-assistant
5.envy installieren und 7.11 installieren. sudo dpkg -i envy*.deb
6.xorg konfig anpassen. sudo gedit /etc/X11/xorg.conf
Unter “Extensions” Composite auf “Disable” setzen
7.Rebooten
8.in der xorg.conf unter “Extension” folgendes hinzufügen 	Option "AIGLX" 	"1" 
9.Rebooten
10.shell öffnen und glxgears ausprobieren sollte jetzt funktionieren
11.compiz installieren
12.xserver-xgl entfernen apt-get remove xserver-xgl
13.xorg.conf anpassen. Unter “Extension” Option		"Composite"	"Enable" stellen.
14.Rebooten
15.xserver-xgl wieder installieren. sudo apt-get install xserver-xgl

Entschuldigt die hässliche Darstellung. Bei Fragen könnt ihr euch an mich wenden, ich helfe sofern ich kann.

mfg

---

### Post by dmf86 on 2007-11-29
Any chance to put this in English please? :)

---

### Post by Yellow Pasque on 2007-11-29
```
sudo gedit /usr/bin/compiz
```
```
....
# Driver whitelist
WHITELIST="nvidia intel ati radeon i810 **[COLOR="Red"]fglrx[/COLOR]**"
....
```

---

### Post by Clancy_s on 2007-12-01
Hi,

I've only been running Ubuntu for 10 days and my understanding is limited, even when the instructions are in English. :confused: So far as I am aware you are the only person to report success in getting 3d working with the *Mobility* Radeon 2xxx series.

I'm wondering exactly what hardware you have.  It looks to me as though this is a way to install the latest ATI drivers and get them working: I was under the impression that the Mobility Radeon 2xxx series are not yet supported by the ATI drivers.  

eta: after a few days looking through discussions hereabouts and on the Phoronix forums I've decided the current ATI linux drivers are too buggy to be bothered with for the moment, regardless of whether they support the Mobility Radeon HD 2*** cards or not.  I'll leave the translation in case anyone else really wants 3D support *now*

I ran the non code part of your post through Google translate which gave me this:

> 1. all fglrx driver. sudo apt-get install 
fglrx-driver 
fglrx-driver-dev
fglrx-control
xorg-driver-fglrx
xorg-driver-fglrx-dev

2. xserver-xgl install. sudo apt-get install xserver-xgl.
3. envy download - [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
4. needed to install packages for envy 
dpatch
linux-headers-generic [7]
build-essential
debconf
dh-make
fakeroot
gcc-3.3
libstdc++5
module-assistant
5. envy install and 7.11. sudo dpkg -i envy*.deb
6. xorg Config adapt. sudo gedit /etc/X11/xorg.conf
In "Extensions" composite "Disable" set
7. Rebooting
8. in the xorg.conf "extension" to add the following option AIGLX "" 1 "
9. Rebooting
10. shell open and glxgears should now try to work
11. compiz install
12. xserver-xgl remove aptitude remove xserver-xgl
13. xorg.conf adapt. Under "extension" option "composite" "Enable".
14. Rebooting
15. xserver-xgl again. sudo apt-get install xserver-xgl

---

### Post by JarrodHayes on 2007-12-08
I took a crack at it.  Apologies to Illubaba (and everyone else) if I completely screw this up.  Has anyone tried this yet?

> How to Ati Mobility HD 2xxx +7.11 +Compiz 
________________________________________
Hello folks,

I have gotten the Mobility Radeon HD2600 + compviz to run under Ubuntu/Gutsy.  I know that not many people have accomplished this task and there is as yet no guide that really works.  Thus, here is my small guide for all the people who have had the same problem I have.  I make no guarantee or commitment for the  function of this guide.


1.Install all fglrx drivers: sudo apt-get install
fglrx-driver
fglrx-driver-dev
fglrx-control
xorg-driver-fglrx
xorg-driver-fglrx-dev

2. Install xserver-xgl. sudo apt-get install xserver-xgl.
3. Download Envy - [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")
4. Install the necessary packages for Envy
dpatch
linux-headers-generic [7] 
build-essential 
debconf 
dh-make 
fakeroot 
gcc-3.3 
libstdc++5 
module-assistant
5. Install Envy and install 7.11. sudo dpkg -i envy*.deb
6. Adjust xorg.conf: sudo gedit /etc/X11/xorg.conf
Under “Extensions” Set Composite to “Disable”
7. Reboot
8. In the xorg.conf under “Extension” add the following option "AIGLX" "1" 
9. Reboot
10. Open shell and try it out.  Glxgears should now function.
11. Install compiz 
12. Remove xserver-xgl: apt-get remove xserver-xgl
13. Adjust xorg.conf. Under “Extension” change option "Composite" to "Enable".
14.Reboot
15. Install xserver-xgl again: sudo apt-get install xserver-xgl

Apologies for the ugly description. If you have any questions ask me and I will help if I can.  


---

### Post by eponymous on 2008-01-05
thanks for this! worked great.

---

### Post by franco81 on 2008-01-16
I have 7.10 Gutsy installed, having issues trying to install libstdc++5 which keeps popping up as a dependency to many of these drivers. I can find libstdc++6 in apt-cache search but no ++5 anywhere.

Complete novice, any help appreciated.

Update: tried this but didn't really work:
[http://ohioloco.ubuntuforums.org/showthread.php?t=586247](http://ohioloco.ubuntuforums.org/showthread.php?t=586247)

---

### Post by franco81 on 2008-01-17
Okay, I am a complete newbie, but I am having real difficulty finding and installing all these packages. apt-get doesn't cut it and I have to hunt them down and their dependencies and install will dpkg - am I doing something wrong?

---

### Post by Yellow Pasque on 2008-01-17
franco81, try installing/using aptitude instead of apt-get. It usually makes things easier.

---

### Post by franco81 on 2008-01-21
Aptitude helped quite a bit thanks, but I still have had extensive difficulties installing dh-make and debhelper. There are conflicts with Perl I think which prohibit me from installing.

Toshiba p200-1ee
Ubuntu 7.10 Gutsy Gibbon
ATI Radeon HD2600

All I really want is to have a higher screen resolution and a display that takes up the whole screen - not too fussed about compiz and all the rest. Problems I'm having at the moment: sometimes on boot up the display is shrunk in considerably from the edge of the monitor.

---

### Post by Hinsky on 2008-02-28
ok
i did everything as described but...
when i come to part 6 i cant find "Extensions" in my xorg.conf.
do i have to add it somewhere?

---

### Post by Yellow Pasque on 2008-02-28
> **Hinsky said:**
> ok
i did everything as described but...
when i come to part 6 i cant find "Extensions" in my xorg.conf.
do i have to add it somewhere?
Yeah, you can add it to the bottom of the file.

---

