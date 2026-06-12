---
title: "ATI Propietary Driver questions"
date: 2011-07-31
forum: Hardware
---

### Post by tech newbie on 2011-07-31
I have recently come back to Ubuntu and using classic Gnome, I've installed the propiteary driver for my ATI card from hardware drivers tool. Now I heard the latest ATI driver from amd's website breaks on kernel upgrades. Is this true/ If I build a package using the buildpkg in the amd installer and install this way instead of using Ubuntu's built in tool, will the driver break on kernel update? I would prefer not to have the driver from the Ubuntu repo since it is a tad outdated.

---

### Post by weezilla on 2011-08-01
Although I'll leave the question as to whether it will break to someone else, I can offer a couple of things which you may or may not already know.

If you perform a kernel upgrade using apt-get install, when you reboot, your grub will list the old kernel, and the new one you just upgraded to. If the driver or linux breaks, you can just boot into your old kernel, uninstall the driver (see below), boot into new kernel, and reinstall new driver.

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu) 

If you click on your flavor of linux, each one has installation and removal guides. If no one is able to give you an answer here, you may want to go ahead and install using Ubuntu's tools, or ask on amd/ati.

I just did an install of catalyst on the default 10.04.3 LTS kernel. Due to my setup, I think, it isn't working. I tried a kernel upgrade to 2.6.38.10. Catalyst still isn't working. I will try to do a reinstall of catalyst tomorrow. If it starts working, that may be an answer to your question.

One more thing. This is from one of the installation pages from the above link:
> New kernel installed?

In theory, DKMS should automatically install the fglrx kernel module for your new kernel the first time you boot it. Should you need to manually install it:

$ sudo dkms build -m fglrx -k `uname -r`
$ sudo dkms install -m fglrx -k `uname -r`

if amdcccle doesn't work and says Identifier is not a valid word. Use lower case letter in xorg.conf

---

