---
title: "OpenOffice 3.0 Error"
date: 2008-11-19
forum: General Help
---

### Post by mschraier on 2008-11-19
I think I made a mistake.  I initially had the Ubuntu version of OOo 3.0 installed. I then wanted to use the version from the OpenOffice web site.  I thought I uninstalled the Ubuntu version.  Anyhow, bottom line,  I now get an error about recovering a document.  What I want to do is to purge every reference to any version of OpenOffice and do a clean install of it.  How do I go about doing that?  I am running Intrepid.

---

### Post by frankleeee on 2008-11-19
> **mschraier said:**
> I think I made a mistake.  I initially had the Ubuntu version of OOo 3.0 installed. I then wanted to use the version from the OpenOffice web site.  I thought I uninstalled the Ubuntu version.  Anyhow, bottom line,  I now get an error about recovering a document.  What I want to do is to purge every reference to any version of OpenOffice and do a clean install of it.  How do I go about doing that?  I am running Intrepid.

If you install ubuntu tweak it will install OO 3 from it's 3rd party section.
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
If you are not familiar with this application it can do a lot of stuff efficiently.
The Tweak install is a launchpad release, here it actually is.
[https://launchpad.net/~openoffice-pkgs/+archive](https://launchpad.net/~openoffice-pkgs/+archive)

---

### Post by tuxxy on 2008-11-19
Search for OpenOffice in synaptic and remove all files, also a clean may delete some unused files

```
sudo apt-get autoremove
```

```
sudo apt-get clean
```

---

