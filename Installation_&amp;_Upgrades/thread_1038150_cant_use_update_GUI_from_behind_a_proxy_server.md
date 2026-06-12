---
title: "cant use update GUI from behind a proxy server"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by pk_rulz on 2009-01-12
Hi

I have installed Ubuntu 8.10. My university uses a proxy server which needs to be authenticated.

I have given my login name and password at

System >> Administration >> Synaptic Package Manager >> Settings >> Preferences >> Network >> Manual Proxy Configuration and given my login details in the authenticate tab

However when I use the update manager and click on reload I get a  message saying
.
.
.
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_IN.bz2)  Could not resolve 'pradeep.podal'
.
.
.

where pradeep.podal is my login name ....

Any Ideas what is going wrong ... Please help

Rgds
Pradeep

---

### Post by avtolle on 2009-01-12
Take a qucik look at /etc/apt/sources.list ```
cat /etc/apt/sources.list
```to see if your login name has somehow become attached to any of the sources. If so, you will need to edit the file using the text editor of your choice to remove that.

EDIT: you will need to run the above from a terminal, accessed through Applications>Accessories>Terminal.

---

### Post by torgrot on 2009-01-12
I would also check Synaptic Package Manager.  Under preferences, network there is a place to enter the proxy server name and information.  I have always had to set it up in both places in order to get out through our proxy server here.

torgrot

---

### Post by pk_rulz on 2009-01-15
Tried both ....

The file /etc/apt/sources.list contains nothing related to my login ....
Also updated the network proxy in my preferences ...

Can some one tell me which file maintains my login name and password ... so that I can have a look there and find is everything is fine there

Thanks
Pradeep

---

### Post by pk_rulz on 2009-01-15
Ok there is some info I got .... I suspected the dot in my name to be culprit and  it turns out that indeed it is .... when I tried a friends login without any dot the update went pass through this stage ... although I still got an error that my key is not valid  ... but atleast it did not say that it was not able to resolve the <login-name> ... Any ideas ... I even tried this "pradeep\.podal" and but to no avail ... any ideas on how can I do with the  DOT in my login-name

---

### Post by pk_rulz on 2009-01-18
Any updates ... any 1

---

