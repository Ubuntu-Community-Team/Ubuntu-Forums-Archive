---
title: "How to Remove VirtualBox (or any program)"
date: 2008-08-07
forum: General Help
---

### Post by MikeyDL on 2008-08-07
How do you uninstall a program?  

I installed VirtualBox with SPM but it doesn't work correctly on my 64 ubuntu so after reading forums saw that a manual install from site seemed to fix the kernel error message I was getting.  I downloaded the .deb and tried to install but it says its already installed so it won't install or write over the old package.  

These manual installs don't seem to show up on my "Add/Remove" menu.  So reading up more on the forums someone posted a basic command to remove a package:

[FONT="Courier New"]sudo dpkg -r vmware[/FONT]

however, when I try to run that i get an error message:

[FONT="Courier New"]dpkg - warning: ignoring request to remove virtualbox which isn't installed.[/FONT]

Any tips on how I can uninstall.  Also is there a better way to take off a package you've installed.  For instance I installed vmware but want to take it off.  If i enter [FONT="Courier New"]sudo dpkg -r vmware[/FONT] then I just get the same "can't find" error message.

Thanks

---

### Post by tuxxy on 2008-08-07
Open synaptic and search for **virtualbox**, then select it for removal and click apply button in the top left.

Second option you could remove it from the terminal by **sudo apt-get remove (app name)**, so

```
sudo apt-get remove virtualbox*
```

---

### Post by y@w on 2008-08-07
vmware and VirtualBox are two completely different products.. Which one did you install? vmware has a different way of uninstalling. I think you run vmware-uninstall.sh(or pl, I forget).

---

### Post by y@w on 2008-08-07
I should say: there's no Debian packages for vmware.

---

### Post by jocko on 2008-08-07
> **y@w said:**
> I should say: there's no Debian packages for vmware.
ehh... Yes there are. In the partner repo.

---

### Post by jocko on 2008-08-07
> **MikeyDL said:**
> How do you uninstall a program?  

I installed VirtualBox with SPM but it doesn't work correctly on my 64 ubuntu so after reading forums saw that a manual install from site seemed to fix the kernel error message I was getting.  I downloaded the .deb and tried to install but it says its already installed so it won't install or write over the old package.  

These manual installs don't seem to show up on my "Add/Remove" menu.  So reading up more on the forums someone posted a basic command to remove a package:

[FONT=Courier New]sudo dpkg -r vmware[/FONT]

however, when I try to run that i get an error message:

[FONT=Courier New]dpkg - warning: ignoring request to remove virtualbox which isn't installed.[/FONT]

Any tips on how I can uninstall.  Also is there a better way to take off a package you've installed.  For instance I installed vmware but want to take it off.  If i enter [FONT=Courier New]sudo dpkg -r vmware[/FONT] then I just get the same "can't find" error message.

Thanks

Why don't you just open up synaptic and search for virtualbox? Then mark it for complete removal and apply.
How did you install it? Synaptic? Then the name of the package is "virtualbox-ose".

---

### Post by Uchiha_madara on 2008-08-07
Some times the Applications have got the Updates when you make the Update


so when you remove the Program with there Updates Type 
it is Better, for the System from unused data
so To remove The virtual box :

> 
sudo apt-get --purge remove virtualbox


> 
sudo apt-get --purge remove "Application name"


---

### Post by MikeyDL on 2008-08-07
Thanks!  I'll give SPM a shot.  Didn't think of that.  I actually installed both and wanted to remove both.  I have a Win license for vmware but that doesn't work on the linux package so didn't want to spend another $189 for a linux license.  So installed vmware and want to get rid of it now.

---

### Post by y@w on 2008-08-07
> **jocko said:**
> ehh... Yes there are. In the partner repo.

In the partner repo?

```

$ cat /etc/apt/sources.list | grep partner
## 'partner' repository. This software is not part of Ubuntu, but is
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

$ sudo apt-get update

$ aptitude search vmware
i A xserver-xorg-video-vmware       - X.Org X server -- VMware display driver   
$ 



```

Am I missing a repository?

---

### Post by jocko on 2008-08-08
Sorry, I wasn't aware that they had removed vmware from hardy. I checked the partner repo, and it only has packages for feisty and gutsy... so I was partially wrong (I still use gutsy).

---

### Post by y@w on 2008-08-08
I thought they had finally put it in the repo's for Hardy.. You got me all excited ;)

---

### Post by Down_with_Windows on 2009-12-12
I was trying to uninstall virtualbox myself, because It would not run from the startup disc I created.  I ran down the list in Synaptic and was not able to find it.  However, when I did a search for virtualbox, it showed in the window, and then I was able to mark it for removal.

---

### Post by vishvesh on 2010-01-25
This command worked for me. I was able to uninstall virtualbox 3.1
> sudo apt-get remove virtualbox*

---

### Post by mercvrivs on 2011-04-14
```
sudo apt-get purge virtualbox-ose virtualbox-ose-dkms
```

---

