---
title: "How install Ekiga 3.0.1 on Ubuntu 8.10?"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by ice-boy on 2008-12-19
In order install Ekiga 3.0.1 at first we must install libopal3.4.2 and libpt2.4.2.
This libraries we can get from [http://packages.ubuntu.com](http://packages.ubuntu.com).
All this packages are for ubuntu 9.04 and all this we can download and install on ubutnu 8.10. Only we can not install libpt2.4.2-plugins-alsa, because this package is depends from "libasound2 ( >> 1.0.18 )" but ubunut 8.10 has "libasound2 ( 1.0.17 )"...

In control file of libpt2.4.2-plugins-alsa package i was replace "libasound2 ( >> 1.0.18 )" with "libasound2 ( >> 1.0.17 )" and then install modified libpt2.4.2-plugins-alsa package and all others - after that I ascertained that all work fine...

I was wrote the [script]("http://ubuntuforums.org/attachment.php?attachmentid=102753&stc=1&d=1234198956") which download depends packages and then install. This script also configure libpt2.4.2-plugins-alsa package and then install that.

[LIST=1]
[*]Download [_*script*_]("http://ubuntuforums.org/attachment.php?attachmentid=102753&stc=1&d=1234198956") to home directory and open terminal...
[*]```
chmod 755 install-ekiga.sh
```
[*]```
sudo ./install-ekiga.sh
```
[/LIST]
I hope these help someone :)


I am sorry my english is not so good

***

Hi!
**Since ~09.03.2009 "install-ekiga.sh" don't work properly** becouse released the new version of the ekiga_3.0.1-1ubuntu package

In order install Ekiga 3.0.1:
1) download ekiga_3.0.1-1ubuntu1_i386.deb to home directory (You can find it [here]("http://www.adrive.com/public/7f596d4c66f23817bea6585c90f33a7820a07edc9abd8d87374a523827662d6d.html")  or somewhere else) and open terminal...
	```
cp ~/ekiga_3.0.1-1ubuntu1_i386.deb /tmp
```
	
2) Download [script]("http://ubuntuforums.org/attachment.php?attachmentid=102753&d=1234198860") to home directory and delete line 36 ([ -f "$ekiga" ] && sudo rm $ekiga) and save
	```
chmod 755 ~/install-ekiga.sh
```
3) 
	```
sudo ~/install-ekiga.sh
```

or try [new script]("http://ubuntuforums.org/attachment.php?attachmentid=106532&stc=1&d=1237153018")

Download [new script]("http://ubuntuforums.org/attachment.php?attachmentid=106532&d=1237153016") to home directory and open terminal...
```
chmod 755 ~/new_install-ekiga.sh; sudo ~/new_install-ekiga.sh
```

this [new script]("http://ubuntuforums.org/attachment.php?attachmentid=106532&stc=1&d=1237153018") do all that previous and  it replace in control file of ekiga_3.0.1-1ubuntu2_i386.deb:
1)libdbus-glib-1-2 (>= 0.78) with libdbus-glib-1-2 (>= 0.76),
2)libebook1.2-9 (>= 2.25.92) with libebook1.2-9 (>= 2.24.3),
3)libedataserver1.2-11 (>= 2.25.92) with libedataserver1.2-11 (>= 2.21.1),
4)libgtk2.0-0 (>= 2.15.0) with libgtk2.0-0 (>= 2.14.4)


***

Hi!
[COLOR="Red"]**Since ~04.2009 "install-ekiga.sh" and "new_install-ekiga.sh" don't work**[/COLOR] becouse released the new version of the "ekiga_3", "libpt2" and "libopal3" packages...


Regards,
Pavels

---

### Post by janboon438 on 2008-12-25
Hi Ice-boy,
Thanks for the install script. Have you plans to include h264? Maybe you can give me some instructions to install libopal-plugins-h264.
Regards Jan.

---

