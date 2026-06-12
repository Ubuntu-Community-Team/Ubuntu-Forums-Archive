---
title: "/var/cache/apt/archives"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by ayu on 2009-05-24
Hi,

Are ALL the files downloaded by update-manager and synaptics stored in /var/cache/apt/archives? Is it safe to simply move these files to an external drive? And then if I need to upgrade another machine without an internet connection, can I just copy the files to that machine and it knows it doesn't have to download them?

Thanks,
Ayu

---

### Post by cariboo on 2009-05-25
You can copy the archived packages to another partition, and then use:

```
sudo apt-get clean
```

to remove them properly.

---

### Post by ayu on 2009-05-26
> **cariboo907 said:**
> You can copy the archived packages to another partition, and then use:

```
sudo apt-get clean
```

to remove them properly.

Thanks. Do I need to do anything if I want to use them later? Or can I just copy them into the directory?

---

### Post by ayu on 2009-06-02
So what do I need to do to use them later?

Thanks,
Ayu

---

### Post by mcduck on 2009-06-02
> **ayu said:**
> So what do I need to do to use them later?

Thanks,
Ayu

Yes, you can just copy them back and apt-get/synaptic will use theminstead of dowlaoding same package versions again from the net. Or you can insall them one at a time with GDebi or dpkg. Or even install them all at once with "sudo dpkg -i *.deb".

---

### Post by kranny on 2009-06-02
All u need is to backup the deb files and copy them to a new system,followed by a 
```
sudo apt-get update
```

Now you can install them offline thru synaptic

---

### Post by ayu on 2009-06-02
> **mcduck said:**
> Yes, you can just copy them back and apt-get/synaptic will use theminstead of dowlaoding same package versions again from the net. Or you can insall them one at a time with GDebi or dpkg. Or even install them all at once with "sudo dpkg -i *.deb".

> **kranny said:**
> All u need is to backup the deb files and copy them to a new system,followed by a 
```
sudo apt-get update
```

Now you can install them offline thru synaptic

Thanks guys! Is update-manager just a frontend for synaptic/apt-get, and so it will also see them?

---

