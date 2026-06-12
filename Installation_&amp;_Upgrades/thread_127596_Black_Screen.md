---
title: "Black Screen"
date: 2006-02-09
forum: Installation &amp; Upgrades
---

### Post by zemex34 on 2006-02-09
When my Ubuntu finishes installing, it reboots the computer. Then I start Ubuntu in the OS menu, it loads all the software to start ubuntu, but then a black screen is shown, and nothing more is done. What can I do?? :confused: 

Please, Help me

---

### Post by firetux on 2006-02-09
some more info is needed, graphics card, laptop?,...

if you have an ATI you can try this:

<ctrl><alt>F1  (this drops you in a command line)
login with your username and password
type ```
sudo nano -w /etc/X11/xorg.conf
```
enter your password

find this section: 
```
Section "Device"
       Identifier      "ATI Technologies, Inc. Radeon Mobility X700 (RV410)"
       Driver          "ati"
       BusID           "PCI:1:0:0"
       **Option       "MonitorLayout" "LVDS,TMDS"**
EndSection

```
Add the piece that is bold.
Save with ctrl-X, confirm with Y, enter

reboot

---

### Post by zemex34 on 2006-02-09
I've a ACER Aspire 1694WLMi, with an ATI Radeon X700...

---

### Post by firetux on 2006-02-09
[QUOTE=zemex34]I've a ACER Aspire 1694WLMi, with an ATI Radeon X700...[/QUOTE]
Then the little howto I wrote above will VERY likely work. (it worked for my Acer 5024WLMi which is very alike)

---

### Post by shuttleworthwannabe on 2006-02-09
What I did was during the installation, the Xserver comes on asking you to identify the grpahics card; or since you have already installed, you could

$sudo dpkg-reconfigure xserver-xorg

choose a VESA driver and choose a resolution like 1024x768 (something less than your max resoultion); at this poitn do not choose ati or fglrx (you do nto have the driver yet). choose default setting for evrything else, and agree to write to new xorg.conf file.

reboot; and login into the GUI at 1024x768 res.

then follow thes instructions to install the ATI/Radeon driver here [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

Let us know what happens..

I have been thru this so many times, I feel like I have jsut been thru hell..see my post under video and sound.

HTH

---

