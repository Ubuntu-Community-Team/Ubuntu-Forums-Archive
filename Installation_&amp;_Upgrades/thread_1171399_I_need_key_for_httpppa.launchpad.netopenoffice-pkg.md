---
title: "I need key for http://ppa.launchpad.net/openoffice-pkgs/ubuntu"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by ivanhoe75 on 2009-05-27
I want use repo
[http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu)

and I need key    *.dpg file to use it. I tried manualy search on website but no result. Help

---

### Post by drs305 on 2009-05-27
If you are getting a message saying you do not have the public key for a launchpad, run this:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com [COLOR="DarkRed"]ENTER.KEY.HERE[/COLOR]

```

Example:
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com [COLOR="DarkRed"]2BBD133164234534[/COLOR]

---

### Post by lncoll on 2009-05-27
To add a ppa repository with it's key follow this link.
[https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories]("https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories")

---

### Post by ivanhoe75 on 2009-06-02
I ve made all steps acording to algorithm from packaging/ppa-launchpad and Ive not succeded ---open key NO_PUBKEY 60D11217247D1CFF is not available ----from update manager, after that I ve entered 

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 60D11217247D1CFF

in terminal and all works fine

---

