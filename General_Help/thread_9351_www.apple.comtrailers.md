---
title: "www.apple.com/trailers"
date: 2004-12-27
forum: General Help
---

### Post by wazoo on 2004-12-27
This seems to be one of the big tests of a distribution: can it play, or be made to player, a Quicktime codecs?

I can't figure it out. Try the above URL: [http://www.apple.com/trailers](http://www.apple.com/trailers)

If you can get it to work, please post it here. I tried to follow the excellent Ubuntu Multimedia HOWTO, but get stuck on the first wget command to wget Mplayer. It just hung there.

When I try apt-get install mplayer-386 or 586, it tells me that I have dependencies that are more advanced than what the package it looking for.

Advice eagerly welcomed.

---

### Post by Zundfolge on 2004-12-27
read this
[http://www.ubuntuforums.org/showthread.php?t=94](http://www.ubuntuforums.org/showthread.php?t=94)

that got it working for me

---

### Post by wazoo on 2004-12-28
Great tip. Yes, that got mplayer loaded. A wonderfully written, and clear tutorial. (One correction, though: the wget command hung on me. So I just downloaded the same files from the mplayer.site.) 

But I'd already gone through the ubuntu guide, and set up firefox for totem. Interestingly, the mplayer load seems to give me an excellent picture for totem now. But it has no sound.

So I guess I have two questions now:

* how do I replace totem with mplayer in firefox? or alternatively
* how do I get sound working with totem?

---

### Post by Rancoras on 2004-12-28
[QUOTE=wazoo]* how do I replace totem with mplayer in firefox? or alternatively[/QUOTE]

I think further down in that same howto post, there are instructions on how to install the mplayer plugin.

[QUOTE=wazoo]* how do I get sound working with totem?[/QUOTE]

With mplayer working, why do you need totem?

---

### Post by piedamaro on 2004-12-28
Because mplayer stinks :D

---

### Post by Ste on 2004-12-28
[QUOTE=Rancoras]With mplayer working, why do you need totem?[/QUOTE]

Because Linux is about choice. ;)

---

### Post by poptones on 2004-12-28
*But I'd already gone through the ubuntu guide, and set up firefox for totem. Interestingly, the mplayer load seems to give me an excellent picture for totem now. But it has no sound.*

Try this:

sudo vi /etc/mplayer/mplayer.conf

when it appears change the sound entry from "alsa" (alsa-something, don't recall now) to "esd" making sure to leave any trailing apostrophes or commas. You might also change the video from X11 to sdl while you're here.

Hit esc and :w to save, then :q to leave. Reopen your browser and go back to apple.

---

### Post by wazoo on 2004-12-28
Well, I'm still baffled. I successfully installed mplayer, and if I SAVE a file, I can play it with /usr/local/bin/gmplayer. When I look in my /etc/mozpluggerrc file, I see (among other media types):

video/mpeg: mpeg, mpg, mpe: MPEG animation
video/x-mpeg: mpeg, mpg, mpe: MPEG animation
video/x-mpeg2: mpv2, mp2ve: MPEG2 animation
	stream noisy ignore_errors: mplayer -really-quiet -nojoystick -nofs -wid $window -vo xv,x11 -ao esd,alsa9,oss,arts,null -zoom -osdlevel 0 -vc mpeg12 "$file" </dev/null
        nokill noisy: xine -pq "$file"
	loop: mtvp -l -W$window "$file"
	: mtvp -W$window "$file"
	loop: xanim +Av100 -Zr +W$window +q +f "$file"
	: xanim +Av100 -Zr +W$window +q +Ze +f "$file"

I even instructed firefox to open a file one time with gmplayer, which worked beautifully. But since then, no luck at all -- not at Apple, not at Yahoo trailers. So clearly I've done SOMETHING wrong.

All tips appreciated.

Incidentally, even though I installed mplayer, I have no plugin files.

---

### Post by wazoo on 2004-12-28
poptones, my installation doesn't HAVE a /etc/mplayer.conf entry. Is that something that the mplayer install should have created?

I admit that I've been mucking about with another problem (how to recursively delete backup files), so it's possible I had it and blew it away. But right now:

* gmplayer loads.
* my codec and mplayer files and libraries appear to be there
* the mozpluggerrc file looks good

Yet when I seek to load a trailer file, I get an endless loop of waiting -- no error messages, no failure, just a long state of being hung.

---

### Post by balajij on 2005-01-10
[QUOTE=wazoo]This seems to be one of the big tests of a distribution: can it play, or be made to player, a Quicktime codecs?

I can't figure it out. Try the above URL: [http://www.apple.com/trailers](http://www.apple.com/trailers)

If you can get it to work, please post it here. I tried to follow the excellent Ubuntu Multimedia HOWTO, but get stuck on the first wget command to wget Mplayer. It just hung there.

When I try apt-get install mplayer-386 or 586, it tells me that I have dependencies that are more advanced than what the package it looking for.

Advice eagerly welcomed.[/QUOTE]
 I have xine & gxine plugin installed.. The gxine plugin seemed to crash the browser everytime I tried accessing the trailers @ apple.. 

I then installed the mozplugger plugin and this makes gxine come up as a seperate window.. However with this, my browser no longer crashes and I'm able to view a few of the apple trailers  like "The Weather Man, The ring 2" etc.. It however does not seem to be able to play other trailers like "The Aviator, Finding Neverland" etc since it complains about missing codec.. I have installed the "w32codecs".. I would still have liked to play the trailers within the same browser window itself.. This is however a minor inconvenience..

What other codecs do I need to install to be able to play all of the trailers on apple webpages?

---

### Post by wallijonn on 2005-01-10
If you install mozilla-vlc, then also install mozplugger.
Edit -> Preferences -> Downloads -> Plugins 
They should now be listed and enabled.

---

### Post by macewan on 2005-01-26
[QUOTE=wazoo]This seems to be one of the big tests of a distribution: can it play, or be made to player, a Quicktime codecs?

I can't figure it out. Try the above URL: [http://www.apple.com/trailers](http://www.apple.com/trailers)

If you can get it to work, please post it here. I tried to follow the excellent Ubuntu Multimedia HOWTO, but get stuck on the first wget command to wget Mplayer. It just hung there.

When I try apt-get install mplayer-386 or 586, it tells me that I have dependencies that are more advanced than what the package it looking for.

Advice eagerly welcomed.[/QUOTE]


I got it to work with mplayer and mplayerplug-in
[http://www.macewan.org/screenshots/FantasticFour.jpg](http://www.macewan.org/screenshots/FantasticFour.jpg)

Even the microsoft video clips on news.com work

---

### Post by Quest-Master on 2005-01-26
Simply install the mplayer-plugin from SourceForge and you can have MP3s, movies (Apple trailers as well ;)) and a ton of more streaming media. :)

