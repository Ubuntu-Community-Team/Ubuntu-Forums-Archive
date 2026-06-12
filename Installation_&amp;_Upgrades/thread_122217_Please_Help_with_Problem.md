---
title: "Please Help with Problem"
date: 2006-01-27
forum: Installation &amp; Upgrades
---

### Post by fnkaze on 2006-01-27
I installed everything perfectly but after i log in only the backround appears and nothing else loads up. there is backround music and everything. can't seem to find out the problem please help.. noob here :D

---

### Post by amohanty on 2006-01-27
Does Alt+F1 bring up a menu?
Does right click bring up a menu?

AM

---

### Post by fnkaze on 2006-01-27
nope it doesn't but ctrl alt f1 works

---

### Post by amohanty on 2006-01-27
Ok after a ctrl alt f1, login as yourself and then post the output of **dmesg**

AM

---

### Post by fnkaze on 2006-01-27
btw i m running on 
2.4ghz Celeron
256 ddr ram
nvidia geforce4mx 64mb
8.5gb primary hard drive
10.5 gb primary slave

---

### Post by fnkaze on 2006-01-27
how do i do that... im on the forum using a different computer and the list is really long.. how do i copy it? sorry for the incovinience

---

### Post by amohanty on 2006-01-27
Just write down the last 10 odd lines.
If the errors not there, we can then reroute the output and see if you have a network connection.
AM

---

### Post by fnkaze on 2006-01-27
[4294937.214000]IPv6 over IPv4 tunneling driver
[4294937.213000]NET:registered protocol family 10
[4294744.577000]Bluetooth: RFCOMM socket layer
[4294744.547000]Bluetooth: L2CAP socket layer initialized
[4294744.507000]Bluetooth: HCI socket layer initialized
[4294744.507000]NET registered protocol family 31
[4294742.959000]apm: overridden by acpi
[4294736.695000]uhci_hcd 0000:00:01.1: unlink after no-IRQ? controller is probably using the wrong IRQ
[4294726.899000]ibm_acpi: ec object not found
[4294726.765000]ACPI: power button (CM) [pwrb]

yaa this computer is using a wireless usb adapter so i didn't get it to work while installing

---

### Post by aysiu on 2006-01-27
In my experience, this sounds to me like a screen resolution problem. Have you tried control-alt-f1 ```
sudo dpkg-reconfigure xserver-xorg
```?

---

### Post by fnkaze on 2006-01-27
ya tried that b4 and dun work. if it were a resolution problem i can right click right? but it doesn't work

---

### Post by amohanty on 2006-01-27
ok lets try reinstalling the ubuntu-desktop list of pkgs:
when in ctrl alt f1, login as yourself:

> sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop

Post back if this does not fix it, or throws up any error messages.

AM

---

### Post by fnkaze on 2006-01-27
sigh...... shuld i try reinstalling?

---

### Post by fnkaze on 2006-01-27
everything went pretty smooth but nothing happened.... culd it be my video card isnt . working? but i get the login screen.. i dunno

---

### Post by fnkaze on 2006-01-27
i tried the live cd on my other computer and it did the same thing i think theres sumthing wrong with the two cds they sent maybe ill get an burnt iso version later me sleep nowz laters

---

### Post by amohanty on 2006-01-27
> everything went pretty smooth but nothing happened.... culd it be my video card isnt . working? but i get the login screen.. i dunno

So did you do a complete reinstall or just reinstalled ubuntu-desktop?
Its possible the CDs are corrupt, but you should have gotten an error during installation if that was the case?

Can you post the contents of : /var/log/Xorg.0.log and your /etc/X11/xorg.conf
Its kinda long so I would suggest that you hook it up to a wired ethernet connection and transfer the files elsewhere.

AM

---

