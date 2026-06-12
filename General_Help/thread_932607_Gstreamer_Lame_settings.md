---
title: "Gstreamer Lame settings"
date: 2008-09-28
forum: General Help
---

### Post by dstein on 2008-09-28
I am trying to pick my gstreamer settings for ripping CDs. I am currently using ```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=4 vbr-quality=1 preset=1002 vbr-mean-bitrate=256 ! xingmux ! id3v2mux
``` I am actually trying to match my settings closest with those that are used on the MP3s on amazon.com, which I have been very happy with. Can anyone offer any advice?

And now for my main question - what is the difference between quality=1 and vbr-quality=1? I have seen both on different websites. Running ```
gst-inspect lame | less
``` does not give any indication of what the quality parameter does. Any help would be great. Thanks.

Also, does it matter where I put preset=1002, if I would like that to be the default for options I don't specify?

Thanks.

---

### Post by Zatta on 2008-10-16
If you want to know what options given by gst-inspect mean, take a look at the lame manpage:

```
man lame
```

(you quit the man page typing "q")

There you will find the following explanations:

About option "-q":
> -q qual
0 <= qual <= 9
Bitrate  is  of  course the main influence on quality.  The higher the bitrate, the higher the quality.  But for a given bitrate, we have a
choice of algorithms to determine the best scalefactors and Huffman encoding (noise shaping).

and about option "-V":

> -V n   
0 <= n <= 9
Enable VBR (Variable BitRate) and specifies the value of VBR quality (default = 4).  0 = highest quality.

I, for myself, use only "preset=1002" - extreme preset - because "These {presets}  are continually updated to coincide with the latest developments that occur and as a result should provide you with nearly the best quality currently possible from LAME" (again quoting from lame manpage).

The gstreamer line I use is:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=1002 ! xingmux ! id3v2mux
```

---

### Post by dstein on 2008-10-18
Thanks for the reply Zatta. I am familiar with the normal lame options, which I now use independently of gstreamer. However, it seems that although gstreamer uses lame, it takes different options. Examples of these can be seen in my first post.

---

### Post by Kenno on 2009-01-03
[The gstreamer lame plugin is broken.]("https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/195483/comments/22") [Instead, please use rubyripper for ripping CDs.]("http://wiki.hydrogenaudio.org/index.php?title=Rubyripper#Installation_on_Ubuntu_8.04") Happy ripping!

---

### Post by noob5000 on 2009-07-25
> **Kenno said:**
> [The gstreamer lame plugin is broken.]("https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/195483/comments/22") 
does this mean one should NOT AT ALL use gstreamer lame for encoding wavs to mp3?
for example, "sound converter" uses the gstreamer-lame plugin. should i not use it then?

---

### Post by david stevenson on 2010-01-05
> **Kenno said:**
> [The gstreamer lame plugin is broken.]("https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/195483/comments/22") [Instead, please use rubyripper for ripping CDs.]("http://wiki.hydrogenaudio.org/index.php?title=Rubyripper#Installation_on_Ubuntu_8.04") Happy ripping!


According to the link this is now fixed.
However I am still having problems, can any one confirm which versions of gstreamer and sound juicer have the fix, and what is now a good profile pipeline command?

(rubyripper cannot find my usb CD drive)
David

---

### Post by ubun2ibun3 on 2010-04-05
I also cannot find any documentation after some Google searches.  I'm sure it's out there, I just don't know where!

EDIT: Actually, it's right here:
[http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-ugly-plugins/html/gst-plugins-ugly-plugins-lame.html](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-ugly-plugins/html/gst-plugins-ugly-plugins-lame.html)

---

### Post by deezer on 2010-08-19
> **Kenno said:**
> [The gstreamer lame plugin is broken.]("https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/195483/comments/22") [Instead, please use rubyripper for ripping CDs.]("http://wiki.hydrogenaudio.org/index.php?title=Rubyripper#Installation_on_Ubuntu_8.04") Happy ripping!

In Ubuntu 10.04 x64 - fully updated

RubyRipper is excruciatingly slow on Ubuntu 10.04
grip is unstable (compiled from source).
Rhythymbox still has bug 195483 - 128 rip no matter what
abcde only works from the command line (but I might have to resort to this)
Sound Juicer still has bug 195483 - 128 rip no matter what
RipperX does not allow for a correct configuration of lame

It sure would be nice to have a decent CD ripper that works well in 10.04 x64!

---

### Post by deezer on 2010-08-19
> **deezer said:**
> In Ubuntu 10.04 x64 - fully updated

RubyRipper is excruciatingly slow on Ubuntu 10.04
grip is unstable (compiled from source).
Rhythymbox still has bug 195483 - 128 rip no matter what
abcde only works from the command line (but I might have to resort to this)
Sound Juicer still has bug 195483 - 128 rip no matter what
RipperX does not allow for a correct configuration of lame

It sure would be nice to have a decent CD ripper that works well in 10.04 x64!

Well, after using abcde I don't really miss any of the other rippers, it works very well!

Still would be nice if Ubuntu had a GUI-based ripper that was configurable and worked in 10.04 x64, but I'm not missing that too much after I got abcde up and running.

My abcde config, for what it's worth, mostly taken from [http://andrews-corner.org/abcde.html](http://andrews-corner.org/abcde.html)

```

