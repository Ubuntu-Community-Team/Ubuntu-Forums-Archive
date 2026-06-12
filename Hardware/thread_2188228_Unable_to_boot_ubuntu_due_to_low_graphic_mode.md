---
title: "Unable to boot ubuntu due to low graphic mode"
date: 2013-11-16
forum: Hardware
---

### Post by someshangale on 2013-11-16
I am using Ubuntu 12.04 LTS along with Windows XP.But since i have updated the graphic drivers in ubuntu and has restarted the desktop i am unable to boot ubuntu as it is showing a message "it is running on low graphic mode".I tried to correct the problem through the recovery mode but not getting access to it too.I tried some terminal commands but for that the internet need to be connected which i can connect only after proper booting of system as i am using 3G dongle.So please help me to resolve the issue.
I am using 1 GB DDR3 ati radeon graphic card
ATI Radeon HD 5400 Series
Using intel i3-2100 CPU 3.10GHz
with intel DHWW61 motherboard

---

### Post by someshangale on 2014-01-24
somebody please resolve my problem!!!

---

### Post by sudodus on 2014-01-24
I suggest that you add the boot option ***nomodeset*** to the line with starting linux in the grub menu. During boot at the grub menu, press e to enter editing mode and type in nomodeset as the last option (typically after ro quiet splash).

*Edit*: Would it be possible to connect via wired internet and run in text mode? For example borrow an ethernet cable or move the computer to where wired internet is available.

---

### Post by someshangale on 2014-02-04
Thanks [**[COLOR=#dd4814]sudodus[/COLOR]**]("http://ubuntuforums.org/member.php?u=1499021").

I would try your trick.Hope it work or else i would need to find some other way to rectify the blunder i made.

---

### Post by sudodus on 2014-02-04
If you have a chance to use wired internet (ethernet cable), things  would be much easier. Would it be possible for you to either move your  computer or borrow a cable to connect that way to install and test the drivers needed?

I have seen descriptions how to do what you want (install the ATI graphic  card drivers offline and install it through terminal command), but I  have not done it myself. I'm 'spoiled' with a reliable internet  connection :wink:

The following link contains several methods. I hope you will succeed with one of them.

[http://askubuntu.com/questions/974/how-can-i-install-software-or-packages-without-internet-offline](http://askubuntu.com/questions/974/how-can-i-install-software-or-packages-without-internet-offline)

Good luck :-)

---

