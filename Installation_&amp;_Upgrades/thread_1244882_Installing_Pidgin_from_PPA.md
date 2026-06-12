---
title: "Installing Pidgin from PPA?"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by cody7002002 on 2009-08-19
I wanted to be up to date with the latest version of pidgin so I followed the instructions on [this]("http://www.pidgin.im/download/ubuntu/") website. How can I make sure that the installing and updating was successful? How can I check which version I'm currently using?

---

### Post by nilarimogard on 2009-08-20
Pidgin has not been updated in the PPA and I don't think it will be... But I suggest you add the GetDeb repository:

```
echo "deb http://getdeb.masio.com.mx/ jaunty/" | sudo tee -a /etc/apt/sources.list.d/getdeb.list && sudo apt-get update
```

and then just:

```
sudo apt-get update && sudo apt-get upgrade
```

You will then have Pidgin 2.6.1 installed (you can check this by going to Help > About in Pidgin)

---

