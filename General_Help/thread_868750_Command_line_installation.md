---
title: "Command line installation"
date: 2008-07-24
forum: General Help
---

### Post by Ryadt on 2008-07-24
Hi... I am trying to install a command line system on a laptop. After selecting the command line installation mode when I booted from the cd (Alternate cd,Hardy), nothing happens. I don't think it's something wrong with the cd cause it's the same cd with which I installed my current installation.
Any help or suggestions please.

thx

---

### Post by overdrank on 2008-07-24
> **Ryadt said:**
> Hi... I am trying to install a command line system on a laptop. After selecting the command line installation mode when I booted from the cd (Alternate cd,Hardy), nothing happens. I don't think it's something wrong with the cd cause it's the same cd with which I installed my current installation.
Any help or suggestions please.

thx

Hi and can you tell us some system specs? And also you may still need to check the cd for errors as I had a similar issue and the cd did have a error.

---

### Post by Vivaldi Gloria on 2008-07-24
It's been a while since I used the alt cd. You choose the cli version by pressing F4 at the boot menu and then choose install, right?

I'd check the md5sum of the cd anyway.

You can also try the minimal CD available from 

[https://help.ubuntu.com/community/In...tion/MinimalCD](https://help.ubuntu.com/community/In...tion/MinimalCD)

The install of min CD takes a bit longer than alt CD because it downloads everyting from the net. So use min CD if you have a decent connection.

To install a cli system using the min cd you have to enter "cli" in the boot line and press enter.

There is also a server cd which installs a cli sytem but it contains server programs. Don't install this unless you are making a server.

---

### Post by Ryadt on 2008-07-24
> **overdrank said:**
> Hi and can you tell us some system specs? And also you may still need to check the cd for errors as I had a similar issue and the cd did have a error.

I did check the cd for errors, no error was detected.
Specs are 
1.5Gb RAM
80Gb 
1.83Ghz processor.

---

### Post by Ryadt on 2008-08-04
> **Ryadt said:**
> Hi... I am trying to install a command line system on a laptop. After selecting the command line installation mode when I booted from the cd (Alternate cd,Hardy), nothing happens. I don't think it's something wrong with the cd cause it's the same cd with which I installed my current installation.
Any help or suggestions please.

thx

Hi.. Have not been able to work this out...Re-downloaded the alternate cd, the md5sum check was perfect.. Tried it to install the command line version but no luck. Was able to install the normal version on the same laptop with the same cd.
Anyone...plz...

---

### Post by Titan8990 on 2008-08-04
If you already have the full install there you could turn it in to a command line system with these commands:

sudo apt-get remove --purge ubuntu-desktop

sudo apt-get autoremove

Edit: Prior to this you should probably stop GDM:

sudo /etc/init.d/gdm stop

Then hit CTRL+ALT+F1, log in and perform the commands listed above.

---

### Post by Vivaldi Gloria on 2008-08-04
> **Ryadt said:**
> Hi.. Have not been able to work this out...Re-downloaded the alternate cd, the md5sum check was perfect.. Tried it to install the command line version but no luck. Was able to install the normal version on the same laptop with the same cd.
Anyone...plz...

Are you pressing F4 and selecting command line install? Only then press install.

---

### Post by Ryadt on 2008-08-04
> **Titan8990 said:**
> If you already have the full install there you could turn it in to a command line system with these commands:

sudo apt-get remove --purge ubuntu-desktop

sudo apt-get autoremove

Edit: Prior to this you should probably stop GDM:

sudo /etc/init.d/gdm stop

Then hit CTRL+ALT+F1, log in and perform the commands listed above.

I will give this a try..
thx...

---

### Post by Titan8990 on 2008-08-04
I know this will turn it into a CLI system but I am curious to find out if it is going to leave behind GUI only programs such as OO.org when it removes the desktop.

---

### Post by Wiebelhaus on 2008-08-04
> **Titan8990 said:**
> If you already have the full install there you could turn it in to a command line system with these commands:

sudo apt-get remove --purge ubuntu-desktop

sudo apt-get autoremove

Edit: Prior to this you should probably stop GDM:

sudo /etc/init.d/gdm stop

Then hit CTRL+ALT+F1, log in and perform the commands listed above.

I agree with this user.

---

