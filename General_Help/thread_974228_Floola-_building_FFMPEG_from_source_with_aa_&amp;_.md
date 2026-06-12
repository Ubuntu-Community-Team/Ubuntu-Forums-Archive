---
title: "Floola- building FFMPEG from source with aa &amp; h264 plugins?"
date: 2008-11-07
forum: General Help
---

### Post by fINTiP on 2008-11-07
I've never built something from source myself, and figure this is a great chance to learn- if this should go in the multimedia section, I'd be glad to have it moved, but I didn't think it'd quite fit there.

For Floola, an itunes alternative, it is possible to set it up so that you can type in a url from, say, youtube, and have it download, convert, and sync the video to your ipod. However, you have to build FFMPEG from source for this to work- from the FAQ's:

> FFmpeg executable has to be installed under /usr/local/bin. It has to be manually compiled with at least aac and h264 plugins. Linux users should refer to their distribution support forum (or google) for more information about how to manually build ffmpeg with these plugins. 

--http://www.floola.com/modules/wiwimod/index.php?page=docs_troubleshooting (under "web download (youtube, myspace)").

So how do I go about doing this? This isn't by chance already done is it?

running 8.04 studio ubuntu.

K

---

### Post by Yellow Pasque on 2008-11-07
```
This isn't by chance already done is it?
```
[http://packages.medibuntu.org/hardy/ffmpeg.html](http://packages.medibuntu.org/hardy/ffmpeg.html)

After installing, you may have to go into Synaptic (System -> Administration), select ffmpeg and use the 'Lock Version' option under the 'Package' menu to keep Ubuntu from "upgrading" to a newer version without the aac/h.264 support.

---

### Post by fINTiP on 2008-11-07
What exactly does it mean to "install under usr/local/bin"?

So all I need to do is install that package and make sure ubuntu doesn't upgrade it? No exciting jazz?

L

---

### Post by Yellow Pasque on 2008-11-07
> What exactly does it mean to "install under usr/local/bin"?
The directions sound like they are written for multi-user systems. In your case, all you'll need to do is install the correct .deb

> So all I need to do is install that package and make sure ubuntu doesn't upgrade it? No exciting jazz?
Yes. Sorry for the lack of excitement.

---

### Post by fINTiP on 2008-11-16
So, this hasn't worked for me... I did as followed, but for some reason medibuntu's codecs are not being installed, though it says it is the medibuntu build.

I've been trying to figure it out with someone here: [http://ubuntuforums.org/showthread.php?p=6193161&posted=1#post6193161](http://ubuntuforums.org/showthread.php?p=6193161&posted=1#post6193161)

Your help would be greatly appreciated.

K

---

