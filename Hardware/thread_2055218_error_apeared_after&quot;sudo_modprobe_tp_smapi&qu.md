---
title: "error apeared after&quot;sudo modprobe tp_smapi&quot;"
date: 2012-09-08
forum: Hardware
---

### Post by Shareit2you on 2012-09-08
I want to change my Thinkpad's charging area.

So I did following steps:

1.run "sudo aptitude install tp-smapi-source"
  it seems that everything was ok

2.run "sudo m-a a-i tp-smapi"
  i think sth is building. 
  after the building is over,it showed me the folling message:

[I]Updated infos about 1 packages
Getting source for kernel version: 3.2.0-23-generic
Kernel headers available in /usr/src/linux-headers-3.2.0-23-generic
Creating symlink...
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

Done!
unpack 
Extracting the package tarball, /usr/src/tp-smapi.tar.bz2, please wait...
"/usr/share/modass/overrides/tp-smapi-source" build KVERS=3.2.0-23-generic KSRC=/usr/src/linux KDREV=3.2.0-23.36 kdist_image
Done with /usr/src/tp-smapi-modules-3.2.0-23-generic_0.41-1+3.2.0-23.36_amd64.deb .
dpkg -Ei /usr/src/tp-smapi-modules-3.2.0-23-generic_0.41-1+3.2.0-23.36_amd64.deb 
dpkg: error: configuration error: /etc/dpkg/dpkg.cfg.d/multiarch:1: unknown option 'foreign-architecture'

I: Direct installation failed, trying to post-install the dependencies

apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.[/I]

3.run "sudo modprobe tp-smapi"
  it showed me the following message:
*FATAL: Error inserting tp_smapi (/lib/modules/3.2.0-23-generic/extra/tp_smapi.ko): No such device or address*

but in fact,the tp_smapi.ko was in the place of the message metioned "/lib/modules/3.2.0-23-generic/extra/"

why? a error ? 
I think there was no error.:?:

---

### Post by Shareit2you on 2012-09-09
Any one know this? help me,plz.

---

### Post by 2F4U on 2012-09-09
May I ask why you are compiling from source when the tp_smapi module is in the default repositories /tp-smapi-dkms *(universe))*? I never had a problems with this module, given that your ThinkPad model is supported.

---

### Post by linrunner on 2012-09-09
Hi,

as 2F4U already said, you should install the package **tp-smapi-dkms**. Remove **tp-smapi-source** before[B].

[/B]Nevertheless, **tp_smapi** doesn't load. So please tell us: which ThinkPad model do you have exactly?

Btw: you should update your whole system with
```
sudo apt-get update
sudo apt-get dist-upgrade
```the shown kernel 3.2.0-23 is **very** old.

---

