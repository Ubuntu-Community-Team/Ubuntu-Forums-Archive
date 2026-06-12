---
title: "Mplayer-plugin to work in Mozilla"
date: 2004-12-20
forum: General Help
---

### Post by Quest-Master on 2004-12-20
Since many have told to stay away from apt-ting for MPlayer packages, I've compiled everything and it's worked well so far. I want to install the MPlayer-plugin for Mozilla though which can be found here: [http://mplayerplug-in.sourceforge.net/](http://mplayerplug-in.sourceforge.net/)

In the apt repository, it as referred to as mozilla-mplayer. I'm compiling it though, and here's the problem I encounter while doing a ./configure: 

> checking for mozilla-plugin... Package mozilla-plugin was not found in the pkg-config search path.
Perhaps you should add the directory containing `mozilla-plugin.pc'
to the PKG_CONFIG_PATH environment variable
No package 'mozilla-plugin' found
configure: error: Unable to find gecko sdk

I later dug into the bug section of their SF page and found that this is actually a bug in the Debian/Ubuntu mozilla-dev package. Here are details on this bug: [http://sourceforge.net/tracker/index.php?func=detail&aid=1023442&group_id=71239&atid=530623](http://sourceforge.net/tracker/index.php?func=detail&aid=1023442&group_id=71239&atid=530623)

I don't quite understand what's going on in there, but if anyone has successfully gotten this to work, please tell me what to do. ;)

---

### Post by Quest-Master on 2004-12-20
Ack, I can't believe I did this again today. Found the solution 2 minutes after posting this :x

Sorry, lock this again mods.

---

### Post by moser on 2004-12-21
Then post your solution .-)

---

### Post by bob k on 2004-12-21
[QUOTE=Quest-Master]Ack, I can't believe I did this again today. Found the solution 2 minutes after posting this :x

Sorry, lock this again mods.[/QUOTE]

I downloaded mplayer from the mplayerhq.hu site and installed local to my ~ home directory. I followed the directions on the site to install everything. Once I had it working, with a 200 x 300 window. I then printed the manual and man pages (figure @150 pages).

After RTFM I copied the test config file to my .mplayer folder, and started adjusting my options.

Mplayer is a command line program although there is a gui front end which I have only used once.

Once you have the plugin working you will have to edit the ~/.mplayer/config file, all of the command line option can be applied to the config file so that inbedded vidio can be played the way you want it. I'm still in the process of figureing out the options and which ones work the best, I will include my config file to at least give an Idea.

any thing with a # is a comment. I am still playing with this.

##
## MPlayer config file
##
## This file can be copied to /usr/local/etc/mplayer.conf and/or ~/.mplayer/config .
## If both exist, the ~/.mplayer/config's settings override the
## /usr/local/etc/mplayer.conf ones. And, of course command line overrides all.
## The options are the same as in the command line, but they can be specified
## more flexibly here. See below.
##

#vo=x11			# To specify default video driver (see -vo help for
			# list)

#ao=oss			# To specify default audio driver (see -ao help for
			# list)

fs=yes			# Enlarges movie window to your desktop's size.
			# Used by drivers: all

#vm=yes			# Tries to change to a different videomode
			# Used by drivers: dga2, x11, sdl

bpp=24			# Force changing display depth.
			# Valid settings are: 0, 15, 16, 24, 32
			# may need 'vm=yes' too.
			# Used by drivers: fbdev, dga2, svga, vesa

zoom=yes		# Enable software scaling (powerful CPU needed)
			# Used by drivers: svga, x11, vesa

double=yes		# use double-buffering (recommended for xv with
			# SUB/OSD usage)

# monitoraspect=4:3	# standard monitor size, with square pixels
# monitoraspect=16:9	# use this for widescreen monitor! non-square pixels

# ontop=yes		# Makes the player window stay ontop
			# Used by drivers which use X11, except SDL,
			# as well as directx and gl2 under Windows

##
## Specify your preferred default skin here
## (skins are searched in /usr/local/share/mplayer/Skin/yourskin
##  and ~/.mplayer/Skin/yourskin)
##

skin = default

##
## Multiple languages are available :)
##
## Hungarian	igen	nem
## English	yes	no
## German	ja	nein
## Spanish	si	no
## Polish	tak	nie
## Swedish ja nej
## Binary	1	0
##
## You can also use spaces and/or tabs.
##

# sound		= 1
# nosound	= nein
mixer		= /dev/mixer

##
## resample the fonts' alphamap
## 0	plain white fonts
## 0.75	very narrow black outline (default)
## 1	narrow black outline
## 10	bold black outline
##

# ffactor = 0.75

##
## FBdev driver: 

# fb = /dev/fb0				# framebuffer device to use
# fbmode = 640x480-120			# use this mode (read from fb.modes!)
# fbmodeconfig = /etc/fb.modes		# the fb.modes file

## VESA and FBdev driver: specify your monitor's timings
## 
## (see for example /etc/X11/XF86Config for timings!)
## ** CAUTION! IF YOUR DISPLAY DOESN'T SUPPORT AUTOMATICALLY TURNING OFF WHEN
##    OVERDRIVED (AND EVEN IF IT DOES), THIS MAY CAUSE DAMAGE TO YOUR DISPLAY!
##    WE AREN'T RESPONSIBLE, IT'S YOUR DECISION! **
##
## k, K : means multiply by 1000
## m, M : means multiply by 1.000.000
##
 monitor-hfreq = 31.5k-80k		# horizontal frequency range
 monitor-vfreq = 60-75			# vertical frequency range
# monitor-dotclock = 30M-300M		# dotclock (or pixelclock) range

##
## SDL driver
##

# vo = sdl:aalib	# use SDL video driver by default
			# use "vo = sdl:aalib" or "vo sdl:dga" and so on,
			# for specifying SDL subdrivers
# ao = sdl:esd		# use SDL audio driver by default
			# use "ao = sdl:esd" to use SDL's ESD driver
#noxv = no		        # whether to use XVideo hardware acceleration or not
#forcexv = yes		# force XVideo even if not detected


##
## Other (preferred to be default from configfile) switches
##

framedrop 	= yes	# drop frames, when not in sync (slow CPU, videocard,
			# etc)

cache		= 8192	# use 8Mb input cache by default

# slang		= en	# DVD : display english subtitles if available
alang		= en	# DVD : play english audio tracks if available
loop		= 0
really-quiet	= yes


## This is the correct way to use "subconfig" type options in the
## configuration file. In the command line you use :
## -aop list=resample:fout=44100 , but here it is :
# aop=list=resample:fout=44100

##
## You can also include other configfiles
## Specify full path!
##
## Delete this default :)
##

#include = /home/gabucino/.mplayer/i_did_not_RTFM_carefully_enough...

---

### Post by Quest-Master on 2004-12-21
It needed more packages than were listed on the site.. over 200 megs of libraries.

Anyhow, it's working fine now, but it buffers songs up to around 25%, and then only plays 25% of the song. It doesn't load 100% of it and play the entire thing. I know for a fact it isn't playing the entire song either since I have heard it before completed ;)

---

