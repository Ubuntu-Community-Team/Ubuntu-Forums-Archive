---
title: "RockerRAID 2320 installation help needed for 22.04"
date: 2022-04-28
forum: Hardware
---

### Post by rynr on 2022-04-28
[COLOR=#000000][FONT=Verdana]Hi everybody,[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]is it possible to get the RocketRAID 2320 working in Ubuntu 22.04?[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]The connected drives just should used in pass through.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Found a repo on git ([/FONT][/COLOR][https://github.com/siratcliff/RocketRAID](https://github.com/siratcliff/RocketRAID)[COLOR=#000000][FONT=Verdana]) wich one states its running under Kernel 5.3. So i tried following the instructions from the README.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]For building with dkms i get following error:
[/FONT][/COLOR]
```
[FONT=Verdana]rynr@rynr-desktop:/usr/src/RocketRAID/rr232x-linux-src-v1.10$ sudo dkms add -m rr232x -v 1.10[/FONT]
[FONT=Verdana]Creating symlink /var/lib/dkms/rr232x/1.10/source -> /usr/src/rr232x-1.10[/FONT]
[FONT=Verdana]rynr@rynr-desktop:/usr/src/RocketRAID/rr232x-linux-src-v1.10$ sudo dkms build -m rr232x -v 1.10[/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]Kernel preparation unnecessary for this kernel. Skipping...[/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]Building module:[/FONT]
[FONT=Verdana]cleaning build area...[/FONT]
[FONT=Verdana]make -j4 KERNELRELEASE=5.15.0-27-generic -C product/rr232x/linux/ KERNELDIR=/lib/modules/5.15.0-27-generic/build...(bad exit status: 2)[/FONT]
[FONT=Verdana]ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/rr232x-dkms.0.crash'[/FONT]
[FONT=Verdana]Error! Bad return status for module build on kernel: 5.15.0-27-generic (x86_64)[/FONT]
[FONT=Verdana]Consult /var/lib/dkms/rr232x/1.10/build/make.log for more information.[/FONT]
[FONT=Verdana]rynr@rynr-desktop:/usr/src/RocketRAID/rr232x-linux-src-v1.10$ [/FONT]

```
[COLOR=#000000][FONT=Verdana]For building without dkms i get this error:
[/FONT][/COLOR]
```
[FONT=Verdana]rynr@rynr-desktop:/usr/src/RocketRAID/rr232x-linux-src-v1.10/product/rr232x/linux$ sudo make install[/FONT]
[FONT=Verdana]make[1]: Verzeichnis „/usr/src/linux-headers-5.15.0-27-generic“ wird betreten[/FONT]
[FONT=Verdana]make[1]: Makefile: Datei oder Verzeichnis nicht gefunden[/FONT]
[FONT=Verdana]make[1]: *** Keine Regel, um „Makefile“ zu erstellen.  Schluss.[/FONT]
[FONT=Verdana]make[1]: Verzeichnis „/usr/src/linux-headers-5.15.0-27-generic“ wird verlassen[/FONT]
[FONT=Verdana]make: *** [../../../inc/linux/Makefile.def:104: rr232x.ko] Fehler 2[/FONT]
[FONT=Verdana]rynr@rynr-desktop:/usr/src/RocketRAID/rr232x-linux-src-v1.10/product/rr232x/linux$ [/FONT]
[FONT=Verdana]
[/FONT]

```
[COLOR=#000000][FONT=Verdana]Can somebody help with compiling or provide working drivers?[/FONT][/COLOR]


[COLOR=#000000][FONT=Verdana]Thanks in advance.[/FONT][/COLOR]

---

