---
title: "what is the best codeck for rm &amp; rvmb extenstions pls"
date: 2008-08-08
forum: General Help
---

### Post by birlindo on 2008-08-08
[SIZE="5"]what is the best codeck for rm & rvmb extenstions & other like flv etc.... bec i cant run alot of movies by the extinsion :(

thanks ...[/SIZE]

---

### Post by northern lights on 2008-08-08
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by birlindo on 2008-08-08
thanks ... but what is the restrectied formats :confused: sorry iam new in linux all :( thanks

---

### Post by nazish on 2008-08-08
gstreamer should run most of your video files.

But VLC is the best video player for me personally. It plays rm too. VLC is available in synaptic or ADD Programs.

---

### Post by northern lights on 2008-08-08
[quote=from the "Restricted Formats" wiki page]Ubuntu strives to make all software that meets the licensing terms in the Ubuntu License Policy available. However patent and copyright restrictions complicate free operating systems distributing software to support proprietary formats.

Ubuntu's commitment to only include completely free software by default means that proprietary media formats are not configured 'out of the box'.[/quote]

Ubuntu supports free open source codecs, such as Ogg, out of the box. Media formats that are restricted by patent/copyright laws cannot be included in Ubuntu by default. These include:

rm / Real Media - license holder: RealNetworks, Inc
wma/wmv / Windows Media - license holder: Microsoft corp.
mp3 - license holder: Frauenhofer Institute, Germany

All of the above can be activated. The link I gave you provides detailed information on how to do it.

RealNetworks offers a standalone player for Linux also, check [here]("http://www.real.com/linux/?pageid=linuxHomePage&pageregion=footer&src=realhome_linux_bb_0_1_1_0_0_3_0&pcode=rn&opage=realhome_linux_bb")

---

### Post by birlindo on 2008-08-08
thanks every body for this help ...

---

### Post by damoxc on 2008-08-08
[http://www.medibuntu.org](http://www.medibuntu.org)

Their repository includes the w32codecs, which includes a codec that can be used by gstreamer for playing rmvbs, it's not 100% reliable unfortunately but it does work to an extent.

---

### Post by peakshysteria on 2008-08-08
**[VLC]("http://www.videolan.org/vlc/")** and/or **[Mplayer]("http://www.mplayerhq.hu/design7/news.html")** should take care of those. You can find them and install them via synaptic. More info on players and supported media on [**Wikipedia**]("http://en.wikipedia.org/wiki/Comparison_of_media_players#Video_format_support").

---

