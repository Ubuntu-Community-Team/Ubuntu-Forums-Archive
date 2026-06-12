---
title: "DVD Playback"
date: 2005-10-11
forum: Hardware &amp; Laptops
---

### Post by ronmarley1 on 2005-10-11
Hi, I'm new to Ubuntu (and Linux, really) so please excuse my ignorance.  I have tried to follow the steps at the Ubuntu Wiki, with no luck.  I followed the step of adding the repositories and was successful.  I then followed the steps under the Codecs and DVD video.  When I get to the step that says, "update and install packages,"  I get the following message:
[I]"W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may want to run apt-get update to correct these problems
rgoodwin@ubuntu2112:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  w32codecs
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 13.2MB of archives.
After unpacking 31.9MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  w32codecs
Install these packages without verification [y/N]?"[/I]
 If I hit Y or N, I then get
*"E: Some packages could not be authenticated"*
gedit does not appear again, as mentioned in the instructions.  I have run apt-get update as sudo and that seems to run fine.  I then procede to the next steps, and those seem to go OK, but when I insert a DVD, it say that there are no codecs, which I'm guessing is because the step error'ed out.    Any ideas here folks?   Something to do with the "NO_PUBKEY error?" I'm not sure aht to do next.  Please remember that I'm new, so handle with kid gloves.
Thanks,
[email]rgoodwin@polaris.edu[/email]

---

### Post by Zelut on 2005-10-11
DVD playback should work by using the following:
/usr/share/doc/libdvdread3/examples/install-css.sh

As far as w32codecs is concerned they have been removed from the official repositories but you can still find them elsewhere.  From what I'm heard the marillat repositories can cause some problems.  If you can't find a copy of w32codecs via google search PM me and I'll send you a link to a copy I have.

---

### Post by ronmarley1 on 2005-10-11
[QUOTE=kuyaedz]DVD playback should work by using the following:
/usr/share/doc/libdvdread3/examples/install-css.sh

As far as w32codecs is concerned they have been removed from the official repositories but you can still find them elsewhere.  From what I'm heard the marillat repositories can cause some problems.  If you can't find a copy of w32codecs via google search PM me and I'll send you a link to a copy I have.[/QUOTE]
 Hi kuyaedz,
Thanks for the quick reply.  This is my first post, and I can't believe that I such a quick reply!  I love this community!  Anyway, i tried running the above line from a terminal window (was I supposed to do that?-like I wrote, I'm REALLY new, sorry) and I got the following [I] --12:50:32--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb)
           => `/tmp/libdvdcss.deb'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to [www.dtek.chalmers.se](www.dtek.chalmers.se)[129.16.30.198]:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 25,178 [text/plain]

100%[====================================>] 25,178        45.24K/s

12:50:33 (45.17 KB/s) - `/tmp/libdvdcss.deb' saved [25,178/25,178]

