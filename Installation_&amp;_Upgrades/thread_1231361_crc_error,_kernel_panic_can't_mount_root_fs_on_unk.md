---
title: "crc error, kernel panic can't mount root fs on unknown block ?"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by tomasrey88 on 2009-08-04
Hi,

I tried to install Xubuntu alternate install CD on a Dell Latitude Cpi D300XT, but got the following errors;

[1139.059164] crc error
[1139.065658] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(104,1)

What should I do? 

Thanks,
:P

P.S. Laptop is 300 mHz, 128 MB RAM, 4.3 GB HD, 2 MB video card computer.

---

### Post by Vhann on 2009-08-04
Try checking the CD for defects if possible.

If there are no such options, try mount the CD on a running Linux (something like 'sudo mount -o loop -t iso9660 /dev/scd0 /media/cdrom' should do),
there should be a md5sum.txt file on the base CD directory.

If there do is a md5sum.txt file, do the following to know whether
there are any error on the CD:
md5sum -c /path/to/CD/md5sum.txt | grep -v 'OK$'

If you see any single line of output from running this command, it means
the CD is corrupt (or just dirty in which case you might want to try cleaning it with a clean piece of dry cloth).

Hope this helps.

Regards,
Vhann

---

### Post by tomasrey88 on 2009-08-04
tried with xubuntu 9.04 and this error occured;
crc error
- system halted

---

### Post by tomasrey88 on 2009-08-04
when i used the check disc for error function on the disc itself it said the same error;
crc error, system halted.

---

### Post by tomasrey88 on 2009-08-04
panda@pandamonium-desktop:~$ -c /media/cdrom1/md5sum.txt | grep -v'OK$'
grep: invalid option -- O
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.
bash: -c: command not found

What did I do wrong? Above is the terminal cut and paste. 

Thanks,
:P

---

### Post by Vhann on 2009-08-04
> **tomasrey88 said:**
> panda@pandamonium-desktop:~$ -c /media/cdrom1/md5sum.txt | grep -v'OK$'
The command was:
md5sum -c /media/cdrom1/md5sum.txt | grep -v 'OK$'

Therefore your prompt shall resemble this after hitting ENTER:
panda@pandamonium-desktop:~$ md5sum -c /media/cdrom1/md5sum.txt | grep -v 'OK$'

Regards,
Vhann

---

### Post by tomasrey88 on 2009-08-05
The result is the following cut and paste. I tried to burn the disc multiple times on my Ubuntu 8.04 machine and they all failed. What's wrong? I burned an ISO image. Is there a compatiblility problem that is preventing my burning working discs? Argh. Please advise. Thanks. 

