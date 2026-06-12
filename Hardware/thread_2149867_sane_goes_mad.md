---
title: "sane goes mad"
date: 2013-05-30
forum: Hardware
---

### Post by mringer on 2013-05-30
Konica magicolor 1690MF, Lubuntu 12.04, latest versions of foo2zjs and xsane
installed & configured as described here:

[https://help.ubuntu.com/community/KONICA%20MINOLTA%201690MF](https://help.ubuntu.com/community/KONICA%20MINOLTA%201690MF)

```
scanimage -V
scanimage (sane-backends) 1.0.22; backend version 1.0.22
```

On command

```
xsane
```

I get 

```
lcms: Error #12288; File '' not found

```

in the terminal and a panel that says

```
could not open scanner ICM profile
```

on screen. If I persist,  I can get a preview (of very poor quality
but for all I know this may be normal) but it wont actually scan.

Please:

how do I tell sane what file to look for?
what file do I need and where can I find it?
where should it be installed?

thank you

---

### Post by dargaud on 2013-05-30
I don't have a local install of sane, but see if you can disable color profiles in its many options.

---

