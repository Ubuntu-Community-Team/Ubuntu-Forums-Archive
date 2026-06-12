---
title: "pioneer dvd rw cannot write cd iso image"
date: 2009-08-08
forum: Hardware
---

### Post by tomasrey88 on 2009-08-08
Hi,

My pioneer external dvd rw drive can read and write cd and dvd. However, it cannot write cd iso images. For example, it cannot write a xubuntu 9.04 cd at 4x speed (slowest). The disc was corrupted and would not work. 

However, nero in windows xp burns the disc fine. 

This is really embarrassing as I have been trying to persuade my wife to switch to Ubuntu Linux from Windows. She refuses to even try Ubuntu until I can burn a CD iso image. 

I don't know what model pioneer it is. Except for the serial number, there is no marking on the outside. How do I tell so that I can report to you guys? ram xubuntu hardy jaunty

Please help.

Thanks,
:P

---

### Post by infinitejones on 2009-08-08
I'm assuming you're trying to burn the Xubuntu CD image using image-burning software on XP? If not - why not try burning the Xubuntu ISO using Nero?

Also, have you tried:

[LIST]
[*]Deleting the image you've downloaded, downloading it again (maybe from another source) and trying again? There's a chance something went wrong during the download (ie. not Ubuntu's fault!) so hopefully that won't happen again.

[*]Downloading a different Ubuntu image, eg. Ubuntu or Kubuntu? Although I appreciate you may want to use Xubuntu specifically, so that might not be an option.

[*]Using different image-burning software on XP? I haven't used Windows for about four years so I can't suggest anything specific, but there must be more than one.
[/LIST]

Finally, if it's still not working, tell us exactly how you know the Xubuntu CD you're trying to burn is corrupted. At what point in the burning/installation process is it failing? Is the XP software telling you that the process isn't working, or is it failing when you try and install from the image you've just burned?

If it's the second, tell us at what stage it's failing and (if possible) what error message you're getting.

---

### Post by hobo14 on 2009-08-08
I don't think he's saying his problem is burning an Ubuntu disk, it's burning _any_ disk...

---

### Post by infinitejones on 2009-08-08
> **hobo14 said:**
> I don't think he's saying his problem is burning an Ubuntu disk, it's burning _any_ disk...

Well he's already said that Nero on XP burns disks fine. If Ubuntu is having problems burning the disk then he must have, at some point in the past, installed (K/X/)Ubuntu, having successfully burned an Ubuntu disk, using something other than Ubuntu!

So I'm trying to establish if the problem lies with (X/K/)Ubuntu's disc burning capabilities, the Xubuntu image he's downloaded, or his actual drive. If he can burn things with Nero on XP, then it's unlikely to be his drive, so it must be one of the others.

To the OP - sorry to be talking about you in the third person!

---

### Post by tomasrey88 on 2009-08-08
Sorry for the confusion. I am trying to use Ubuntu Hardy to download and burn a xubuntu ISO installation disc. Since I cannot do this, I was forced to use windows XP to do it. Because I did not use Ubuntu to do this, my wife said, "See, I told you so. Billions of Windows users can't be wrong." 

Argh. This is so... embarrassing. 

What terminal commands do I use to figure out what DVD/CD RW I am using? I assume you would need that info to help me with my problem....

Thanks guys,
Tom.

md5sum -c /media/cdrom1/md5sum.txt | grep -v 'OK$'

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

### Post by tgalati4 on 2009-08-08
dmesg | more
I'm sure it's possible to get better performance from your DVD burner.  Have you tried k3b yet?

Sometimes you can update the firmware in the DVD burner, this can also improve performance.

Luckily DVD burners are cheap, I would toss it and get something else that works to your satisfaction.  Life is too short to waste in windows.

---

### Post by tomasrey88 on 2009-08-08
Since dics and DVD/CD burner works fine under XP, I assume that this is a hardware compatibility issue with Ubuntu Hardy. Please tell me how to fix this. Thanks.

burned on slowest x2 speed.

---

### Post by tomasrey88 on 2009-08-09
No, you miss the point. I could buy a new dvd/cd rw. However, that will not get my so to switch to ubuntu from windows because she will not have confidence in ubuntu since it cannot do something that windows can do. 

I have a DVD RW (I don't know what model) that can burn files but it cannot burn CD ISO images. I am guessing that since it is an external USB 2.0 device and the computer is an old USB 1.0 computer, there is a data transfer rate slower than what the RW drive is used to and therefore, it messes up larger jobs. It can handle small files like MP3s and small text files fine, but not the big stuff like an ISO image. This is my best guess. 

I am using an external drive because my internal drive pops open in 1 second. It will play a music CD for 1 second, then eject the disc.It will write a CD iso image or any other file for 1 sec, then eject the disc before the job is finished. 

Please guys, do you have a solution to at least one of these compatibility issue. I would really like to switch from Windows to Ubuntu Linux but the SO will not be convinced if I cannot burn a simple CD while Windows can using the exact same equipment. 

Thanks,
:P

Internal CD RW is a Mitsumi CR-4804te. Thanks.

---

### Post by tomasrey88 on 2009-08-09
dmesg | more

Following is what I think is the relavant part of the output since the complete output is way too long. If I did not cut and paste the correct part, please let me know and I will cut and past all of it. Thank you. 

35.497822] uhci_hcd 0000:00:07.3: irq 10, io base 0x0000d800
[   35.498150] usb usb2: configuration #1 chosen from 1 choice
[   35.498228] hub 2-0:1.0: USB hub found
[   35.498247] hub 2-0:1.0: 2 ports detected
[   35.659950] Floppy drive(s): fd0 is 1.44M
[   35.681162] FDC 0 is a post-1991 82077
[   35.707009] pata_via 0000:00:07.1: version 0.3.3
[   35.725248] scsi0 : pata_via
[   35.733245] scsi1 : pata_via
[   35.733398] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xd000 irq 14
[   35.733407] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xd008 irq 15
[   35.737288] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   35.896840] usb 1-1: configuration #1 chosen from 1 choice
[   35.897873] ata1.00: ATA-5: Maxtor 92041U4, FA520S60, max UDMA/66
[   35.897884] ata1.00: 40020624 sectors, multi 16: LBA 
[   35.898678] hub 1-1:1.0: USB hub found
[   35.900628] hub 1-1:1.0: 7 ports detected
[   35.916175] ata1.00: configured for UDMA/66
[   36.510416] ata2.00: ATAPI: CR-4804TE, 2.6C, max MWDMA1
[   36.510482] ata2.01: ATAPI: IDE/ATAPI CD-ROM 50XS, 196A, max UDMA/33
[   36.598276] usb 1-1.1: new full speed USB device using uhci_hcd and address 3
[   36.681802] ata2.00: configured for MWDMA1
[   36.711417] usb 1-1.1: configuration #1 chosen from 1 choice
[   36.845408] ata2.01: configured for UDMA/33
[   36.845763] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 92041U4   FA52 PQ
: 0 ANSI: 5
[   36.848734] scsi 1:0:0:0: CD-ROM            MITSUMI  CR-4804TE        2.6C PQ
: 0 ANSI: 5
[   36.850065] scsi 1:0:1:0: CD-ROM            ATAPI    CD-ROM 50X       196A PQ
: 0 ANSI: 5
[   36.923114] usb 1-1.2: new full speed USB device using uhci_hcd and address 4
[   37.043217] usb 1-1.2: configuration #1 chosen from 1 choice
[   37.571521] Driver 'sr' needs updating - please use bus_type methods
[   37.577602] Driver 'sd' needs updating - please use bus_type methods
[   37.577805] sd 0:0:0:0: [sda] 40020624 512-byte hardware sectors (20491 MB)
[   37.577849] sd 0:0:0:0: [sda] Write Protect is off
[   37.577858] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   37.577925] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, does
n't support DPO or FUA
[   37.578071] sd 0:0:0:0: [sda] 40020624 512-byte hardware sectors (20491 MB)
[   37.578109] sd 0:0:0:0: [sda] Write Protect is off
[   37.578117] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   37.578209] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, does
n't support DPO or FUA
[   37.578222]  sda:sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tra
y
[   37.581646] Uniform CD-ROM driver Revision: 3.20
[   37.581799] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   37.591803] sr1: scsi3-mmc drive: 8x/11x cd/rw xa/form2 cdda tray
[   37.591975] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   37.604715]  sda1 sda2 sda3 sda4
[   37.613221] usbcore: registered new interface driver libusual
[   37.625730] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   37.625793] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   37.625849] sr 1:0:1:0: Attached scsi generic sg2 type 5
[   37.634007] sd 0:0:0:0: [sda] Attached SCSI disk
[   37.676718] Initializing USB Mass Storage driver...
[   37.709678] scsi2 : SCSI emulation for USB Mass Storage devices
[   37.723006] usb-storage: device found at 3
[   37.723019] usb-storage: waiting for device to settle before scanning
[   37.746007] scsi3 : SCSI emulation for USB Mass Storage devices
[   37.760674] usbcore: registered new interface driver usb-storage
[   37.760696] USB Mass Storage support registered.
[   37.760991] usb-storage: device found at 4
[   37.760999] usb-storage: waiting for device to settle before scanning
[   38.626888] Attempting manual resume
[   38.626900] swsusp: Resume From Partition 8:4
[   38.626905] PM: Checking swsusp image.
[   38.640326] PM: Resume from disk failed.
[   38.726354] kjournald starting.  Commit interval 5 seconds
[   38.726390] EXT3-fs: mounted filesystem with ordered data mode.
[   42.721090] usb-storage: device scan complete
[   42.724041] scsi 2:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-111D 1.19 PQ
: 0 ANSI: 0
[   42.760011] usb-storage: device scan complete
[   42.763883] sr2: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   42.764188] sr 2:0:0:0: Attached scsi CD-ROM sr2
[   42.764352] sr 2:0:0:0: Attached scsi generic sg3 type 5
[   42.764621] scsi 3:0:0:0: Direct-Access     WDC WD12 00JB-00REA0      0000 PQ
: 0 ANSI: 0
[   42.769854] sd 3:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[   42.774857] sd 3:0:0:0: [sdb] Write Protect is off
[   42.774870] sd 3:0:0:0: [sdb] Mode Sense: 27 00 00 00
[   42.774879] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[   42.779847] sd 3:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[   42.784839] sd 3:0:0:0: [sdb] Write Protect is off
[   42.784847] sd 3:0:0:0: [sdb] Mode Sense: 27 00 00 00
[   42.784854] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[   42.784868]  sdb: sdb1
[   42.802181] sd 3:0:0:0: [sdb] Attached SCSI disk
[   42.802329] sd 3:0:0:0: Attached scsi generic sg4 type 0
[   56.450920] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   56.653437] parport_pc: VIA 686A/8231 detected
[   56.653450] parport_pc: probing current configuration
[   56.653476] parport_pc: Current parallel port base: 0x378
[   56.653578] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRI
STATE,COMPAT,ECP]

