---
title: "Updates wont install"
date: 2008-07-25
forum: General Help
---

### Post by infocom on 2008-07-25
Hi
I have 243 updates ready to install but it wont. I get an error. First I get an error saying there is an error in dpkg so I uncheck that one for installation. Then when I try to install I get an error saying:-

> 
Not all changes and updates succeeded. For further details of the failure please expand the 'terminal' panel below
which says..
> Extracting templates from packages 100%
Preconfiguring packages...

So it stops the whole updates, so I cant update anything anymore.

Thanks

---

### Post by ajmorris on 2008-07-25
hi there,
have you tried running a dpkg reconfigure?
```
sudo dpkg-reconfigure -a
```

AJ

---

### Post by infocom on 2008-07-25
i get this when running that command:-

```
dpkg-query: parse error, in file `/var/lib/dpkg/status' near line 3984 package `jockey-common':
 `Replaces' field, invalid package name `restrict%d-manager-core': character `%' not allowed (only letters, digits and characters `-+._')
/usr/sbin/dpkg-reconfigure: acl is not installed.
```

---

### Post by Joeb454 on 2008-07-26
Sounds like a bad install of dpkg or apt.

Also what release are you running? If you haven't long installed the system, I'd recommend re-burning a CD and trying to install again :)

---

### Post by ajmorris on 2008-07-26
> **infocom said:**
> i get this when running that command:-

```
dpkg-query: parse error, in file `/var/lib/dpkg/status' near line 3984 package `jockey-common':
 `Replaces' field, invalid package name `restrict%d-manager-core': character `%' not allowed (only letters, digits and characters `-+._')
/usr/sbin/dpkg-reconfigure: acl is not installed.
```

I am sorry to tell you this, but that appears to be a borked apt. You will have to re-install ubuntu :(

AJ

---

### Post by bushda on 2008-07-26
> **ajmorris said:**
> I am sorry to tell you this, but that appears to be a borked apt. You will have to re-install ubuntu :(

AJ

Why couldn't he boot to an Ubuntu live CD, copy that file to a USB drive, reboot to the OS, and copy the file from the USB file over the existing screwed up file?

No it's not perfect, but if it gets this guy going again without forcing him to do a total reinstall then it's worth it.

---

### Post by infocom on 2008-07-27
I think I'll reinstall anyway, because as stated in another thread it hangs nearly everytime I run it. Was hoping if I keep installing updates it might fix one day (because it seems to be a very common problem), but as I cant install updates I'll just re-install it. Actually may give another distro a go because of this hanging issue, does not seem stable enough to me. 
Thanks

---

