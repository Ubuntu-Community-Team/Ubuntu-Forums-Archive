---
title: "Open With Question"
date: 2008-08-05
forum: General Help
---

### Post by MikeyDL on 2008-08-05
New to ubuntu but I've been learning a few tips and tricks over the last couple of days.  I decided to try and get utorrent to work with wine which I was able to do and get running.  

Then I decided to use some office 2003 wine instructions for associating filetypes with to get an openwith function in firefox for torrent files.  I created the following script:

~~~~

#!/bin/bash
COMMAND=`echo $* | sed -e s#\/#\\\\\\\#g`
if [ ${COMMAND} ]; then
COMMAND='Z:'$COMMAND
fi
wine "C:\Program Files\uTorrent\uTorrent.exe" "${COMMAND}" 

~~~~~

I saved the script as "utorrent" in my /home/user/bin directory for using.

Then when I downloaded the torrent file I choose the "Open With" function and then chose the "utorrent" script file I just created.  However it just ended up not opening utorrent and instead opening in TransBT.

Is this a "doable" thing?  Also since it's running in wine is TransBT a better client for BT downloads?

Thanks!

---

### Post by tamoneya on 2008-08-06
it really doesnt make sense to run the bittorrent client through wine.  Transmission is a well featured client and its better to have a native linux app instead of a windows one.  Dont get me wrong, if uTorrent was release for linux I would most likely use it but things are plain easier if you can run it straight out of linux.  Because of this wine has recently become reserved primarily for games and photoshop since so many windows applications have good or better linux alternatives.  If you want to try a couple more torrent clients out because transmission doesnt quite work for you take a look here:[http://www.osalt.com/](http://www.osalt.com/)

---

### Post by MikeyDL on 2008-08-06
You are correct.  I ran with the transmission app, guess it's hard to wean urself off winapps at times.  However it runs and looks a bit strange running Utorrent after working with regular linux apps.

---

