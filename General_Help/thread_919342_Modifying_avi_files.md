---
title: "Modifying avi files"
date: 2008-09-13
forum: General Help
---

### Post by QwUo173Hy on 2008-09-13
I ripped a few DVDs of a TV series I like. The episodes are only 24 minutes long yet the file sizes for each file varies from 300 to 600 megabytes.

I forget how I ripped them, but can someone guide me on how I might re-compress them to something more reasonable?

---

### Post by mb_webguy on 2008-09-13
Transcoding from a lossy format to a lossy format always results in degraded audio and video, so I don't recommend it.  If you still have the DVDs, it would probably be better to re-rip them rather than transcode the ripped files.  I recommend OGMrip ("sudo apt-get install ogmrip"), because it has a simple interface and supports the latest and best containers and codecs (particularly mkv-x264-AAC... *drool*) as well as the more common avi-xvid-mp3 combo.

Having said that, there are several applications you can use to transcode your files.  Some people prefer using mencoder in the command line, and while this does give you the most options, I think it's overkill for the casual user.  A simpler option would be Avidemux, which you can find in the repositories ("sudo apt-get install avidemux").  Just open the file using Avidemux, select the video codec, audio codec, and container from the drop-down controls on the left, and (in your case) configure the codecs.  You probably want to configure the video codec for "Two Pass - Video Size" and set the target file size for something more reasonable like 150MB-200MB.

---

### Post by QwUo173Hy on 2008-09-13
Thanks mb_webguy. That's everything I need to know. I've left the DVDs in my friends attic and copied everything to the computer before moving house so I think AVIdemux will suit best on this occasion.

Thanks again,
Jarlath

---

### Post by QwUo173Hy on 2008-09-14
I've noticed that although all the files are the same running time (about 25 minutes). One is 228 MB while another s 643 MB. I've checked the properties using nautilus / totem and all the properties seem identical (dimensions, codec, framerate, audio codec, running time). What property remains that could be causing this difference?

I ask because this is what I need to change when I encode the new version.

---

