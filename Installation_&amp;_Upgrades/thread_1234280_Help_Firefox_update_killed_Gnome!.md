---
title: "Help Firefox update killed Gnome!"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by Darthnix on 2009-08-07
Ok so I was doing a routine update via the update manager and I noticed that the firefox update had crashed and firefox would no longer launch. The machine kept running for a couple of days until I decided to do a reboot. I got to the ubuntu desktop picture but non of the icons or menu bars would come up. The menu bars would flash on for a moment and then disappear. I did some searching around and tried some things:

sudo aptitude remove firefox-3.0
sudo aptitude install firefox-3.0

sudo dpkg-reconfigure xulrunner-1.9

It looks like the problem is with xulrunner-1.9 but I cant seem to repair it. Now when I try to use "sudo apt-get update" I am getting a failer to connect message.

Thanks in advance for any help!

---

