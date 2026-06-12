---
title: "Firefox starts with offline mode"
date: 2008-07-22
forum: General Help
---

### Post by rushikesh988 on 2008-07-22
hello friends I am getting some problem with my  Firefox 
It always starts with the offline mode ??
Actually I am connected to internet via Lan and MY default connection device is 
" eth0:avahi " and yes their is some anther problem with my UBUNTU PC It shows the Icon OF I am not connected to any network  
bt I am able  to access the network

can some body help me???

---

### Post by Potatoj316 on 2008-07-22
If I remember correctly there is an option if firefox's settings (edit->prefrences) that lets you tell it to start in offline mode, try looking for that.

---

### Post by rushikesh988 on 2008-07-22
can you tell me its full path edit-->preferences -->??? what ??
I AM USING FIREFOX 3.5 beta version

---

### Post by Potatoj316 on 2008-07-22
I just said I think theres one, maybe under the connections tab (thats one of the tabs right) im not using linux right now (unfortunatly) and its no fun if I tell you exactly where it is, this is how you learn

---

### Post by coderpp on 2008-07-22
[https://answers.launchpad.net/ubuntu/+faq/96](https://answers.launchpad.net/ubuntu/+faq/96)
> Please open Firefox and type into address bar about:config
if is the first time you are using about:config on Firefox, a warning window come in front of you, please confirm the "promise".

Then search ( type the parameter name into the "filter row" field ) for the Firefox config param named:

network.online

double click on the filtered row and set it to true

Quit and restart Firefox


Edit:
> **rushikesh988 said:**
> 
Actually I am connected to internet via Lan and MY default connection device is 
" eth0:avahi " and yes their is some anther problem with my UBUNTU PC It shows the Icon OF I am not connected to any network  
bt I am able  to access the network

Then problem is not with Firefox, but with network-manager.

---

### Post by rushikesh988 on 2008-07-22
anybody know how to install firefox 3.0 


By typing some command in terminal
as:
su7do apt-get install <something>

---

### Post by coderpp on 2008-07-22
[http://www.cyberciti.biz/faq/ubuntu-linux-install-firefox-3-web-browser/](http://www.cyberciti.biz/faq/ubuntu-linux-install-firefox-3-web-browser/)
> 
sudo apt-get update
sudo apt-get install firefox-3.0


---

