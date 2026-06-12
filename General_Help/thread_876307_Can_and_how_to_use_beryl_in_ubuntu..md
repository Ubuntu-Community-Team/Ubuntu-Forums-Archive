---
title: "Can and how to use beryl in ubuntu."
date: 2008-07-31
forum: General Help
---

### Post by broivan on 2008-07-31
Can and how to use beryl in ubuntu. Please help.

---

### Post by Rumel on 2008-07-31
You can't use Beryl anymore, it's been replaced by Compiz Fuison.

---

### Post by dje on 2008-07-31
Beryl is discontinued, replaced by compiz fusion a merge of compiz and beryl ;) It is included with ubuntu, just go to System >> Preferences >> Appearance and go to the effects tab you can enable it from there.
You may want to install the advanced settings manager to enable extra effects, in a terminal (Applications >> Accessories >> Terminal) run the following:
```
sudo apt-get install compizconfig-settings-manager
```
Once installed you can find it at System >> Preferences >> Advanced Desktop Settings

If you cannot enable the effects, have a look in System >> Administration >> Drivers manager and see if there are any graphics drivers that are available to install, if there are no drivers to install please post the output of the following command from the terminal:
```
lspci
```

hope that helps,
dje

---

### Post by daimaru on 2008-07-31
install "compizconfig-settings-manager" to get full access to compiz options.
```
sudo apt-get compizconfig-settings-manager[code]
It will show up under System-Prefernece-Advanced Desktop Effects Settings.

Or you can install the simple version (Simple CompizConfig Settings Manager)
[code]sudo apt-get install simple-ccsm
```
Which I do not really like. So i recommend going with the advanced  one.

---

### Post by UbuntuNerd on 2008-07-31
this guide is very simple 

[http://thegabfather.wordpress.com/2008/05/17/how-to-install-compiz-fusion-in-ubuntu-hardy-heron/]("http://thegabfather.wordpress.com/2008/05/17/how-to-install-compiz-fusion-in-ubuntu-hardy-heron/")

---

### Post by gjoellee on 2008-07-31
I have mad a video:
[http://www.youtube.com/watch?v=uz4ZoRUk0GM](http://www.youtube.com/watch?v=uz4ZoRUk0GM)

---

### Post by steveneddy on 2008-08-01
> **Rumel said:**
> You can't use Beryl anymore, it's been replaced by Compiz Fuison.

You actually **can** use beryl. **[COLOR="Blue"]Many people are doing it as we speak.[/COLOR]**

But Beryl isn't supported anymore and it has been merged with Compiz Fusion.

Compiz is installed by default in Ubuntu 8.04 Hardy Heron.

---

