---
title: "Configure New Install For New User"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by Nopposan on 2009-10-15
Hi there, everybody.  I know there's a way to install Xubuntu such that the first time the computer boots the user will be able to make configuration decisions (time settings, language) and create a new user.  How can I configure a completed installation so that it works the same way but still uses my customized settings in /etc/skel?

Basically, I configured the Xubuntu desktop and installed software packages that I think a new user would want; now, I want to make sure the system doesn't have any other user's home folders on there and that there are no users other than root and the new user, whose name I will not know until they come to pick up the laptop.  I'm working for a non-profit computer refurbisher that distributes their computers to low-income residents.  This is the first computer that I've installed Linux on for them; the default Xubuntu desktop had to be configured to look more like Windows XP, the organization's logo was put on an Xfce splash screen, i8kmon had to be installed and its defaults made to run as daemon for all new users -- Dell Inspiron laptop needs it -- and several apps that we think our users will want needed to be installed.  Now, I just want the computer to give that "brand new" experience to the new user.

Please help me if you can.  Thanks in advance for any help you can offer.

Cheers.

---

### Post by Bucky Ball on 2009-10-15
Are you are saying can you change the user name and password now you have set the machine up so they can put in a user name and password of their choosing?

---

### Post by tommcd on 2009-10-16
For future reference the alternate install CD has an option for: **OEM install (for manufacturers)**. On the Karmic beta CD you have to hit F4 to see it as an option. It is an option on the Jaunty alternate CD as well. You may want to try that next time. This would give the "brand new" computer experience you are looking for. I don't know if the OEM install gives you the option to install additional software or customizations beyond what is on the CD though.

---

### Post by Nopposan on 2009-10-16
I was aware of the OEM install but I was also under the impression that it would not allow me to customize or install new software during or following the OEM install if I used it.  I am still under that impression, but perhaps I'm wrong.  

Another possible downside to using the OEM install on an old laptop is that it might not allow me to test out the install before I distribute the laptop; if I've already tested out the install on the exact same hardware then this might be o.k., but as there are many models for me to utilize and I've only just begun introducing Linux here, well I need to test things out first or people will have problems and then just decide Linux is no good.  For example, there was the issue with the Dell Inspiron needing i8kmon to run the temp monitoring and control the fans; if I'd just done a straight default install and distributed this without testing then I'd be giving the end user a machine that was seriously flawed and unwittingly sabotaged.

Please, if anyone knows how to change my current installation so as to eliminate all users but root and also prompt a new user to create a username and password at next boot, please let me know.  As far as I know, using the administrative boot option under GRUB and logging in as root, then removing users and home folders via the command line will just result in the X-window system becoming unusable.

---

### Post by Nopposan on 2009-10-16
O.K., well I guess I was wrong about OEM.

[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview]("https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview")

> Once the system is configured to your satisfaction, run 'sudo oem-configure-prepare'.  This will cause the system to delete the temporary 'oem' user and ask the end user various configuration questions the next time it boots.

'Sorry to waste your time folks, I guess I'll just use the OEM install next time.

Thanks anyway.

---

### Post by Bucky Ball on 2009-10-16
Well, I've learned something.

---

### Post by Nopposan on 2009-10-17
I'd also like to add that it was possible for me to do oem-config-prepare AFTER doing a normal install.  All I had to do was ```
apt-get install oem-config
```then create the user "oem," give oem sudo-admin priveleges, log out, log in as oem, delete the initial user account and home folder, then run sudo oem-config-prepare, and shut down; now when I boot the computer I'm faced with a dialogue that allows me to create a new user and password along with locale settings.  'Tried that out and it works!

Thanks again.

---

### Post by tommcd on 2009-10-18
> **Bucky Ball said:**
> Well, I've learned something.
I learned a lot here also. I knew there must be a way to do this, since companies like System76 and Zareason sell computers with Ubuntu preinstalled. I know that System76 includes some custom drivers and stuff, so OEM customization on a production level scale is possible. I suspected that the OEM install was the way to go about it, but I have no experience in this area. Now I know for sure.

---

