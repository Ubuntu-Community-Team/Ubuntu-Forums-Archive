---
title: "Cannot update jaunty"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by CaKiwi on 2009-04-26
I have upgraded to Jaunty and when I try to update it with the Update manager I get a message saying I need to run a partial upgrade. When I try to do this, I was getting a popup saying

Please insert the disc labeled: 'Ubuntu 9.04 _Jaunty Jackalope_ -
Release i386 (20090420.1)' in the drive '/cdrom/' and press enter.

I tried inserting 9.04 alternative CD and when that wasn't recognized I downloaded the the install CD which also wasn't recognized.

Now that I am trying it again to get the details for this post, when I try to start the partial upgrade, the dialog just disappears.

---

### Post by joshrobinson on 2009-04-26
Is the jaunty computer hooked to the internet with a working network connection?  Or are you posting from a seperate pc?

If the jaunty computer has internet click System > Administration > Software Sources and uncheck Jaunty Jackalope cd.  Also make sure all the check boxes above are checked except sources (unless you really need them)

Then run update manager from System > Administration > Update manager.  Click check, then click upgrade.

---

### Post by CaKiwi on 2009-04-26
Thanks for the response. The CD was checked in the sources but I am still not able to do the upgrade. When I click on "Start Upgrade" the dialog disappears.

---

### Post by joshrobinson on 2009-04-26
Are the check boxes at the top checked?

Canonical-Supported
Community-Maintained
Proprietary Drivers
Software Restricted
They should all be checked.  If they are, open a terminal.  Applications > Accesories > Terminal

Type the following command, and post the output here.

```
sudo apt-get update
```
If there are no errors type
```
sudo apt-get upgrade
```

---

### Post by CaKiwi on 2009-04-26
sudo apt-get update ran without errors and when it completed the graphical update sprang into life and started doing some updates, including Firefox. But the it got the same error about needing to do a partial upgrade. I ran sudo apt-get upgrade and it gave these messages

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  brasero flashplugin-nonfree gnome-themes gstreamer0.10-ffmpeg hwtest
  hwtest-gtk libavformat52 sound-juicer
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

Any thoughts?

---

### Post by CaKiwi on 2009-04-26
I found this command

sudo aptitude dist-upgrade

in this post

[http://ubuntuforums.org/showthread.php?t=1138396](http://ubuntuforums.org/showthread.php?t=1138396)

and it worked for me

---

### Post by joshrobinson on 2009-04-26
I was about to tell you to do that, and someone showed up at my house and was away from the computer.  Sorry about that.  But in all honesty its better that you worked it out for yourself, helps the learning process.

---