---

### Post by tomasrey88 on 2009-08-09
thank you for telling me how to check what hardware i have. after a search, it seems that others have had the same problem. please tell us how to fix it:

[http://ubuntuforums.org/showthread.php?t=1049819&highlight=DVR-111D](http://ubuntuforums.org/showthread.php?t=1049819&highlight=DVR-111D)

At least it works for smaller files with brasero. however, the program k3b will not work at all with this dvd rw: 

[http://ubuntuforums.org/showthread.php?t=953838&highlight=DVR-111D](http://ubuntuforums.org/showthread.php?t=953838&highlight=DVR-111D)

what's the fix? 

Thanks, 
:P

---

### Post by tgalati4 on 2009-08-09
Here's a curious entry:

36.923114] usb 1-1.2: new full speed USB device using uhci_hcd and address 4
[ 37.043217] usb 1-1.2: configuration #1 chosen from 1 choice
[ 37.571521] Driver 'sr' needs updating - please use bus_type methods
[ 37.577602] Driver 'sd' needs updating - please use bus_type methods

Looks like the kernel developers have found something that they don't know how to fix, but they have at least marked it on their todo list.

You can try to turn "Burn Underrun off" or look for ways to increase or decrease cache size.

I think that you have missed the point.  There are lots of devices that don't work well under linux.  That is a fact.  Those that want to use linux do research and find hardware that works well under linux and move on.

The purpose of an operating system is to run hardware so that you can get something done.  If windows works for burning ISO's, then that is what you have to use.

You can buy new internal or external DVD writers for $29 US.  Some work better than others.  The fact that you are using USB 1.1 would be an issue for any high-speed device:  external harddisk or DVD writer.

A simple google search of:  Driver 'sr' needs updating please use bus_type methods

Yields:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/186167](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/186167)


