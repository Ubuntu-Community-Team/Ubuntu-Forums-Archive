---
title: "Adobe Reader"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by n3tef on 2009-11-04
Hi All,
 
My son bought me this laptop  with a ubuntu operating system and I am learning. I have been a windows guy for a long time so I need help.

I went to adobe website and downloaded the following file but I can not install it. What do I need to do to install the reader?

AdbeRdr9.2-1_i486linux_enu.bin

---

### Post by lisati on 2009-11-04
If you want to view PDF files, you should be able to use "evince" which comes installed as standard on most Ubuntu installations.

If you want to use the file you've downloaded, open up a termainal (Applications->Accesories->Terminal), then type (assuming you downloaded the file to your desktop):
```
cd ~/Desktop
chmod +X AdbeRdr9.2-1_i486linux_enu.bin 
AdbeRdr9.2-1_i486linux_enu.bin 

```

---

### Post by ausmuso on 2009-11-04
The best way to get a working Adobe reader is by using Synaptic. First enable the Medibuntu repositories (read the Ubuntu Wiki on this), then start Synaptic and search for "acroread". Mark it for installation and it's all automatic from there on.

Welcome to the Ubuntu community and good luck!

---

### Post by aysiu on 2009-11-04
I would recommend installing it using the package manager.

**Step 1**:
Make sure you have extra repositories enabled
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

**Step 2**:
Install it
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Ishipaco on 2010-08-14
> **lisati said:**
> If you want to view PDF files, you should be able to use "evince" which comes installed as standard on most Ubuntu installations.

If you want to use the file you've downloaded, open up a termainal (Applications->Accesories->Terminal), then type (assuming you downloaded the file to your desktop):
```
cd ~/Desktop
chmod +X AdbeRdr9.2-1_i486linux_enu.bin 
**AdbeRdr9.2-1_i486linux_enu.bin** 

```

Since you would be trying to execute a file that may not be in your $PATH, you may get a "command not found" error. In that case, use the following command for the one in bold above:

**./AdbeRdr9.2-1_i486linux_enu.bin**

---