### Post by meho_r on 2008-12-25
Any advantage over installing from Yannick's [repo]("https://launchpad.net/~sevmek/+archive") or Troels' [repo]("https://launchpad.net/~tlbdk/+archive")? I found that my webcam doesn't work with Ekiga 3 (although it worked with v2).

---

### Post by ice-boy on 2008-12-26
Hi Jan,
To install h264 for Ekiga 3.0.1 on ubuntu 8.10 you must make real the following files:

/usr/lib/libx264.so.<xx>
/usr/lib/opal-3.4.2/codecs/video/h264_video_pwplugin.so
/usr/lib/opal-3.4.2/codecs/video/h264_video_pwplugin_helper



1) libx264.so.64
Thank meho_r, go to [https://launchpad.net/~tlbdk/+archive](https://launchpad.net/~tlbdk/+archive)
Downlaod libx264-64_0.svn20080917-1~ppa0_i386.deb and install


2) h264_video_pwplugin.so and h264_video_pwplugin_helper
Go to [https://launchpad.net/~tlbdk/+archive](https://launchpad.net/~tlbdk/+archive)
Download libopal-plugins-h264_3.4.2-0ubuntu2_i386.deb to home directory
Open termianl
```
cd
mkdir libopal-plugins-h264_3.4.2-0ubuntu2_i386_c
mkdir libopal-plugins-h264_3.4.2-0ubuntu2_i386_c/DEBIAN
dpkg-deb -e ./libopal-plugins-h264_3.4.2-0ubuntu2_i386.deb ./libopal-plugins-h264_3.4.2-0ubuntu2_i386_c/DEBIAN
dpkg-deb -x ./libopal-plugins-h264_3.4.2-0ubuntu2_i386.deb ./libopal-plugins-h264_3.4.2-0ubuntu2_i386_c

gedit ./libopal-plugins-h264_3.4.2-0ubuntu2_i386_c/DEBIAN/control

```
Replace "libopal (= 3.4.2-0ubuntu2)" with "libopal3.4.2" and save...
```

sudo dpkg-deb --build libopal-plugins-h264_3.4.2-0ubuntu2_i386_c
sudo apt-get install libc6 libgcc1 libstdc++6 libx264-64 libopal3.4.2 libavcodec51 libx264-59 libx264-dev
sudo dpkg -i libopal-plugins-h264_3.4.2-0ubuntu2_i386_c.deb
sudo rm libopal-plugins-h264_3.4.2-0ubuntu2_i386_c.deb
```


_I don't have webcam..._



I'm sorry for my English

Regards,
Pavels

---

### Post by janboon438 on 2008-12-28
Hi Iceboy,
Have now h264 available on my Asus EeePC Intrepid with integrated webcam. Did some echo tests on Ekiga.net, but that was a little bit too much for this machine. Did not crash however :-).
Will keep you posted if it will be of any any value to me. Not many video-phones support h261. All are going to h263/h264. Ordered myself a Grandstream and hope to do some internal tests soon.
Thanks and regards Jan.

---

### Post by bojo42 on 2009-01-14
Hello there,

i opened a bugreport that aims for packages of those non free codecs in multiverse. As x264 is also there, this should atleast be no problem (beside the packing work) for ekiga's h264 plugin.

