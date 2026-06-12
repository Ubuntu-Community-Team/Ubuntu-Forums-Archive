---
title: "[SOLVED] Installing restricted-extras without everything"
date: 2008-08-02
forum: General Help
---

### Post by dstein on 2008-08-02
Hi. I would like to install the restricted-extras package without installing everything (like Flash). I use aptitude for package management. Is there any command that can tell aptitude to install a package, while omitting specified dependencies? While the example I gave here is specific to restricted-extras, I am looking for a general way to do this. That is, I am not interested in which packages that I can install separately that will give me all the restricted extras except flash (unless this is the only method, of course). More specifically, I am looking to do something such as: ```
$aptitude install restricted-extras -omit flash
``` That is just a completely hypothetical example though.

Also, on a somewhat similar note, is there any way to see where a package will be installed to and what files will be installed? In the past, I have used Synaptic for the installation location, looking at the 'Installed Files' tab of the Properties menu. However, this only works for installed packages, and the directory that they will be installed to (not the files that will be installed).

Thanks.

---

### Post by Joeb454 on 2008-08-02
You could probably run ```
sudo apt-get install ubuntu-restricted-extras && sudo apt-get purge flashplugin-nonfree
``` which would then remove flash afterwards.

Other than that I don't think you can omit packages from a meta-package

---

### Post by aysiu on 2008-08-02
I think you can't omit a dependency - a metapackage by definition is an empty package that depends on a bunch of other packages. Best to install *ubuntu-restricted-extras* and then just remove Flash.

---

### Post by brandyamy on 2008-10-30
Install support for playback of many types of audio and video, web fonts, Java, Flash, and DVD playback all in one go. Ubuntu restricted extras allow you to easy install everything that Ubuntu can’t include by default for legal reasons.

---

