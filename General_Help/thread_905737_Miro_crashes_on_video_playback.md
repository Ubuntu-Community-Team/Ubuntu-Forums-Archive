---
title: "Miro crashes on video playback"
date: 2008-08-30
forum: General Help
---

### Post by maxclimber1w on 2008-08-30
Hello! I am having a problem with the wonderful program MIRO. Whenever I attempt to play a video, the program exits promptly with no error messages, nothing at all. It downloads and browses fine, and it worked fine on my previous machine...

I am running a Dell Inspiron 530
Q6600, 4 GB ram, ATI graphics, and Compiz. When I disable compiz, the problem still occurs.

I followed the instructions here: [http://ubuntuforums.org/showthread.php?t=785961&highlight=miro+works+fine]("http://ubuntuforums.org/showthread.php?t=785961&highlight=miro+works+fine") 
but no solution. Any ideas?
thanks in advance!
Max

---

### Post by Mister.Vash on 2008-08-30
Try starting miro from the gnome-terminal and then play the video.  You should be able to see the error message in the terminal window when it crashes.

---

### Post by maxclimber1w on 2008-08-31
Hmmmm... this is the output from the terminal window.

max@dell-desktop:~$ miro

*************** INITIALIZE MOZEMBED
location: /usr/lib/xulrunner-1.9.0.1/libxpcom.so 
before 3
INFO     Starting up Miro
INFO     Version:    1.1.2
INFO     Revision:   [https://svn.participatoryculture.org/svn/dtv/tags/Miro-1.1.2/tv/resources](https://svn.participatoryculture.org/svn/dtv/tags/Miro-1.1.2/tv/resources) - 6194
INFO     Builder:    buildd@vernadsky
INFO     Build Time: 1202986841.91
INFO     Loading preferences...
INFO     Starting event loop thread
INFO     Restoring database...
INFO     Connecting to /home/max/.miro/sqlitedb
TIMING   Database load slow: 2.326
TIMING   idle (Initializing database) too slow (2.573 secs)
INFO     Spawning auto downloader...
INFO     Displaying main frame...
INFO     Creating video display...
INFO     *** Launching Downloader Daemon ****
WARNING  Menu item action "RenameVideo" not implemented
WARNING  Menu item action "FastForward" not implemented
WARNING  Menu item action "Rewind" not implemented
WARNING  Menu item action "UpVolume" not implemented
WARNING  Menu item action "DownVolume" not implemented
INFO     loaded renderer 'xinerenderer'
TIMING   gtkSyncMethod: <function getDisplay at 0x8b0387c> took too long: 1.040
INFO     First URL is [https://www.miroguide.com/](https://www.miroguide.com/)
INFO     got file:///tmp/tmpmAENo9.html
TIMING   Icon clear: 0.261
INFO     Starting movie data updates
INFO     Finished startup sequence
TIMING   idle (finalizing startup) too slow (2.395 secs)
INFO     got file:///tmp/tmpU0HvPR.html
INFO     First URL is [https://www.miroguide.com/](https://www.miroguide.com/)
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
INFO     got file:///usr/share/miro/resources/html/guide-navigation.html
INFO     First URL is [https://www.miroguide.com/](https://www.miroguide.com/)
INFO     got [https://www.miroguide.com/](https://www.miroguide.com/)
INFO     First URL is [https://www.miroguide.com/](https://www.miroguide.com/)
INFO     *** Daemon ready ***
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
TIMING   timeout (Save database) too slow (1.401 secs)
INFO     got [https://www.miroguide.com/channels/2696](https://www.miroguide.com/channels/2696)
INFO     got javascript:top.miro_navigation_frame.guideUnloaded()
INFO     got action:handleSelect?area=tablist&viewName=staticTabs&id=790&shiftDown=0&ctrlDown=0
INFO     got file:///tmp/tmpAAqM8W.html
INFO     got action:handleSelect?area=tablist&viewName=feedTabs&id=264&shiftDown=0&ctrlDown=0
INFO     got file:///tmp/tmpESACJF.html
INFO     got action:handleSelect?area=tablist&viewName=feedTabs&id=366&shiftDown=0&ctrlDown=0
INFO     got action:playViewNamed?viewName=watchableItems&firstItemId=368
INFO     Playing item with renderer: <frontend_implementation.xinerenderer.Renderer instance at 0x9c2b2cc>
Segmentation fault
max@dell-desktop:~$ WARNING  downloader: connection closed -- quitting
INFO     Shutting down downloaders...
max@dell-desktop:~$ 




Segmentation fault... seems like the same problem others are having.

---

### Post by maxclimber1w on 2008-08-31
UPDATE**

I upgraded to the latest version of Miro (1.2.7) and now video plays for 6 seconds, then crashes... no better than before.

The new output:

TIMING   dispatch action playViewNamed too slow (0.520 secs)
TIMING   idle (dispatchAction() (using asUrgent)) too slow (1.110 secs)
INFO     got file:///tmp/tmpP5BFPx.html
INFO     got action:playViewNamed?viewName=watchableItems&firstItemId=373
INFO     got file:///tmp/tmpvFofrW.html
INFO     got file:///tmp/tmpA3mClr.html

---

### Post by allspiritseve on 2008-09-01
I am getting this segmentation fault error as well. Any help would be much appreciated.

---

### Post by maxclimber1w on 2008-09-04
Any more ideas? This segmentation fault is crampin my style.

---

### Post by virogenesis1 on 2008-09-07
I am also getting this error. Miro worked really well for me in Gutsy, now it's unusable as a player.:sad:

---

### Post by pasokon on 2008-09-17
I am getting the same segmentation error. 
Someone please help us!

---

### Post by maxclimber1w on 2008-10-08
Anybody have ideas?

---

### Post by tdotthomas on 2009-03-14
2 years later and I'm getting the same problem. I looked for a way to fix this but no one has anything real to say just switch to gstreamer but they never said how to do it. I found someone giving a menu path for the old Miro (1.2) but that doesn't work for the new (2.0) player I think its the same problem because I also have an ATI card. If anyone can help with this please do because Miro looks great but it sucks because some people can't use it. I'm thinking about just building my own deb files for it.

---

### Post by hadrins on 2009-03-22
Hi,
I just installed this on my laptop. I have used it on my desktop for some time. 

I had the same problem on my laptop, I think. using Miro 1.2.6  It would crash without and error. Loaded from the command line and only noticed the segment fault. 

So poking around I found the options.  Under video options then playback I changed form Xine to gstream.   It still crashed.  I then change the audio playback.  Miro didn't crash.  So I changed the video playback to Xine. Still no crash.  

Hope this helps. 

hadrins

---

