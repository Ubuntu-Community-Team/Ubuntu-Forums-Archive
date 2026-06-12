---
title: "How do I uninstall thinkfinger?"
date: 2009-12-15
forum: Hardware
---

### Post by n3xtgen on 2009-12-15
I installed thinkfinger using the following guide:

```
http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger
```

I can not get it to work and keep getting "Could not claim USB device". How do I uninstall thinkfinger? I am also new to Ubuntu;)

Thanks

---

### Post by IcarusR on 2009-12-15
If you installed it from a deb file you should be able to uninstall from synaptic.

System > Administration > Synaptic Package Manager 
Enter your password 
Search for package
Hilite package
Right click 
Select 'Mark For Removal'
Hit 'Apply' button

---

### Post by n3xtgen on 2009-12-15
I did if from the source. Any way to remove that?

---

### Post by IcarusR on 2009-12-16
From the source directory (where you extracted the tarball to) run
```
make uninstall
```

Check the readme or install files included with the source they may give uninstall info.

If all else fails manually delete all installed files.
To find installed files run 'make install again & note location of files.

---

