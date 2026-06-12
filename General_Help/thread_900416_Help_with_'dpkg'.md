---
title: "Help with 'dpkg'"
date: 2008-08-25
forum: General Help
---

### Post by Mashy on 2008-08-25
Ok so I'm trying to install Cinelerra, I've found a thread on these forums which details how, but I am having some trouble.

The first step is to meet a bunch of dependancies, and it tells me to type this into the terminal - 

```
sudo apt-get install build-essential automake1.7 libtool xorg-dev libasound2-dev libogg-dev libvorbis-dev libtheora-dev libopenexr-dev libdv4-dev libpng12-dev libjpeg62-dev uuid-dev libmjpegtools-dev liba52-dev liblame-dev libsndfile1-dev libfaac-dev libfaad-devllibfaad2 libfaad0 fftw3-dev libraw1394-dev libavc1394-dev libiec61883-dev libtiff4-dev subversion checkinstall yasm nasm libarts1-mpeglib libmpeg-dev libmpeg1 libmpeg2-4-dev libmpeg3-1 libmpeg3-dev x264
```

Which is all very well, except when I press enter I get 

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

I was wondering if there is anything I can do to make this work? I also get a similar error while doing other things in the terminal, usually trying to download programs, I think.

The only thing that I can think that might have something to do with it is that a while back, to make ubuntu work, I typed something like

```
sudo dpkg-reconfigure xserver-xorg
```
but I don't see why that would have any effect, the only thing that connects the two, as far as I can tell, is the 'dpkg'.

Any help with this will be much appreciated.

Thanks.

---

### Post by tuxxy on 2008-08-25
Make sure you have any other package managers closed, it gives this error as there is already one open somewhere

---

### Post by Ryadt on 2008-08-25
The error you got means that you have synaptic open and try to install via the terminal. Make sure that synaptic is closed then retry.;)

---

### Post by Mashy on 2008-08-25
Lol, thanks guys. I didn't think that I usually had synaptic open, but I must have, it's worked now. 

Thanks alot.

---