pen or read
./pool/main/libj/libjpeg6b/libjpeg62_6b-14_i386.deb: FAILED open or read
./pool/main/libr/librsvg/librsvg2-2_2.26.0-0ubuntu1_i386.deb: FAILED open or read
./pool/main/libr/librsvg/librsvg2-common_2.26.0-0ubuntu1_i386.deb: FAILED open or read
./pool/main/libr/libraw1394/libraw1394-8_1.3.0-4ubuntu1_i386.deb: FAILED open or read
./pool/main/libr/librpc-xml-perl/librpc-xml-perl_0.64-1_all.deb: FAILED open or read
./pool/main/libr/librpcsecgss/librpcsecgss3_0.18-1_i386.deb: FAILED open or read
./pool/main/libh/libhtml-tree-perl/libhtml-tree-perl_3.23-1_all.deb: FAILED open or read
./pool/main/libh/libhtml-format-perl/libhtml-format-perl_2.04-2_all.deb: FAILED open or read
./pool/main/libh/libhtml-tagset-perl/libhtml-tagset-perl_3.20-2_all.deb: FAILED open or read
./pool/main/libh/libhtml-parser-perl/libhtml-parser-perl_3.59-1ubuntu1_i386.deb: FAILED open or read
./pool/main/libu/libuuid-perl/libuuid-perl_0.02-3build1_i386.deb: FAILED open or read
./pool/main/libu/libusb/libusb-0.1-4_0.1.12-13_i386.deb: FAILED open or read
./pool/main/libu/libusb/libusb-0.1-udeb_0.1.12-13_i386.udeb: FAILED open or read
./pool/main/libu/liburi-perl/liburi-perl_1.37+dfsg-1ubuntu1_all.deb: FAILED open or read
./pool/main/t/t1lib/libt1-5_5.1.2-3_i386.deb: FAILED open or read
./pool/main/t/thunderbird/thunderbird_2.0.0.21+nobinonly-0ubuntu1.9.04.1_i386.deb: FAILED open or read
./pool/main/t/thunderbird/mozilla-thunderbird_2.0.0.21+nobinonly-0ubuntu1.9.04.1_all.deb: FAILED open or read
./pool/main/t/ttf-lao/ttf-lao_0.0.20060226-2_all.deb: FAILED open or read
./pool/main/t/ttf-arabeyes/ttf-arabeyes_2.0-2_all.deb: FAILED open or read
./pool/main/t/tftp-hpa/tftpd-hpa_0.48-2.3ubuntu1_i386.deb: FAILED open or read
./pool/main/t/tftp-hpa/tftp-hpa_0.48-2.3ubuntu1_i386.deb: FAILED open or read
./pool/main/t/tasksel/tasksel_2.73ubuntu18_all.deb: FAILED open or read
./pool/main/t/tasksel/tasksel-data_2.73ubuntu18_all.deb: FAILED open or read
./pool/main/t/toshset/toshset_1.73-3_i386.deb: FAILED open or read
./pool/main/t/talloc/libtalloc1_1.2.0~git20080616-1_i386.deb: FAILED open or read
./pool/main/t/totem-pl-parser/libtotem-plparser12_2.26.1-0ubuntu1_i386.deb: FAILED open or read
./pool/main/t/tcpdump/tcpdump_3.9.8-4ubuntu2_i386.deb: FAILED open or read
./pool/main/t/taglib/libtagc0_1.5-3_i386.deb: FAILED open or read
./pool/main/t/taglib/libtag1c2a_1.5-3_i386.deb: FAILED open or read
./pool/main/t/tslib/libts-0.0-0_1.0-4ubuntu2_i386.deb: FAILED open or read
./pool/main/t/tzsetup/tzsetup-udeb_0.24ubuntu1_all.udeb: FAILED open or read
./pool/main/t/timedate/libtimedate-perl_1.1600-9_all.deb: FAILED open or read
./pool/main/t/tar/tar_1.20-1_i386.deb: FAILED open or read
./pool/main/t/tracker/libtrackerclient0_0.6.93-0ubuntu1_i386.deb: FAILED open or read
./pool/main/t/tcp-wrappers/libwrap0_7.6.q-16_i386.deb: FAILED open or read
./pool/main/t/tcp-wrappers/tcpd_7.6.q-16_i386.deb: FAILED open or read
./pool/main/t/ttf-bitstream-vera/ttf-bitstream-vera_1.10-7_all.deb: FAILED open or read
./pool/main/t/tdb/libtdb1_1.1.3~git20081222-2build1_i386.deb: FAILED open or read
./pool/main/t/totem/totem-common_2.26.1-0ubuntu5_all.deb: FAILED open or read
./pool/main/t/totem/totem-mozilla_2.26.1-0ubuntu5_all.deb: FAILED open or read
./pool/main/t/totem/totem-gstreamer_2.26.1-0ubuntu5_i386.deb: FAILED open or read
./pool/main/t/totem/totem-plugins_2.26.1-0ubuntu5_i386.deb: FAILED open or read
./pool/main/t/totem/totem_2.26.1-0ubuntu5_all.deb: FAILED open or read
./pool/main/t/texinfo/info_4.11.dfsg.1-4_i386.deb: FAILED open or read
./pool/main/t/ttf-dejavu/ttf-dejavu-core_2.28-1_all.deb: FAILED open or read
./pool/main/t/ttf-freefont/ttf-freefont_20080323-3_all.deb: FAILED open or read
./pool/main/t/time/time_1.7-23_i386.deb: FAILED open or read
./pool/main/t/thaifonts-scalable/ttf-thai-tlwg_0.4.11-2_all.deb: FAILED open or read
./pool/main/t/transmission/transmission-gtk_1.51-0ubuntu3_i386.deb: FAILED open or read
./pool/main/t/transmission/transmission-common_1.51-0ubuntu3_all.deb: FAILED open or read
./pool/main/t/texlive-bin/libkpathsea4_2007.dfsg.2-4ubuntu2_i386.deb: FAILED open or read
./pool/main/t/tcl8.4/tcl8.4_8.4.19-2_i386.deb: FAILED open or read
./pool/main/t/ttf-arphic-uming/ttf-arphic-uming_0.2.20080216.1-3ubuntu2_all.deb: FAILED open or read
./pool/main/t/tiff/libtiff4_3.8.2-11_i386.deb: FAILED open or read
./pool/main/t/ttf-indic-fonts/ttf-indic-fonts-core_0.5.4ubuntu2_all.deb: FAILED open or read
./pool/main/t/thunderbird-locales/thunderbird-locale-fr_2.0.0.14+1-0ubuntu2_all.deb: FAILED open or read
./pool/main/t/thunderbird-locales/thunderbird-locale-ru_2.0.0.14+1-0ubuntu2_all.deb: FAILED open or read
./pool/main/t/thunderbird-locales/thunderbird-locale-ja_2.0.0.14+1-0ubuntu2_all.deb: FAILED open or read
./pool/main/t/thunderbird-locales/thunderbird-locale-de_2.0.0.14+1-0ubuntu2_all.deb: FAILED open or read
./pool/main/t/ttf-sazanami/ttf-sazanami-gothic_20040629-2ubuntu2_all.deb: FAILED open or read
./pool/main/t/ttf-sazanami/ttf-sazanami-mincho_20040629-2ubuntu2_all.deb: FAILED open or read
./pool/main/t/ttf-unfonts/ttf-unfonts-core_1.0.1-7ubuntu1_all.deb: FAILED open or read
./pool/main/t/tzdata/tzdata_2009f-0ubuntu1_all.deb: FAILED open or read
./pool/main/libt/libtext-charwidth-perl/libtext-charwidth-perl_0.04-5build1_i386.deb: FAILED open or read
./pool/main/libt/libthai/libthai0_0.1.9-4_i386.deb: FAILED open or read
./pool/main/libt/libthai/libthai-data_0.1.9-4_all.deb: FAILED open or read
./pool/main/libt/libtext-wrapi18n-perl/libtext-wrapi18n-perl_0.06-6_all.deb: FAILED open or read
./pool/main/libt/libtasn1-3/libtasn1-3_1.5-1_i386.deb: FAILED open or read
./pool/main/libt/libtie-ixhash-perl/libtie-ixhash-perl_1.21-2_all.deb: FAILED open or read
./pool/main/libt/libtunepimp/libtunepimp5_0.5.3-7ubuntu3_i386.deb: FAILED open or read
./pool/main/libt/libtest-pod-perl/libtest-pod-perl_1.26-2_all.deb: FAILED open or read
./pool/main/libt/libterm-size-perl/libterm-size-perl_0.2-4build2_i386.deb: FAILED open or read
./pool/main/libt/libtheora/libtheora0_1.0-2_i386.deb: FAILED open or read
./pool/main/libt/libtool/libltdl7_2.2.6a-1ubuntu1_i386.deb: FAILED open or read
./pool/main/libt/libtext-iconv-perl/libtext-iconv-perl_1.7-1build1_i386.deb: FAILED open or read
./pool/main/libt/libterm-readkey-perl/libterm-readkey-perl_2.30-4_i386.deb: FAILED open or read
./pool/main/libc/libcompress-zlib-perl/libcompress-zlib-perl_2.015-1_all.deb: FAILED open or read
./pool/main/libc/libcap2/libcap2_2.11-2_i386.deb: FAILED open or read
./pool/main/libc/libcompress-raw-zlib-perl/libcompress-raw-zlib-perl_2.015-1_i386.deb: FAILED open or read
./pool/main/libc/libcap/libcap1_1.10-14build1_i386.deb: FAILED open or read
./pool/main/libc/libclass-accessor-perl/libclass-accessor-perl_0.31-2_all.deb: FAILED open or read
./pool/main/libc/libcaca/libcaca0_0.99.beta16-1_i386.deb: FAILED open or read
./pool/main/libc/libcdio/libcdio7_0.78.2+dfsg1-3_i386.deb: FAILED open or read
./pool/main/libc/libcdio/libcdio-cdda0_0.78.2+dfsg1-3_i386.deb: FAILED open or read
./pool/main/libc/libcdio/libcdio-paranoia0_0.78.2+dfsg1-3_i386.deb: FAILED open or read
./pool/main/libc/libcairo-perl/libcairo-perl_1.060-1_i386.deb: FAILED open or read
./pool/main/libc/libcroco/libcroco3_0.6.1-2_i386.deb: FAILED open or read
./pool/main/libc/libcanberra/libcanberra-gtk-module_0.11-1ubuntu5_i386.deb: FAILED open or read
./pool/main/libc/libcanberra/libcanberra0_0.11-1ubuntu5_i386.deb: FAILED open or read
./pool/main/libc/libcanberra/libcanberra-gtk0_0.11-1ubuntu5_i386.deb: FAILED open or read
./pool/main/x/xfonts-utils/xfonts-utils_7.4+1ubuntu1_i386.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-rendition/xserver-xorg-video-rendition_4.2.0.dfsg.1-2ubuntu1_i386.deb: FAILED open or read
./pool/main/x/xsane/xsane-common_0.996-1ubuntu2_all.deb: FAILED open or read
./pool/main/x/xsane/xsane_0.996-1ubuntu2_i386.deb: FAILED open or read
./pool/main/x/xinit/xinit_1.0.9-2_i386.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-tdfx/xserver-xorg-video-tdfx_1.4.0-2_i386.deb: FAILED open or read
./pool/main/x/xdg-utils/xdg-utils_1.0.2-6.1_all.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-i740/xserver-xorg-video-i740_1.2.0-2_i386.deb: FAILED open or read
./pool/main/x/x11-utils/x11-utils_7.4+1build1_i386.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-openchrome/xserver-xorg-video-openchrome_0.2.903+svn713-1ubuntu1_i386.deb: FAILED open or read
./pool/main/x/xfonts-75dpi/xfonts-75dpi_1.0.0-4_all.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.6.3-0ubuntu9_i386.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-i128/xserver-xorg-video-i128_1.3.1-2ubuntu1_i386.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-sisusb/xserver-xorg-video-sisusb_0.9.0-4_i386.deb: FAILED open or read
./pool/main/x/x-ttcidfont-conf/x-ttcidfont-conf_32_all.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-s3/xserver-xorg-video-s3_0.6.1-1_i386.deb: FAILED open or read
./pool/main/x/xcursor-themes/xcursor-themes_1.0.1-5ubuntu1_all.deb: FAILED open or read
./pool/main/x/xdg-user-dirs/xdg-user-dirs_0.10-1ubuntu2_i386.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-sis/xserver-xorg-video-sis_0.10.1-1_i386.deb: FAILED open or read
./pool/main/x/x11-apps/x11-apps_7.3+4_i386.deb: FAILED open or read
./pool/main/x/xfonts-terminus/console-terminus_4.26-2.1_all.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-mga/xserver-xorg-video-mga_1.4.9.dfsg-3_i386.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-fbdev/xserver-xorg-video-fbdev_0.4.0-3_i386.deb: FAILED open or read
./pool/main/x/x11-xserver-utils/x11-xserver-utils_7.4+1_i386.deb: FAILED open or read
./pool/main/x/xbitmaps/xbitmaps_1.0.1-2ubuntu1_all.deb: FAILED open or read
./pool/main/x/xscreensaver/xscreensaver-gl_5.07-0ubuntu3_i386.deb: FAILED open or read
./pool/main/x/xscreensaver/xscreensaver-data_5.07-0ubuntu3_i386.deb: FAILED open or read
./pool/main/x/xorg-server/xserver-xorg-core_1.6.0-0ubuntu14_i386.deb: FAILED open or read
./pool/main/x/xorg-server/xserver-common_1.6.0-0ubuntu14_all.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-siliconmotion/xserver-xorg-video-siliconmotion_1.7.0-1_i386.deb: FAILED open or read
./pool/main/x/xorg/xserver-xorg_7.4~5ubuntu18_i386.deb: FAILED open or read
./pool/main/x/xorg/xserver-xorg-video-all_7.4~5ubuntu18_i386.deb: FAILED open or read
./pool/main/x/xorg/x11-common_7.4~5ubuntu18_all.deb: FAILED open or read
./pool/main/x/xorg/xserver-xorg-input-all_7.4~5ubuntu18_i386.deb: FAILED open or read
./pool/main/x/xorg/xbase-clients_7.4~5ubuntu18_all.deb: FAILED open or read
./pool/main/x/xorg/xorg_7.4~5ubuntu18_i386.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-vesa/xserver-xorg-video-vesa_2.0.0-1ubuntu6_i386.deb: FAILED open or read
./pool/main/x/xfonts-scalable/xfonts-scalable_1.0.0-6ubuntu0.8.04.1_all.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-mach64/xserver-xorg-video-mach64_6.8.0-3_i386.deb: FAILED open or read
./pool/main/x/xft/libxft2_2.1.13-3ubuntu1_i386.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-ark/xserver-xorg-video-ark_0.7.1-1_i386.deb: FAILED open or read
./pool/main/x/x11-xkb-utils/x11-xkb-utils_7.4+1ubuntu2_i386.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-geode/xserver-xorg-video-geode_2.11.1-1_i386.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-nv/xserver-xorg-video-nv_2.1.12-1ubuntu5_i386.deb: FAILED open or read
./pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.8+nobinonly-0ubuntu2_i386.deb: FAILED open or read
./pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.8+nobinonly-0ubuntu2_i386.deb: FAILED open or read
./pool/main/x/x-kit/python-xkit_0.4.2_all.deb: FAILED open or read
./pool/main/x/xfonts-encodings/xfonts-encodings_1.0.2-3_all.deb: FAILED open or read
./pool/main/x/xinput/xinput_1.4.0-1_i386.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-ati_6.12.1-0ubuntu2_i386.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-radeon_6.12.1-0ubuntu2_i386.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-tseng/xserver-xorg-video-tseng_1.2.0-1ubuntu1_i386.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-chips/xserver-xorg-video-chips_1.2.1-1_i386.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-apm/xserver-xorg-video-apm_1.2.1-1_i386.deb: FAILED open or read
./pool/main/x/xfonts-base/xfonts-base_1.0.0-5_all.deb: FAILED open or read
./pool/main/x/xml-core/xml-core_0.12_all.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-s3virge/xserver-xorg-video-s3virge_1.10.2-1_i386.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-savage/xserver-xorg-video-savage_2.2.1-4ubuntu2_i386.deb: FAILED open or read
./pool/main/x/xcb-util/libxcb-render-util0_0.2.1+git1-1_i386.deb: FAILED open or read
./pool/main/x/xapian-core/libxapian15_1.0.7-4_i386.deb: FAILED open or read
./pool/main/x/xserver-xorg-input-keyboard/xserver-xorg-input-kbd_1.3.1-2ubuntu1_i386.deb: FAILED open or read
./pool/main/x/xterm/xterm_241-1ubuntu1_i386.deb: FAILED open or read
./pool/main/x/xfsprogs/xfsprogs-udeb_2.10.2-1_i386.udeb: FAILED open or read
./pool/main/x/xfsprogs/xfsprogs_2.10.2-1_i386.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-voodoo/xserver-xorg-video-voodoo_1.2.0-1ubuntu1_i386.deb: FAILED open or read
./pool/main/x/xkeyboard-config/xkb-data_1.5-2ubuntu11_all.deb: FAILED open or read
./pool/main/x/xfree86-driver-synaptics/xserver-xorg-input-synaptics_0.99.3-2ubuntu4_i386.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-neomagic/xserver-xorg-video-neomagic_1.2.2-1_i386.deb: FAILED open or read
./pool/main/x/xfonts-100dpi/xfonts-100dpi_1.0.0-4_all.deb: FAILED open or read
./pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev_2.1.1-1ubuntu4_i386.deb: FAILED open or read
./pool/main/x/xauth/xauth_1.0.3-2_i386.deb: FAILED open or read
./pool/main/x/xserver-xorg-input-mouse/xserver-xorg-input-mouse_1.4.0-1_i386.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-vmware/xserver-xorg-video-vmware_10.16.5-2_i386.deb: FAILED open or read
./pool/main/x/x11-session-utils/x11-session-utils_7.3+1_i386.deb: FAILED open or read
./pool/main/x/x11-xfs-utils/x11-xfs-utils_7.4+1build1_i386.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-r128/xserver-xorg-video-r128_6.8.0+git20090201.08d56c88-1_i386.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-cirrus/xserver-xorg-video-cirrus_1.2.1-3_i386.deb: FAILED open or read
./pool/main/x/xapian-bindings/python-xapian_1.0.7-3.1ubuntu2_i386.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-v4l/xserver-xorg-video-v4l_0.2.0-1ubuntu5_i386.deb: FAILED open or read
./pool/main/x/xserver-xorg-video-trident/xserver-xorg-video-trident_1.3.0-1ubuntu1_i386.deb: FAILED open or read
./pool/main/s/screensaver-default-images/screensaver-default-images_0.2-1_all.deb: FAILED open or read
./pool/main/s/samba/libwbclient0_3.3.2-1ubuntu3_i386.deb: FAILED open or read
./pool/main/s/samba/libsmbclient_3.3.2-1ubuntu3_i386.deb: FAILED open or read
./pool/main/s/samba/samba_3.3.2-1ubuntu3_i386.deb: FAILED open or read
./pool/main/s/samba/smbclient_3.3.2-1ubuntu3_i386.deb: FAILED open or read
./pool/main/s/samba/samba-common_3.3.2-1ubuntu3_i386.deb: FAILED open or read
./pool/main/s/software-properties/python-software-properties_0.71.5_all.deb: FAILED open or read
./pool/main/s/software-properties/software-properties-gtk_0.71.5_all.deb: FAILED open or read
./pool/main/s/scim-tables/scim-tables-additional_0.5.8-1_all.deb: FAILED open or read
./pool/main/s/scim-tables/scim-modules-table_0.5.8-1_i386.deb: FAILED open or read
./pool/main/s/squashfs/squashfs-tools_3.3-7ubuntu2_i386.deb: FAILED open or read
./pool/main/s/scim/scim-gtk2-immodule_1.4.7-3ubuntu12_i386.deb: FAILED open or read
./pool/main/s/scim/libscim8c2a_1.4.7-3ubuntu12_i386.deb: FAILED open or read
./pool/main/s/scim/scim_1.4.7-3ubuntu12_i386.deb: FAILED open or read
./pool/main/s/scim/scim-modules-socket_1.4.7-3ubuntu12_i386.deb: FAILED open or read
./pool/main/s/splix/splix_2.0.0-0.1ubuntu3_i386.deb: FAILED open or read
./pool/main/s/shadow/passwd_4.1.1-6ubuntu6_i386.deb: FAILED open or read
./pool/main/s/shadow/login_4.1.1-6ubuntu6_i386.deb: FAILED open or read
./pool/main/s/shared-mime-info/shared-mime-info_0.60-1_i386.deb: FAILED open or read
./pool/main/s/seahorse-plugins/seahorse-plugins_2.26.1-0ubuntu1_i386.deb: FAILED open or read
./pool/main/s/setserial/setserial_2.17-45_i386.deb: FAILED open or read
./pool/main/s/sed/sed_4.1.5-8_i386.deb: FAILED open or read
./pool/main/s/screen-profiles/screen-profiles_1.44-0ubuntu1_all.deb: FAILED open or read
./pool/main/s/strace/strace-udeb_4.5.17+cvs080723-2ubuntu1_i386.udeb: FAILED open or read
./pool/main/s/strace/strace_4.5.17+cvs080723-2ubuntu1_i386.deb: FAILED open or read
./pool/main/s/system-tools-backends/system-tools-backends_2.6.0-2ubuntu8_i386.deb: FAILED open or read
./pool/main/s/screen/screen_4.0.3-11ubuntu4_i386.deb: FAILED open or read
./pool/main/s/speex/libspeex1_1.2~rc1-1_i386.deb: FAILED open or read
./pool/main/s/speex/libspeexdsp1_1.2~rc1-1_i386.deb: FAILED open or read
./pool/main/s/sysfsutils/libsysfs2_2.1.0-5_i386.deb: FAILED open or read
./pool/main/s/startup-notification/libstartup-notification0_0.9-1_i386.deb: FAILED open or read
./pool/main/s/sgml-base/sgml-base_1.26_all.deb: FAILED open or read
./pool/main/s/system-config-printer/system-config-printer-common_1.1.3+git20090218-0ubuntu19_all.deb: FAILED open or read
./pool/main/s/system-config-printer/python-cupshelpers_1.1.3+git20090218-0ubuntu19_all.deb: FAILED open or read
./pool/main/s/system-config-printer/system-config-printer-gnome_1.1.3+git20090218-0ubuntu19_all.deb: FAILED open or read
./pool/main/s/sshfs-fuse/sshfs_2.1-1_i386.deb: FAILED open or read
./pool/main/s/sexy-python/python-sexy_0.1.9-1ubuntu2_i386.deb: FAILED open or read
./pool/main/s/seahorse/libcryptui0_2.26.1-0ubuntu1_i386.deb: FAILED open or read
./pool/main/s/seahorse/seahorse_2.26.1-0ubuntu1_i386.deb: FAILED open or read
./pool/main/s/slang2/libslang2-udeb_2.1.3-3ubuntu3_i386.udeb: FAILED open or read
./pool/main/s/slang2/libslang2_2.1.3-3ubuntu3_i386.deb: FAILED open or read
./pool/main/s/sane-backends/libsane_1.0.19-23ubuntu7_i386.deb: FAILED open or read
./pool/main/s/sane-backends/sane-utils_1.0.19-23ubuntu7_i386.deb: FAILED open or read
./pool/main/s/scim-bridge/scim-bridge-agent_0.4.14-2ubuntu5_i386.deb: FAILED open or read
./pool/main/s/scim-bridge/scim-bridge-client-gtk_0.4.14-2ubuntu5_i386.deb: FAILED open or read
./pool/main/s/sgml-data/sgml-data_2.0.3_all.deb: FAILED open or read
./pool/main/s/ssl-cert/ssl-cert_1.0.23ubuntu1_all.deb: FAILED open or read
./pool/main/s/syslinux/syslinux_3.63+dfsg-2ubuntu3_i386.deb: FAILED open or read
./pool/main/s/sysvinit/sysv-rc_2.86.ds1-61ubuntu11_all.deb: FAILED open or read
./pool/main/s/sysvinit/sysvinit-utils_2.86.ds1-61ubuntu11_i386.deb: FAILED open or read
./pool/main/s/sysvinit/initscripts_2.86.ds1-61ubuntu11_i386.deb: FAILED open or read
./pool/main/s/silc-toolkit/libsilc-1.1-2_1.1.7-2ubuntu1_i386.deb: FAILED open or read
./pool/main/s/synaptic/synaptic_0.62.5ubuntu2.1_i386.deb: FAILED open or read
./pool/main/s/sysklogd/klogd_1.5-5ubuntu3_i386.deb: FAILED open or read
./pool/main/s/sysklogd/sysklogd_1.5-5ubuntu3_i386.deb: FAILED open or read
./pool/main/s/sqlite3/libsqlite3-0_3.6.10-1_i386.deb: FAILED open or read
./pool/main/s/sudo/sudo_1.6.9p17-1ubuntu3_i386.deb: FAILED open or read
./pool/universe/g/gigolo/gigolo_0.3.0-0ubuntu1_i386.deb: FAILED open or read
./pool/universe/g/gutenprint/cupsys-driver-gutenprint_5.2.3-0ubuntu5_all.deb: FAILED open or read
./pool/universe/g/goffice/libgoffice-gtk-0-6_0.6.6-1ubuntu1_all.deb: FAILED open or read
./pool/universe/g/gnumeric/gnumeric-gtk_1.8.4-3ubuntu2_all.deb: FAILED open or read
./pool/universe/g/gpicview/gpicview_0.1.11-1_i386.deb: FAILED open or read
./pool/universe/g/gtk2-engines-xfce/gtk2-engines-xfce_2.6.0-1_i386.deb: FAILED open or read
./pool/universe/m/mousepad/mousepad_0.2.16-1ubuntu2_i386.deb: FAILED open or read
./pool/universe/libn/libnotify/libnotify-bin_0.4.5-0ubuntu1_i386.deb: FAILED open or read
./pool/universe/c/catfish/catfish_0.3.2-1_all.deb: FAILED open or read
./pool/universe/libi/libisofs/libisofs6_0.6.6-1_i386.deb: FAILED open or read
./pool/universe/e/exo/exo-utils_0.3.100-1ubuntu1_i386.deb: FAILED open or read
./pool/universe/e/exo/libexo-0.3-0_0.3.100-1ubuntu1_i386.deb: FAILED open or read
./pool/universe/libx/libxfce4util/libxfce4util4_4.6.0-1ubuntu2_i386.deb: FAILED open or read
./pool/universe/libx/libxfcegui4/libxfcegui4-4_4.6.0-1~ubuntu1_i386.deb: FAILED open or read
./pool/universe/libx/libxfce4menu/libxfce4menu-0.1-0_4.6.0-1~ubuntu1_i386.deb: FAILED open or read
./pool/universe/p/p7zip/p7zip-full_4.58~dfsg.1-1_i386.deb: FAILED open or read
./pool/universe/p/python-musicbrainz2/python-musicbrainz2_0.6.0-2_all.deb: FAILED open or read
./pool/universe/p/pymad/python-pymad_0.5.4-3.2build2_i386.deb: FAILED open or read
./pool/universe/p/python-pysqlite2/python-pysqlite2_2.5.0-2ubuntu1_i386.deb: FAILED open or read
./pool/universe/o/openoffice.org-dictionaries/myspell-en-us_3.0.1-8ubuntu1_all.deb: FAILED open or read
./pool/universe/o/orage/orage_4.6.0-1ubuntu1_i386.deb: FAILED open or read
./pool/universe/o/oss-compat/oss-compat_0.0.4+nmu2_all.deb: FAILED open or read
./pool/universe/l/listen/listen_0.5-6ubuntu1_i386.deb: FAILED open or read
./pool/universe/libb/libburn/libburn4_0.5.0-1_i386.deb: FAILED open or read
./pool/universe/libd/libdiscid/libdiscid0_0.1.0-1_i386.deb: FAILED open or read
./pool/universe/a/app-install-data-partner/app-install-data-commercial_11.9.04_all.deb: FAILED open or read
./pool/universe/a/arj/arj_3.10.22-6_i386.deb: FAILED open or read
./pool/universe/a/a2ps/a2ps_4.14-1_i386.deb: FAILED open or read
./pool/universe/a/aumix/aumix_2.8-22_i386.deb: FAILED open or read
./pool/universe/t/tango-icon-theme/tango-icon-theme_0.8.90-1_all.deb: FAILED open or read
./pool/universe/t/thunar-volman/thunar-volman_0.3.80-0ubuntu1_i386.deb: FAILED open or read
./pool/universe/t/thunar/libthunar-vfs-1-2_1.0.0-1ubuntu3_i386.deb: FAILED open or read
./pool/universe/t/thunar/thunar-data_1.0.0-1ubuntu3_all.deb: FAILED open or read
./pool/universe/t/thunar/thunar_1.0.0-1ubuntu3_i386.deb: FAILED open or read
./pool/universe/t/thunar-thumbnailers/thunar-thumbnailers_0.4.1-0ubuntu1_i386.deb: FAILED open or read
./pool/universe/t/thunar-media-tags-plugin/thunar-media-tags-plugin_0.1.2+svn-r04939-0ubuntu2_i386.deb: FAILED open or read
./pool/universe/t/thunar-archive-plugin/thunar-archive-plugin_0.2.4-4_i386.deb: FAILED open or read
./pool/universe/t/tango-icon-theme-common/tango-icon-theme-common_0.7-0ubuntu1_all.deb: FAILED open or read
./pool/universe/libt/libtunepimp/python-tunepimp_0.5.3-7ubuntu3_all.deb: FAILED open or read
./pool/universe/x/xfce4-notes-plugin/xfce4-notes-plugin_1.6.3-0ubuntu2_i386.deb: FAILED open or read
./pool/universe/x/xfce4-governor-plugin/xfce4-governor-plugin_0.1.0-0ubuntu1_i386.deb: FAILED open or read
./pool/universe/x/xfce4-mixer/xfce4-mixer_4.6.0-1ubuntu2_i386.deb: FAILED open or read
./pool/universe/x/xubuntu-artwork/xubuntu-artwork-usplash_0.26_i386.deb: FAILED open or read
./pool/universe/x/xubuntu-artwork/xubuntu-artwork_0.26_all.deb: FAILED open or read
./pool/universe/x/xfce4-cpugraph-plugin/xfce4-cpugraph-plugin_0.4.0-0ubuntu1_i386.deb: FAILED open or read
./pool/universe/x/xfswitch-plugin/xfswitch-plugin_0.0.1-0ubuntu1_i386.deb: FAILED open or read
./pool/universe/x/xfce4-verve-plugin/xfce4-verve-plugin_0.3.6-0ubuntu1_i386.deb: FAILED open or read
./pool/universe/x/xfce4-utils/xfce4-utils_4.6.0-1ubuntu2_i386.deb: FAILED open or read
./pool/universe/x/xfconf/xfconf_4.6.0-1~ubuntu1_i386.deb: FAILED open or read
./pool/universe/x/xfconf/libxfconf-0-2_4.6.0-1~ubuntu1_i386.deb: FAILED open or read
./pool/universe/x/xfce4-netload-plugin/xfce4-netload-plugin_0.4.0-3ubuntu3_i386.deb: FAILED open or read
./pool/universe/x/xubuntu-docs/xubuntu-docs_9.04.2_all.deb: FAILED open or read
./pool/universe/x/xfce4-terminal/xfce4-terminal_0.2.10-1ubuntu2_i386.deb: FAILED open or read
./pool/universe/x/xfprint4/xfprint4_4.6.0-1ubuntu3_i386.deb: FAILED open or read
./pool/universe/x/xfce4-xkb-plugin/xfce4-xkb-plugin_0.5.3.2-0ubuntu1_i386.deb: FAILED open or read
./pool/universe/x/xubuntu-default-settings/xubuntu-default-settings_0.56_all.deb: FAILED open or read
./pool/universe/x/xfburn/xfburn_0.4.1-1_i386.deb: FAILED open or read
./pool/universe/x/xfce4-panel/xfce4-panel_4.6.0-1ubuntu1_i386.deb: FAILED open or read
./pool/universe/x/xfce4-smartbookmark-plugin/xfce4-smartbookmark-plugin_0.4.2-1ubuntu4_i386.deb: FAILED open or read
./pool/universe/x/xfce4-battery-plugin/xfce4-battery-plugin_0.5.1-0ubuntu1_i386.deb: FAILED open or read
./pool/universe/x/xfce4-session/xfce4-session_4.6.0-1ubuntu2_i386.deb: FAILED open or read
./pool/universe/x/xfce4-settings/xfce4-settings_4.6.0-1ubuntu2_i386.deb: FAILED open or read
./pool/universe/x/xfce4-screenshooter/xfce4-screenshooter_1.5.1-0ubuntu1_i386.deb: FAILED open or read
./pool/universe/x/xfce4-mailwatch-plugin/xfce4-mailwatch-plugin_1.1.0-0ubuntu1_i386.deb: FAILED open or read
./pool/universe/x/xfce4-quicklauncher-plugin/xfce4-quicklauncher-plugin_1.9.4-2ubuntu2_i386.deb: FAILED open or read
./pool/universe/x/xfce4-fsguard-plugin/xfce4-fsguard-plugin_0.4.2-0ubuntu1_i386.deb: FAILED open or read
./pool/universe/x/xfwm4/xfwm4_4.6.0-1ubuntu3_i386.deb: FAILED open or read
./pool/universe/x/xfce4-dict/xfce4-dict_0.5.2-0ubuntu1_i386.deb: FAILED open or read
./pool/universe/x/xfce4-dict/xfce4-dict-plugin_0.5.2-0ubuntu1_all.deb: FAILED open or read
./pool/universe/x/xfce4-clipman-plugin/xfce4-clipman-plugin_0.9.0-0ubuntu1_i386.deb: FAILED open or read
./pool/universe/x/xfce4-weather-plugin/xfce4-weather-plugin_0.6.2-1ubuntu2_i386.deb: FAILED open or read
./pool/universe/x/xubuntu-meta/xubuntu-desktop_2.82_i386.deb: FAILED open or read
./pool/universe/x/xfce4-mount-plugin/xfce4-mount-plugin_0.5.5-1_i386.deb: FAILED open or read
./pool/universe/x/xchat/xchat-common_2.8.6-2.1ubuntu4_all.deb: FAILED open or read
./pool/universe/x/xchat/xchat_2.8.6-2.1ubuntu4_i386.deb: FAILED open or read
./pool/universe/x/xfdesktop4/xfdesktop4-data_4.6.0-1ubuntu1_all.deb: FAILED open or read
./pool/universe/x/xfdesktop4/xfdesktop4_4.6.0-1ubuntu1_i386.deb: FAILED open or read
./pool/universe/x/xfce4-places-plugin/xfce4-places-plugin_1.1.0-2_i386.deb: FAILED open or read
./pool/universe/x/xfwm4-themes/xfwm4-themes_4.6.0-1_all.deb: FAILED open or read
./pool/universe/x/xfce4-appfinder/xfce4-appfinder_4.6.0-1_i386.deb: FAILED open or read
./pool/universe/x/xfce4-systemload-plugin/xfce4-systemload-plugin_0.4.2-1ubuntu3_i386.deb: FAILED open or read
./pool/universe/x/xarchiver/xarchiver_0.5.2+dfsg-1_i386.deb: FAILED open or read
./README.diskdefines: FAILED open or read

