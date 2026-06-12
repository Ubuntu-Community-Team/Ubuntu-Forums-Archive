---
title: "Unable to upload photo's with Joomla backend"
date: 2008-10-15
forum: General Help
---

### Post by mariourk on 2008-10-15
When I'll try to upload a jpg-file with Joomla, I'll get an error:
```

Photo too small, please keep our photo manifest in mind!

```
I have this problem on 2 Ubuntu machines. When I use windows to upload the same file, it works ok. I also have a third Ubuntu machine that works as well. So, it seems to be a problem on the local computer. Does anyone have an idea what might cause this? :confused:

---

### Post by forger on 2008-10-15
You host joomla on ubuntu? Which version of joomla, which ubuntu release are we talking about here?
You might have to report a bug about this: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)

---

### Post by forger on 2008-10-15
Based on [this source]("http://www.reference.joomlademo.de/media/system/js/uploader.js.source.html"), I think that the problem is that it uses swf/flash movies

What version of flash are you currently using? Maybe they don't fully support flash 10 yet
Post the output of these commands in terminal:
```
uname -a
apt-cache policy flashplugin-nonfree
```

---

### Post by mariourk on 2008-10-15
The Joomla website (1.5.7) is hosted on a different server. I'm trying to upload some photo's to this website, using the media-manager of the Joomla backend. Strangely enough, this won't work when I use my Ubuntu desktop (8.04) I have another Ubuntu desktop (also 8.04) that gives the same problem. No photo will upload. A third Ubuntu desktop (also 8.04) does work, but I can't say why. A windows desktop also works. On all Desktops I tried this with the same photo. No changes where made.

As far as I can see, this problem is Ubuntu related and has nothing to do with Joomla. So I decided to post the problem here. Perhaps Ubuntu messes with the jpg format??

---

### Post by forger on 2008-10-15
post back the output of the commands in post #3 :)

---

### Post by mariourk on 2008-10-15
**uname -a**
```

Linux GBU-2008-04 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

```
**apt-cache policy flashplugin-nonfree**
```

flashplugin-nonfree:
  Geïnstalleerd: 9.0.124.0ubuntu2
  Kandidaat: 9.0.124.0ubuntu2
  Versietabel:
 *** 9.0.124.0ubuntu2 0
        500 http://nl.archive.ubuntu.com hardy/multiverse Packages
        100 /var/lib/dpkg/status

```

---

### Post by forger on 2008-10-15
here's what you can do to see if there are any problems with flash or firefox:
1) Close all your firefox windows, by going to menu File > Quit
2) Run firefox 3.0 from terminal:
```
firefox-3.0
```
3) Go to your website, try to upload a file again
4) Quit firefox, menu File > Quit
any error messages shown in terminal??

Also, check out Tools > Error Console after you're done uploading, maybe it mentions something about this upload problem.

a similar problem to a similar uploading tool (mootools):
[http://forum.mootools.net/viewtopic.php?id=2726&p=4](http://forum.mootools.net/viewtopic.php?id=2726&p=4)
> masseur: check your php, i hope you not simply copied mine! Check the onError function in FancyUpload.js.

I have no idea what's wrong though, you should file a bug report if it's reproduceable :)

---

### Post by forger on 2008-10-15
It might have to do with the flash player 9 itself:
[http://digitarald-de.disqus.com/fancyupload_swiff_meets_ajax_1_0/#comment-628460](http://digitarald-de.disqus.com/fancyupload_swiff_meets_ajax_1_0/#comment-628460)
> Seems to be a bug on Flash 9 for linux, can not handle properly flash file upload. :( 

---

### Post by mariourk on 2008-10-15
When I start Forefox with the terminal, I get no errors there. The error-console, however, gives some warnings:
```

Fout tijdens het parsen van waarde voor eigenschap 'cursor'. Declaratie genegeerd.

```
Freely translated this means:
```

Error during parsing of value for property 'cursor'. Declaration ignored.

```
This error comes from *administrator/components/com_media/assets/medialist-thumbs.css*

I will see what versions of flash are installed on the 3 Ubuntu machines. Maybe that gives a clue.

---

### Post by forger on 2008-10-15
Looks like a lot of codes don't actually work with flash uploading, e.g.
[http://demo.swfupload.org/](http://demo.swfupload.org/)

---

### Post by thndrbck on 2010-09-17
I went into Joomla configuration, system tab, and set 'enable flash uploader' to no. Problem solved.

---

