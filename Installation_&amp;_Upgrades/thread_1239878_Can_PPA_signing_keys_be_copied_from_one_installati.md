---
title: "Can PPA signing keys be copied from one installation to another ?"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by brjoon1021 on 2009-08-14
Hi,

I have two computers running ubuntu. They have exactly the same repositories enabled. However, my laptop keeps spitting out signing key errors when I update apt / synaptic.

The desktop, with the same repos does not give me any errors. Where can I find the PPA keys and can I then save them to a thumb drive and install them in the laptop to get rid of the errors ?

If this is doable, or even what everyone does do... please give me the know-how to get it done.

Thanks,

B

---

### Post by Partyboi2 on 2009-08-14
Hi, you can open a terminal on your laptop and download and add the key with
```
gpg --keyserver keyserver.ubuntu.com --recv 4874D3686E80C6B7
gpg --export --armor 4874D3686E80C6B7  | sudo apt-key add -
``` * You would need to change the key number ( 4874D3686E80C6B7) to the ones listed when you run
```
sudo apt-get update
```

---

### Post by brjoon1021 on 2009-08-14
thanks !

---

