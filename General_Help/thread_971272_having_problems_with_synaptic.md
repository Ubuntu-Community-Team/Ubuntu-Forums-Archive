---
title: "having problems with synaptic"
date: 2008-11-04
forum: General Help
---

### Post by CraymelCage on 2008-11-04
I did a fresh install of ubuntu over windows xp. I keep getting errors when trying to do anything with synaptic.

```
E: Type 'e' is not known on line 55 in source list /etc/apt/sources.list
E: The list of sources could not be read.

```

I have ubuntu 8.04 installed.

Officially calling this a closed cased and synaptic is working perfectly now. This problem was brought to you by the letter "E".

---

### Post by taurus on 2008-11-04
There is something wrong on line 55 of /etc/apt/sources.list.

Open a terminal and edit your /etc/apt/sources.list.

```
gksudo gedit /etc/apt/sources.list
```
Then, move down to line 55 and fix the type or put a # in front of it to comment it out.  Save it and open the gedit window.

Now run

```
sudo apt-get update
sudo apt-get upgrade
```

And if you're not sure what to do, post your /etc/apt/sources.list here then.

---

### Post by CraymelCage on 2008-11-04
thanks that helped. Line 55 was only the letter e. I don't know how that happened since this was a fresh install and I didn't even touch that list.

---

### Post by CraymelCage on 2008-11-20
Ok I did another fresh install recently because intrepid was annoying me with all the sound issues. I think there is something wrong with the 8.04 install disc I'm using because I have another problem with synaptic. This time it wasn't brought to me by the letter "e". 

When I try to install ubuntu restricted extras I get this error

```
W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-07-3ubuntu2_i386.deb
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/universe/c/cabextract/cabextract_1.2-2_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libg/libgsm/libgsm1_1.0.12-1_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libd/libdc1394/libdc1394-13_1.1.0-5ubuntu1_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-ffmpeg/gstreamer0.10-ffmpeg_0.10.3-6_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-pitfdll/gstreamer0.10-pitfdll_0.9.1.1+cvs20080215-1_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/universe/libc/libcdaudio/libcdaudio1_0.99.12p2-3_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gmyth/libgmyth0_0.7.debian1-1~hardy1_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/universe/libi/libiptcdata/libiptcdata0_1.0.2-2_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/universe/libf/libfreebob/libfreebob0_1.0.7-1_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/universe/j/jack-audio-connection-kit/libjack0_0.109.2-1ubuntu1_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/universe/libm/libmms/libmms0_0.3-6_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libm/libmpcdec/libmpcdec3_1.2.2-1build1_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/universe/libo/libopenspc/libopenspc0_0.3.99a-2_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/universe/s/soundtouch/libsoundtouch1c2_1.3.0-2.2ubuntu0.1_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/universe/w/wildmidi/libwildmidi0_0.2.2-2_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-bad0.10/gstreamer0.10-plugins-bad_0.10.6-5ubuntu0.1_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/f/faac/libfaac0_1.26-0.1ubuntu1_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/universe/libq/libquicktime/libquicktime1_1.0.0+debian-5_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/m/mjpegtools/libmjpegtools0c2a_1.8.0-0.2ubuntu5_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/x/x264/libx264-57_0.svn20071224-0.0ubuntu1_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/x/xvidcore/libxvidcore4_1.1.2-0.1ubuntu3_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-bad-multiverse0.10/gstreamer0.10-plugins-bad-multiverse_0.10.6-1_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/universe/a/a52dec/liba52-0.7.4_0.7.4-11ubuntu1_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/universe/libd/libdvdread/libdvdread3_0.9.7-8ubuntu1_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libi/libid3tag/libid3tag0_0.15.1b-10_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libm/libmad/libmad0_0.15.1b-2.1ubuntu1_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/universe/m/mpeg2dec/libmpeg2-4_0.4.1-1_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/universe/libs/libsidplay/libsidplay1_1.36.59-4_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-ugly0.10/gstreamer0.10-plugins-ugly_0.10.7-3ubuntu1_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/l/lame/liblame0_3.97-0.0_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-ugly-multiverse0.10/gstreamer0.10-plugins-ugly-multiverse_0.10.7-1_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/m/msttcorefonts/msttcorefonts_2.4_all.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-plugin_6-07-3ubuntu2_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/u/ubuntu-restricted-extras/ubuntu-restricted-extras_15.2_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/u/unrar-nonfree/unrar_3.7.8-1_i386.deb
  Unable to connect to ca.archive.ubuntu.com http:

```

Thanks for help in advanced.

---

### Post by taurus on 2008-11-20
Go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and pick another server, Main Server should be fine.  Press Reload and see if you can update your machine now.

---

