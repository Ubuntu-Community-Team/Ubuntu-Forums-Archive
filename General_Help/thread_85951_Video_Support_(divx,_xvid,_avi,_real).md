---
title: "Video Support (divx, xvid, avi, real)"
date: 2005-11-03
forum: General Help
---

### Post by fmanji on 2005-11-03
Okay,

I really have tried everything I can think of short of a complete re-install.
I have tried everything in ubuntuguide, I have reinstalling certain packages, I have tried using automatix.

But I simply can't get video to play in any player, I have tried, vlc, real, totem, xine, mplayer.

I have also downloaded w32codecs, and libdvdcss2.

I can't play any movie in xvid format, or any format for that matter, sound works just fine.

Can anybody guide me in the right direction?  How about some baby steps like getting vlc working?

---

### Post by mwillems on 2005-11-03
I have similar problems - I can play but not well. Sound lags. Ot aspect ratio os wrong. Etc. I do hope we can get some instructions posted somewhere: media playing is not an option, it is a sine qua non necessity.

---

### Post by fmanji on 2005-11-03
Especially mplayer, I get an errora
alsa-control: unable to find simple control 'PCM',0

---

### Post by Metro on 2005-11-03
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies)

I have installed folowing this guide:)

---

### Post by CyiPherX on 2005-11-04
[QUOTE=fmanji]Okay,

I really have tried everything I can think of short of a complete re-install.
I have tried everything in ubuntuguide, I have reinstalling certain packages, I have tried using automatix.

But I simply can't get video to play in any player, I have tried, vlc, real, totem, xine, mplayer.

I have also downloaded w32codecs, and libdvdcss2.

I can't play any movie in xvid format, or any format for that matter, sound works just fine.

Can anybody guide me in the right direction?  How about some baby steps like getting vlc working?[/QUOTE]

Heres what i did to get everything working, with totem as the video player.

Use the package manager to download all thse packages-

Libraries (multiverse) > gstreamer0.8-plugins-multiverse
Libraries (universe) > gstreamer0.8-plugins
Libraries (universe) > gstreamer0.8-ffmpeg
Libraries (universe) > gstreamer0.8-mad
Multimedia > vorbis-tools
Multimedia (multiverse) > lame
Multimedia (multiverse) > faad
Multimedia (multiverse) > gstreamer0.8-lame
Multimedia (universe) > sox
Graphics (multiverse) > mjpegtools
Graphics (universe) > ffmpeg
GNOME Desktop Enviroment (universe) > totem-xine

Some the above may not be found, if so just skip to the next one.
Then register the G-Streamer in terminal by typing "gst-register-0.8", without the quotes.

next install “xine-ui” in the package manager.

Launch Totem and try to play a video (this will create a .config file).

Download the W32 codecs from this website:
[http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html)
(just download the “essential codecs package”)

Now open the terminal and follow these steps:

a) Get to the directory where you have downloaded the file 

"cd /home/(your download folder)"

b) Create the directory in which you are going to put the codecs 

"sudo mkdir /usr/lib/win32"

c) Now, assuming the file you downloaded is “essential-20050412.tar.bz2”

copy this to the terminal "tar -xjf essential-20050412.tar.bz2" (this will extract the file)

"sudo mv essential-20050412/* /usr/lib/win32" (this command will move the files to the desired folder)

d) Now restart totem (if you were using it)

Congratulations, now you can open wma, wmv, divx, quicktime mpegs and avi files by using Totem and Xine!

CyiPherx:smile:

---

### Post by fmanji on 2005-11-04
Metro I followed the directions on [http://help.ubuntu.com/starterguide/...sic-and-movies](http://help.ubuntu.com/starterguide/...sic-and-movies)

Most of it is covered off by automatix, so still no change

CyiPherX, I thought I had it fixed because there were no codecs in /usr/lib/win32, so I installed those, but still no luck, I also restarted LINUX, still nothing.

In XINE-UI I moved the video driver from auto to xv, no change, so I moved it back.

It's quite strange because the video player knows the meta details about the video, e.g. it changes the aspect ratio, you can hear audio, but NO video!

Anyone else willing to give it a shot?

---

### Post by Jack_S on 2005-11-04
Hi,

In a mater of xvid , in my opinion you should install libxvidcore4 library. Go to Synaptic and search for xvid, then check libraries concerned with xvid and other video formats.

Regards,
Jack

---

### Post by 357Magnum on 2005-11-04
[QUOTE=CyiPherX]Heres what i did to get everything working, with totem as the video player.

Use the package manager to download all thse packages-

Libraries (multiverse) > gstreamer0.8-plugins-multiverse
Libraries (universe) > gstreamer0.8-plugins
Libraries (universe) > gstreamer0.8-ffmpeg
Libraries (universe) > gstreamer0.8-mad
Multimedia > vorbis-tools
Multimedia (multiverse) > lame
Multimedia (multiverse) > faad
Multimedia (multiverse) > gstreamer0.8-lame
Multimedia (universe) > sox
Graphics (multiverse) > mjpegtools
Graphics (universe) > ffmpeg
GNOME Desktop Enviroment (universe) > totem-xine

Some the above may not be found, if so just skip to the next one.
Then register the G-Streamer in terminal by typing "gst-register-0.8", without the quotes.

next install “xine-ui” in the package manager.

Launch Totem and try to play a video (this will create a .config file).

Download the W32 codecs from this website:
[http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html)
(just download the “essential codecs package”)

Now open the terminal and follow these steps:

a) Get to the directory where you have downloaded the file 