So anyone with a few packing skills is really welcome there :) [https://bugs.launchpad.net/ubuntu/+source/opal/+bug/316971](https://bugs.launchpad.net/ubuntu/+source/opal/+bug/316971)

---

### Post by elprez on 2009-01-17
Thanks Ice-boy,

Your install script works fine. 

Does any of you have try to connect to the french provider freephonie ... seems to be still buggy :-(

Regards Vincent.

---

### Post by sgarib on 2009-02-08
Hello Ice Man,

I get a lot of 404 errors:

error: Can't find libpt2.4.2_2.4.2-2_i386.deb
libopal3.4.2_3.4.2~dfsg-2_i386.deb ...OK
error: Can't find libpt2.4.2-plugins-oss_2.4.2-2_i386.deb
error: Can't find libpt2.4.2-plugins-dc_2.4.2-2_i386.deb
error: Can't find libpt2.4.2-plugins-v4l2_2.4.2-2_i386.deb
error: Can't find libpt2.4.2-plugins-v4l_2.4.2-2_i386.deb
error: Can't find libpt2.4.2-plugins-avc_2.4.2-2_i386.deb
error: Can't find libpt2.4.2-plugins-alsa_2.4.2-2_i386.deb
ekiga_3.0.1-1ubuntu1_i386.deb ...OK

Altough it is able to download some files... am I doing something wrong?

Thanks a lot for these script!

---

### Post by ice-boy on 2009-02-09
Hello Sgarib,
Thank for post.

This error occurred because released the new version of the libpt2.4.2 package...
	
Try the new [script]("http://ubuntuforums.org/attachment.php?attachmentid=102752&stc=1&d=1234197838")

Regards,
Pavels

---

### Post by helpdeskdan on 2009-02-18
3.0.2 is out

---

### Post by crjackson on 2009-02-23
> **helpdeskdan said:**
> 3.0.2 is out

I wish someone could just make a deb file for ignorant people like me. ;)

I would love to see a Hardy build and an Intrepid build. An apt repo would be the bomb...

---

### Post by crjackson on 2009-02-28
Thanks ice-boy,

I just ran your script and NOW I finally have Ekiga with working sound. The default install from the Ubuntu Repositories wouldn't record sound on my end. I could always here the other party but they couldn't ever hear me.

Your script fixed it. Now running 3.01 and planning to test it with distant relatives this weekend.

btw, what does 3.02 offer that 3.01 doesn't?

---

### Post by mtopro on 2009-03-14
Didn't work for me.  Not quite sure why. Seems most of it installed ok.  Here is where it fails.  I am running 64bit, don't know if that is the difference.

```
--2009-03-14 19:41:42--  http://fr.archive.ubuntu.com/ubuntu/pool/main/e/ekiga/ekiga_3.0.1-1ubuntu1_i386.deb
Resolving fr.archive.ubuntu.com... 88.191.250.131
Connecting to fr.archive.ubuntu.com|88.191.250.131|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-03-14 19:41:43 ERROR 404: Not Found.

libpt2.4.2_2.4.2-2ubuntu1_i386.deb ...OK
libopal3.4.2_3.4.2~dfsg-2_i386.deb ...OK
libpt2.4.2-plugins-oss_2.4.2-2ubuntu1_i386.deb ...OK
libpt2.4.2-plugins-dc_2.4.2-2ubuntu1_i386.deb ...OK
libpt2.4.2-plugins-v4l2_2.4.2-2ubuntu1_i386.deb ...OK
libpt2.4.2-plugins-v4l_2.4.2-2ubuntu1_i386.deb ...OK
libpt2.4.2-plugins-avc_2.4.2-2ubuntu1_i386.deb ...OK
libpt2.4.2-plugins-alsa_2.4.2-2ubuntu1_i386.deb ...OK
error: Can't find ekiga_3.0.1-1ubuntu1_i386.deb

Occurred some error, try change downloads server... 
This error could occur if released new version of some package or occurred downloads server error

```

Any ideas?

---

### Post by ice-boy on 2009-03-15
Hello Mtopro,
Thank for post.

This error occurred because released the new version of the ekiga_3.0.1-1ubuntu package...
In order install Ekiga 3.0.1:
1) download ekiga_3.0.1-1ubuntu1_i386.deb to home directory (You can find it [here]("http://www.adrive.com/public/7f596d4c66f23817bea6585c90f33a7820a07edc9abd8d87374a523827662d6d.html")  or somewhere else) and open terminal...
	```
cp ~/ekiga_3.0.1-1ubuntu1_i386.deb /tmp
```
	
2) Download [script]("http://ubuntuforums.org/attachment.php?attachmentid=106537&stc=1&d=1237155837") to home directory and delete line 36 ([ -f "$ekiga" ] && sudo rm $ekiga) and save
	```
chmod 755 ~/install-ekiga.sh
```
3) 
	```
sudo ~/install-ekiga.sh
```

