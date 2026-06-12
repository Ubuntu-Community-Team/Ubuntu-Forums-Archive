---
title: "General rTorrent question - choosing where to save individual files"
date: 2008-09-17
forum: General Help
---

### Post by TMcKSmith on 2008-09-17
Can anyone tell me if rTorrent supports this functionality?  

Here's what I'd like to do:

When I download a .torrent file and save it into my "torrent" folder (where rTorrent picks it up from), I'd like to choose a specific folder to save the file to so I can seed the file "forever".  

For example, if I download a 100% free, legally hosted album by a band called "Torrent Jam", I'd like to save it in my very-organized music collection under the folder called "Torrent Jam".  Currently, I can only configure rTorrent to save the file into a generic "download" folder, where I eventually have to copy the file into my organized music collection.  This causes me to have doubles if I want to seed.

Thanks for the responses in advance.

---

### Post by TMcKSmith on 2008-09-17
any input would be appreciated...

---

### Post by TMcKSmith on 2008-09-17
please help...

---

### Post by asezen on 2008-09-17
Hello,

Yes it has support for that function, once you open your torrent into rtorrent you can change its download directory with ctrl+o key.

hth

---

### Post by TMcKSmith on 2008-09-17
right, I figured that out - but you have to wait until the download completes, then "close" the download, move the file from the default directory to the new [artist] directory - then change the download location and re-hash in rtorrent. 

I was content with doing that, so I changed all of my torrents to their respective new artist/download directories, but when I restarted rTorrent all of the torrents started to download to the default directory found in rtorrent.rc  ugh!!!  

this is frustrating, any other help would be appreciated

---

### Post by TMcKSmith on 2008-09-17
anyone?

---

### Post by TMcKSmith on 2008-09-18
hate to keep bumping this, but I'm convinced someone has to have some input here...

---

### Post by shaggy999 on 2008-09-18
The man pages are your friend. 'man rtorrent'

The description for the ^O command states that a torrent must be closed, not finished. Use the ^K command to close a torrent followed by ^O followed by ^S to restart the torrent.

^K = Stop and close
^O = Move
^S = Start

There ya go.

---

