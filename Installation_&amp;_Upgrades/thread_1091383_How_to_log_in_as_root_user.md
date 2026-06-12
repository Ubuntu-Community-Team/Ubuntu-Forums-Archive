---
title: "How to log in as root user?"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by r1e1z1a on 2009-03-09
Hello and thanks for answering to my last Questions(very much!!)

how can i log in as root user!!!(in ubuntu 8.10)

(I should log in as root for installing my NVIDIA driver)

---

### Post by Therion on 2009-03-09
You can simply type **sudo** on the command line and enter your password when prompted.

*Voila!*  You're operating as Root.

If you want to actually *create* a root-user account that's different, but really, sudo should get you through what you need to do.

---

### Post by Neo_The_User on 2009-03-09
I can't post a guide or a HOWTO on how to log in as root from the login screen because its against the rules. Maybe somebody else will pop in this thread and teach you how to do that. ...I could just send you a private message too on how to login as root from the login screen if you insist.

---

### Post by m_duck on 2009-03-09
It's not advised to enable the root account. For security, Ubuntu has the root account disabled by default. Have a read through [this]("https://help.ubuntu.com/community/RootSudo"). The majority of things can be accomplished through sudo - meaning **su**per user **do**. I don't think I've come across anything that has actually ***needed*** the root account to be enabled.

---

### Post by Neo_The_User on 2009-03-09
> **m_duck said:**
> It's not advised to enable the root account. It is disabled by default in Ubuntu for security. Have a read through [this](https://help.ubuntu.com/community/RootSudo). The majority of things can be accomplished through sudo. I don't think I've come across anything that has ***needed*** the root account to be enabled.

Well it takes the hassle out of typing "sudo" every 2 seconds. I just open up ttys. tty7 for my desktop environment and tty2 for my root account. That way I'm already logged in as root and a normal user. But sudo works just as well as far as permissions go. I also disabled the need to enter a password for sudo by editing visudo as root. ...What I did may not be a good idea for you though if you don't know what you're doing. Doesn't su mean switch user? Because when I login as root via cli, when I type in su - neo, it switches the user and takes away root privileges meaning sudo is needed.

---

### Post by m_duck on 2009-03-09
In the linked page there are methods to have a root session in console without having the root user enabled. I can't remember the ins and outs but it's safer than having the root account fully enabled. I'm primarily an arch user so I do tend to have the root account enabled, but especially as a new user it is best to use sudo, if only to make you think twice about the commands that are being entered. Having said that, I thought I was in ABT :rolleyes:

---

### Post by Neo_The_User on 2009-03-09
Oh sweet I love Arch!

---

### Post by Therion on 2009-03-09
> **Neo_The_User said:**
> 

Well it takes the hassle out of typing "sudo" every 2 seconds.
I thought one use of "sudo" was good for... Is it 15 minutes?  Something like that.  Or so I thought.  Is that not the case?

---

### Post by m_duck on 2009-03-09
Yeah, well, using sudo for one command, and entering the password will have it so you don't need the password for 15 mins, but you will still need to prefix commands with sudo if the commands need to be run as a privalidged user.

---

### Post by Therion on 2009-03-09
> **m_duck said:**
> Yeah, well, using sudo for one command, and entering the password will have it so you don't need the password for 15 mins, but you will still need to prefix commands with sudo if the commands need to be run as a privalidged user.
Thanks for the clarification.

Hope you're happy, BTW... I'm downloading an Arch install CD.

---

### Post by sisco311 on 2009-03-09
> **r1e1z1a said:**
> Hello and thanks for answering to my last Questions(very much!!)

how can i log in as root user!!!(in ubuntu 8.10)

(I should log in as root for installing my NVIDIA driver)

Go to *System->Administration->Hardware Drivers* and enable the driver.

[http://psychocats.net/ubuntu/nvidia]("http://psychocats.net/ubuntu/nvidia") 

[uhelp]community/BinaryDriverHowto/Nvidia[/uhelp]

---

### Post by Neo_The_User on 2009-03-09
> **sisco311 said:**
> Go to *System->Administration->Hardware Drivers* and enable the driver.

[http://psychocats.net/ubuntu/nvidia]("http://psychocats.net/ubuntu/nvidia") 

[uhelp]community/BinaryDriverHowto/Nvidia[/uhelp]

Hahaha. Or that.

---

