---
title: "Dell Precision T3500 install from Redhat"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by Elan Noy on 2009-07-31
I have a Dell Precision T3500 running Radhat. 
Configuration: 12GB ram, [FONT=Arial][SIZE=2]Dual Core Processor W3505 2.53GHz processor.[/SIZE][/FONT]
 
I am tyring to install Ubuntu 64 bit with no success. 
I have tried both a 32 and 64 bit and in both cases it shows the intial screen, asking to choose a language, folowed by the screen that allows you to select Install.
 
Once Install is selected it starts and than the screen goes blank for ever and nothing happens.
?
Any good ideas

---

### Post by BrandanLloyd on 2009-08-20
Elan, I have the 3500 also. To get an install to succeed I had to install Intrepid and perform an upgrade to Jaunty. This worked and the install was successful but everytime I have to boot I have to add acpi=off to get it to successfully boot.

---

### Post by skmah on 2009-09-16
I'm running into the same issue.

On the T3500 9.04 will not install unless I use noacpi.
Ubuntu 8.10 will install without any issues.

However, we use scripted installs for our company standard and "noacpi" or acpi=off does not appear to work.

Also, the power off button does an abrupt power off. Not really desired.

Any ideas?

steve

---

