---
title: "Installing a .tar.gz"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by finisterra on 2009-10-05
I'm an Ubuntu newbie, and I may be asking one of the most stupid questions ever asked in the forum, but how do I install a .tar.gz file? I'd be really pleased if you could guide me through the process. I'm trying to install the latest version of Songbird.

Thanks in advance.

Edit:

I found a guide, and so far I've navigated to where the file is located and extracted it. I can't get any further than that.

---

### Post by friv_livs on 2009-10-05
Open the extracted directory, and look for a INSTALL or README text file. Open those files and see what they say to do.

If not found, someone else will have to step in for me.

Did you check the repos for Songbird first?

---

### Post by finisterra on 2009-10-05
> **friv_livs said:**
> Open the extracted directory, and look for a INSTALL or README text file. Open those files and see what they say to do.

If not found, someone else will have to step in for me.

Did you check the repos for Songbird first?

There is a README file inside, but it doesn't contain any installation information. Songbird isn't available in the repos.

Thanks anyway. :)
[PHP][/PHP]

---

### Post by orange-wedge on 2009-10-05
Actually with songbird once you have extracted the archive you have installed it.  Really you just need to decide where you want to extract it to install songbird.  If you only have one user account logging into the desktop, you could easily just extract it to your home directory and call it quits.

Give me a few to work up tutorial to install Songbird like any other app.

EDIT:

Download Songbird

Copy the Songbird archive to the /usr/lib directory:
```
sudo cp Downloads/Songbird_1.2.0-1146_linux-i686.tar.gz /usr/lib/.
```Now lets unpack Songbird:
```
cd /usr/lib/
``````
sudo gunzip Songbird_1.2.0-1146_linux-i686.tar.gz 
``````
sudo tar xvf Songbird_1.2.0-1146_linux-i686.tar
```Now we need to modify the permissions to allow all users to use Songbird (Probably could have done this a little more efficiently, but I got it to work on my laptop with these steps):

```
sudo find /usr/lib/Songbird/ -type d -exec chmod 755 \{} \;
``````
sudo find /usr/lib/Songbird/ -type f -executable -exec chmod 755 \{} \;
``````
sudo find /usr/lib/Songbird/ -type f  -exec chmod a+r \{} \;
```At this point you can use Songbird, but it's not in your path.  So let's make a link to the Songbird script:

```
sudo ln -s /usr/lib/Songbird/songbird /usr/bin/songbird
```Finally we need to add Songbird to the Gnome menu, so let's create the following file using gedit:

```
sudo gedit /usr/share/applications/songbird.desktop
```Insert the following lines into the songbird.desktop file  (Thank you banshee.desktop):

```

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Songbird
Comment=Play and organize your media collection
Exec=songbird
Icon=/usr/lib/Songbird/chrome/icons/default/default.xpm
Terminal=false
Type=Application
Categories=GNOME;Application;Audio;Music;Player;AudioVideo;
MimeType=application/musepack;application/ogg;application/ram;application/sdp;application/smil;application/vnd.rn
-realmedia;application/x-ape;application/x-extension-m4a;application/x-extension-mp4;application/x-flac;applicati
on/x-flash-video;application/x-id3;application/x-matroska;application/x-musepack;application/x-netshow-channel;ap
plication/x-ogg;application/x-quicktime-media-link;application/x-quicktimeplayer;application/x-shorten;applicatio
n/x-smil;application/x-troff-msvideo;application/xspf+xml;audio/3gpp;audio/AMR;audio/AMR-WB;audio/ac3;audio/ape;a
udio/avi;audio/basic;audio/flac;audio/midi;audio/mp;audio/mp3;audio/mp4;audio/mp4a-latm;audio/mpc;audio/mpeg;audi
o/mpeg3;audio/mpegurl;audio/musepack;audio/ogg;audio/vnd.rn-realaudio;audio/vorbis;audio/wav;audio/wave;audio/x-a
pe;audio/x-flac;audio/x-it;audio/x-m4a;audio/x-matroska;audio/x-mod;audio/x-mp;audio/x-mp3;audio/x-mpc;audio/x-mp
eg;audio/x-mpeg-3;audio/x-mpegurl;audio/x-ms-asf;audio/x-ms-asx;audio/x-ms-wax;audio/x-ms-wma;audio/x-musepack;au
dio/x-ogg;audio/x-pn-aiff;audio/x-pn-au;audio/x-pn-realaudio;audio/x-pn-realaudio-plugin;audio/x-pn-wav;audio/x-p
n-windows-acm;audio/x-real-audio;audio/x-realaudio;audio/x-s3m;audio/x-sbc;audio/x-scpls;audio/x-speex;audio/x-tt
a;audio/x-vorbis;audio/x-vorbis+ogg;audio/x-wav;audio/x-wavpack;audio/x-xm;image/avi;image/vnd.rn-realpix;image/x
-pict;misc/ultravox;text/google-video-pointer;text/x-google-video-pointer;video/3gpp;video/avi;video/dv;video/fli
;video/flv;video/mp4;video/mp4v-es;video/mpeg;video/msvideo;video/quicktime;video/vivo;video/vnd.divx;video/vnd.r
n-realvideo;video/vnd.vivo;video/x-anim;video/x-avi;video/x-flc;video/x-fli;video/x-flic;video/x-flv;video/x-m4v;
video/x-matroska;video/x-mpeg;video/x-mpg;video/x-ms-asf;video/x-ms-wm;video/x-ms-wmv;video/x-ms-wmx;video/x-ms-w
vx;video/x-msvideo;video/x-nsv;video/x-ogm+ogg;video/x-theora+ogg;x-content/audio-cdda;x-content/audio-player;

```

