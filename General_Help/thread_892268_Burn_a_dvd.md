---
title: "Burn a dvd"
date: 2008-08-17
forum: General Help
---

### Post by fedex1993 on 2008-08-17
Okay well i have a .avi file and my question is how can i burn it to a dvd almost like a movie. Like i can put it into my dvd player and have a dvd menu and stuff. Is this possbile?

---

### Post by Rumel on 2008-08-17
You'll have to get something like DVD Styler. I've only used this program in Windows and it didn't work the best. It's built on linux though so I'm going to assume it works better on linux.
[DVD Styler]("http://www.dvdstyler.de/")
If that doesn't work maybe something in the list at the bottom of this page will.
[Good 'ole Wikipedia]("http://en.wikipedia.org/wiki/Dvd_authoring")

---

### Post by sleepingdragon on 2008-08-17
There are couple of good programs in Ubuntu to make DVDs.

DeVeDe is a small program that allows for simple menu creation, it creates a .ISO file which can then burnt to CD/DVD. It'd also pretty fast. DeVeDe also has the option of making a DVD with no menu at all, you insert the disk into your DVD player and the film starts immediately. 

QDVDAuthor is a bit more complex to use, but does offer a wide range of facilities to make interactive menus. With a bit of practice, they can be as good as something you would find on a professionally made DVD.

Both of these are available in the Ubuntu repositories.

---

### Post by fedex1993 on 2008-08-17
> **sleepingdragon said:**
> There are couple of good programs in Ubuntu to make DVDs.

DeVeDe is a small program that allows for simple menu creation, it creates a .ISO file which can then burnt to CD/DVD. It'd also pretty fast. DeVeDe also has the option of making a DVD with no menu at all, you insert the disk into your DVD player and the film starts immediately. 

QDVDAuthor is a bit more complex to use, but does offer a wide range of facilities to make interactive menus. With a bit of practice, they can be as good as something you would find on a professionally made DVD.

Both of these are available in the Ubuntu repositories.
devede seems pretty slow the last time i used it. is there a way i can speed it up?

---

### Post by sleepingdragon on 2008-08-17
yes, i did find DeVeDe a little slow at first, but there are a few tricks you can do to help. When you add a video file to DeVeDe, there is an "Advanced Options" section you can use. From that, remove the tick from the "Use 16:9 aspect ratio for output", and under the *Quality Options* tab, remove the tick from *Use Trellis Search *and tick *Use MBCMP (faster)*. The 16:9 aspect ratio tick doesn't improve speed, but the video seems to become amorphic (it changes to fit your actual screen ratio), so it fits whatever screen you're using... nice. 

Using the above seems to drop my processing time to about 55 mins on a 2.4 Celeron with 1Gb of RAM. This is about twice as fast as not changing those options.

---

### Post by fedex1993 on 2008-08-17
> **sleepingdragon said:**
> yes, i did find DeVeDe a little slow at first, but there are a few tricks you can do to help. When you add a video file to DeVeDe, there is an "Advanced Options" section you can use. From that, remove the tick from the "Use 16:9 aspect ratio for output", and under the *Quality Options* tab, remove the tick from *Use Trellis Search *and tick *Use MBCMP (faster)*. The 16:9 aspect ratio tick doesn't improve speed, but the video seems to become amorphic (it changes to fit your actual screen ratio), so it fits whatever screen you're using... nice. 

Using the above seems to drop my processing time to about 55 mins on a 2.4 Celeron with 1Gb of RAM. This is about twice as fast as not changing those options.
yeah it took me 1 hour 8 mins. Also i had a problem playing it on my dvd player. Is there some setting that will enable it for me to play it on a dvd player?

---

### Post by lisati on 2008-08-17
> **Rumel said:**
> You'll have to get something like DVD Styler. I've only used this program in Windows and it didn't work the best. It's built on linux though so I'm going to assume it works better on linux.
[DVD Styler]("http://www.dvdstyler.de/")
If that doesn't work maybe something in the list at the bottom of this page will.
[Good 'ole Wikipedia]("http://en.wikipedia.org/wiki/Dvd_authoring")

Thanks for the reference, I'll be checking it out some time. As someone frustrated with some of the Linux offerings for video editing and DVD authoring, I'll find it useful to know about this one.

EDIT: I just downloaded the DEB package. I got an error about an unsatisfiable dependency (libwxgtk2.6-0), so I might have to come back to it when I have the inclination to research it.

---

### Post by tuxulin on 2008-08-17
do it on the command line i find quick and simple in 4 easy steps

(1) transcode -i your-movie.avi -y ffmpeg --export_prof dvd-ntsc --export_asr 2 -o movie -D0 -s2 -m movie.ac3 -J modfps=clonetype=3 --export_fps 29.97

(2) mplex -f 8 -o dvd_movie.mpg movie.m2v movie.ac3

(3) create a text file with these contents and save as dvdauthor.xml
<dvdauthor dest="DVD">
  <vmgm />
   <titleset>
     <titles>
       <pgc>
         <vob file="dvd_movie.mpg" chapters="0,15:00,30:00,45:00,1:00:00"/>
       </pgc>
      </titles>
   </titleset>
 </dvdauthor>

(4) dvdauthor -x dvdauthor.xml

thats the way i do all my DVD's and they all work great. plus doing it this way makes you do some research on the commands in which gives you a better understanding in how things really work.

Tuxulin

---

### Post by fedex1993 on 2008-08-17
> **tuxulin said:**
> do it on the command line i find quick and simple in 4 easy steps

(1) transcode -i your-movie.avi -y ffmpeg --export_prof dvd-ntsc --export_asr 2 -o movie -D0 -s2 -m movie.ac3 -J modfps=clonetype=3 --export_fps 29.97

(2) mplex -f 8 -o dvd_movie.mpg movie.m2v movie.ac3

(3) create a text file with these contents and save as dvdauthor.xml
<dvdauthor dest="DVD">
  <vmgm />
   <titleset>
     <titles>
       <pgc>
         <vob file="dvd_movie.mpg" chapters="0,15:00,30:00,45:00,1:00:00"/>
       </pgc>
      </titles>
   </titleset>
 </dvdauthor>

(4) dvdauthor -x dvdauthor.xml

thats the way i do all my DVD's and they all work great. plus doing it this way makes you do some research on the commands in which gives you a better understanding in how things really work.

Tuxulin

does it work in your dvd player?

---

### Post by tuxulin on 2008-08-17
it sure does ...... 
at the end it will create a DVD folder with all the needed files needed to be watchable on any if not all (home) dvd players.

all you need to do is open K3b and choose "New video DVD project"
simply drag all the files within your ~/name-of-avi-folder/DVD/VIDEO_TS/
to the VIDEO_TS folder thats in kb3 8 minutes laters youll be watching your DVD

Tuxulin

---

### Post by fedex1993 on 2008-08-17
> **tuxulin said:**
> it sure does ...... 
at the end it will create a DVD folder with all the needed files needed to be watchable on any if not all (home) dvd players.

all you need to do is open K3b and choose "New video DVD project"
simply drag all the files within your ~/name-of-avi-folder/DVD/VIDEO_TS/
to the VIDEO_TS folder thats in kb3 8 minutes laters youll be watching your DVD

Tuxulin

thats cool. Hmm it works with my old tube tv but not our widescreen i am guessing it is the wrong aspect ratio

---

### Post by tuxulin on 2008-08-17
im not sure what the problem is a i have a boring tube tv. 
however if it is the aspect ratio then see here for getting the correct
aspect ratio
[http://www.transcoding.org/cgi-bin/transcode?action=browse&diff=1&id=Aspect_Ratio](http://www.transcoding.org/cgi-bin/transcode?action=browse&diff=1&id=Aspect_Ratio)

i hope it helps

Tuxulin

---

### Post by fedex1993 on 2008-08-17
well my boring tube tv it runs okay but i think the dvd was to scratched and now everything is miss matched and messed up oh well i am getting a new one tomorrow

---

### Post by sleepingdragon on 2008-08-18
I'm a little surprised you could not get a DeVeDe ISO to work correctly on your DVD player. Personally, I've never had a single failure using it.

Does your DVD player have problems playing any other type of DVD? Sometimes, older players do have problems playing DVD-R/RW

---

### Post by fedex1993 on 2008-08-19
> **sleepingdragon said:**
> I'm a little surprised you could not get a DeVeDe ISO to work correctly on your DVD player. Personally, I've never had a single failure using it.

Does your DVD player have problems playing any other type of DVD? Sometimes, older players do have problems playing DVD-R/RW

Well i found out that the .avi format when i transcoded it from the dvd rip was actually messed up but the dvd has scratches all over there should be a new one tomorrow.

---

### Post by Cresho on 2008-08-19
I use mandvd.  IT is fawless.  The only thing you cannot do is mix 16:9 or 4:3.  It is one or the other.  Another thing is the slideshow is not working but I have a fix for it.

Here is apart of my notes i keep around.(not my notes but someone elses, DUH!)  sorry for typo

[http://fuocotools.byethost13.com/index.php?topic=90.0](http://fuocotools.byethost13.com/index.php?topic=90.0)


sudo apt-get install sox libsox-fmt-all ffmpeg


gksudo gedit  /usr/bin/dvd-slideshow

replace the script with the info found in 
dvd-slideshow file

original download here
[http://www.mediafire.com/?obhkmt3xfjg](http://www.mediafire.com/?obhkmt3xfjg)

---

### Post by Bigtime_Scrub on 2008-08-19
Just so you get a 2nd opinion....

I love DeVeDe. It does everything I want it to do. Very solid program.

I want to add though, a useful tool for video conversions is AcetoneISO2.It can convert images to iso and play mount/play iso images. If you use a lot of multimedia it helps.

---

### Post by fedex1993 on 2008-08-19
well i am ripping the dvd with dvdrip and the problem seems to be when making the .avi file. After it is finished the movie seems to play fine but then it the movie freezes buit the sound is still going so if you fast forward the sound is all in the wrong place. Are there any other dvd ripping program out there?

---

