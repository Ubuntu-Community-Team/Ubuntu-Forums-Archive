---
title: "Garmin eTrex GPS on Ubuntu"
date: 2008-07-30
forum: Hardware
---

### Post by gerkin on 2008-07-30
Hi all

just an update to my previous threads on Garmin eTrex GPS:

[http://ubuntuforums.org/showthread.php?t=413438&highlight=etrex&page=2](http://ubuntuforums.org/showthread.php?t=413438&highlight=etrex&page=2)

I have been using Garmin eTrex GPS with gpsbabel very successfully with several previous versions of Ubuntu

Gpsbabel is very reliable and works great with the eTrex and Ubuntu 

I have a couple of simple bash scripts to download waypoints and tracks as .gpx files (which my mapping software prefers) 

I have attached them and would welcome any suggestions or improvements

ideally I would like to combine the options with feedback in to a single script & have it auto-detect the appropriate port etc. but my skills are not quite there yet

EG.

"what would you like to do?"

"1. to download waypoints"
"2. to download tracklogs"
"3  upload etc. etc.

Anyway I hope they will be of some help to someone.

I also have a script for converting and uploading Geocaching.com caches to the eTrex and bluetooth/USB Holux M-241 data-logger upload/download scripts & will post them here when I get them a bit more tidied up


The following scripts are well tested and commented so even a n00b should be able to follow them, but feel free to contact me or post to the list with questions or comments

cheers ........gerkin

---

### Post by sandyeggoboy on 2008-07-31
hi there, i would be very interested in whatever you have for talking to a HOLUX m-1200 -- so far i have not been able to get mone to work. i can see it when i browse devices, but can not get any data from it, and am still looking at posts on here to see how to config my bluetooth

thanks,

Deric Stowell

---

### Post by gerkin on 2008-08-02
sandyeggoboy

I might need a day or two to digest this further ...

but in the meantime here are a few links with info that might help:

[http://wiki.openstreetmap.org/index.php/GPS_Reviews](http://wiki.openstreetmap.org/index.php/GPS_Reviews)
(according to this it looks like the M-1000 uses the MTK chipset and from googling here:

[http://www.gpspassion.com/FORUMSEN/topic.asp?TOPIC_ID=96916](http://www.gpspassion.com/FORUMSEN/topic.asp?TOPIC_ID=96916) and here:

[http://www.google.co.nz/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=hHF&q=holux+m-1200&btnG=Search](http://www.google.co.nz/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=hHF&q=holux+m-1200&btnG=Search)

... it looks like the M-1200 does also (same as the M-241)

Firstly I'm using bluetooth on a EePC 900, with a Jaycar Electronics adapter:

[http://www.jaycar.co.nz/productView.asp?ID=XC4892](http://www.jaycar.co.nz/productView.asp?ID=XC4892)

I followed these instructions initially:

[http://www.rigacci.org/wiki/doku.php/doc/appunti/hardware/gps_logger_i_blue_747](http://www.rigacci.org/wiki/doku.php/doc/appunti/hardware/gps_logger_i_blue_747)

I couldn't figure these instructions out (so I'm using MTKBabel to manage the Holux):

[http://www.enricozini.org/tags/index.html](http://www.enricozini.org/tags/index.html)

Then I modified my /etc/bluetooth/rfcomm.conf similar to the post from "ymod" in this post:

[http://ubuntuforums.org/showthread.php?p=1497680](http://ubuntuforums.org/showthread.php?p=1497680)

My actual /etc/bluetooth/rfcomm.conf looks like this:

rfcomm4 {
bind yes;
device 00:1B:C1:04:83:FB;
channel 1;
#comment "Holux M-241";
}

I installed MTKBabel from the repos (I think) or just google it for the latest version 0.7

Then I turn the Holux plug in the bluetooth adapter and the icon pops up in the tray as active and I can see the Holux device.  They talk to each other automatically after about 10 seconds, but you will need system > preferences > sessions > bluetooth manager running

I use the following scripts to manage/download waypoints & tracks (they are still a bit rough but work ok):

Also heres a python script I found to manage waypoints:

[http://www.enricozini.org/2008/tips/holux-m241-waypoints.html](http://www.enricozini.org/2008/tips/holux-m241-waypoints.html)

Have a play around and let me know how you get on

cheers ......dave

---

### Post by gerkin on 2008-10-09
If anyone is interested here is the latest version of my bash script to manage the Holux M-241 datalogger/gps (MTK chipset)

I am using it on mostly on a EeePC 900 with a bluetooth adaptor but it also works fine on my desktop with USB

At the least it may provide a starting point/ideas for something better

I am keen to hear of any suggestions or improvements 

cheers .............. gerkin

---

### Post by gerkin on 2009-07-12
Hi all

This is the latest version "garmin_download_0.3.9-6.sh" of my Garmin eTrex H download bash script that will become: 0.4  

As always I hope it is of use to someone and I would welcome any feedback

cheers.......

---

### Post by gerkin on 2009-07-19
Hi all

This is the latest version "holux_download_0.3.9-4.sh" of my Holux M-241 download bash script that will become: 0.4

I would be interested to hear if it works on other MTK based datalogger or GPS devices

As always I hope it is of use to someone and I would welcome any feedback

cheers.......

---

### Post by gerkin on 2009-08-30
Hi all

the latest versions of the Garmin eTrex & Holux M-241 download scripts are available at:
[http://dl.getdropbox.com/u/1448458/gps_download.tar.gz](http://dl.getdropbox.com/u/1448458/gps_download.tar.gz)

---

### Post by 7he on 2010-02-17
Thanks a lot for this piece of software. Please post a new message if you have a new version avalaible.

regards

---

### Post by gerkin on 2011-03-04
I'm regularly updating both the Garmin & Holux scripts, and adding the latest versions to the "gps_download.tar.gz" archive listed above

Feel free to download it from time to time, for updates.

gerkin

---