I have a problem regarding the same bug. Because of the sr0 - device needs updating via bus-type methods i can not burn successfully any cd's while dvd burning is just fine. I can burn cd's but when i try to mount them later (or use them for installing ubuntu for example) hal gives me an error and when i try to copy something from them it gives i/o errors... Here is some info...

[ 5.219866] Driver 'sr' needs updating - please use bus_type methods
[ 5.247383] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[ 5.247536] sr 0:0:0:0: Attached scsi CD-ROM sr0

So you have stumbled on a bug in the kernel.  The developers are aware of it.  

Try Jaunty or Koala and see if it was fixed or follow the google search that I did and see if there are other work arounds.

Since I don't have an external DVD writer I can't test it.

Your concerns are valid, but blaming Ubuntu for a piece of hardware that doesn't work isn't productive.

Since support for Ubuntu is community-driven, we have to work together to solve problems.

Why exactly do we have to convince your wife that Ubuntu is better than Windows?

---

### Post by tomasrey88 on 2009-08-10
I have to convince the misses because I don't want to pay the Microcrap tax for a new computer. It's a matter of principle. Windows Vista is a broken product. It has so much bloatware that it turns a perfectly good computer into a piece of crap. You have to have at least a dual core to run decent in Windows Vista. I heard through the grapevine that Windows 7 is going to be a subscriptions product. So, I have to buy a bicycle and pay you every month for the priviledge of riding it?! The way I see it, if I buy a bicycle, the warranty to keep it running should be included in the purchase price. Subscriptions are only for products that give you something different to enjoy every month, such as a different TV show every time you watch (cable) or different articles at every reading (newspaper). This is just clearly a stinky monopolistic behavior on Microcrap's part. 

