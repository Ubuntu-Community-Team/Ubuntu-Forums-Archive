---
title: "dvd-slideshow - no vob file is generated"
date: 2005-11-14
forum: General Help
---

### Post by element on 2005-11-14
Im really exited to use dvd-slideshow, but for some reason when I try it I dont get the .vob file as mentioned in the example here...
[http://dvd-slideshow.sourceforge.net/examples/complete/]("http://dvd-slideshow.sourceforge.net/examples/complete/")

All I get is the .xml file.  Can anyone help me out with this?  
Thanks!
[B]
Here is the command I am running...[/B]

dvd-slideshow -o /home/cory/dvd -n 'myfirstdvd'  -f myfirstdvd.txt

**Here are the three errors I see when it tries to build it...**

############################################
[dvd-slideshow] Creating black background
[dvd-slideshow] Working on 0/23 title, 0:0:5.0
[dvd-slideshow] Making title slide:
[dvd-slideshow]         Title1=myfirstdvd
[dvd-slideshow]         Title2=
**ERROR: [mpeg2enc] Could not read YUV4MPEG2 header: stream requires unsupported  features!
[dvd-slideshow]########################################

[dvd-slideshow]########################################
[dvd-slideshow] waiting for mpeg2enc to finish...
mv: cannot stat `/home/cory/dvd/video_0.mpg': No such file or directory
[dvd-slideshow]###############

[dvd-slideshow]########################################
[dvd-slideshow] Multiplexing audio and video.
[dvd-slideshow] Some sequence marker warnings here are normal
**ERROR: [mplex] Unable to open file /home/cory/dvd/video.mpg for reading.
[dvd-slideshow] No subtitles... removing .spumux file
[dvd-slideshow] total chapters=18
[dvd-slideshow]##########################################

---

### Post by poptones on 2005-11-14
I found this answer after googling the complete error message you are getting 

[mpeg2enc] Could not read YUV4MPEG2 header: stream requires unsupported features!

[http://fredrik.hubbe.net/hacker/viewtopic.php?p=1597](http://fredrik.hubbe.net/hacker/viewtopic.php?p=1597)

I do not have the software installed. Scroll down to the bottom of the page and see if it makes sense to you. Not sure where you would invoke this option, but it seems to work.

Other way would be to just download mjpegtools 1.6.2 and compile it for your machine.

---

### Post by element on 2005-11-15
I emailed the developer and this is the response I got...

"This is a known issue with newer versions of mjpegtools.  In the mean
time, please try out my latest unreleased version (0.7.2).  It should
fix your problems, but hopefully not add to many more problems! ;-)"

If you want the latest unreleased version PM me and I will email it to you.

---