---

### Post by Vhann on 2009-08-05
Wow, your CD is seriously messed up. 

There are numerous reasons I can think of: 
- The ISO file you downloaded is corrupt
- Your CD burner drive is malfunctioning (dead, dirty len, mispluged, etc)
- All the CDs you tried were already burned, damaged, etc 

I'd go for the most-likely to happen first choice.

Therefore, we are going to compute the md5sum of your ISO image.
Assuming your ISO file is /home/user/foo.iso, you'd issue the following command:
md5sum /home/user/foo.iso

Which should look like:
user@pc~: md5sum /home/user/foo.iso
cfb056bf5ff5e21596fe25705ea044e6 /home/user/foo.iso

Keep this command prompt opened, you'll need it later on. 

Then, go to (these are the MD5SUMs for Xubuntu 9.04 Jaunty Jackalope ISO images):
[http://hex1a4.net/xubuntu/mirror/releases/9.04/release/MD5SUMS](http://hex1a4.net/xubuntu/mirror/releases/9.04/release/MD5SUMS)

(To find this link I went to [http://www.xubuntu.org/get](http://www.xubuntu.org/get) then choose a mirror for
the release I wanted: Canada (Ontario) in my case. Then opened the link that
read 'MD5SUMS') 

in the MD5SUMS webpage, find the line which looks like
[random number here] *foo.iso
(where foo.iso is your ISO image filename)

Then, compare the two strings by hand or type this in a commmand prompt
(where str1 is the computed md5sum for your ISO image (the one in the command prompt earlier) and str2 is the [random number here]):
[ "str1" = "str2" ]; echo $?

If the output is 1, your image is corrupt and you must redownload it.
Otherwise, if the output is 0, your downloaded image is OK and the problem
is probably with the burner and/or the blank CDs you used (I don't believe this might be the case here though). In which case, I'd recommend trying with new CDs on another burner drive.

Hope this helps.
Regards,
Vhann

---

### Post by tomasrey88 on 2009-08-07
thank you i figured it out. the cd rom drive is shot and the computer is too old so the bios will not allow bootup from usb. argh. only allows bootup from floppy (impossible, too small) and cd (broken). 

i wonder, if i put more memory in the laptop (it is now 128 mb ram). like if i put a total of 256 mb ram, will i be able to run a live cd from the usb to install it? 

or maybe i could put the contents of the cd on the hard drive and just install it from the hard drive? i wonder....

thanks, 
:P

---

### Post by Vhann on 2009-08-07
Ok, so basically, if I understood everything correctly,
you have an old laptop whose BIOS won't let you boot from USB and
whose CD drive is dead.

I can think of a few avenues to try in order to install something on
this wrecked dinosaur.

-Check if the BIOS allows you to boot from PXE (i.e. Network Boot)
-Maybe you'd have some luck booting BusyBox or something from a floppy
from which you could load the USB modules and then install from a USB key
-Find a new CD drive and install it.

One of these ideas might work for you. But then, I am by no mean an Ubuntu
expert and have no idea if this is at all possible with Ubuntu.
But I know these are possible since I would know how to it to install Slax or Slackware.

Hope this helps.
Regards,
Vhann

---

### Post by tomasrey88 on 2009-08-07
you're right i'm wrong i think i have some compatiblility issues with my dvd/cd burner. argh....

It also treats all rw discs as write once only discs, too. argh....

this is an external rw disc drive since my internal rw disc drive is totally not working. it keeps ejecting the disc after only 1 sec. it will read files for 1 sec only....

Problem solved: I burned the disc with nero in windows and the installation disc works fine. I think there is a compatibility issue with my dvd/cd burner working in linux. Solved one problem, but discovered another one. I could burn discs fine, just not iso images. A bug, perhaps?

---