"cd /home/(your download folder)"

b) Create the directory in which you are going to put the codecs 

"sudo mkdir /usr/lib/win32"

c) Now, assuming the file you downloaded is “essential-20050412.tar.bz2”

copy this to the terminal "tar -xjf essential-20050412.tar.bz2" (this will extract the file)

"sudo mv essential-20050412/* /usr/lib/win32" (this command will move the files to the desired folder)

d) Now restart totem (if you were using it)

Congratulations, now you can open wma, wmv, divx, quicktime mpegs and avi files by using Totem and Xine!

CyiPherx:smile:[/QUOTE]


Hi, thx for posting this info, I followed it and now when I click on a video at big-boys.com it actually starts it.

The problem I'm having is the video only plays for about 3 seconds and then just stops. If I reload the page to get it to start over it does the same thing. Can't watch more than the first 3 secs or so.

Any idea as to why???

---

### Post by fmanji on 2005-11-04
Bump.

Guys this is still a no go, have tried every suggestion here, can we maybe ge some guidance from someone in the know?

---

### Post by tardis on 2005-11-04
Don't know if this will help but here goes.  I had to install kunbutu so that I could have kaffeine movie player.  If you do as stated in the other post you can use kaffeine in gnome.  But you will have to choose the kaffeine engine instead of the kaffeine-gstreamer engine.  It was tough to get working right but worth the time, give it a try...

---

### Post by ubuntu27 on 2005-11-05
I am having similar problem with sounds. WMA. I've followed[ the Guide](http://help.ubuntu.com/starterguide/C/faqguide-all.html), installed all the codecs, eve the restricted ones...
and and yet I cannot play MWA files.... [I can play MP3 though]

---

### Post by fmanji on 2005-11-05
It just shouldn't be this difficult, there's got to be someone who has done this and got it working.

I have tried every suggestion in this thread, and still no go.

I really think it is something very simple that's being overlooked, anyone with experience here to guide me through it?:confused:

---

### Post by fmanji on 2005-11-06
Bump

---

### Post by TonyDTV on 2005-11-06
I have no luck playing any video with this distro, Im about to give it up and go back to windoz at least I can watch my videos on that platform.Maybe when this OS matures enough to get this situation under control Ill check it out again.I was just getting to like it till this happened and by reading all the post I feel like I have to get a degree in computer programming to get a player that only stays on for 3 sec!!

---

### Post by fmanji on 2005-11-06
Well i'ts nice to know i'm not alone, but I'm amazed that this hasn't become a bigger issue, it seems there are a lot of people in the same boat, I was really hoping that one of the Senior members of the forums would have an answer.

If anyone can solve this, I promise to post the fix back here in easy to read point form, hey maybe we can even make it a sticky!

Someone help us!!

---

### Post by RAOF on 2005-11-06
You could try the totem-xine backend, if you haven't already.

Install the package "totem-xine" in synaptic.  It will tell you that it will remove "totem-gstreamer" - that's ok.  Xine handles some things better, particularly dvds.  Give it a try.

---

### Post by fmanji on 2005-11-06
RAOF, thanks for the guidance, unfortunately I have this installed and it's still a no-go.  I'm close to the point of moving to Mandriva or something because how can one live with a distro that does not play video?:???:

---

### Post by RAOF on 2005-11-06
Ohh, oh, I seem to remember helping this guy who had video-playback problems, and coincidentally also had video driver problems.  Fixing the driver problems **also** fixed the video-playback problems.

