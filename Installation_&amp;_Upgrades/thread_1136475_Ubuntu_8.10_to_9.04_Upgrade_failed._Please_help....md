---
title: "Ubuntu 8.10 to 9.04 Upgrade failed. Please help..."
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by blackfalcon03 on 2009-04-25
Hi Friends,

I am facing a big trouble in Upgarding from 8.10 to 9.04.:(

It started of as a normal upgrade using the upgrade manager. Even though I faced some trouble downloading the packages because of loss of internet connection, I was able to continue from where I left out, when I tried the upgrade again.
Once the packages are downloaded it started installing the packages one by one. Everything was going fine until the PC shutdown itself for no reason. I was really confused:confused: what happened as i did not really see it happening.

Now when I boot the PC, it loads the GRUB Loader. I was surprised to see only the 8.10 version entries in the GRUB menu list. However when I selected the latest entry i got the 9.04 splash screen and the login screen also resembled the 9.04 login. Once i entered my credentials, it took me to a blank screen- No icons, No taskbar, nothing....

I am able to start the terminal window with the shortcut key i had set earlier while using the 8.10 version. And using the terminal I can start browsers and applications required. However I could not get the internet connection also(I connect from a Wireless router). I am sure that the upgrade did not succeed before the PC went down, but not sure on how to repair my system with 9.04 in complete working condition.

Could you please help me...........:cry:

For your information I faced a similar problem while upgrading from 8.04 to 8.10. During that period I got some commands that could redo the upgrade step by step through the terminal from the forums. The upgrade still had minor problems but i was able to fix it in due course.

---

### Post by syncmasterpt on 2009-04-25
I have exactly the same problem!

After upgrade My KDE desktop has no taskbar, but plasma is running...

---

### Post by Unhban on 2009-04-25
Hi! I had problems upgrading to 9.10 similar to yours, shown in another post elsewhere.

I found the answer was to get to a command line and type:

[B]sudo apt-get update

sudo apt-get dist-upgrade[/B]

The machine then completed the upgrade nicely and I rebooted and all was well. You must, of course, have internet available.

Please let me know if this works OK.

Unh.

---

### Post by syncmasterpt on 2009-04-25
Ok.

 This seems to solve the issue:

 mv ~/.kde ~/.kde_old
 kquitapp plasma
 plasma&

 A new .kde4 is created and the taskbar appears.

 mv ~/.kde_old ~/kde

-----------------------------------

No it doesn't work. After reboot, same issue....

---

### Post by abn91c on 2009-04-25
Uhnban solution works, had the same thing happen to me thursday night, had to finish upgrade from the command line as listed in the above post. If using Kubuntu and you may lose the network connection, re-adding the network widget to the lower task bar should get the network going again.be prepared it may take several hours to upgrade

---

### Post by syncmasterpt on 2009-04-25
The main issue here is that:

 On 8.10 I've already had 4.2.2.

 That version used .kde for storing settings

 After the upgrade it seems that 9.04 kde packages want to use .kde4 but, there is a conflict with .kde directory....

EDIT:---

 Ok, went to .kde/share/config and moved out the plasma* files

 kquitapp plasma
 
 and 

 plasma&

It seems to work now...

---

### Post by shahzadak on 2009-08-11
I fixed it by :

dpkg --configure -a

it did a lot of configurations and after restart it was fixed. It replaced my gdm.conf file too (I am on gnome).

---

