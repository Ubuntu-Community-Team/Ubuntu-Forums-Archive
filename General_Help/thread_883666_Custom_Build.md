---
title: "Custom Build"
date: 2008-08-08
forum: General Help
---

### Post by AsIzZy on 2008-08-08
Hi Guys,
Iam new to linux and have little linux knowledge but i can learn.
I would like to be able to get a live CD from which installation can be done (like Ubuntu). What id like to have on this live CD is a custom Ubuntu configured for my specs and aswell being able to install it with the custom settings and configuration.

1)Access to student records - requires telnet from a terminal supporting VT220 and ISO8859-1

2)Mailer such as evolution configured to use my Exchange server

3)VPN access. Currently works using Cisco client but this installs kernel modules and has to be re-installed each time there is a kernel upgrade.
Maybe VPNC?

4)rdesktop to give remote access to xxx.xxx.xxx.au

5)Fancy effects such as switchable themes from Linux/Windows/Apple would be nice.

6)Browser configured to use xxx proxy. Preferably can switch proxy on/off using something like MM3 plugin.

I would like to have this as a live cd/ and installation disc aswell. if you guys can help me out on how to achieve it will be a great help. like if i can get some kind of a step by step help, i know im asking too much but please i want this to work.

thanks.

---

### Post by nbayiha on 2008-08-08
ALL that in a live CD ?

---

### Post by nazish on 2008-08-08
what you are asking will take a lot of time to do it.

There are projects like linux from scratch which let you build your own custom linux, but they require some expertise.

You may try the reconstructer utility which is in the ubuntu repos. It is a graphical tool with which you can custom build your own cd. But I dont think it will cover all your requirements.

more info about reconstructor can be found at [http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/)

---

### Post by AsIzZy on 2008-08-08
> **nbayiha said:**
> ALL that in a live CD ?
Yes i would like to have all that on a live cd.

---

### Post by AsIzZy on 2008-08-08
Like i know that there is a Ubuntu live cd/installation disc all i want is i just add the requirements that im asking.

---

### Post by northern lights on 2008-08-08
> **nazish said:**
> You may try the reconstructer utility which is in the ubuntu repos. It is a graphical tool with which you can custom build your own cd. But I dont think it will cover all your requirements.
[http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/)
This is your best bet, anything beyond reconstructor would indeed be a time consuming task and is - no offense - most likely beyond your scope right now.

---

### Post by red_team316 on 2008-08-09
I'm with the Reconstructor project and while what you are wanting to do, some of it could be done by reconstructor, most of the customizations you have listed are going to require you to chroot into your LiveCD and manually make the changes. You may want to look into remastersys. I know some of the Linux Mint builds were made through a combination of reconstructor and remastersys. UCK is also another option but I can't really comment on how it may help you with the customizations you're looking for.

If you're planning on using KDE, you can build the AKDC themes and add them to your live CD for Windows themes. Other than that, there are plenty of Mac/Apple type of themes available.

Like northern lights said, it seems that most of what you want may be beyond your scope, but don't let that discourage you. Actually trying to do it yourself is going to be the best way for you to learn it. Mainly your going to need to become familiar with making the customizations manually, but using a customization program such as reconstructor will help.

---