---

### Post by finisterra on 2009-10-06
Thanks a lot Orange-Wedge! That worked to perfection.

---

### Post by Spiffjiggins on 2009-12-09
> **orange-wedge said:**
> Actually with songbird once you have extracted the archive you have installed it.  Really you just need to decide where you want to extract it to install songbird.  If you only have one user account logging into the desktop, you could easily just extract it to your home directory and call it quits.

Give me a few to work up tutorial to install Songbird like any other app.

EDIT:

Download Songbird

Copy the Songbird archive to the /usr/lib directory:
```
sudo cp Downloads/Songbird_1.2.0-1146_linux-i686.tar.gz /usr/lib/.
```Now lets unpack Songbird:
```
cd /usr/lib/
``````
sudo gunzip Songbird_1.2.0-1146_linux-i686.tar.gz 
``````
sudo tar xvf Songbird_1.2.0-1146_linux-i686.tar
```Now we need to modify the permissions to allow all users to use Songbird (Probably could have done this a little more efficiently, but I got it to work on my laptop with these steps):

```
sudo find /usr/lib/Songbird/ -type d -exec chmod 755 \{} \;
``````
sudo find /usr/lib/Songbird/ -type f -executable -exec chmod 755 \{} \;
``````
sudo find /usr/lib/Songbird/ -type f  -exec chmod a+r \{} \;
```At this point you can use Songbird, but it's not in your path.  So let's make a link to the Songbird script:

```
sudo ln -s /usr/lib/Songbird/songbird /usr/bin/songbird
```Finally we need to add Songbird to the Gnome menu, so let's create the following file using gedit:

```
sudo gedit /usr/share/applications/songbird.desktop
```Insert the following lines into the songbird.desktop file  (Thank you banshee.desktop):

```

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Songbird
Comment=Play and organize your media collection
Exec=songbird
Icon=/usr/lib/Songbird/chrome/icons/default/default.xpm
Terminal=false
Type=Application
Categories=GNOME;Application;Audio;Music;Player;AudioVideo;
MimeType=application/musepack;application/ogg;application/ram;application/sdp;application/smil;application/vnd.rn
-realmedia;application/x-ape;application/x-extension-m4a;application/x-extension-mp4;application/x-flac;applicati
on/x-flash-video;application/x-id3;application/x-matroska;application/x-musepack;application/x-netshow-channel;ap
plication/x-ogg;application/x-quicktime-media-link;application/x-quicktimeplayer;application/x-shorten;applicatio
n/x-smil;application/x-troff-msvideo;application/xspf+xml;audio/3gpp;audio/AMR;audio/AMR-WB;audio/ac3;audio/ape;a
udio/avi;audio/basic;audio/flac;audio/midi;audio/mp;audio/mp3;audio/mp4;audio/mp4a-latm;audio/mpc;audio/mpeg;audi
o/mpeg3;audio/mpegurl;audio/musepack;audio/ogg;audio/vnd.rn-realaudio;audio/vorbis;audio/wav;audio/wave;audio/x-a
pe;audio/x-flac;audio/x-it;audio/x-m4a;audio/x-matroska;audio/x-mod;audio/x-mp;audio/x-mp3;audio/x-mpc;audio/x-mp
eg;audio/x-mpeg-3;audio/x-mpegurl;audio/x-ms-asf;audio/x-ms-asx;audio/x-ms-wax;audio/x-ms-wma;audio/x-musepack;au
dio/x-ogg;audio/x-pn-aiff;audio/x-pn-au;audio/x-pn-realaudio;audio/x-pn-realaudio-plugin;audio/x-pn-wav;audio/x-p
n-windows-acm;audio/x-real-audio;audio/x-realaudio;audio/x-s3m;audio/x-sbc;audio/x-scpls;audio/x-speex;audio/x-tt
a;audio/x-vorbis;audio/x-vorbis+ogg;audio/x-wav;audio/x-wavpack;audio/x-xm;image/avi;image/vnd.rn-realpix;image/x
-pict;misc/ultravox;text/google-video-pointer;text/x-google-video-pointer;video/3gpp;video/avi;video/dv;video/fli
;video/flv;video/mp4;video/mp4v-es;video/mpeg;video/msvideo;video/quicktime;video/vivo;video/vnd.divx;video/vnd.r
n-realvideo;video/vnd.vivo;video/x-anim;video/x-avi;video/x-flc;video/x-fli;video/x-flic;video/x-flv;video/x-m4v;
video/x-matroska;video/x-mpeg;video/x-mpg;video/x-ms-asf;video/x-ms-wm;video/x-ms-wmv;video/x-ms-wmx;video/x-ms-w
vx;video/x-msvideo;video/x-nsv;video/x-ogm+ogg;video/x-theora+ogg;x-content/audio-cdda;x-content/audio-player;

```

I tried doing it this way, however I get this message:"cp: cannot stat `Downloads/Songbird_1.2.0-1146_linux-i686.tar.gz': No such file or directory"
Is it because I have Xubuntu?

---

### Post by MelDJ on 2009-12-09
the .deb for songbird is available here: [http://old.getdeb.net/release.php?id=4460](http://old.getdeb.net/release.php?id=4460)

---

