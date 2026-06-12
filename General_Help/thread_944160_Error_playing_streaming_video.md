---
title: "Error playing streaming video"
date: 2008-10-11
forum: General Help
---

### Post by DartzMan on 2008-10-11
G'day everyone... Total Noob here and I have struck a problem since I weened myself off of Windows to Ubuntu...

I am registered via subscription with a sports website ([www.planetdarts.tv](www.planetdarts.tv)) and to view live subscribed matches I have to enter my user name and password for the movie page to load up.... That all works..... The movie player says Playing ------ Connecting--------- Cache fill.. then stops...

If I go to the public viewing page where you don't have to login the movies play.. This tells me my codec is fine...

Looking at the source code of the secure page it is pointing to a WMV file which I believe then links to a MOV file...

If I copy the link directly into the address bar it opens up Totem player then says ERROR This file is encrypted and cannot be played..... I am sensing that it is some sort of error transferring the license to play issue?

I really could do with a fix as it would be wasted money on the sports site

thanks in advance.... Kevin

---

### Post by Julius1988 on 2008-10-11
try installing w32codecs
```

wget -c http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb
sudo dpkg -i w32codecs_20071007-0medibuntu2_i386.deb

```

---

### Post by DartzMan on 2008-10-11
thanks for that... Will try it now and come back to you

---

### Post by DartzMan on 2008-10-11
no luck.... same thing........

---

### Post by Julius1988 on 2008-10-11
try
```

sudo apt-get install ubuntu-restricted-extras 

```
personally i use mplayer instead of totem.

---

### Post by DartzMan on 2008-10-11
still no luck.... on the built in player on the page it says... Playing... Connecting.. Cache fill .. 0.00 then stops.

Looks like it plays the wmf loader, when it goes to the mov file it just stops

---

### Post by Julius1988 on 2008-10-11
try playing mov with the mplayer by downloading it to your system or set mplayer as the default player in your firefox.

---

### Post by DartzMan on 2008-10-11
When I managed to get the mov file and play it, all I got was colour bars and squares on the screen....

---

### Post by Julius1988 on 2008-10-11
if possible could you give the link to the video file....so that i could test it.

---

### Post by DartzMan on 2008-10-11
[http://10.2.200.143:80/pdc/videoarchive/sky_poker_worldgp_day1_071008_350k.wmv](http://10.2.200.143:80/pdc/videoarchive/sky_poker_worldgp_day1_071008_350k.wmv)

[http://video.premiumtv.co.uk/pdc/videoarchive/sky_poker_worldgp_day1_071008_350k.wmv](http://video.premiumtv.co.uk/pdc/videoarchive/sky_poker_worldgp_day1_071008_350k.wmv)

---

### Post by Julius1988 on 2008-10-11
tell me whether you could play this video or not?
```

http://rapidshare.com/files/153026149/spirit.wmv.tar.gz.html

```

---

