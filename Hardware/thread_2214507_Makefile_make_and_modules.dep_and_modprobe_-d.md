---
title: "Makefile make and modules.dep and modprobe -d *"
date: 2014-04-01
forum: Hardware
---

### Post by waterreedshimmer on 2014-04-01
```
[COLOR=#008000][COLOR=#000000]modprobe -d *[/COLOR][/COLOR]
```[COLOR=#008000][COLOR=#000000]
FATAL: Could not load Bureau/lib/modules/3.11.0-19-generic/modules.dep: No such file or directory
[COLOR=#008000][COLOR=#000000](Bureau means Desktop in french)
Another time:
FATAL: Could not load bin/lib/modules/3.11.0-19-generic/modules.dep: No such file or directory
Another time:
FATAL: [/COLOR][/COLOR]Could not load fonts/lib/modules/3.11.0-19-generic/modules.dep: No such file or directory

```
uname -r
```
3.11.0-19-generic
```

sudo update-initramfs -c -k 3.11.0-19-generic
```
update-initramfs: Generating /boot/initrd.img-3.11.0-19-generic
According to: [http://www.linuxquestions.org/questions/debian-26/modprobe-fatal-could-not-load-lib-modules-modules-dep-335214/](http://www.linuxquestions.org/questions/debian-26/modprobe-fatal-could-not-load-lib-modules-modules-dep-335214/)

[COLOR=#0000ff]Don't know what to do with this[/COLOR].

```
cd /lib/modules/3.11.0-19-generic/build/lib/modules/
```
bash: cd: /lib/modules/3.11.0-19-generic/build/lib/modules/: Aucun fichier ou dossier de ce type

```
cd /lib/modules/
ls
cd ./3.11.0-19-generic/
cd ./build
cd ./lib
ls
```
fonts  Kconfig  Kconfig.debug  Kconfig.kgdb  Kconfig.kmemcheck  lz4  lzo  Makefile  mpi  raid6  reed_solomon  xz  zlib_deflate  zlib_inflate

```
cd ./modules
```
bash: cd: ./modules: Aucun fichier ou dossier de ce type

Don't understand what to do ?

```

fairy@tales:/lib/modules/3.11.0-19-generic/build/lib$ make
```
make: *** Pas de règle pour fabriquer la cible « /gen_crc32table », nécessaire pour « /crc32table.h ». Arrêt.

[/COLOR][/COLOR]

---

