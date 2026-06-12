---
title: "Tiny Laptop. Model A360. Network Card."
date: 2005-07-23
forum: Hardware &amp; Laptops
---

### Post by sunoj81 on 2005-07-23
Dear All,

Am from United Arab Emirates. 
I got an old laptop from Tiny Computers ([www.tiny.com)](www.tiny.com)). Model A360. I installed Ubuntu, but unfortunately the network card is not detected by Ubuntu. I would appreciate if anyone can help me out for this issue. 

One more problem am facing is, when the time of installation it didn't ask for the "root" password and now i cannot get into system as "root".

Please help me to troouble-shoot this issue.

Thanks & Regards
Sunoj

---

### Post by balthus on 2005-07-23
Hi Sunoj,

To get some information about your network card model, it would be helpful if you could provide the output of the following command in a terminal :
** lspci **

Normally you should see a line with "Ethernet controller" in it.

Concerning the root password, the fact that you were not asked for a root password during the installation is normal.

Ubuntu deactivates the root account so that you cannot directly login as root.

On the other hand, it uses sudo as the tool which enables you to run commands as root.
E.g. :
**sudo halt**
will stop the computer while you are not root.
Depending on the configuration, sudo may ask for your password.

In case you'd like to become root for more than just one command, you can always type
**sudo -s**

Kind regards
Xavier

---

### Post by varunus on 2005-07-23
Sunoj,

Ubuntu starts with the root account disabled as a security measure.  You can do everything you need by prefixing the "sudo" command in a terminal.  (This will ask you for your password instead of the root password.)   If you wish to enable root, you can do so by typing "sudo passwd" in a terminal.  (You will also have to configure your login manager using System->Administration->Login Screen Setup to let you log in as root graphically.)  I would recommend not doing so, though, and learning the sudo method, as it makes your computer much more secure (people trying to ssh in have to guess your username and your password since root is disabled, and it makes it much harder to damage your system since you have to prefix sudo to a command to do something irreparable.).

 What is the output of "lspci" in a terminal?  This will give us some idea of what ethernet card you have.  Do you have any idea of the brand?

Good luck.

---

### Post by sunoj81 on 2005-07-26
Hi friends,

Am really sorry for a late reply, was busy travelling for some official work. Thanks a lot for ur replies. I need to checkout the output from the provided command and will get back to you, meanwhile I tried to boot a cd (windows 2000 pro & xp) from the same ubuntu installed laptop, unfortunately it isn't booting-up. I tried the same CD with other computers & its working fine. I rechecked the BIOS on laptop and made sure whether it is configured to take the CD-ROM first. 

I would really appreciate helping me out on this too.

Thanks & Regards
Sunoj

---

### Post by Azef on 2007-03-13
hi Sunoj,

I also have a tiny a360+ on which i installed ubuntu with the same problems regarding the network card.

As suggested by Xavier, the command lspci unfortunately did not list the ethernet controller - it lists all other components apart from the crucial! but I am sure you understand that Tiny had a whole host of issues in terms of incompatability. However fruther research reveals the ethernet controller is listed as being, "Intel 82559 Fast Ethernet LAN driver" and i hope this helps.

So Xavier, Sunoj, please help this frustrated Ubuntu Tiny owner resolve this issue as quickly as possible.

Thanking you in advance.

Regards,
Azef

---

