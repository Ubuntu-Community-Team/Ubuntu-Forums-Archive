---
title: "[SOLVED] Upgrading OpenOffice to 3.0"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by beastrace91 on 2008-12-21
Ok so I see several different .deb files on openoffice.org which one should I install to upgrade? Or a better question is open office 3 in the repositories?

~Jeff

---

### Post by davec64 on 2008-12-21
I've loaded it from this repository:

[http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) Intrepid main

Sorry but I can't find the Howto it's here somewhere on the forum though!

If I remember correctly it was just a simple "get rid of 2.4" and select version 3 from synaptic.

Of course the benefit of using the repository is you get the updates (as long as the repository is kept up to date!)

---

### Post by beastrace91 on 2008-12-22
So I should just add that to my repositories and then I should be able to see Open Office 3 in my add/remove programs?

~Jeff

---

### Post by Partyboi2 on 2008-12-22
After you have add the repo all you need to do is 
```
sudo apt-get update &&  sudo apt-get upgrade
```

---

### Post by beastrace91 on 2008-12-22
So adding the following to my sources.list throws an error "unknown url"

[quote="My sources.list"]deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) Intrepid main[/quote]

Did I add this wrong?...

~Jeff

---

### Post by Partyboi2 on 2008-12-22
Open a Terminal and try this
```
echo deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main | sudo tee -a /etc/apt/sources.list
```
```
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by abn91c on 2008-12-22
follow this guide to install openoffice 3.0: [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by beastrace91 on 2008-12-23
Thank you that guide worked like a charm! It is updating now.

~Jeff

---

### Post by jrusso2 on 2008-12-23
Is there any guides to installing Open Office 3 on Hardy?  Or is this not possible?

---

### Post by ubuntu27 on 2008-12-23
> **jrusso2 said:**
> Is there any guides to installing Open Office 3 on Hardy?  Or is this not possible?

[https://launchpad.net/~openoffice-pkgs/+archive](https://launchpad.net/~openoffice-pkgs/+archive)

Yes there is. Just add the following PPA to your Software Sources [System Menu/Administration/Software Sources]

```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
```

```
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
```

Reload or Update your repository.

Now upgrade ;)


Good Luck!

---

### Post by jrusso2 on 2008-12-23
Thanks

---

### Post by jrusso2 on 2009-01-01
I took your advice and installed Open Office 3 but where is the thunderbird calendar I can't find it anywhere.  Except for the thunderbird I have installed already.

---

### Post by ubuntu27 on 2009-01-02
> **jrusso2 said:**
> I took your advice and installed Open Office 3 but where is the thunderbird calendar I can't find it anywhere.  Except for the thunderbird I have installed already.

Thunderbird doesn't come with Calendar. But there is an Calendar Add-on for Thunderbird mail client.  Just install the "[lightning-extension]("apt://lightning-extension")" package from the repositories.

```
sudo apt-get install lightning-extension
```

---

### Post by davidself1001 on 2009-01-03
> **abn91c said:**
> follow this guide to install openoffice 3.0: [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)
I followed this method and all appeared to go as described.  However, I still don't have the office tools in the Applications->Office group.  How do I get them in there?  Where is the oo 3 stuff installed?

---

### Post by abn91c on 2009-01-04
> **davidself1001 said:**
> I followed this method and all appeared to go as described.  However, I still don't have the office tools in the Applications->Office group.  How do I get them in there?  Where is the oo 3 stuff installed?
did you log out?

---