# -----------------$HOME/.abcde.conf----------------- #

# Specify the encoder to use for MP3. In this case
# the alternatives are gogo, bladeenc, l3enc, xingmp3enc, mp3enc.
MP3ENCODERSYNTAX=lame 

# Specify the path to the selected encoder. In most cases the encoder
# should be in your $PATH as I illustrate below, otherwise you will 
# need to specify the full path. For example: /usr/bin/lame
LAME=lame

# Specify your required encoding options here. Multiple options can
# be selected as '--preset standard --another-option' etc.
#normal
LAMEOPTS='--preset extreme' 
#voice
#LAMEOPTS='-V 8 --vbr-new -mm --id3v2-only'

# Output type for MP3.
OUTPUTTYPE="mp3"

# The cd ripping program to use. There are a few choices here: cdda2wav,
# dagrab, cddafs (Mac OS X only) and flac.
CDROMREADERSYNTAX=cdparanoia            
                                     
# Give the location of the ripping program and pass any extra options:
CDPARANOIA=cdparanoia  
#CDPARANOIAOPTS="--never-skip=40"

# Give the location of the CD identification program:       
#CDDISCID=cd-discid            
                               
# Give the base location here for the encoded music files.
OUTPUTDIR="$HOME/Music/abcderips/"               

# The default actions that abcde will take.
ACTIONS=cddb,read,encode,tag,replaygain,move,playlist,clean
              
# Decide here how you want the tracks labelled for a standard 'single-artist',
# multi-track encode and also for a multi-track, 'various-artist' encode:
OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}/${ALBUMFILE}_(${YEAR})/${TRACKNUM}-${ARTISTFILE}-${TRACKFILE}'
VAOUTPUTFORMAT='${OUTPUT}/Various/${ALBUMFILE}_(${YEAR})/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'

# Decide here how you want the tracks labelled for a standard 'single-artist',
# single-track encode and also for a single-track 'various-artist' encode.
# (Create a single-track encode with 'abcde -1' from the commandline.)
ONETRACKOUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}/${ALBUMFILE}_(${YEAR})/${TRACKNUM}-${TRACKFILE}'
VAONETRACKOUTPUTFORMAT='${OUTPUT}/Various/${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'

# Create playlists for single and various-artist encodes. I would suggest
# commenting these out for single-track encoding.
PLAYLISTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}.m3u'
VAPLAYLISTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}.m3u'

# What extra options?
MAXPROCS=2                              # Run a few encoders simultaneously
PADTRACKS=y                             # Makes tracks 01 02 not 1 2
EXTRAVERBOSE=y                          # Useful for debugging
EJECTCD=y                               # Please eject cd when finished :-)
DOSPLAYLIST=y
INTERACTIVE=y

```

---

### Post by andrew.46 on 2010-08-20
Hi deezer,

> **deezer said:**
> My abcde config, for what it's worth, mostly taken from [http://andrews-corner.org/abcde.html](http://andrews-corner.org/abcde.html)

Nice page, if I say so myself :).

Andrew

---

