---
title: "Add/Remove Progs"
date: 2005-01-08
forum: Installation &amp; Upgrades
---

### Post by Kaddo on 2005-01-08
I've just got Ubuntu running and still learning my way around.
How does one install and uninstall applications? 

Also, I downloaded an update for my dialup modem, 
but not so sure how to use it.

Your helpful suggestions will be appreciated.

---

### Post by Adrenal on 2005-01-08
Applications/System/Synaptic
Play around with that
As for the modem, not sure there, but i'm sure someone will have an answer

---

### Post by Karlos on 2005-01-09
Have a little look through this.........

[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by Karlos on 2005-01-09
I also think it's worth learning about "apt-get"

[http://forum.libranet.com/viewtopic.php?t=6363&highlight=aptget](http://forum.libranet.com/viewtopic.php?t=6363&highlight=aptget)

that is a thread i started on the libranet forum a few months back

check out some of the links on that page....I learnt a lot from that...

hope this helps

..Karlos

---

### Post by Karlos on 2005-01-09
apt-get install package
installs package
apt-get remove package
uninstalls package
apt-get --purge remove package
removes packages config files too
apt-cache seach package
searches for specified string and displays results
apt-cache policy package
especially useful: used to determine if a package is installed, and if so, what version number. Also, when using multiple software sources, as does Libranet, all versions available in all available
repositories will be shown. Depending on what you system is pinned to, you can always override by adding an extra switch on your apt-get command. EX: apt-get -t unstable install openoffice.org.
apt-get update

update your sources.list file
apt-get upgrade
upgrades system to the most current versions of software that your system is pinned to.
apt-get --no-act install package
this is like a dry run. Displayed will be the results on your system without actually doing it. Not a bad idea sometimes.
And of course, always best to read the man page.

---

### Post by twisted_steel on 2005-01-10
[QUOTE=Kaddo]
  Also, I downloaded an update for my dialup modem, 
 but not so sure how to use it.[/QUOTE]Can you point us to the page where you downloaded the update? Perhaps we can figure out more from there. :)

---

### Post by Benn on 2005-01-10
Synaptic is an excellent software. When you've played whit this tool and move around it you should add the Universe sources, so you'll be able to download a huge variety of software.

Don't forget to use Ubuntu Forums and read UbuntuGuide!

Good Look!  8)

---

### Post by Kaddo on 2005-01-11
[QUOTE=twisted_steel]Can you point us to the page where you downloaded the update? Perhaps we can figure out more from there. :)[/QUOTE]

Thanks, problem solved.

---

### Post by Kaddo on 2005-01-11
[QUOTE=Karlos]apt-get install package
installs package
apt-get remove package
uninstalls package
[/QUOTE]

Thanks for the help, will do as suggested.

---

