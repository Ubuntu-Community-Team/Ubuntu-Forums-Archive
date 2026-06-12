---
title: "howto upgrade sshd in 8.04 LTS"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by tuthsok on 2009-08-13
Hi,

I have been provided an Ubuntu 8.04 LTS dedicated server which seems to have OpenSSH 4.7p1 installed and the apt-get system considers it "the newest version".

I am not having luck finding documentation on how to unmask later versions of OpenSSH for installation using the ubuntu package management system. Can somebody please point me to documents explaining this or give me a quick rundown on how it would be performed.

I am more familliar with package management within the Gentoo portage system.

Thank you,

Chris

---

### Post by Partyboi2 on 2009-08-13
Hi, you can add a 3rd party repo to your sources.list to upgrade to a later release. Have a look at [[COLOR=Blue]this[/COLOR]]("https://launchpad.net/%7Erainct/+archive/ppa") 3rd party repo, it offers openssh. All you need to do is add the repo and the key, this can be done by opening up a terminal (Applications>Accessories.Terminal) and open your sources.list
```
gksu gedit /etc/apt/sources.list
``` add these 2 lines to the bottom of the file
```
deb [http://ppa.launchpad.net/rainct/ppa/ubuntu](http://ppa.launchpad.net/rainct/ppa/ubuntu) hardy main 
deb-src [http://ppa.launchpad.net/rainct/ppa/ubuntu](http://ppa.launchpad.net/rainct/ppa/ubuntu) hardy main
```
save the changes and back in the terminal add the key
```
gpg --keyserver keyserver.ubuntu.com --recv 9F762A8E
gpg --export --armor 9F762A8E | sudo apt-key add -
```
then
```
sudo apt-get update
sudo apt-get upgrade
```

---