Given that everything but the actual video display works, perhaps that's the problem?  What graphics card/xorg drivers are you using?  Have you tried all the possible video outputs (I don't know xine-ui, but there should be some of xv, opengl, X11, X11-shm, SDL,... try each of those, whatever is there).  I'll try and find the thread... [here it is]("http://www.ubuntuforums.org/showthread.php?t=82154&page=3&highlight=video").  The symptoms were different, but that guy couldn't play video, and the fix was to get his graphics drivers working...

---

### Post by fmanji on 2005-11-06
But if my graphics drivers were the problem, would I not be able to use gnome and firefox?

Because my graphics seems just fine, I can see pictures, and use gnome.

Well, regardless, I'll take a look at the thread, and try to follow it, maybe it will help, i'll post back...thanks!

---

### Post by RAOF on 2005-11-06
[QUOTE=fmanji]But if my graphics drivers were the problem, would I not be able to use gnome and firefox?

Because my graphics seems just fine, I can see pictures, and use gnome.

Well, regardless, I'll take a look at the thread, and try to follow it, maybe it will help, i'll post back...thanks![/QUOTE]
Actually, video playback uses pretty much unique parts of your graphics driver (it uses all sorts of overlay-mumbo-jumbo).  So it's entirely possible that Gnome and everything works, but video doesn't display.

---

### Post by PsychoTrauma on 2005-11-06
I always set up video by doing the following:

```
sudo apt-get install totem-xine
```

Then I browse to the mplayer website and download the linux "all" codec package.

After the codec package has been downloaded I right click it and uncompress it.

```
sudo mkdir /usr/lib/win32
```

```
sudo nautilus
```

I then use the root nautilus I just opened to move the contents of the codec package to the win32 directory I just made.

After I have done that I can open and view all types of video with no problems.

---

### Post by fmanji on 2005-11-07
GREAT NEWS!!

I got video working and here's what I did, thanks to RAOF for jogging my memory with this thread [http://www.ubuntuforums.org/showthread.php?t=82154&page=3&highlight=video](http://www.ubuntuforums.org/showthread.php?t=82154&page=3&highlight=video)
while it did not directly address my issue, it got me thinking...

You need to modify your xorg.conf file using dpkg-reconfigure, I have attached my old and new xorg-conf files for reference, the old one has the extension .bak.

I think the key is in the 'module' section, where the new xorg.conf loads a lot more modules than the old, anyways that's what I did and now video works.

Thanks to everyone to helped!

---

### Post by klemens on 2005-11-11
worked great for me ty.

---

### Post by amyfan on 2007-08-04
not sure but i have had the same thing with mplayer so i will link what someone said on my post about the movies and stuff maybe this might help let me know u can email me to let me know i barly check the forums 

What to do if Video players crash while using Beryl

see bug 96226 Currently you will need to change video driver from xv to x11 in ~/.mplayer/config and gstreamer-properties
[edit]
How do I fix black windows during video playback

It is a known bug and there is a workaround by changing the video output device on your video player.

* GStreamer (The default video player in Ubuntu, totem-gstreamer, and any video player that is based on the gstreamer backend)
o Open a terminal and type "gstreamer-properties". Press Enter.
o Click the Video tab.
o Under Default Video Plugin select "X Window System (No Xv)".
o Click Test to verify that video playback is working (you should be able to see the standard TV testing colour stripes).
o Click Close

* VLC (VLC is not installed by default; you need to search in the package manager, then install)
o Start VLC and click on Settings, then Preferences.
o Expand Video and then expand Output modules. You will notice several options for output device.
o Select the item Output modules, and notice the checkbox at the bottom right that says Advanced options. Check the box, and now you have the option to select a different output device.
o Pick X11 video output
o Click on Save and you are set!

* MPlayer (Mplayer is not installed by default)
o Start Mplayer
o Right-click on the screen and select Preferences
o Select the Video tab and under Available Drivers select "X11 (XImage/Shm)"
o Click Save and restart the program for the setting to take effect.
+ Some users reported that MPlayer may not be able to show videos in full screen.

* Xine
o Start xine
o Click File, then Configure and then Preferences
o In experience_level select "Master Of The Known Universe" so that all available settings are visible.
o Select the tab for video.
o Under Driver select "xshm".
o Restart xine.
+ The same process enables Totem that has the totem-xine backend configured.

* RealPlayer
o Start RealPlayer
o Click Tools, then Preferences.
o Select the Hardware tab.
o Deselect "Use XVideo"
o Click on Apply, then OK.
o Restart RealPlayer.

Sources

---

### Post by Shmits on 2007-08-04
some one please help, i know this is in a different catagory but please, answer, when i turn on my computer and get to the logon screen and type in my username and password, it will go to a blank black screen for approx. 6 secs then go's back to the logon screen, please can anyone help

---