I'm actually thinking about starting a computer store that specializes in Linux products. I am a Linux noob, but I will hire knowledgeable people and I learn quickly. I also enjoy showing other noobs how to get started. So, even though it is a free OS, I am paying with sweat capital because I want this Ubuntu to continue to succeed and improve. I have a stack of computers that I am reviving for friends and family with Ubuntu. I would like to set-up a free internet cafe in my computer store so people could try Ubuntu before they buy. I would also like to sell fresh fruit juices in my internet cafe/computer store so people would hang around and talk/plan this digital revolution against the microcrap giant. I hate powerful monopolies that prey on the little guy. 

So, in answering your question, why do I have to convince my wife to use Ubuntu? For the same reason I would like to convince everyone else to use it: LET THEM KNOW THAT THERE IS AN ALTERNATIVE TO MICROCRAP'S MONOPOLY. 

The first step to a revolution is awareness of the masses, to achieve a critical mass of awareness (tell everyone you know).

The second step is action (buy a Linux computer). 

:popcorn:


Thanks for your info, by the way.

---

### Post by tgalati4 on 2009-08-10
Well, if you have a computer store, then you are definitely on the front lines of the revolution.

Good luck with your endeavors.  Sorry I couldn't help more with cd-burning, but I'm confident there are work-arounds.  When you find one, please post it.

---

