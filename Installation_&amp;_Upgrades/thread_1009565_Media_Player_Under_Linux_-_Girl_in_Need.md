---
title: "Media Player Under Linux - Girl in Need"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by EricaMae999 on 2008-12-12
Hello Everybody,

First to introduce myself, I am a total beginner to the linux scene.  I'm am running it on my second desktop and so far I love it, even though it can be frustrating. 

Anyway... my first problem.

I like to watch movies on [http://themoviepit.org/](http://themoviepit.org/) on my windows box, but so far I haven't been able to get most of them to work under linux. Namely Veoh movies and Divx movies. Can anybody help? These are the best quality movies and I hate having to switch to windows every time I want to kick back and enjoy a movie....

Thanks!

Erica :)

---

### Post by tuxxy on 2008-12-12
Did you install the codecs needed to play the movies? it works fine here so assume you didnt.

If its a fresh ubuntu installation you will want to download the ubuntu-restricted-extras package this provides Flash, Java, Codecs etc open a terminal and enter

```
sudo apt-get install ubuntu-restricted-extras
```

Try this and see if it works, also you could install VLC a great media player that comes with codecs also.
```

sudo apt-get install vlc

```

---

### Post by arjay27529 on 2008-12-18
have attempted the commands listed above with these results:

sudo apt-get install ubuntu-restricted-extras

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras

sudo apt-get install vlc

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vlc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package vlc has no installation candidate

am a linux newbie i have no idea where to go or what to do next.

also - have had pretty much constant problems getting .wmv files to run in movie player.  during one wmv download/play was advised to install codecs which i did succesfully since wmvs worked.  but then a ubuntu upgrade was "needed" and installed and now the condecs apparently are gone.  at least they no longer work as wmvs are dead again.  attempted a download; firefox indicated it was completed; movie player launched; video blinked quickly, stopped and movieplayer closed.  firefox download showed no record of download - even though it tracked progress and said completed.

and - finally got sound to at least squeak out of the speakers, but even on full blast it is just that - a barely audible squeak.

any and all help will be greatly appreciated.

---

### Post by Trist on 2008-12-18
Hi,
Have you tried installing mplayer, mozilla-mplayer and the w32codecs.
arjay27529 by the looks of it I don't think you have all the repositories enabled.

---

### Post by Partyboi2 on 2008-12-18
> **arjay27529 said:**
> have attempted the commands listed above with these results:

sudo apt-get install ubuntu-restricted-extras

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras

sudo apt-get install vlc

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vlc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package vlc has no installation candidate

am a linux newbie i have no idea where to go or what to do next.

also - have had pretty much constant problems getting .wmv files to run in movie player.  during one wmv download/play was advised to install codecs which i did succesfully since wmvs worked.  but then a ubuntu upgrade was "needed" and installed and now the condecs apparently are gone.  at least they no longer work as wmvs are dead again.  attempted a download; firefox indicated it was completed; movie player launched; video blinked quickly, stopped and movieplayer closed.  firefox download showed no record of download - even though it tracked progress and said completed.

and - finally got sound to at least squeak out of the speakers, but even on full blast it is just that - a barely audible squeak.

any and all help will be greatly appreciated.
As mentioned by Trist it looks like you don't have the muliverse repo enabled. To do this open up Software Sources (System>Admin>Software Sources) and on the first tab make sure that you have ticked the multiverse repo box. Then close Software Sources (which will update) and try installing ubuntu-restricted-extras again

---

### Post by arjay27529 on 2008-12-20
partyboi2 & trist

many thanks for the help.  most of it worked - at least somewhat.  enabled multiverse repo.  many new items were installed and the apps available list grew.  

installed ubuntu-restricted-extras and it seemed to finish properly - no error messages.   took awhile.

installed both mplayer and mozilla mplayer successfully but attempts to install w32codecs produced this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

again have no idea what to do next - to correct this situation.

also, virtually all video file (mpg, wmv, avi, etc) types are now running (in all 4 players i have installed) but none of them show color (looks like a 1950 tv).  if it makes any difference youtube videos show full color.  sound is barely a squeak - even at full volume - for all including youtube.

thanks for your help and for any you can offer on the other issues.

---

### Post by Trist on 2008-12-20
> **arjay27529 said:**
> partyboi2 & trist

many thanks for the help.  most of it worked - at least somewhat.  enabled multiverse repo.  many new items were installed and the apps available list grew.  

installed ubuntu-restricted-extras and it seemed to finish properly - no error messages.   took awhile.

installed both mplayer and mozilla mplayer successfully but attempts to install w32codecs produced this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

again have no idea what to do next - to correct this situation.

also, virtually all video file (mpg, wmv, avi, etc) types are now running (in all 4 players i have installed) but none of them show color (looks like a 1950 tv).  if it makes any difference youtube videos show full color.  sound is barely a squeak - even at full volume - for all including youtube.

thanks for your help and for any you can offer on the other issues.

Hi,
To install the w32codecs (or the w64codecs depending on whether your using a 32bit or 64bit system) you need to add the medibuntu repositories
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
As for the b&w playback have you tried going into mplayer preferences and changing the video drivers? You'll need to exit mplayer then reopen it again every time for the changes to take effect.
Not sure about the sound problem you might wont to open the volume control go to preferences and check everything and then turn everything up.

---

### Post by infamous-online on 2008-12-20
> **Trist said:**
> Hi,
Have you tried installing mplayer, mozilla-mplayer and the w32codecs.
arjay27529 by the looks of it I don't think you have all the repositories enabled.

this is what i use as well, so mplayer is your friend!

---

### Post by arjay27529 on 2008-12-23
trist


> Hi,
To install the w32codecs (or the w64codecs depending on whether your using a 32bit or 64bit system) you need to add the medibuntu repositories
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
As for the b&w playback have you tried going into mplayer preferences and changing the video drivers? You'll need to exit mplayer then reopen it again every time for the changes to take effect.
Not sure about the sound problem you might wont to open the volume control go to preferences and check everything and then turn everything up.

did that with (seeming) success.  have not tested yet, but received no error messages.  feel stupid as some of the selections in the volume control were muted.  cant find mplayer preferences, tho it is much better than other video players.

thanks again.

---

### Post by Trist on 2008-12-24
> **arjay27529 said:**
> trist




did that with (seeming) success.  have not tested yet, but received no error messages.  feel stupid as some of the selections in the volume control were muted.  cant find mplayer preferences, tho it is much better than other video players.

thanks again.

To get into mplayer preferences open mplayer. Then right click on mplayer and it will pull up a menu with things like open file, playlist, equalizer and preferences in it. Then just click preferences and the preferences window will open.

---

