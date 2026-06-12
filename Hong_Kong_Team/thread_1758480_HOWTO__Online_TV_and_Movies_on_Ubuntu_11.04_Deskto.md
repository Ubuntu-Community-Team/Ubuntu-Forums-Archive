---
title: "HOWTO : Online TV and Movies on Ubuntu 11.04 Desktop"
date: 2011-05-14
forum: Hong Kong Team
---

### Post by samiux on 2011-05-14
If you want to watch online TV or movies on Ubuntu 11.04, you can use SopCast and PPStream.  The setup is quiet easy.  Just let's go and enjoy!

[The tutorial is here ...]("http://samiux.blogspot.com/2011/05/howto-sopcast-and-ppstream-on-ubuntu.html")

Samiux

---

### Post by kwanylongy on 2011-05-18
Thank you soooo much for posting this. I have tried steps 1-3 and so far it's working great!! :D

One question: Would you know a way to get totem to display channel names in Traditional Chinese? My totem currently displays the names of sopcast channels and ppstream categories in Simplified Chinese, and I would like to change that to Traditional Chinese if it is possible (and does not require too much of your effort.


Many thanks again for this brilliant HowTo post!! :P

---

### Post by samiux on 2011-05-18
> **kwanylongy said:**
> Thank you soooo much for posting this. I have tried steps 1-3 and so far it's working great!! :D

One question: Would you know a way to get totem to display channel names in Traditional Chinese? My totem currently displays the names of sopcast channels and ppstream categories in Simplified Chinese, and I would like to change that to Traditional Chinese if it is possible (and does not require too much of your effort.


Many thanks again for this brilliant HowTo post!! :P

For SopCast, just edit the following file.  However, this file may change from time to time.

```
~/.local/share/totem/plugin/sopcast/channels.xml
```

---

### Post by AlanHK on 2012-01-26
I've just installed Ubuntu 11.10  and then PPStream, using the deb on their site.
[http://dl.pps.tv/pps_linux_download.html](http://dl.pps.tv/pps_linux_download.html) 

(Reports elsewhere say the totem method doesn't work now.)

It installed with a few warnings, and sort of works, but I cannot open links in the list of available videos on the left. But if I click a link on the right hand side, amongst the info, and the video linked then does play.

I can see only the top level of categories, but if I click to open one, nothing happens.  
The search box doesn't give me any clickable links either.


I found the readme: [http://download.ppstream.com/linux/readme.txt](http://download.ppstream.com/linux/readme.txt)

which said to do this:
> sudo apt-get install libqt4-core libqt4-dbus libqt4-gui libqt4-network libqt4-webkit libqt4-xml libfuse2 mplayer
sudo dpkg -i ppstream_1.0.2-1_i386.deb 

So I tried that too, no change.
But it indicates that the problem could be related to a change in libqt

Note that I don't read Chinese, but my daughter does (who insisted I install this for her), and if I can't get this working I'll have to install Windows.....

---

