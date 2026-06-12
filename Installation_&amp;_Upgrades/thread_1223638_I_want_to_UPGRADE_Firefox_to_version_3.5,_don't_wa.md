---
title: "I want to UPGRADE Firefox to version 3.5, don't want to have both 3 and 3.5."
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by Repgahroll on 2009-07-26
Hello.

Firefox 3.5 is the new stable and standard version, but the official repos still supporting the old 3.0 version, there are unsupported 3.1 and 3.5 versions in the repos, but i could not find a way to UPGRADE the firefox, i installed the 3.5 version, but it installs in parallel and it's called Shiretoko (development nickname)... i don't want to install another Firefox, i want to upgrade my Firefox.

Is there a simple way to do that? I could uninstall the ff3, but it will uninstall a lot of other things too, like java plugin, sunbird, and a ton of other important thing that i don't want to write down and install them all later.

Thanks and sorry my english.

---

### Post by ptn107 on 2009-07-26
```
sudo aptitude install firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support && sudo aptitude purge firefox-3.0 firefox-3.0-branding firefox-3.0-gnome-support
```

---

### Post by Repgahroll on 2009-07-26
Thanks man, but look this:
```
The following packages will be REMOVED:
  dvd-slideshow{u} dvdauthor{u} exiv2{u} ffmpeg{u} gnokii-common{u} 
  gnupg-agent{u} ia32-libs{u} jhead{u} kde-icons-oxygen{u} 
  kdebase-runtime{u} kdebase-runtime-bin-kde4{u} kdebase-runtime-data{u} 
  kdebase-runtime-data-common{u} kdelibs-bin{u} kdelibs-data{u} 
  kdelibs4c2a{u} kdelibs5{u} kdelibs5-data{u} kdemultimedia-kio-plugins{u} 
  kdepim-kresources{u} kdepimlibs-data{u} kdepimlibs5{u} khelpcenter4{u} 
  ladcca2{u} lame{u} lesstif2{u} lib32asound2{u} lib32gcc1{u} 
  lib32ncurses5{u} lib32stdc++6{u} lib32z1{u} libakonadiprivate1{u} 
  libao2{u} libaudclient1{u} libaudid3tag1{u} libavahi-qt3-1{u} 
  libavdevice52{u} libavfilter0{u} libbinio1ldbl{u} 
  libboost-program-options1.35.0{u} libbtctl4{u} libc6-i386{u} libcddb2{u} 
  libclucene0ldbl{u} libcurl3{u} libexiv2-5{u} libfluidsynth1{u} 
  libgammu-i18n{u} libgammu5{u} libgda3-3{u} libgda3-bin{u} 
  libgda3-common{u} libgdl-1-0{u} libgdl-1-common{u} libgnokii3{u} 
  libgnomebt0{u} libimlib2{u} libjpeg-progs{u} libkcddb4{u} libkdepim4{u} 
  libkholidays4{u} libkleo4{u} libkpgp4{u} libksieve4{u} libloudmouth1-0{u} 
  liblua50{u} liblualib50{u} libmcs1{u} libmimelib4{u} libmjpegtools-1.9{u} 
  libmowgli1{u} libnetpbm10{u} libphonon4{u} libpq5{u} libqt3-mt{u} 
  libqt4-test{u} libqt4-webkit{u} libquicktime1{u} librasqal1{u} librdf0{u} 
  libresid-builder0c2a{u} libsidplay2{u} libsoprano4{u} libsox-fmt-all{u} 
  libsox-fmt-alsa{u} libsox-fmt-ao{u} libsox-fmt-base{u} 
  libsox-fmt-ffmpeg{u} libsox-fmt-mp3{u} libsox-fmt-oss{u} libsox1{u} 
  libspeechd2{u} libstreamanalyzer0{u} libstreams0{u} libtagc0{u} 
  libtre4{u} libxcb-shape0{u} libxcb-shm0{u} libxcb-xv0{u} libxine1{u} 
  libxine1-bin{u} libxine1-console{u} libxine1-ffmpeg{u} 
  libxine1-misc-plugins{u} libxine1-plugins{u} libxine1-x{u} 
  linux-headers-2.6.28-11{u} linux-headers-2.6.28-11-generic{u} 
  mjpegtools{u} netpbm{u} nspluginwrapper{u} oss-compat{u} phonon{u} 
  phonon-backend-gstreamer{u} pinentry-gtk2{u} python-bluez{u} 
  python-cddb{u} python-chardet{u} python-gamin{u} python-gammu{u} 
  python-gnome2-extras{u} python-gpod{u} python-mutagen{u} python-ogg{u} 
  python-pyogg{u} python-pyvorbis{u} python-wxgtk2.8{u} python-wxversion{u} 
  redland-utils{u} soprano-daemon{u} sox{u} stardict-common{u} 
  stardict-gnome{u} stardict-plugin{u} timidity{u} toolame{u} videotrans{u} 
  vorbis-tools{u} 
0 packages upgraded, 4 newly installed, 138 to remove and 0 not upgraded.
Need to get 140kB/1244kB of archives. After unpacking 529MB will be freed.

```
Dunno why such thing happens.

Thank you.

---

### Post by Repgahroll on 2009-07-26
OK, I uninstalled ff and a lot of other things, but now i have another problem... ff3.5 depends on ff3.0 :(.

---

### Post by anuraggautam on 2009-07-26
> **ptn107 said:**
> ```
sudo aptitude install firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support && sudo aptitude purge firefox-3.0 firefox-3.0-branding firefox-3.0-gnome-support
```

What the command have u written ? I have written the same command in my termainal and current verison of firefox got carsh.

I am not able to open my firefox , help me to come up with this .....

---

### Post by Repgahroll on 2009-07-26
I think it's because you uninstalled your ff3.0... you have to launch ff3.5 using the "firefox-3.5" command or clickin the "shiretoko" icon in internet menee.

BTW, i'm giving up... i'll just use the ff3.5 even if ff3.0 is installed... no big problem @ all, i just think there should be a way to **""UPGRADE""** and not install i parallel and delete the older version, or keep both versions...

If ff3.5 is stable and standard, why would i want to keep the older version? On windows the browser asks if you want to upgrade and after some somple clicks youll have the newest browser... on Ubuntu it's almost impossible.

---

### Post by anuraggautam on 2009-07-26
> **Repgahroll said:**
> I think it's because you uninstalled your ff3.0... you have to launch ff3.5 using the "firefox-3.5" command or clickin the "shiretoko" icon in internet menee.

BTW, i'm giving up... i'll just use the ff3.5 even if ff3.0 is installed... no big problem @ all, i just think there should be a way to **""UPGRADE""** and not install i parallel and delete the older version, or keep both versions...

If ff3.5 is stable and standard, why would i want to keep the older version? On windows the browser asks if you want to upgrade and after some somple clicks youll have the newest browser... on Ubuntu it's almost impossible.


My Firefox 3.0 is already there in sysytem, but when i click the shortcut at my desktop panel it throwing a message 
"Failed to execute child process "/home/anurag/firefox/firefox-bin" (No such file or directory) " , I am afraid how to correct it ? while typing firefox in terminal is working fine.

I have runned your command, and type 

"anurag@Anurag-Laptop:~$ firefox-3.5 
bash: firefox-3.5: command not found"

You can see the output.

I am ready to keep both the versions of firefox but how to do that ?

---

### Post by cb951303 on 2009-07-28
does anyone know if force installation (without installing ff-3.0) of sun java plugin will work with ff-3.5

---

