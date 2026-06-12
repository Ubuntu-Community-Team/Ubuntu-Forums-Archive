---
title: "HP Laserjet P2015 does not print from ubuntu after hardy upgrades"
date: 2008-06-25
forum: Hardware
---

### Post by Tharmas on 2008-06-25
Hi, We have a HP Laserjet P2015 printer in our network. It printed ok with Edgy, Feisty, Gutsy and the first month or so with Hardy. Well, it actually blinked a yellow light when print jobs were submitted from ubuntu, but pressing this button made it complete the work.
Now it stopped printing anything from ubuntu. And the nasty box keeps printing from windows ](*,) .

Anybody out there had similar problems?

---

### Post by stchman on 2008-06-25
> **Tharmas said:**
> Hi, We have a HP Laserjet P2015 printer in our network. It printed ok with Edgy, Feisty, Gutsy and the first month or so with Hardy. Well, it actually blinked a yellow light when print jobs were submitted from ubuntu, but pressing this button made it complete the work.
Now it stopped printing anything from ubuntu. And the nasty box keeps printing from windows ](*,) .

Anybody out there had similar problems?

I recommend the clean install route that the upgrade route.

That printer is reported to work OOB with Linux using the postsctipt driver.

[http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_P2015](http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_P2015)

---

### Post by Tharmas on 2008-06-25
> **stchman said:**
> I recommend the clean install route that the upgrade route.
[/url]

Me, too!
But we have some specially compiled software that is a big pain to re-install ...

And after upgrade from gutsy to hardy all was well. The problem only started after the latest hardy updates (last month).


> **stchman said:**
> 
That printer is reported to work OOB with Linux using the postsctipt driver.
[http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_P2015](http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_P2015)

The problem happens with both the postscript and the foomatic/hpijs driver.

---

### Post by Deeg on 2009-07-02
Found the answer elsewhere on the ubuntuforums:
[https://answers.launchpad.net/ubuntu/+question/22565](https://answers.launchpad.net/ubuntu/+question/22565)

---

### Post by dubbelodub on 2009-12-03
What I did was change the driver to HP Laserjet p2015n hpijs 3.9.8

Point you browser to [http://localhost:631](http://localhost:631) -> Printers -> Pick the p2015 -> Go from Administration dropdown to Modify Printer. Go continue till you get to choose a driver and pick the aformentioned from the drop down list.

Chillin...

---

