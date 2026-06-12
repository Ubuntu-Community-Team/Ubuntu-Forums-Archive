---
title: "Need Help on updating to Firefox 3.5.x"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by neverknowsbest~!! on 2009-09-23
Hello everyone! I would like to start off that I am loving Ubuntu. I Just installed version 9.04 which I believe is nicknamed "Jaunty Jackalope. I have noticed that the default Firefox comes in 3.0 but I would like to update it to a non-beta 3.5 version. I checked the repos and found Shiretoko but Shiretoko is the codename for Firefox's beta versions or so I am told.

I found some blog articles showing the method of downloading the archive from Mozilla's site etc. but when I did that, I had to reinstall Ubuntu because it screwed with my network settings.

Another reason why I would like to update Firefox to 3.5 is so that I can also use the latest foxdie theme.

---

### Post by zvacet on 2009-09-23
You don´t have to reinstall to fix problems.This is not another OS.To upgrade you have to download tar.bz2 package from [here]("http://www.mozilla.com/en-US/products/download.html") to your home directory. After that applications>accessories>terminal and type ( you can copy/paste)

```
if [[ ! -f /usr/bin/firefox ]]; then sudo apt-get update && sudo apt-get install firefox; fi && if [[ -e ~/.mozilla ]]; then cp -R ~/.mozilla ~/.mozilla.backup; fi && sudo tar -jxvf firefox-3*.tar.bz2 -C /opt && rm firefox-3*.tar.bz2 && sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup && sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins && sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox && sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```

---

### Post by Yvan300 on 2009-09-23
Or an even easier alternative would be to just use a small program called ubuntuzilla which will automize the installation of the new version of firefox.Instructions are found on this site [http://tombuntu.com/index.php/2009/07/15/install-firefox-35-in-ubuntu-904-using-ubuntuzilla/](http://tombuntu.com/index.php/2009/07/15/install-firefox-35-in-ubuntu-904-using-ubuntuzilla/)

---

### Post by Khakilang on 2009-09-24
I just downloaded Mozilla 3.5.4 which is Shiretoko from Ubuntu repo and its work fine for now.

---

### Post by neverknowsbest~!! on 2009-09-24
> **Koh Kook Loon said:**
> I just downloaded Mozilla 3.5.4 which is Shiretoko from Ubuntu repo and its work fine for now.

Hmm I did the same but only got 3.5.2 so i updated it using the update manager and only got 3.5.3.. is there something I should be tweaking? I would like to avoid using the terminal as much as possible because I sort of have bad history with it.

---

### Post by prinknash on 2009-09-24
> **neverknowsbest~!! said:**
> Hmm I did the same but only got 3.5.2 so i updated it using the update manager and only got 3.5.3.. is there something I should be tweaking? I would like to avoid using the terminal as much as possible because I sort of have bad history with it.

According to Mozilla's Firefox website, 3.5.3 is the latest version available. As you say, it's now available through update manager.

p

---

### Post by neverknowsbest~!! on 2009-09-25
> **prinknash said:**
> According to Mozilla's Firefox website, 3.5.3 is the latest version available. As you say, it's now available through update manager.

p

Thanks, I guess I am too impatient.

---

