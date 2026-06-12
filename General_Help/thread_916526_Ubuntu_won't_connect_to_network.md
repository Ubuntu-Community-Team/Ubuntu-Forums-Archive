---
title: "Ubuntu won't connect to network"
date: 2008-09-11
forum: General Help
---

### Post by Danilux on 2008-09-11
Hi i just installed ubuntu 8.04 and it's a great OS, i come form windows wanting to stay in linux, Everything worked great the only problem i have is that my wireless card can't connect, i can see my network and other networks as well but when i connect it stays connecting for a while and then it asks for the password again, i have search a lot and first i downloaded a linux driver for my card from D-Link named DRIVER LINUX_DWL-G520_v1.2.1b.tar.gz, bad thing is i'm new and don't know how to install the driver, searching in the forum i got to download wicd_1.5.1_all.deb cause a guy had a similar problem and managed to make it work with this program but again don't know how to intall it, Any help is appreciated, Thanks in advanced.

---

### Post by hwttdz on 2008-09-11
I think with a deb file you can just double click and it will open an install dialog.  Also you can go to the terminal and do
```
dpkg -i debfile
```

To "unzip" a tar.gz, one can do
```
tar -xzf archive_name.tar.gz
```
x for extract, z for gzip compression type, f to maintain file structure
or you can just double click again.  

After unzipping you will probably have a deb or something which you can install as above.

---

