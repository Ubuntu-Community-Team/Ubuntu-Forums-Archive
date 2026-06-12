---
title: "AVI Converter, &quot;Archos 2&quot; mp3 player"
date: 2009-07-31
forum: Hardware
---

### Post by ertw1 on 2009-07-31
Hello,

I recently purchased an Archos 2 mp3 player ([http://www.archos.com/products/mp3_players/archos_2/index.html](http://www.archos.com/products/mp3_players/archos_2/index.html)) which Archos states is fully compatible with Linux.  It works like a dream on Ubuntu :) except for one detail...to play AVI files on the unit the AVI files first need to be converted to a special AVI format (changes in resolution, frame rate, audio sampling rate, codec, etc).  The unit ships with Windows-only AVI converter software ([http://mympxdownloads.com/Downloads/p13_sectionid/2/p13_fileid/26](http://mympxdownloads.com/Downloads/p13_sectionid/2/p13_fileid/26)) creatively called AVIConverter.  This software won't work on Wine.  I would like to avoid using a Virtual Machine with Windows if at all possible.  I've performed my own trial and error with several Linux based video conversion software I found on Google and in the repositories...with no success.  So here is my challenge:

Archos left an example AVI file on the mp3 player (which works)

Is there any software out there that can analyze this AVI file and extract all the relevant format details (resolution, frame rate, codec, etc)?  In addition, I'll need a second piece of software to convert my AVI files to this format.  

Thanks in advance! :D

---

### Post by ertw1 on 2009-08-01
SOLVED!

I found the solution at [http://forum.archosfans.com/viewtopic.php?f=48&t=23544](http://forum.archosfans.com/viewtopic.php?f=48&t=23544) credit goes to user: pliny, enter the following into the command line:

mencoder $source -o $output -ofps 15 -vf-add scale=160:128 -vf-add expand=160:128:-1:-1:1 -srate 44100 -ovc xvid -xvidencopts bitrate=$bitrate:max_bframes=0:quant_type=h263 -oac lavc -lavcopts acodec=mp2:abitrate=96

"Replace $source, $output, and $bitrate with whatever is appropriate for you. The converter had options for bitrates of 400, 300, and 250. In my tests, I didn't really notice a difference, but your mileage may vary." -pliny

Worked like a charm!

---

### Post by scorp123 on 2009-08-05
Thanks for your posting. I just got my wife an "Archos 2" player :)

---

### Post by little_penguin on 2009-09-17
You can also try _Iriverter_ from the repositories, it converts videos for devices with smaller screens and has a very easy interface.

---

### Post by scorp123 on 2009-09-19
> **little_penguin said:**
> You can also try _Iriverter_ from the repositories, it converts videos for devices with smaller screens and has a very easy interface. The idea certainly sounds nice but "iriverter" has a ton of dependencies:

```
 > sudo apt-get install iriverter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  fastjar gcj-4.2-base gcj-4.3-base gij-4.2 gij-4.3 java-gcj-compat java-gcj-compat-headless libbcel-java libgcj-bc libgcj-common libgcj8-1 libgcj8-1-awt libgcj8-jar libgcj9-0
  libgcj9-0-awt libgcj9-jar liblog4j1.2-java liblog4j1.2-java-gcj libmozjs0d libmx4j-java libregexp-java libswt3.2-gtk-gcj libswt3.2-gtk-java libswt3.2-gtk-jni libxul-common
  libxul0d
Suggested packages:
  gcj-4.2 gcj-4.3 libgcj9-src libgcj9-dbg libbcel-java-doc libgcj8-dbg libgnumail-java jython
The following NEW packages will be installed
  fastjar gcj-4.2-base gcj-4.3-base gij-4.2 gij-4.3 iriverter java-gcj-compat java-gcj-compat-headless libbcel-java libgcj-bc libgcj-common libgcj8-1 libgcj8-1-awt libgcj8-jar
  libgcj9-0 libgcj9-0-awt libgcj9-jar liblog4j1.2-java liblog4j1.2-java-gcj libmozjs0d libmx4j-java libregexp-java libswt3.2-gtk-gcj libswt3.2-gtk-java libswt3.2-gtk-jni
  libxul-common libxul0d
0 upgraded, 27 newly installed, 0 to remove and 0 not upgraded.
Need to get 60.6MB of archives.
After this operation, 169MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
```

Just using the "mencoder" shell command certainly is leaner and quicker IMHO. But OK ... if someone really wants a GUI. Just be aware that "iriverter" pulls in a ton of other stuff ...

---

### Post by mfdc1969 on 2010-08-01
I just bought this player on sale a few weeks ago and also was struggling to get my videos to play ... the only thing that has so far worked came from this post on Linux Format (UK Magazine):

[http://www.linuxformat.co.uk/forums/viewtopic.php?p=83649]("http://www.linuxformat.co.uk/forums/viewtopic.php?p=83649")

I copy it here for convenience and give full credit to the user Woofage for making my videos play!:

If you want to use Linux to re-scale video for the above player, save the following string into a text file (say called archos_video) and give it executable permissions:
Code:
```
mencoder -noodml "$1" -of avi -o "$2" -ofps 18 -vf-add scale=220:176, -vf-add expand=220:176:-1:-1:1,rotate=2,flip -srate 44100 -ovc xvid -xvidencopts bitrate=550:max_bframes=0:quant_type=h263:me_quality=0 -oac lavc -lavcopts acodec=mp2:abitrate=64
```


Run using:
Code:
```
./archos_video original_video_filename rescaled_video.avi
```

---

### Post by cataclysmic on 2011-06-07
Hey guys  I tried the above settings and tried to replicate them in avidemux as well. But my videos speeds up incredibly.  It is a 1 minute video which basically runs through in under 1 sec. 
The framerate of this input file is already 15fps but if I do not "resample" only audio works, if I resample the speeding up happens.  Any ideas what my mistake might be? 

PS: The speeding up happens with mencoder as well as avidemux.

PPS: I installed the aviconverter from the device onto a windows machine and that output works. :confused:

---

