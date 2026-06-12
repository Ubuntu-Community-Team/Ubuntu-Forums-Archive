---
title: "amd catalyst 13.4 and ubuntu 12.04.1 weird problem"
date: 2013-05-31
forum: Hardware
---

### Post by rogerdv on 2013-05-31
I have downloaded lates stable catalyst version and genrated the db files according to this [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) they install successfully, but the module and programs cant be loaded,  this is the X log:  [    16.146] (II) LoadModule: "fglrx" [    16.147] (WW) Warning, couldn't open module fglrx [    16.147] (II) UnloadModule: "fglrx" [    16.147] (II) Unloading fglrx [    16.147] (EE) Failed to load module "fglrx" (module does not exist, 0)  amdconfig and amdcccle  cant neither be found, but they are there, at /usr/lib/fglrx/bin.  Should I discard this and download drivers again via repository?

---

### Post by Mark Phelps on 2013-05-31
From what I recently read, Catalyst 13.4 is a Beta version, not a Stable version.  Others have had similar problems -- which were corrected when they used the Legacy 13.1 Stable version, instead.  You should try that -- link: [http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx]("http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx")

---

### Post by rogerdv on 2013-05-31
13.6 is beta, 13.4 is stable. I fixed the problem going directly to /usr/lib/... and running aticonfig there, also I uninstalled nvidia driver, restarted and everything started working.

---

### Post by Mark Phelps on 2013-05-31
Sorry ... because you said 12.04.1, I made the presumption that you were running one of the Legacy HD 2x/3x/4x series cards -- for which Catalyst 13.1 is the stable version.

---

### Post by Deviljho on 2013-05-31
Are you using a Radeon 2xxx-4xxx or Radeon 5xxx-7000 series card? If 2xxx-4xxx then you can only use 13.1 legacy - [http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip](http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip) . Use this guide to install - [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI), but for the > 
sudo apt-get install dh-make dh-modaliases execstack

instead use
 > 
sudo apt-get install dh-make dh-modaliases execstack dkms lib32gcc1 libc6-i386

or you will get compiling errors.

---

