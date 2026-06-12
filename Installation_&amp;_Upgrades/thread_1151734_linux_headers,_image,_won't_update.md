---
title: "linux headers, image, won't update"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by lesterness on 2009-05-07
When I run 

sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade

in Terminal, I get the following error message.

Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.28-12-generic_2.6.28-12.43_i386.deb](http://cn.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.28-12-generic_2.6.28-12.43_i386.deb) Unable to connect to cn.archive.ubuntu.com http:
Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.28-12_2.6.28-12.43_all.deb](http://cn.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.28-12_2.6.28-12.43_all.deb) Unable to connect to cn.archive.ubuntu.com http:
Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.28-12-generic_2.6.28-12.43_i386.deb](http://cn.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.28-12-generic_2.6.28-12.43_i386.deb) Unable to connect to cn.archive.ubuntu.com http:
Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.28.12.16_i386.deb](http://cn.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.28.12.16_i386.deb) Unable to connect to cn.archive.ubuntu.com http:
Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.28.12.16_i386.deb](http://cn.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.28.12.16_i386.deb) Unable to connect to cn.archive.ubuntu.com http:

What should I do next to fix things?

Thanks.

Lesterness

---

### Post by Partyboi2 on 2009-05-07
Hi, try changing your download server in Software Sources.

---

### Post by lesterness on 2009-05-07
> **Partyboi2 said:**
> Hi, try changing your download server in Software Sources.

I switched to the USA servers, got the following:


W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_non-free_binary-i386_Packages)

Any suggestions?

Thanks.

Lesterness

---

### Post by HyRax on 2009-05-07
Looks like you've got a lot of sources files everywhere.

Go into your /etc/apt/sources.list.d/ directory and move or delete ALL files there.

Next make sure that your /etc/apt/sources.list file refers to the American mirror servers (as per the Software Sources tool).

Next re-update your local packages list cache from the terminal with:

```

$ sudo apt-get update

```
...and see if you get any errors. If not, you're good. Do your required system updates and then restore your Medibuntu sources list and whatever else you had in /etc/apt/sources.list.d/ again.

---