---

### Post by Yukonjack on 2005-01-26
Also works great for me, I use the install script posted here 
[How To mplayer](http://www.ubuntuforums.org/showthread.php?t=9850) 

Everything works on apple/trailers

---

### Post by tanari on 2005-01-27
I have installed mplayerplug-in, now I can watch movies on apple.com, but I don't hear any sound :(
I have all codecs for mplayer.
What is the problem?

---

### Post by rapala61 on 2005-02-02
[QUOTE=Yukonjack]Also works great for me, I use the install script posted here 
[How To mplayer](http://www.ubuntuforums.org/showthread.php?t=9850) 

Everything works on apple/trailers[/QUOTE]

tried that.. and no luck.. i mean, i have it installed but no plugin at all... i have muzplugger but i cant play  trailers or anything at all... this is the only thing that really sucks about media support and websites in linux.. IMO

---

### Post by ctt1wbw on 2005-02-02
[QUOTE=rapala61]tried that.. and no luck.. i mean, i have it installed but no plugin at all... i have muzplugger but i cant play  trailers or anything at all... this is the only thing that really sucks about media support and websites in linux.. IMO[/QUOTE]


It doesn't suck just because you can't get it working the first time, or even the second time.  It took me over a week to figure out what was wrong with my installation of MPlayer.  I needed the file alsa-oss and now it works.  Took me over a week to figure that out.  And that was in my SECOND week of using Linux ever in my life.  

Just keep trying to figure it out.  The reward is greater that way instead of the other way involving Microsoft Windows. :)

---

### Post by rapala61 on 2005-02-02
[QUOTE=ctt1wbw]It doesn't suck just because you can't get it working the first time, or even the second time.  It took me over a week to figure out what was wrong with my installation of MPlayer.  I needed the file alsa-oss and now it works.  Took me over a week to figure that out.  And that was in my SECOND week of using Linux ever in my life.  

Just keep trying to figure it out.  The reward is greater that way instead of the other way involving Microsoft Windows. :)[/QUOTE]


Yeah ur right... im aware of that , its not that it bothers me to play with it and find a solution , cuz believe me, this las week has been the hardest to me regarding linux, cuz i decided to completely switch from windows but i have learn way much about linux than on my other tries  during this year... 

it fun tho , i think  that if it worked  i would have trashed it just to compile it again... just this past 4 days i've installed debian/arch/ubuntu on my my PC .. more than twice each.. lol

---

### Post by ctt1wbw on 2005-02-03
I started out trying FC3 on my laptop but it wouldn't work.  I tried and tried.  I got Mandrake 10.1, but couldn't figure out how to get the wireless working.  Ubuntu pretty much worked from the start.  Great distro.

---

