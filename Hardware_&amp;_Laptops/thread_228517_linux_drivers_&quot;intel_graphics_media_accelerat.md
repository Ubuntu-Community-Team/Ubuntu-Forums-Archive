---
title: "linux drivers &quot;intel graphics media accelerator 950&quot;"
date: 2006-08-03
forum: Hardware &amp; Laptops
---

### Post by web-man on 2006-08-03
Hi
Anyone have the inux drivers "intel graphics media accelerator 950" ?

---

### Post by lenninct on 2007-06-09
someone plz if you know anything about this, help us

---

### Post by NeoLithium on 2007-06-09
Hmmm, there's 2 sets of drivers in the repos, can you copy and paste the output of ```
lspci
``` just to make sure I don't give you the wrong one? :)

---

### Post by Syke on 2007-06-10
This should install the right drivers:

```
sudo apt-get install xserver-xorg-video-intel
```

---

### Post by nanophobic on 2007-06-10
How is this package different from the default one Ubuntu installs?

---

### Post by Syke on 2007-06-12
"-intel" is essentially the currently maintained version, and as such includes some features that "-i810" doesn't, like support for the latest chipsets, and native resolution setting so tweaks like 915resolution are no longer needed.

---

### Post by lenninct on 2007-06-13
ill say widescreen laptops...

---

### Post by tdwester on 2007-06-14
It works very well, I have the same chipset on my laptop.

---

### Post by zakeen on 2007-07-02
> **Syke said:**
> This should install the right drivers:

```
sudo apt-get install xserver-xorg-video-intel
```

Once I install this, I cant have desktop effects on and I cant enter into my Screen Resolution properties anymore. Is this normal?

---

### Post by FlowerBoy on 2007-07-10
interesting, even when I run this in terminal mode it says that this package doesn't exist
dunno,

---

### Post by o5iri5 on 2007-07-16
Works like a charm on the HP Pavillion dv6206ea, thanks so much...


Just copy and paste (Ctrl+Shift+Insert) the command in your term...

---