**or** try [new script]("http://ubuntuforums.org/attachment.php?attachmentid=106538&stc=1&d=1237155837")

Download [new script]("http://ubuntuforums.org/attachment.php?attachmentid=106538&stc=1&d=1237155837") to home directory and open terminal...
```
chmod 755 ~/new_install-ekiga.sh; sudo ~/new_install-ekiga.sh
```

this [new script]("http://ubuntuforums.org/attachment.php?attachmentid=106538&stc=1&d=1237155837") do all that previous and  it replace in control file of ekiga_3.0.1-1ubuntu2_i386.deb:
1)libdbus-glib-1-2 (>= 0.78) with libdbus-glib-1-2 (>= 0.76),
2)libebook1.2-9 (>= 2.25.92) with libebook1.2-9 (>= 2.24.3),
3)libedataserver1.2-11 (>= 2.25.92) with libedataserver1.2-11 (>= 2.21.1),
4)libgtk2.0-0 (>= 2.15.0) with libgtk2.0-0 (>= 2.14.4)

Regards,
Pavels

---

### Post by mtopro on 2009-04-07
Thank you ice-boy for all the effort and very thorough instruction.  I finally got around to trying to make it work, but now it fails for another reason.  I traced down the files trying to install, and it seems there is also a new version now for all of the plugins. 
Every file that that the script tried to download issued a 404 file not found error.  Seems it is these are up to v2.6 now and whereas the script calls for 2.4.

---

### Post by ice-boy on 2009-04-11
Hello Mtopro,
Thank for post.


In order install Ekiga 3.0.1 at first download [libpt2.4.2_2.4.2-2_i386.deb]("http://www.adrive.com/public/7ccb58bf91652e3ba76bb21427908acc5bab38421e92e7e18087916dbcd1816a.html"), [libopal3.4.2_3.4.2~dfsg-2_i386.deb]("http://www.adrive.com/public/d4f24c4638e024562981bcc817e815c8139483987c37d74a366c48a9c42a646b.html"), [libpt2.4.2-plugins-oss_2.4.2-2_i386.deb]("http://www.adrive.com/public/dee11e6b5d013eaff49561e600313b6562ed688d8b0bb93e56afc83f378c6c1b.html"), [libpt2.4.2-plugins-dc_2.4.2-2_i386.deb]("http://www.adrive.com/public/267be5e4d0b867a4a4ae59a2b5d3eaf9e55890d55a3862ab24be1252642656a4.html"), [libpt2.4.2-plugins-v4l2_2.4.2-2_i386.deb]("http://www.adrive.com/public/f62d22e998e8fc46008a6d0e40c370122cdc56e6891596d5b2eb7ece983ec065.html"), [libpt2.4.2-plugins-alsa_2.4.2-2_i386-ubuntu8.10.deb]("http://ubuntuforums.org/attachment.php?attachmentid=109485&stc=1&d=1239466912") and [ekiga_3.0.1-1ubuntu1_i386.deb]("http://www.adrive.com/public/a61d071dba23058abe0a12bd9e1842f66d4e24bb0a1d046112df0d0eeb8e5dbd.html") to home directory... (These downloads will expired after 14 days)


And open terminal...
```
sudo gdebi ~/libpt2.4.2_2.4.2-2_i386.deb
sudo gdebi ~/libopal3.4.2_3.4.2~dfsg-2_i386.deb
sudo gdebi ~/libpt2.4.2-plugins-oss_2.4.2-2_i386.deb
sudo gdebi ~/libpt2.4.2-plugins-dc_2.4.2-2_i386.deb
sudo gdebi ~/libpt2.4.2-plugins-v4l2_2.4.2-2_i386.deb
sudo gdebi ~/libpt2.4.2-plugins-alsa_2.4.2-2_i386-ubuntu8.10.deb
sudo gdebi ~/ekiga_3.0.1-1ubuntu1_i386.deb
```

Regards,
Pavels

---

