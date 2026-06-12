---
title: "Radio Playlist on Rhythmbox"
date: 2008-08-16
forum: General Help
---

### Post by colobix on 2008-08-16
HI all.

When I have added radio streams to Rhythmbox, but where can I find the playlist file with the saved links in, and whats the filename? 

Thanks :)

---

### Post by ad_267 on 2008-08-16
They are in ~/.gnome2/rhythmbox/rhythmdb.xml

That file contains all of your music library though so it's pretty huge.

You want the entries that have:
<entry type="iradio">

---

### Post by colobix on 2008-08-16
Hmm, are you sure? I can't find the file rhythmdb.xml when I search for it. Not even a Gnome2 directory in root.

---

### Post by ad_267 on 2008-08-16
You can also get the details in rhythmbox by right clicking on the radio stream and viewing the properties if that's all you want.

Yeah it should be in /home/yourname/.gnome2/rhythmbox

The .gnome2 directory is hidden as it has a "." in front so you have to select view hidden files or press Ctl+H.

---

### Post by colobix on 2008-08-16
I found it now. Thank you.
But I hoped the radio stations was in an own playlist file.

---

### Post by ad_267 on 2008-08-16
If all of the streams are http ones then you can use this to output a file just containing them.

Open a terminal (applications - accessories - terminal) and enter:
```
cd .gnome2/rhythmbox
grep "http://" rhythmdb.xml > radio_stations.txt
```

That will put them all in their own text file called radio_stations.txt.
There might be some other entries that are mms:// or something so you could append the file with:
```
grep "mms://" rhythmdb.xml >> radio_stations.txt
```
Just change the mms to the different protocols used.

---

### Post by colobix on 2008-08-16
OK cool. But is it possible to add more protocols like mms:// and rtsp:// too. How will the command look like then?

---

### Post by ad_267 on 2008-08-16
> **colobix said:**
> OK cool. But is it possible to add more protocols like mms:// and rtsp:// too. How will the command look like then?

Yeah you can use this:
```
egrep "(http://)|(mms://)|(rtsp://)" rhythmdb.xml > radio_stations.txt
```

Note the "egrep" instead of "grep".

---

### Post by colobix on 2008-08-16
Thank you so much.
It worksfine now :)

---

### Post by swoosh on 2008-08-26
> **colobix said:**
> Thank you so much.
It worksfine now :)

Hi, currently I'm not able to play rstp:// streams in my Rhythmbox.

Are you able to play it? 

Can you repeat your solution here?

Thanks.

---

### Post by nutsy.ben on 2011-01-05
Update for Ubuntu 10.10

rhythmdb.xml

is in:
/home/benoitc/.local/share/rhythmbox

---

