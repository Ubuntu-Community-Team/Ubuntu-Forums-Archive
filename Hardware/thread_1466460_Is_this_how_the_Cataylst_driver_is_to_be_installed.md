---
title: "Is this how the Cataylst driver is to be installed manually?"
date: 2010-04-30
forum: Hardware
---

### Post by Fatfool on 2010-04-30
Good day

Could These steps be verified for 64 bit Lucid?

download the drivers from [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-10-4-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-10-4-x86.x86_64.run)

cd to the directory then

```
./ati-driver-installer-10-4-x86.x86_64.run --buildpkg Ubuntu/lucid

```

i then get 4 packages

```
fglrx_8.723-0ubuntu1_amd64.deb
```
```
fglrx-amdcccle_8.723-0ubuntu1_amd64.deb
```
```
fglrx-dev_8.723-0ubuntu1_amd64.deb
```
```
fglrx-modaliases_8.723-0ubuntu1_amd64.deb
```
plus this document:
```
fglrx-installer_8.723-0ubuntu1_amd64.changes
```


I then proceed to install

```
fglrx_8.723-0ubuntu1_amd64.deb
```
```
fglrx-amdcccle_8.723-0ubuntu1_amd64.deb
```

however, after that, when i type the command 'fglrxinfo'

i get 

```
Segmentation Fault
```

no driver seems to be working, I can't even set the fancy desktop effects and the command 'amdcccle' doesn't work.

---

### Post by jaycee23 on 2010-04-30
Have been trying to get this driver to work - have both Karmic and Lucid - fails to work on either!!!

Sticking with 10.3 on Karmic and Lucid works well with the restricted driver it offers you.

Please post back if you get 10.4 to work

---

### Post by Fatfool on 2010-04-30
> **jaycee23 said:**
> Have been trying to get this driver to work - have both Karmic and Lucid - fails to work on either!!!

Sticking with 10.3 on Karmic and Lucid works well with the restricted driver it offers you.

Please post back if you get 10.4 to work
10.4 works when you use the restricted drivers. I had to remove the manually installed one and use the restricted ones.

damn, isn't Linux like supposed to give us more 'freedom'? Why do I always have to rely on Canonical to get things installed through the respositries.

---

