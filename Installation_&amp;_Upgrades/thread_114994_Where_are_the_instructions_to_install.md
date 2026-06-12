---
title: "Where are the instructions to install"
date: 2006-01-09
forum: Installation &amp; Upgrades
---

### Post by Rick Harvey on 2006-01-09
Im a newbie, just got a Ubuntu machine going.  I want to download and install Thunderbird mail because the mail that came with the Ubuntu looks exactly like outlook express, and I HATE microlimp, so I need to get one that does not make me sick to look at it.

I went to Mozilla's releases and they did not show an installer, and it was compressed.  Is there a link I can download from and install it automatically?

Thanks
Rick Harvey

---

### Post by kaamos on 2006-01-09
Hello and welcome to ubuntu and the forums!

You can install software with synaptic: [https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)
I also suggest you enable the extra repositories to get your hands on more packages: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by manicka on 2006-01-09
Open Synaptic

System--> Administration--. Synaptic Package Manager

and search for and install thunderbird with synaptic

or from a cli

sudo apt-get update
sudo apt-get install mozilla-thunderbird

---

### Post by Rick Harvey on 2006-01-09
Thanks I will work on that in the morning.  One thing is sure, this machine renders images so much better than my windows machines, ever thought about.  It has been a long time coming.  Now if I can get Thunderbird and my mail addresses straightened out, (to one only).  2 servers and a third location, makes it a confusing mess.  That has nothing to do with Linux, but locations, trying to change 2 ISPs and then being here, and using DSL on a 3rd server.

At least I now have a VIRGIN computer.  It has never been raped by microlimp.  It will never have any microlimp software.  Tux will be one happy penguin, huh?

Rick

---

### Post by manicka on 2006-01-09
p.s. don't give up on evolution as a mail client. It looks a bit like outlook, but it's much better integrated into the standard Ubuntu desktop...imho

---

### Post by Rick Harvey on 2006-01-11
Ok I went and found Mozilla Suite and installed it, but it does not have a way to open the bundled mail that is in the Moziilla Suite (like in the windows version)  Does it not have a mail client in the Mozilla Suite for Linux?  Thunderbird for Linux is quite different in the preferences / settings from the Mozilla mail I have for windows.  I want those optional settings here.  

I found a place to set it to "Mozilla Mail", but in the list, it still only shows the Evolution and now also Thunderbird mail. in the list of programs.  How do I download the mail that is bundled with the Mozilla Suite?

This Linux is working so good, so far, I haven't even got pissed off yet today.  I can't say that when I use winduuhs!

Thanks
Rick

---

### Post by Rick Harvey on 2006-01-13
In the Mozilla Suite, v1.7.12,  does the Linux version have the mail client with it,  like in the windows version, or not?

---

### Post by manicka on 2006-01-16
[QUOTE=Rick Harvey]In the Mozilla Suite, v1.7.12,  does the Linux version have the mail client with it,  like in the windows version, or not?[/QUOTE]

sudo apt-get install mozilla-mailnews

---

