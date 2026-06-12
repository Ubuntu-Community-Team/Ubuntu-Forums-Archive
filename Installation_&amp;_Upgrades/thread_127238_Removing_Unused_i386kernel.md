---
title: "Removing Unused i386kernel"
date: 2006-02-08
forum: Installation &amp; Upgrades
---

### Post by John.Michael.Kane on 2006-02-08
How can you remove unused i386kernel from kubuntu using adept. i have tried, and it gives errors. i have install the propper kernel so it says. however i have no use for the old one.

---

### Post by BenTyreman on 2006-02-08
Much easier to do in the terminal. Run
```
dpkg -l 'linux-image*'|grep ii
```

Look for the version you want to remove. For instance, I have linux-image-2.6.15-15-386 installed.

You will then want to run
```
sudo apt-get remove linux-386 linux-image-2.6.15-15-386 linux-image-386
  linux-restricted-modules-2.6.15-15-386 linux-restricted-modules-386
```

---

