---
title: "Upgrading from Beta failing !"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by feras.ws on 2009-05-09
Dear Users :

I'm trying to upgrade from 9.04 beta to the stable version , the problem started when I tried to upgrade using the update manager , a message appeared to me saying that some of these packages may not be compatible with your version so use the partial upgrade , I used it , I downloaded about 345 package and I think there are 100 more ! i'm trying to continue but a message appears to me saying :
that Ubuntu cannot fetch the backages !
then I went to the terminal and wrote  :
```
sudo apt-get dist-upgrade --fix-missing

```

I don't know it was working on unpacking (that's what I think) , then It asked me to restart , I restarted my system , but the same ! it's still beta !! I ran the update manager again but nothing appeared to me ! I mean the partial upgrade message didn't appear ! and when I tried to install the updates normally a message came saying :
> 
W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/p/python-central/python-central_0.6.11ubuntu6_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/p/python-central/python-central_0.6.11ubuntu6_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/libpython2.6_2.6.2~rc1-0ubuntu2_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/libpython2.6_2.6.2~rc1-0ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6_2.6.2~rc1-0ubuntu2_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6_2.6.2~rc1-0ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6-minimal_2.6.2~rc1-0ubuntu2_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6-minimal_2.6.2~rc1-0ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/p/python-defaults/python_2.6.1-0ubuntu9_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/p/python-defaults/python_2.6.1-0ubuntu9_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/p/python-defaults/python-minimal_2.6.1-0ubuntu9_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/p/python-defaults/python-minimal_2.6.1-0ubuntu9_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs5-data_4.2.2-0ubuntu4_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs5-data_4.2.2-0ubuntu4_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs-bin_4.2.2-0ubuntu4_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs-bin_4.2.2-0ubuntu4_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs5_4.2.2-0ubuntu4_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs5_4.2.2-0ubuntu4_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-ar/language-pack-ar_9.04+20090410_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-ar/language-pack-ar_9.04+20090410_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-ar-base/language-pack-ar-base_9.04+20090410_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-ar-base/language-pack-ar-base_9.04+20090410_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_9.04+20090410_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_9.04+20090410_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en-base/language-pack-en-base_9.04+20090410_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en-base/language-pack-en-base_9.04+20090410_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-ar/language-pack-gnome-ar_9.04+20090410_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-ar/language-pack-gnome-ar_9.04+20090410_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-ar-base/language-pack-gnome-ar-base_9.04+20090410_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-ar-base/language-pack-gnome-ar-base_9.04+20090410_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_9.04+20090410_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_9.04+20090410_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en-base/language-pack-gnome-en-base_9.04+20090410_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en-base/language-pack-gnome-en-base_9.04+20090410_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-dri_7.4-0ubuntu1_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-dri_7.4-0ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-glx_7.4-0ubuntu1_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-glx_7.4-0ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/initramfs-tools_0.92bubuntu28_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/initramfs-tools_0.92bubuntu28_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.28-11-generic_2.6.28-11.41_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.28-11-generic_2.6.28-11.41_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-dev_7.4-0ubuntu1_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-dev_7.4-0ubuntu1_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/m/mesa/mesa-common-dev_7.4-0ubuntu1_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/m/mesa/mesa-common-dev_7.4-0ubuntu1_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libglu1-mesa_7.4-0ubuntu1_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libglu1-mesa_7.4-0ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/m/mesa/mesa-utils_7.4-0ubuntu1_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/m/mesa/mesa-utils_7.4-0ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.7.20.2ubuntu5_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.7.20.2ubuntu5_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2009e-1_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2009e-1_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-utils_0.7.20.2ubuntu5_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-utils_0.7.20.2ubuntu5_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-transport-https_0.7.20.2ubuntu5_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-transport-https_0.7.20.2ubuntu5_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/c/command-not-found/command-not-found-data_0.2.34ubuntu2_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/c/command-not-found/command-not-found-data_0.2.34ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/c/command-not-found/command-not-found_0.2.34ubuntu2_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/c/command-not-found/command-not-found_0.2.34ubuntu2_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.111.4_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.111.4_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.111.4_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.111.4_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/a/apport/python-problem-report_1.0-0ubuntu4_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/a/apport/python-problem-report_1.0-0ubuntu4_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/a/apport/python-apport_1.0-0ubuntu4_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/a/apport/python-apport_1.0-0ubuntu4_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/a/apport/apport_1.0-0ubuntu4_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/a/apport/apport_1.0-0ubuntu4_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/a/apport/apport-gtk_1.0-0ubuntu4_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/a/apport/apport-gtk_1.0-0ubuntu4_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/c/compiz/libdecoration0_0.8.2-0ubuntu7_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/c/compiz/libdecoration0_0.8.2-0ubuntu7_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgail-common_2.16.1-0ubuntu1_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgail-common_2.16.1-0ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgail18_2.16.1-0ubuntu1_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgail18_2.16.1-0ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-common_2.16.1-0ubuntu1_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-common_2.16.1-0ubuntu1_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/gtk2-engines-pixbuf_2.16.1-0ubuntu1_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/gtk2-engines-pixbuf_2.16.1-0ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.3.9-17_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.3.9-17_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.16.1-0ubuntu1_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.16.1-0ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-gnome_0.8.2-0ubuntu7_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-gnome_0.8.2-0ubuntu7_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-plugins_0.8.2-0ubuntu7_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-plugins_0.8.2-0ubuntu7_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-wrapper_0.8.2-0ubuntu7_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-wrapper_0.8.2-0ubuntu7_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-core_0.8.2-0ubuntu7_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-core_0.8.2-0ubuntu7_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz_0.8.2-0ubuntu7_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz_0.8.2-0ubuntu7_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-dev_0.8.2-0ubuntu7_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-dev_0.8.2-0ubuntu7_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/c/computer-janitor/computer-janitor-gtk_1.12.1-0ubuntu2_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/c/computer-janitor/computer-janitor-gtk_1.12.1-0ubuntu2_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/c/computer-janitor/computer-janitor_1.12.1-0ubuntu2_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/c/computer-janitor/computer-janitor_1.12.1-0ubuntu2_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.3.9-17_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.3.9-17_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler4_0.10.5-1ubuntu1_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler4_0.10.5-1ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/p/poppler/poppler-utils_0.10.5-1ubuntu1_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/p/poppler/poppler-utils_0.10.5-1ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript_8.64.dfsg.1-0ubuntu7_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript_8.64.dfsg.1-0ubuntu7_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs8_8.64.dfsg.1-0ubuntu7_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs8_8.64.dfsg.1-0ubuntu7_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.3.9-17_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.3.9-17_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups_1.3.9-17_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups_1.3.9-17_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-bsd_1.3.9-17_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-bsd_1.3.9-17_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-client_1.3.9-17_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-client_1.3.9-17_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserver1.2-11_2.26.0-0ubuntu2_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserver1.2-11_2.26.0-0ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libcamel1.2-14_2.26.0-0ubuntu2_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libcamel1.2-14_2.26.0-0ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebackend1.2-0_2.26.0-0ubuntu2_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebackend1.2-0_2.26.0-0ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebook1.2-9_2.26.0-0ubuntu2_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebook1.2-9_2.26.0-0ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libecal1.2-7_2.26.0-0ubuntu2_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libecal1.2-7_2.26.0-0ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-book1.2-2_2.26.0-0ubuntu2_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-book1.2-2_2.26.0-0ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-cal1.2-6_2.26.0-0ubuntu2_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-cal1.2-6_2.26.0-0ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libegroupwise1.2-13_2.26.0-0ubuntu2_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libegroupwise1.2-13_2.26.0-0ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libgdata1.2-1_2.26.0-0ubuntu2_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libgdata1.2-1_2.26.0-0ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libgdata-google1.2-1_2.26.0-0ubuntu2_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libgdata-google1.2-1_2.26.0-0ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server_2.26.0-0ubuntu2_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server_2.26.0-0ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server-common_2.26.0-0ubuntu2_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server-common_2.26.0-0ubuntu2_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserverui1.2-8_2.26.0-0ubuntu2_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserverui1.2-8_2.26.0-0ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libexchange-storage1.2-3_2.26.0-0ubuntu2_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libexchange-storage1.2-3_2.26.0-0ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution_2.26.0-0ubuntu5_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution_2.26.0-0ubuntu5_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-common_2.26.0-0ubuntu5_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-common_2.26.0-0ubuntu5_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-plugins_2.26.0-0ubuntu5_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-plugins_2.26.0-0ubuntu5_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/libpanel-applet2-0_2.26.0-0ubuntu6_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/libpanel-applet2-0_2.26.0-0ubuntu6_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/gnome-panel-data_2.26.0-0ubuntu6_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/gnome-panel-data_2.26.0-0ubuntu6_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/gnome-panel_2.26.0-0ubuntu6_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/gnome-panel_2.26.0-0ubuntu6_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/f/fast-user-switch-applet/fast-user-switch-applet_2.24.0-0ubuntu12_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/f/fast-user-switch-applet/fast-user-switch-applet_2.24.0-0ubuntu12_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-x_8.64.dfsg.1-0ubuntu7_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-x_8.64.dfsg.1-0ubuntu7_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-cards-data_2.26.0-0ubuntu4_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-cards-data_2.26.0-0ubuntu4_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games-data_2.26.0-0ubuntu4_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games-data_2.26.0-0ubuntu4_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games_2.26.0-0ubuntu4_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games_2.26.0-0ubuntu4_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/i/indicator-applet/libindicate1_0.1.5-0ubuntu1_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/i/indicator-applet/libindicate1_0.1.5-0ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/i/indicator-messages/indicator-messages_0.1.5-0ubuntu1_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/i/indicator-messages/indicator-messages_0.1.5-0ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/i/indicator-applet/indicator-applet_0.1.5-0ubuntu1_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/i/indicator-applet/indicator-applet_0.1.5-0ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/t/tracker/libtrackerclient0_0.6.92-1ubuntu2_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/t/tracker/libtrackerclient0_0.6.92-1ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/t/tracker/libtracker-gtk0_0.6.92-1ubuntu2_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/t/tracker/libtracker-gtk0_0.6.92-1ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/t/tracker/tracker-search-tool_0.6.92-1ubuntu2_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/t/tracker/tracker-search-tool_0.6.92-1ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/t/tracker/tracker-utils_0.6.92-1ubuntu2_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/t/tracker/tracker-utils_0.6.92-1ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler-glib4_0.10.5-1ubuntu1_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler-glib4_0.10.5-1ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/t/tracker/tracker_0.6.92-1ubuntu2_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/t/tracker/tracker_0.6.92-1ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/t/tracker/libdeskbar-tracker_0.6.92-1ubuntu2_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/t/tracker/libdeskbar-tracker_0.6.92-1ubuntu2_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-bin_2.16.1-0ubuntu1_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-bin_2.16.1-0ubuntu1_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-util1_0.7.1~rc4.1.cf199a964-0ubuntu1_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-util1_0.7.1~rc4.1.cf199a964-0ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-glib0_0.7.1~rc4.1.cf199a964-0ubuntu1_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-glib0_0.7.1~rc4.1.cf199a964-0ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.28-11_2.6.28-11.41_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.28-11_2.6.28-11.41_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.28-11-generic_2.6.28-11.41_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.28-11-generic_2.6.28-11.41_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.28-11.41_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.28-11.41_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.7.1~rc4.1.cf199a964-0ubuntu1_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.7.1~rc4.1.cf199a964-0ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.7.1~rc4.1-0ubuntu1_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.7.1~rc4.1-0ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/n/notify-osd/notify-osd_0.9.11-0ubuntu1_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/n/notify-osd/notify-osd_0.9.11-0ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/python-cupshelpers_1.1.3+git20090218-0ubuntu18_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/python-cupshelpers_1.1.3+git20090218-0ubuntu18_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/system-config-printer-common_1.1.3+git20090218-0ubuntu18_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/system-config-printer-common_1.1.3+git20090218-0ubuntu18_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/system-config-printer-gnome_1.1.3+git20090218-0ubuntu18_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/system-config-printer-gnome_1.1.3+git20090218-0ubuntu18_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-common_2.26.1-0ubuntu4_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-common_2.26.1-0ubuntu4_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-plugins_2.26.1-0ubuntu4_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-plugins_2.26.1-0ubuntu4_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-gstreamer_2.26.1-0ubuntu4_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-gstreamer_2.26.1-0ubuntu4_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/l/lirc/liblircclient0_0.8.4a-0ubuntu4_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/l/lirc/liblircclient0_0.8.4a-0ubuntu4_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem_2.26.1-0ubuntu4_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem_2.26.1-0ubuntu4_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-mozilla_2.26.1-0ubuntu4_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-mozilla_2.26.1-0ubuntu4_all.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/universe/x/xserver-xorg-input-vmmouse/xserver-xorg-input-vmmouse_12.5.1-4ubuntu4_i386.deb](http://sy.archive.ubuntu.com/ubuntu/pool/universe/x/xserver-xorg-input-vmmouse/xserver-xorg-input-vmmouse_12.5.1-4ubuntu4_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-documentation-en_2.26.0-0ubuntu5_all.deb](http://sy.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-documentation-en_2.26.0-0ubuntu5_all.deb)
  404 Not Found [IP: 91.189.88.40 80]




so could you plz help ?

---

### Post by Partyboi2 on 2009-05-09
Try changing your download server  then try reloading the package list before upgrading.

---

