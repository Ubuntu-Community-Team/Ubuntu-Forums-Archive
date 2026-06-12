---
title: "vlc player"
date: 2008-11-01
forum: General Help
---

### Post by JohnL2009 on 2008-11-01
I was trying to add a new skin to my vlc player, now it will not open just opens to:  "open a skin file"  How do I get the player to open?  Have uninstalled and reinstalled twice.  thanks

---

### Post by rudihawk on 2008-11-01
Launch it from terminal and post the output here.

---

### Post by JohnL2009 on 2008-11-01
> **rudihawk said:**
> Launch it from terminal and post the output here.

not sure how to do that - help

---

### Post by chaoswings on 2008-11-01
open the terminal...to do that:

**Applications>accessories>terminal**

then once you are in there type:

 **script ~/vlc_output.txt**

press ENTER

then type:

**vlc**

press ENTER

VLC will start and you should see a whole bunch of text appear in the terminal. After you apply the skin close VLC. In the terminal again type:
[B]
exit[/B]

Then go to your **home folder** and you should see a file named **vlc_output.txt** paste the contents of that on the forum.

---

### Post by JohnL2009 on 2008-11-01
> **chaoswings said:**
> open the terminal...to do that:

**Applications>accessories>terminal**

then once you are in there type:

 **script ~/vlc_output.txt**

press ENTER

then type:

**vlc**

press ENTER

VLC will start and you should see a whole bunch of text appear in the terminal. After you apply the skin close VLC. In the terminal again type:
[B]
exit[/B]

Then go to your **home folder** and you should see a file named **vlc_output.txt** paste the contents of that on the forum.

didn't work this is the error message I got:[00000405] skins2 interface error: failed to parse /usr/share/vlc/skins2/default.vlt

---

### Post by JohnL2009 on 2008-11-01
Script started on Sat 01 Nov 2008 03:46:03 PM PDT
]0;john@john-desktop: ~john@john-desktop:~$ vlc

VLC media player 0.9.4 Grishenko

