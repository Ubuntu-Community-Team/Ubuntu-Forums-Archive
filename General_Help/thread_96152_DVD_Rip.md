---
title: "DVD Rip"
date: 2005-11-28
forum: General Help
---

### Post by ed_d on 2005-11-28
OK, I have just done a rip of a movie, but didnt encode as didnt know had to from the start. Anyway, I can veiw the movie from my hard drive without issue, but want to burn it to a dvd. How do I go about compreeing the vob files to fit on a dvd? Its an older burner and only does single layer iirc.

---

### Post by Ufo on 2005-11-28
I have come across couple of solutions for this but have not tried any. Here are discussions of them:
[http://ubuntuforums.org/showthread.php?p=523368](http://ubuntuforums.org/showthread.php?p=523368)
[http://www.ubuntuforums.org/showthread.php?t=76245&highlight=dvd+backup](http://www.ubuntuforums.org/showthread.php?t=76245&highlight=dvd+backup)
[http://www.ubuntuforums.org/showthread.php?t=78127&highlight=dvd+backup](http://www.ubuntuforums.org/showthread.php?t=78127&highlight=dvd+backup)

They are about making copy of DVD, but I think they work also if you have your DVD already copied to hard drive.

---

### Post by Original Brownster on 2005-11-28
[QUOTE=ed_d]OK, I have just done a rip of a movie, but didnt encode as didnt know had to from the start. Anyway, I can veiw the movie from my hard drive without issue, but want to burn it to a dvd. How do I go about compreeing the vob files to fit on a dvd? Its an older burner and only does single layer iirc.[/QUOTE]

Hi,
For native tools try lxdvdrip and xdvdshrink, both work well, the latter I prefer as it just does the main movie and strips the rest.
Otherwise you could try using dvdshrink with wine, theres a decent howto floating around for this that I followed - check the ubuntu wiki.

Regards

---

### Post by xdarkness2 on 2005-12-05
[EDIT]
SORRY WRONG POST :/ its late here... 
was ment for : [http://ubuntuforums.org/showthread.php?p=547102#post547102](http://ubuntuforums.org/showthread.php?p=547102#post547102)
[/edit]

Mini howto,
Check if you have most of its dependencies right (in preferences)
you can check this again and again after installing additional tools.

Ok assuming everything is installed:

dvd rip is pritty easy, start a new project, enter its name and then your are as ready as every. You simply work your way trough each tab above.

Storage should be alright for now (default)
go to the next tab, (rip title)
enter your dvd in the dvdplayer, click on read dvd/chapter or whatever button you will find ... and ... 
select the chapters/titles you wand to rip, you can preview them with the button at the bottom, when ready select RIP chapter/title, wait and your done with that tab

next tab: clip and zoom
Here you can finetune your zooming and with the button " zoom calculator" you can finetune it to a predefined selection. Everything in RED is 1:1 ratio, the BPP and other options can be found in the manual of dvdrip, for mpeg a good BPP would be 0.2 for video, and 0.4-0.5 for dvd :) 
the other values, well i cant recall them from memory... you should figure that out for your own or leave it for now (not that important)
click OK at the zoom calculator after and your good as ready for the next tab

subtitles, wel your on your own here, its pritty mutch self explainable... you go and experiment... or skip it, if your not interested in subs

next tab transcode: this is where the you select what format your ripped files should be.. tune them as you like then hit the big transcode button...
have a nice nap and when you wake up your files will be ready :D

well thats all there is to it, just work from one tab to another... pritty easy huh!

---

### Post by Matt Houston on 2006-01-14
Hey, 

I enter the project name, leave the path as default, click the rip title and get the following error:

```

An Internal Exception was Thrown
The Error Message Was:

mkdir /home/projectname: Permissoin denied at usr/share/perl5/video/DVDRip/Project.pm line 261

```

Any ideas?

---

### Post by handy on 2006-01-14
For anyone who is running on 32bit Breezy, I highly recommend installing Wine using **Automatix**,

[http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295)

 & then use **WineTools**

[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)

 to configure Wine. (Don't install internet explorer, especially it you are going to install DVDshrink) then download & install **DVDshrink**,

[http://doc.gwos.org/index.php/DVD_Shrink_Breezy](http://doc.gwos.org/index.php/DVD_Shrink_Breezy)

 which is so simple to use & incredibly reliable.  

For easy burns, as fast as your media allows (max speed of your burner permitting) download **NeroLINUX** trial.

**[EDIT:]  Nero does multi-session too!**

[http://www.nero.com/us/NeroLINUX.html](http://www.nero.com/us/NeroLINUX.html)

If you like it $20- US.

Works for me...:D

---

### Post by BathroomNinja on 2006-01-14
The above method works great for me.  Although, I use K3b instead of Nero Linux.

---

### Post by gubemton on 2008-02-25
The "internal exception was thrown!" error seems to be caused by the way dvd:rip writes the paths to the various directories it wants to use. 

If you poke around in the dvd:rip preferences menu (edit/edit preferences), you'll see that it want to uses various directories on (for example) "ha8" for the base directory and the project files. However, the partition I'm using is "hda8", not "ha8"--hence the error message.

Renaming the hard disc name (or the partition name) in these paths should get rid of the error message. 

After you've corrected the faulty paths under the preferences menu, you'll also need to do the same thing on the "storage" tab for the directories for the project's VOB, AVI and temp files.

---

