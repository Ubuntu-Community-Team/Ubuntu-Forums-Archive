---
title: "libgupnp-igd-1.0.so.2.0.1"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by sileliasdan on 2009-09-17
Hello Forum!

I've been trying to update my packages but I keep getting this persistent error message: 

/var/cache/apt/archives/libgupnp-igd-1.0-2_0.1.3-3~jjamsn4_i386.deb: trying to overwrite `/usr/lib/libgupnp-igd-1.0.so.2.0.1', which is also in package libgupnp-igd

My searches on this has yielded no hits! I believe it's something to do with aMsn. 

Your input as always is greatly appreciated! 

Daniel

---

### Post by quixote on 2009-09-18
I don't know what the error message is trying to tell you.  (To me, it looks like a warning that you could ignore??.)  The easiest step is often to see whether a general "fix broken packages" helps: ```
sudo dpkg --configure -a
```

---

### Post by Partyboi2 on 2009-09-18
The libgupnp-igd that is being updated is trying to overwrite a older file. if you want you can force overwrite the file with[FONT=monospace]
[/FONT]```
cd /var/cache/apt/archives
```
```
sudo dpkg --force-overwrite --install libgupnp-igd-1.0-2_0.1.3-3~jjamsn4_i386.deb
```

---

### Post by sileliasdan on 2009-09-20
Thank you. Your post seems to have worked. 

The results:

daniel@blueberry:~$ cd /var/cache/apt/archives
daniel@blueberry:/var/cache/apt/archives$ sudo dpkg --force-overwrite --install libgupnp-igd-1.0-2_0.1.3-3~jjamsn4_i386.deb
(Reading database ... 182647 files and directories currently installed.)
Unpacking libgupnp-igd-1.0-2 (from libgupnp-igd-1.0-2_0.1.3-3~jjamsn4_i386.deb) ...
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/libgupnp-igd-1.0.so.2.0.1', which is also in package libgupnp-igd
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/libgupnp-igd-1.0.so.2', which is also in package libgupnp-igd
Setting up libgupnp-igd-1.0-2 (0.1.3-3~jjamsn4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

---