[[32;1m00000001[0m] main libvlc debug: [0mVLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team[0m

[[32;1m00000001[0m] main libvlc debug: [0mlibvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'[0m

[[32;1m00000001[0m] main libvlc debug: [0mtranslation test: code is "C"[0m

[[32;1m00000414[0m] access_directory access error: [31;1m/home/john/Dalin_Media_Player.vlt: No such file or directory[0m

[[32;1m00000414[0m] access_file access error: [31;1mcannot open file /home/john/Dalin_Media_Player.vlt (No such file or directory)[0m

[[32;1m00000405[0m] main interface error: [31;1mno suitable access module for `/home/john/Dalin_Media_Player.vlt'[0m

[[32;1m00000405[0m] skins2 interface error: [31;1mfailed to open /home/john/Dalin_Media_Player.vlt for reading[0m

[[32;1m00000405[0m] skins2 interface error: [31;1mfailed to parse /home/john/Dalin_Media_Player.vlt[0m

[[32;1m00000419[0m] xml xml error: [31;1mXML parser error (line 1) : failed to load external entity "skin.dtd"

[0m

[[32;1m00000419[0m] xml xml error: [31;1mXML parser error (line 2) : Validation failed: no DTD found ![0m

[[32;1m00000405[0m] skins2 interface error: [31;1mfailed to parse /tmp/vlt2AVEh0/default/theme.xml[0m

[[32;1m00000405[0m] skins2 interface error: [31;1merror while parsing /tmp/vlt2AVEh0/default/theme.xml[0m

[[32;1m00000422[0m] xml xml error: [31;1mXML parser error (line 1) : Document is empty

[0m

[[32;1m00000405[0m] skins2 interface error: [31;1mfailed to parse /usr/share/vlc/skins2/default.vlt[0m

[[32;1m00000409[0m] main generic error: [31;1mobject is not attached[0m

]0;john@john-desktop: ~john@john-desktop:~$ 

]0;john@john-desktop: ~john@john-desktop:~$ vlc

VLC media player 0.9.4 Grishenko

[[32;1m00000001[0m] main libvlc debug: [0mVLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team[0m

[[32;1m00000001[0m] main libvlc debug: [0mlibvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'[0m

[[32;1m00000001[0m] main libvlc debug: [0mtranslation test: code is "C"[0m

[[32;1m00000414[0m] access_directory access error: [31;1m/home/john/Dalin_Media_Player.vlt: No such file or directory[0m

[[32;1m00000414[0m] access_file access error: [31;1mcannot open file /home/john/Dalin_Media_Player.vlt (No such file or directory)[0m

[[32;1m00000405[0m] main interface error: [31;1mno suitable access module for `/home/john/Dalin_Media_Player.vlt'[0m

[[32;1m00000405[0m] skins2 interface error: [31;1mfailed to open /home/john/Dalin_Media_Player.vlt for reading[0m

[[32;1m00000405[0m] skins2 interface error: [31;1mfailed to parse /home/john/Dalin_Media_Player.vlt[0m

[[32;1m00000419[0m] xml xml error: [31;1mXML parser error (line 1) : failed to load external entity "skin.dtd"

[0m

[[32;1m00000419[0m] xml xml error: [31;1mXML parser error (line 2) : Validation failed: no DTD found ![0m

[[32;1m00000405[0m] skins2 interface error: [31;1mfailed to parse /tmp/vltqxyt0F/default/theme.xml[0m

[[32;1m00000405[0m] skins2 interface error: [31;1merror while parsing /tmp/vltqxyt0F/default/theme.xml[0m

[[32;1m00000422[0m] xml xml error: [31;1mXML parser error (line 1) : Document is empty

[0m

[[32;1m00000405[0m] skins2 interface error: [31;1mfailed to parse /usr/share/vlc/skins2/default.vlt[0m

[[32;1m00000409[0m] main generic error: [31;1mobject is not attached[0m

]0;john@john-desktop: ~john@john-desktop:~$ exit

---

### Post by mc4man on 2008-11-01
you didn't mention if your using hardy or intrepid. Trying to use a different skin in intrepid with the embedded video enabled may prove to be frustrating.
To restore back to orig. go into home folder -> .config (hidden) and delete the vlc folder. Then restart vlc

---

### Post by JohnL2009 on 2008-11-01
I'm not getting any place - looks like I really fouled it up.  Will just wait until I have to reformt and reinstal intrepid.  Thanks for the effort.

---

### Post by chaoswings on 2008-11-01
uninstall vlc completely and then reinstall it

sudo apt-get remove vlc

sudo apt-get clean

sudo apt-get install vlc

---

### Post by JohnL2009 on 2008-11-01
Thank you but it didn't work - the "skin file" where ever it is still stopping vlc from booting up.

---

### Post by JohnL2009 on 2008-11-02
I finally found the file - it is listed as default.vlt /usr/share/vlt/skins2,  type is a Gzip archive.  How do I delete it, can't move it to the trash, Have tried remove in terminal with sudo apt-get remove etc but system tells me it can't find the default.vlt file.

---

### Post by JohnL2009 on 2008-11-02
I finally found the file in default.vlt usr/share/vlc/skins2 but how do you delete it.  Have tried get-edit remove etc. that will not work.  Any suggestions?

---

### Post by mc4man on 2008-11-02
Type gksudo nautilus in the terminal and then navigate there in the file browser that opens. Do a shift+delete on it.
I'm surprised that deleting the vlc folder in home -> .config didn't restore vlc to orig. settings, you still may need to do so.

---

### Post by JohnL2009 on 2008-11-02
Thanks for the clue - got rid of the file uninstalled vlc then reinstalled, Still will not come up - still looking for a skin file.

---

### Post by mc4man on 2008-11-02
Are you deleting the vlc folder in .config?

---

### Post by JohnL2009 on 2008-11-02
no ?

---

### Post by Josh C on 2008-11-02
Perhaps you could help me with vlc as well.  It hasn't worked for me in many months.  When I select vlc from Applications list I get nothing.  When I type vlc in the terminal I get...
josh@josh-laptop:~$ vlc
VLC media player 0.8.6e Janus
Inconsistency detected by ld.so: ../sysdeps/i386/dl-machine.h: 550: elf_machine_rel_relative: Assertion `((reloc->r_info) & 0xff) == 8' failed!
josh@josh-laptop:~$ 
I tried the uninstall, clean, reinstall as well as the reinstallation and remove then install fresh from synaptic.  Nothing works.  VLC just won't do anything.  Please help.

---

### Post by benerivo on 2008-11-02
Have you removed all your existing vlc configurations? As well as the one at ~/.config/vlc there is also one at /home/johnny/.local/share/vlc

---

### Post by JohnL2009 on 2008-11-02
Thank you so much - its working & I've really learned a lot.  Thanks again

---

