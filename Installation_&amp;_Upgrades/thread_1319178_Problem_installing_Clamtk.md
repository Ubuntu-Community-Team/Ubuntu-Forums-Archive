---
title: "Problem installing Clamtk"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by Ian Ferguson on 2009-11-08
I have been trying to install Clamav with the clamtk graphical front end.

( I know the arguments about whether or not you need antivirus in Linux, but I need to share files with a Windows machine, and forward emails to people who use Windows).

When I try to install it using Synaptic, I get The attached screenshot.

So I tried doing it from command line and got this:

```
ian@Fergubuntu:~$ sudo apt-get install clamtk
[sudo] password for ian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  clamtk: Depends: clamav (>= 0.90) but it is not going to be installed
E: Broken packages
ian@Fergubuntu:~$ 
```Any ideas?

---

### Post by MelDJ on 2009-11-08
go to synaptic, click on edit, then fix broken packages. after that, try installing clamtk

---

### Post by Ian Ferguson on 2009-11-08
> **MelDJ said:**
> go to synaptic, click on edit, then fix broken packages. after that, try installing clamtk
I'm afraid that still doesn't work

---

### Post by MelDJ on 2009-11-08
do you know what the broken packages are? 
try: [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by tony1212 on 2009-11-08
I usually install Clam by ticking the Clamtk package and letting that pick up all the dependences, I have installed it with no problem since doing a reinstall of 9.10 You could try marking it for complete removal doing that then doing a reinstall, it worked a few days ago when I mucked up an installation of virtual box.

---

### Post by Ian Ferguson on 2009-11-09
I've solved the problem by opening Synaptic, doing Settings>Preferences, clicking the "Distribution" tab, and changing from "Always prefer the highest version" (the default option) to "Prefer versions from Jaunty".

I guess it must have been trying to install a Karmic version when I'm still using Jaunty.

Thanks for you suggestions. ):P

---

