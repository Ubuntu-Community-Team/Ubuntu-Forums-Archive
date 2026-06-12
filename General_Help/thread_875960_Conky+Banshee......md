---
title: "Conky+Banshee....."
date: 2008-07-31
forum: General Help
---

### Post by armageddon08 on 2008-07-31
How do I make Conky show "Now Playing" information with progress-bar using banshee?

---

### Post by tuxxy on 2008-07-31
Cool idea, I may be tempted by it also :)

EDIT: Not looking gode for banshee though, [http://ubuntuforums.org/showthread.php?t=751802](http://ubuntuforums.org/showthread.php?t=751802)

---

### Post by armageddon08 on 2008-07-31
> **tuxxy said:**
> Cool idea, I may be tempted by it also :)

EDIT: Not looking gode for banshee though, [http://ubuntuforums.org/showthread.php?t=751802](http://ubuntuforums.org/showthread.php?t=751802)

Can be better if the code becomes player-independent.......something like the 'Now Playing' screenlet.

---

### Post by armageddon08 on 2008-08-01
okay......I got Conky to show the song info playing in banshee.
But i can't get the progress-bar.

---

### Post by SomeGuyDude on 2008-08-11
How'd you manage that? Even without the progress bar, that's something. I love banshee, but I'm a conky addict and without my music info onscreen I feel incomplete.

---

### Post by tuxxy on 2008-08-11
If you cant wait im sure there is a **now playing** screenlet installed by default, its just not the same as in conky though :(

---

### Post by foppeh on 2008-11-06
It all seems possible just nobody seems to have done it.
(I'm just starting with Conky so don't blame me ;) )
From the thread mentioned you query banshee to get the information. This is Conky code that goed after the TEXT entry:
```
${color #5c1f1f}Banshee${hr 2}${color #b23d3d}
${exec banshee-1 --query-artist}
${exec banshee-1 --query-title}
${exec banshee-1 --query-track-number}
${exec banshee-1 --query-album}
${exec banshee-1 --query-position}
```
The other information is also available.
Do
```
$ banshee-1 --help
```
and
```
$ banshee-1 --help-query-track
```
The latter reveals the queries for the track (what's in a name?)
```
  --query-uri               URI
  --query-artist            Artist Name
  --query-album             Album Title
  --query-title             Track Title
  --query-duration          Duration
  --query-track-number      Track Number
  --query-track-count       Track Count
  --query-disc              Disc Number
  --query-year              Year
  --query-rating            Rating
```
The other query
```
$ banshee-1 --help-query-player
```
reveals some information on the player (Banshee itself)
```
  --query-current-state      Current player state
  --query-last-state         Last player state
  --query-can-pause          Query whether the player can be paused
  --query-can-seek           Query whether the player can seek
  --query-volume             Player volume
  --query-position           Player position in currently playing track
```
The --query-current-state can be useful to set up an if statement to hide the Conky text if the player is not active.
I will dig into this tomorrow.

Have fun

---

### Post by armageddon08 on 2008-11-06
Yup....sometime ago I'd been able to get the song info displayed in conky using codes similar to this and also the progress-bar. But now I've stopped using GNOME and don't use conky quite often....specially for displaying music info. So, I don't really remember how to do it.

---

### Post by cl0ckwork on 2008-11-06
i was running this a little while ago.
dropped it because with the commands running in conky, banshee always started up whenever conky was running.

might not be that big of a problem but there's other media players out there.
the real challenge is to get conky working with **songbird** :)

---

### Post by foppeh on 2008-11-07
Hi,

I wrote the Conky and bash script that can display everything Banshee can output. This includes a progress bar and it fixes problems with Banshee starting when the Conky script is run.

Basic usage 
```
conky -c ~/Conky/conky_banshee
```
if you extract the Conky folder to /home/user/.

It standard outputs only Artist, Title and progressbar as seen in the screenshot. In the file /Conky/conky_banshee all options are mentioned with an example of usage. In this file are some hints if the script doesn't work as expected - most likely you need to make the script executable with:
```
chmod +x /path/to/Conky/scripts/banshee.sh
```
or you want to change the path to the script in /Conky/conky_banshee.

Have fun

---

### Post by sanjit on 2008-12-18
Thanks.

How about album art?

---

### Post by mirek on 2009-01-06
> **cl0ckwork said:**
> i was running this a little while ago.
dropped it because with the commands running in conky, banshee always started up whenever conky was running.

try to add this line to .conkyrc:

${if_running banshee-1}${color black}Music:$color ${exec banshee-1 --query-title | cut -f2- -d" "}${endif}

so - it will provide you track information only if banshee is running (and aso - it cuts 'title:' prefix)

---

### Post by ljrmorgan on 2009-04-01
I'm having problems with ${if_running banshee-1}. I currently have in my .conkyrc (simply to test where the problem is):
```
${if_running banshee-1}
${font}Banshee Now Playing
${else}${color white} ${font}Banshee is not running!${endif}
```

"Banshee is not running!" is always displayed, even when banshee is running. I've tried changing the process name from banshee-1 to 'banshee-1', banshee, /usr/bin/banshee-1, /usr/bin/banshee etc etc.

I also use the avant window navigator, so I tried changing banshee-1 to awn, at which point "Banshee Now Playing" showed up.

Any ideas?

---

### Post by foppeh on 2009-04-01
> **ljrmorgan said:**
> I'm having problems with ${if_running banshee-1}. I currently have in my .conkyrc (simply to test where the problem is):
```
${if_running banshee-1}
${font}Banshee Now Playing
${else}${color white} ${font}Banshee is not running!${endif}
```

"Banshee is not running!" is always displayed, even when banshee is running. I've tried changing the process name from banshee-1 to 'banshee-1', banshee, /usr/bin/banshee-1, /usr/bin/banshee etc etc.

I also use the avant window navigator, so I tried changing banshee-1 to awn, at which point "Banshee Now Playing" showed up.

Any ideas?
Something is wrong with ${if_running banshee-1}. I can't find anything in the Conky documentation and some experimenting doesn't reveal a clue. The banshee starts working again if you leave the if / endif out.

---

### Post by ljrmorgan on 2009-04-01
I think without the if statement banshee will be opened every time conky is open, which isn't great to be honest. I can't really think of any other way of doing things. I've only just started using conky, which doesn't help.

---

### Post by foppeh on 2009-04-02
> **ljrmorgan said:**
> I think without the if statement banshee will be opened every time conky is open, which isn't great to be honest. I can't really think of any other way of doing things. I've only just started using conky, which doesn't help.

Concider yourself unlucky.
I'll have a go with the --query-current-state in the bash script. If I can use that in a while loop it should have similar results.
What's more: this is either a Conky or a Banshee bug. As soon as I've found a clue I'll file a bug report.

Have fun

---

### Post by ljrmorgan on 2009-04-02
Well, for anyone who's interested, I've made a bit of a hack workaround. First of all, I edited the banshee.sh file so that if you ask for the artist, say, the output you get is (for example)```
The Beatles
```instead of```
artist: The Beatles
```
I then created another script called bansheewrap.sh:
```
#!/bin/bash
#Wrapper for banshee.sh

running=`exec ps -C banshee-1 | wc -l`
if [  "$running" -gt 1 ]; then
 echo "`exec ~/scripts/banshee.sh title`"
 echo "by `exec ~/scripts/banshee.sh artist`"
 echo "from `exec ~/scripts/banshee.sh album` (`exec ~/scripts/banshee.sh year`)" 
else
 echo "Banshee is not running"
fi
```
and then in my .conkyrc I simply have:
```
${execi 1 ~/scripts/bansheewrap.sh}
```

A screenshot of my current conky is attached, the music is towards the bottom.

---

### Post by foppeh on 2009-04-02
> **ljrmorgan said:**
> Well, for anyone who's interested, I've made a bit of a hack workaround. First of all, I edited the banshee.sh file so that if you ask for the artist, say, the output you get is (for example)```
The Beatles
```instead of```
artist: The Beatles
```
I then created another script called bansheewrap.sh:
```
#!/bin/bash
#Wrapper for banshee.sh

running=`exec ps -C banshee-1 | wc -l`
if [  "$running" -gt 1 ]; then
 echo "`exec ~/scripts/banshee.sh title`"
 echo "by `exec ~/scripts/banshee.sh artist`"
 echo "from `exec ~/scripts/banshee.sh album` (`exec ~/scripts/banshee.sh year`)" 
else
 echo "Banshee is not running"
fi
```
and then in my .conkyrc I simply have:
```
${execi 1 ~/scripts/bansheewrap.sh}
```

A screenshot of my current conky is attached, the music is towards the bottom.
Looks great. Thanks for your contribution. I was thinking along this line
```
if[exec banshee-1 --query-current-state == 'running']
etc
fi
```
We should be able to find out what takes least recourses.

Good luck

---

### Post by ljrmorgan on 2009-04-02
> **foppeh said:**
> Looks great. Thanks for your contribution. I was thinking along this line
```
if[exec banshee-1 --query-current-state == 'running']
etc
fi
```
We should be able to find out what takes least recourses.

Good luck

The problem with running "banshee-1 --query-currnet-state" is that that will open banshee, so every time you start conky banshee will start up too. Even if you close it, it'll open again the next time conky checks if it's running. I think current state is more about telling you whether banshee is playing or paused, things like that.

I might edit my script to report the current state, after checking that banshee is running of course, as currently if banshee's state is "idle" (e.g. after just being opened) my script will display:
```

 
by 
from  ()
```
which isn't great. 
Really though that's just cosmetics, the script itself is hacky, I'd much rather do things the "proper" way using if_running etc.

banshee-1 appears as one of my processes, so I assume the problem is with conky's if_running command, though I don't know how that works well enough to figure out what the problem might be. I tried posting in the conky IRC channel on freenode, but no one replied. If anyone has any ideas they'd be greatly appreciated!

Incidentally, I've changed the script to cut off song/artist/album names that are too long, so if I'm listening to "Upon Settling on the Frozen Island, Lecithin Presents Claude and Coquelicot With His Animal Creations for them to Approve or Reject" by of Montreal from "Coquelicot Asleep in the Poppies: A Variety of Whimsical Verse" (for example!) conky wont take up my whole screen! I might upload the updated script once I've put in the state-checking part.

---

### Post by mervin on 2009-04-21
I don't know if this is of any use to anyone, but I modified a little python script I found [here]("http://bbs.archlinux.org/viewtopic.php?id=55155") which uses dbus calls to get the info from banshee. It should be a little more efficient than invoking the program each time. It checks for a running banshee so no unwanted starts

```
#!/usr/bin/env python

 
import sys,os,dbus

if sys.argv[1] == "--help":
	print("Usage: <script> --artist | --name | --album | --percent | --track")
else:
	rc = os.system( "ps -ef | grep -v grep | grep -c 'banshee' > /dev/null" )

	if rc == 0:


	    bus = dbus.SessionBus()
	    banshee = bus.get_object("org.bansheeproject.Banshee", "/org/bansheeproject/Banshee/PlayerEngine")
    
	    state = banshee.GetCurrentState()

	    if state == 'playing':
   
        	if sys.argv[1] == "--artist":
	            print(banshee.GetCurrentTrack()['artist'])

	        elif sys.argv[1] == "--name":
	            print(banshee.GetCurrentTrack()['name'])

	        elif sys.argv[1] == "--album":
	            print(banshee.GetCurrentTrack()['album'])

	        elif sys.argv[1] == "--percent":
	            print(100*banshee.GetPosition()/banshee.GetLength())

	        elif sys.argv[1] == "--track":
	            print(banshee.GetCurrentTrack()['track-number'])

	        elif sys.argv[1] == "--percent":
	            print(100*banshee.GetPosition()/banshee.GetLength())

	        elif sys.argv[1] == "--status":
	            print(state)	
	    else:
	        if sys.argv[1] == "--status":
	            print(state)
	else:
	        print "Banshee not running"
```

example of conky code:

```
TEXT
${execi 3 <location of script> --name}
${execibar 3 <location of script> --percent}
${execi 3 <location of script> --track}
${execi 3 <location of script> --artist}
${execi 3 <location of script> --album}
```

---

### Post by Ryuki_NdranC on 2009-05-25
> **mervin said:**
> I don't know if this is of any use to anyone, but I modified a little python script I found [here]("http://bbs.archlinux.org/viewtopic.php?id=55155") which uses dbus calls to get the info from banshee. It should be a little more efficient than invoking the program each time. It checks for a running banshee so no unwanted starts

```
#!/usr/bin/env python

 
import sys,os,dbus

if sys.argv[1] == "--help":
	print("Usage: <script> --artist | --name | --album | --percent | --track")
else:
	rc = os.system( "ps -ef | grep -v grep | grep -c 'banshee' > /dev/null" )

	if rc == 0:


	    bus = dbus.SessionBus()
	    banshee = bus.get_object("org.bansheeproject.Banshee", "/org/bansheeproject/Banshee/PlayerEngine")
    
	    state = banshee.GetCurrentState()

	    if state == 'playing':
   
        	if sys.argv[1] == "--artist":
	            print(banshee.GetCurrentTrack()['artist'])

	        elif sys.argv[1] == "--name":
	            print(banshee.GetCurrentTrack()['name'])

	        elif sys.argv[1] == "--album":
	            print(banshee.GetCurrentTrack()['album'])

	        elif sys.argv[1] == "--percent":
	            print(100*banshee.GetPosition()/banshee.GetLength())

	        elif sys.argv[1] == "--track":
	            print(banshee.GetCurrentTrack()['track-number'])

	        elif sys.argv[1] == "--percent":
	            print(100*banshee.GetPosition()/banshee.GetLength())

	        elif sys.argv[1] == "--status":
	            print(state)	
	    else:
	        if sys.argv[1] == "--status":
	            print(state)
	else:
	        print "Banshee not running"
```

example of conky code:

```
TEXT
${execi 3 <location of script> --name}
${execibar 3 <location of script> --percent}
${execi 3 <location of script> --track}
${execi 3 <location of script> --artist}
${execi 3 <location of script> --album}
```

I tried this script, everything works fine but banshee is still launched every time conky starts. I'm myself beginning to study bash scripting and python, but so far i know next to nothing, any1 able to tell if this can be fixed?

---

### Post by octobuntu on 2009-06-12
${color 6666ff}${font Mac Dingbats::size=18}o${font}${hr 2}$color
  ${color 9966CC}
  $alignc${pre_exec banshee-1 --query-artist| cut -f2- -d" "}
  $alignc${pre_exec banshee-1 --query-album | cut -f2- -d" "}
  $alignc${pre_exec banshee-1 --query-title | cut -f2- -d" "}
  $alignc${color 993366}${exec banshee-1 --query-position | cut -f2- -d" "} / $alignc${color 990099}${exec banshee-1 --query-duration | cut -f2- -d" "}

---

### Post by lunatico on 2009-06-12
> **octobuntu said:**
> ${color 6666ff}${font Mac Dingbats::size=18}o${font}${hr 2}$color
  ${color 9966CC}
  $alignc${pre_exec banshee-1 --query-artist| cut -f2- -d" "}
  $alignc${pre_exec banshee-1 --query-album | cut -f2- -d" "}
  $alignc${pre_exec banshee-1 --query-title | cut -f2- -d" "}
  $alignc${color 993366}${exec banshee-1 --query-position | cut -f2- -d" "} / $alignc${color 990099}${exec banshee-1 --query-duration | cut -f2- -d" "}

this spikes cpu to ~70%
:(

---

### Post by octobuntu on 2009-06-12
maybe then:

${color 6666ff}${font Mac Dingbats::size=18}o${font}${hr 2}$color
  ${color 9966CC}
  $alignc${execi 24 banshee-1 --query-artist| cut -f2- -d" "}
  $alignc${execi 24 banshee-1 --query-album | cut -f2- -d" "}
  $alignc${execi 24 banshee-1 --query-title | cut -f2- -d" "}
$alignc${color 993366}${execi 8 banshee-1 --query-position | cut -f2- -d" "} / $alignc${color 990099}${execi 8 banshee-1 --query-duration | cut -f2- -d" "}

---

### Post by gualeve on 2009-06-18
my single solution:

...
142 ${if_running mono /usr/lib/banshee-1/Banshee.exe}
143 ${color2}Artista : ${exec banshee-1 --query-artist}
144 ${color2}Álbum : ${exec banshee-1 --query-album}
145 ${color2}Título : ${exec banshee-1 --query-title}
146 ${color2}Duração : ${exec banshee-1 --query-duration}
147 ${else}
148 ${color lightgrey}Banshee não está em execução
149 $endif
...

[]s
AFG

---

### Post by bjohansen on 2009-07-06
> **ljrmorgan said:**
> Well, for anyone who's interested, I've made a bit of a hack workaround. First of all, I edited the banshee.sh file so that if you ask for the artist......

Any update on this script?
I got it working, but I'd like to get that mod of the Banshee.sh so that it doesnt say "artist:   *artist's name here*  ".

And one more thing that bugs me... The Conky window scale from how long the title of the song is.

---

### Post by feelshift on 2009-08-05
> **ljrmorgan said:**
> Well, for anyone who's interested, I've made a bit of a hack workaround. First of all, I edited the banshee.sh file so that if you ask for the artist, say, the output you get is (for example)```
The Beatles
```instead of```
artist: The Beatles
```
I'd also want that banshee.sh :D

---

### Post by hetx on 2009-08-10
The python scripts gets my CPU up to 25% every time it's run (3.6GHz Core 2 Duo). What makes it so heavy, it speaking with dbus?

---

### Post by the_Ben on 2009-08-18
> **bjohansen said:**
> Any update on this script?
I got it working, but I'd like to get that mod of the Banshee.sh so that it doesnt say "artist:   *artist's name here*  ".

And one more thing that bugs me... The Conky window scale from how long the title of the song is.

Any progress along these lines?

---

### Post by ljrmorgan on 2009-08-21
> **the_Ben said:**
> Any progress along these lines?

Sorry everyone, haven't checked this for ages. I basically gave up on this, it wasn't working properly: if you closed banshee it often re-opened it, and would keep doing so until you closed conky.

From what I remember all I did was print out a substring, so for example, instead of ```
echo "$art"
```
which would give, say "artist: The Beatles"

I had ```
echo "${art:8}"
``` which just misses out the first 8 characters (which are "artist: ") so the output is just "The Beatles". You can do a similar thing for title, album, etc etc.

I've just downloaded the new beta version of banshee, I'll see if I can figure out a better way of doing this, but hope that helps for now.

---

### Post by ljrmorgan on 2009-08-21
> **bjohansen said:**
> Any update on this script?
I got it working, but I'd like to get that mod of the Banshee.sh so that it doesnt say "artist:   *artist's name here*  ".

And one more thing that bugs me... The Conky window scale from how long the title of the song is.

See the above post :-)

Also, as for the length of the title: I had a similar issue with a (python) script which checks my gmail account. You can again pick a substring so that it isn't too long, e.g. take only the first 25 characters, or if you want to get rid of "title: " then take from the 7th to the 32nd character (32nd since 32 - 7 = 25...). Try something like ```
echo "${tit:7:32}"
```

If you want to be fancy you could even do something like this (pseudocode, not actual code!):

```
temptitle = title:7
If length(temptitle) < 25 then
 echo temptitle
else
 echo temptitle:0:25 + '...'
end if

```
i.e. if the title is less than 25 characters long then print it out, otherwise print the first 25 characters and "...".

I haven't done bash programming for ages (and even then barely did any) but it shouldn't be difficult to figure out how to do this, only really need to figure out how to get the length of the string.

---

### Post by kedde on 2009-09-25
See this thread

[http://ubuntuforums.org/showthread.php?t=1223883](http://ubuntuforums.org/showthread.php?t=1223883)

This makes it possible to get album art as well.

---

### Post by LinuxFree on 2010-08-17
> **ljrmorgan said:**
> Well, for anyone who's interested, I've made a  bit of a hack workaround. First of all, I edited the banshee.sh file so  that if you ask for the artist, say, the output you get is (for  example)```
The Beatles
```instead of```
artist: The  Beatles
```I then created another script called bansheewrap.sh:
```
#!/bin/bash
#Wrapper for banshee.sh

running=`exec ps -C banshee-1 | wc -l`
if [  "$running" -gt 1 ]; then
 echo "`exec ~/scripts/banshee.sh title`"
 echo "by `exec ~/scripts/banshee.sh artist`"
 echo "from `exec ~/scripts/banshee.sh album` (`exec ~/scripts/banshee.sh year`)" 
else
 echo "Banshee is not running"
fi
```and then in my .conkyrc I simply have:
```
${execi 1 ~/scripts/bansheewrap.sh}
```A screenshot of my  current conky is attached, the music is towards the bottom.

I like this way of doing things but when I try to find banshee.sh in terminal it says no such file or directory. I have banshee, it runs. For some reason no sh file though. Can someone help me with this? If I don't have that file the wrapper won't work after all...

---

