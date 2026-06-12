---
title: "new 8.10 install, unable to install krb5-user"
date: 2008-10-31
forum: General Help
---

### Post by blaked on 2008-10-31
clean install, performing

blake@bobo:/etc$ sudo apt-get install krb5-user
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package krb5-user is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package krb5-user has no installation candidate

Any help appreciated.

blaked

---

### Post by Yellow Pasque on 2008-10-31
That's strange. Perhaps all of your repos are not enabled?
Check System -> Administration -> Software Sources

My Synaptic shows krb5-user as available from the main repo.
Ubuntu packages shows it here: [http://packages.ubuntu.com/intrepid/krb5-user](http://packages.ubuntu.com/intrepid/krb5-user)

---

### Post by blaked on 2008-10-31
> **Temüjin said:**
> That's strange. Perhaps all of your repos are not enabled?
Check System -> Administration -> Software Sources

My Synaptic shows krb5-user as available from the main repo.
Ubuntu packages shows it here: [http://packages.ubuntu.com/intrepid/krb5-user](http://packages.ubuntu.com/intrepid/krb5-user)

I should have the default list:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

---

### Post by blaked on 2008-10-31
> **Temüjin said:**
> That's strange. Perhaps all of your repos are not enabled?
Check System -> Administration -> Software Sources

My Synaptic shows krb5-user as available from the main repo.
Ubuntu packages shows it here: [http://packages.ubuntu.com/intrepid/krb5-user](http://packages.ubuntu.com/intrepid/krb5-user)

Sorry, I needed to re-read your message.  The top 4 are checked under software sources.

---

### Post by Yellow Pasque on 2008-10-31
If those are the only repos in your /etc/apt/sources.list, then something is wrong, because those repos are only for security updates. The default should look like this:
```
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-security main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-security main restricted multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe main multiverse restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe main multiverse restricted
```

---

### Post by blaked on 2008-11-03
I added those lines and re-ran apt-get udpate, but I recieve the same error.

---

### Post by blaked on 2008-11-03
Is there a way I can download the needed files locally and run from there?

---

### Post by Yellow Pasque on 2008-11-03
You can download the package from packages.ubuntu.com, but you should still figure out why you can't get it from the repo. Do you see the package in System -> Administration -> Synaptic?

EDIT: Do you have the heimdal-clients package installed? (It conflicts with krb5)

---

### Post by blaked on 2008-11-03
The package didn't appear in Synaptic

and it was a completely fresh install, so no Heimdall conflict.  First thing I tried to install after the OS booted was krb5-user.

I'd love any insight into troubleshooting the problem.  I was able to manually download the .deb file, but this is a headache.

---

### Post by Yellow Pasque on 2008-11-03
Post your entire /etc/apt/sources.list file
```
gedit /etc/apt/sources.list
```

> First thing I tried to install after the OS booted was krb5-user
- Have you been able to get any other package from the repos?
- Is your internet connection functioning normally? 
- Do you use a proxy?

---