(Reading database ... 58115 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.5-1 (using /tmp/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.5-1) ...
[/I]
then nothing else.  Do I need to do something next?
Thanks again,
rg

---

### Post by ronmarley1 on 2005-10-11
Me Again,
When I insert a DVD now, Totem player seems to lock up.  Before, I got a CODEC not found error.  I've read about an MPlayer?, should I try that?
Thanks so much,
rg

---

### Post by Zelut on 2005-10-11
the command I gave you downlaoded and isntalled the DVDplayback codec.. it sounds like you might want to check out [www.ubuntuguide.org](www.ubuntuguide.org) and install the codecs and players from there.  I'm sure you'll notice a difference if you haven't already.

---

### Post by ronmarley1 on 2005-10-11
Hi again kuyaedz,
I got the DVD video to play in Totem play, just no audio, so it looks like I'm getting closer.  Thanks for the link.  Any ideas for sound?  Interestingly, I have a WMV file at my web site I use with my students, and I can play it, it plays the aduio, but not the video!  Interesting puzzle...  Tried MPlayer with no luck.
[email]rgoodwin@polaris.edu[/email]

---

### Post by Zelut on 2005-10-11
have you installed the codecs listed here?  [www.ubuntuguide.org/#codecs](www.ubuntuguide.org/#codecs)  this should be video/audio codecs for just about everything you need.  Again, if you haven't gone thru the list at that link you're probably missing a thing or two that I'm sure you'll want.

Also, I've had much better luck using xine to play my videos than anything else.  Might want to try that... totem & mplayer can be buggy in my opinion

---

### Post by ronmarley1 on 2005-10-11
[QUOTE=kuyaedz]have you installed the codecs listed here?  [www.ubuntuguide.org/#codecs](www.ubuntuguide.org/#codecs)  this should be video/audio codecs for just about everything you need.  Again, if you haven't gone thru the list at that link you're probably missing a thing or two that I'm sure you'll want.

Also, I've had much better luck using xine to play my videos than anything else.  Might want to try that... totem & mplayer can be buggy in my opinion[/QUOTE]

kuyaedz,
Whoo Hoo!  Looks like we got it running!  I saw a bit of information at another site that mentioned switching from totem-gstremer to totem-xine.  Did that and now I get audio and video!  But not for all DVDs.  I'll keep playing.  I did go and try the scripts at [www.ubuntuguide.org/#codecs](www.ubuntuguide.org/#codecs) and this is the output I get: [I]root@ubuntu2112:/home/rgoodwin # sudo apt-get install gstreamer0.8-plugins
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-artsd gstreamer0.8-caca
  gstreamer0.8-festival gstreamer0.8-jack gstreamer0.8-mad gstreamer0.8-mikmod
  gstreamer0.8-mpeg2dec gstreamer0.8-sid gstreamer0.8-swfdec jackd
  liba52-0.7.4 libid3tag0 libjack0.80.0-0 libmad0 libmikmod2 libmpeg2-4
  libsidplay1-c102 libsndfile1 libswfdec0.3
Suggested packages:
  qjackctl jack-tools meterbridge libjackasyn0 sidplay-base xsidplay
The following NEW packages will be installed:
  gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-artsd gstreamer0.8-caca
  gstreamer0.8-festival gstreamer0.8-jack gstreamer0.8-mad gstreamer0.8-mikmod
  gstreamer0.8-mpeg2dec gstreamer0.8-plugins gstreamer0.8-sid
  gstreamer0.8-swfdec jackd liba52-0.7.4 libid3tag0 libjack0.80.0-0 libmad0
  libmikmod2 libmpeg2-4 libsidplay1-c102 libsndfile1 libswfdec0.3
0 upgraded, 22 newly installed, 0 to remove and 0 not upgraded.
Need to get 1174kB of archives.
After unpacking 3486kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
root@ubuntu2112:/home/rgoodwin #
[/I]
Even if I type Y it still aborts...
I'm gonna try the other lines and see.  Thanks for the help.  I need to go home from school now (I teach) or my wife will kill me!

---

### Post by Zelut on 2005-10-11
Yeah, try those one at a time & you'll be fine.  I can tell you now that you'll run into a 'package not found' at the w32codecs but if you already watch wmv then you're probably fine.  If you'd still like a copy however I can send you the package I have.

That whole site is full of cool tips & tricks, tweaks, updates & plugins.  A Ubuntu box is never done until you've gone thru that :)

Let me know if you need anything else... my wife wants to kill me for spending so much time on this forum too but she also likes that I'm so passionate about something :)

---

### Post by ronmarley1 on 2005-10-11
[QUOTE=kuyaedz]Yeah, try those one at a time & you'll be fine.  I can tell you now that you'll run into a 'package not found' at the w32codecs but if you already watch wmv then you're probably fine.  If you'd still like a copy however I can send you the package I have.

That whole site is full of cool tips & tricks, tweaks, updates & plugins.  A Ubuntu box is never done until you've gone thru that :)

Let me know if you need anything else... my wife wants to kill me for spending so much time on this forum too but she also likes that I'm so passionate about something :)[/QUOTE]
Hey Again,
Thanks so much.  I decided to blow away the install and reload Ubuntu.  Everything is working fine with DVDs, but still having trouble with .wmv files.  Microsoft crap...  Maybe send me the w32codecs?  I'm gonna try the scripts from the site again and see what happens now with a fresh install.  I'll let you know what happens...
[email]rgoodwin@polaris.edu[/email]

---

### Post by Zelut on 2005-10-11
Fresh install is definitely nice from time to time.  I hope you went with Breezy :)  I'll send a link for the w32codecs to the email you posted above.  You should go thru the [www.ubuntuguide.org](www.ubuntuguide.org) and get all of those codecs and plugins too though definitely.

---

### Post by ronmarley1 on 2005-10-11
Oy,
Still no luck.  I'm gonna google for the w32codecs.  Since it's a Microsoft file (wmv), i'm guessing it's the problem
rg

---

### Post by ronmarley1 on 2005-10-12
Back again,
Fresh install seems to have cleared up some issues.  I went with Hoary again, as that is what was given to me at a free conference (Ohio LinuxFest).  My colleague is playing with Kubuntu, and since we work at a school, we will probably look at Edubuntu for obvious cost reasons (OS plus OpenOffice fits our budget!)  I got the e-mail for the codecs.  Thanks a lot!  In a side note, the WMV i'm trying to play is from an app. called Camtasia.  It allows for audio and video screen captures.  It's a great tool for teachers that need to demo. how to do something on a PC.  One of my class sites is [http://seniorenglish.rwlo.org](http://seniorenglish.rwlo.org).  In the middle of the page is the link to the video that is a tour of my course site.  That's the file causing the struggle.  Maybe there is not Linux codec for it...  
I'll run the codecs you sent and see what happens.  By the way, you've taught me more about Linux via this forum that I knew before!
Thanks,
rg

---

