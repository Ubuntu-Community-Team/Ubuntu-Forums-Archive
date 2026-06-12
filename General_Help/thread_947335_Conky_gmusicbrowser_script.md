---
title: "Conky gmusicbrowser script"
date: 2008-10-14
forum: General Help
---

### Post by loomsen on 2008-10-14
Hi folks.

I decided to write a script to integrate gmusicbrowser into conky without having to patch the source, which isn't really necessary imho.

If anyone is interested in it, here it is:
```

See below for updated version

```

Save it to a textfile, for example to 
~/Scripts/gmusicinfo.sh
Assuming you saved it to the place above, you gotta make it executable with:
```

chmod +x ~/Scripts/gmusicinfo.sh

```

Then you're ready to run it.

A conky example:
```

${color black}${font Comic Sans MS:size=11}${if_existing ~/.config/gmusicbrowser/gmusicbrowser.fifo}${execi 2 cat ~/.config/gmusicbrowser/nowplaying.info|grep "Artist:"|cut -d":" -f2} - ${execi 2 cat ~/.config/gmusicbrowser/nowplaying.info|grep "Title:"|cut -d":" -f2}${else} ${alignr}${font Comic Sans MS:size=7}no music played  $endif$color$font 
${color black}${font Comic Sans MS}${if_existing ~/.config/gmusicbrowser/gmusicbrowser.fifo}${execi 5 cat ~/.config/gmusicbrowser/nowplaying.info|grep "Album:"|cut -d":" -f2}(${execi 5 cat ~/.config/gmusicbrowser/nowplaying.info|grep "Date:"|cut -d":" -f2}) ${else} $endif
${font Sans:size=8}${if_existing ~/.config/gmusicbrowser/gmusicbrowser.fifo}${execi 2 ~/Scripts/gmusicinfo.sh position} of ${execi 10 ~/Scripts/gmusicinfo.sh total} ${execibar 2 ~/Scripts/gmusicinfo.sh progress}   $endif

```

Will give you sth like in the screenshot.

Enjoy.

---

### Post by loomsen on 2008-10-14
[COLOR="Red"]OBSOLETE - SEE NEW VERSION BELOW

However, the part about the ratings isn't included in the new script, thus I won't remove it[/COLOR]

Added rating...

But, obviously I'm a pretty lonesome using gmusicbrowser?

However, here it is:
```

#!/bin/bash
# gmusicbrowser script by loomsen
# if you want to contact me: loomsen<at>googlemail.com
#
# You should enable the nowplaying plugin in gmusicbrowsers options, i.e. you could specify the command as: 
# tee ~/.config/gmusicbrowser/nowplaying.info
# and check option to send standard input. Usage of this script:
# ./gmusicbrowser.sh <variable> (Possible var: total, position, progress)
# for conky you could use sth like this:
# ${execi 2 ~/path/to/script/gmusicbrowser.sh position} 
# to get the current position

file=~/.config/gmusicbrowser/nowplaying.info  ## the file gmusic sends standard input to
time=`cat $file | grep "Length" | cut -d":" -f2`
elapsed=`dbus-send --print-reply --dest=org.gmusicbrowser /org/gmusicbrowser org.gmusicbrowser.GetPosition | grep "double" | cut -d" " -f5 | cut -d"." -f1`
stars=`cat /home/docter/.config/gmusicbrowser/nowplaying.info | grep "Rating: " | cut -d" " -f2`

case $stars in
	10|20|30|40|50|60|70|80|90|100 )
	WERTUNG=`expr $stars / 1`
	;;
	* )
	WERTUNG=`expr 50 / 1`
	;; 
esac

case "$1" in

total)
{ 
	MINS=`expr $time / 60`
	REST=`expr $time % 60`
	SECS=`expr $REST % 60`
	printf "%02d:%02d" "$MINS" "$SECS"
}
;;
position)
{ 
	MINSEL=`expr $elapsed / 60`
	RESTEL=`expr $elapsed % 60`
	SECSEL=`expr $RESTEL % 60`
	printf "%02d:%02d" "$MINSEL" "$SECSEL"
}
;;
progress)
	expr $elapsed \* 100 / $time
;;
## rating)
#{	
#	printf $WERTUNG
#}
#;;
sterne)
{
case $WERTUNG in 
	0|5|10|15 )
	printf "rrrrr"
	;;
	20|25|30|35 )
	printf "srrrr"
	;;
	40|45|50|55 )
	printf "ssrrr"
	;;
	60|65|70|75 )
	printf "sssrr"
	;;
	80|85|90|95 )
	printf "ssssr"
	;;
	100 )
	printf "sssss"
	;;
esac
}
esac

```

The stars are part of the Pizzadude Stars font.
You may grab em, and some of pizzadudes other fonts, [ by clicking here](http://www.dafont.com/search.php?psize=m&q=pizzadude). To install just extract the .ttf file to ~/.fonts.

Further if you wanna use the rating you have to edit the nowplaying plugin.

```
 
sudo gedit /usr/share/gmusicbrowser/plugins/nowplaying.pm

```

Find the Sub Changed section, usually at the end of the file, where the standard output is specified, and add a line to it making it look like this:
```

{	my $ref=$::Songs[$ID];
		my $string=	'Artist:'.$ref->[::SONG_ARTIST]."\n"
				.'Title:'. $ref->[::SONG_TITLE]." \n"
				.'Album:'.$ref->[::SONG_ALBUM]."\n"
				.'Date:'.$ref->[::SONG_DATE]."\n"
				.'Length: '.$ref->[::SONG_LENGTH]."\n" 
ADD THIS LINE ----->	        .'Rating: '.$ref->[::SONG_RATING]."\n"
		;
		open my$out,'|-',@cmd;

```

Close and save it. 

The updated conky code for gmusic with rating:
```

${color black}${font Comic Sans MS:size=11}${if_existing /home/docter/.config/gmusicbrowser/gmusicbrowser.fifo}${goto 950}${execi 2 cat ~/.config/gmusicbrowser/nowplaying.info|grep "Artist:"|cut -d":" -f2} - ${execi 2 cat ~/.config/gmusicbrowser/nowplaying.info|grep "Title:"|cut -d":" -f2}${voffset 15}${goto 1350}${font Pizzadude Stars:size=15}${execi 10 ~/Scripts/gmusic_custom_2.sh sterne}${else} ${alignr}${font Comic Sans MS:size=7}no music played  $endif$color
${color black}${font Comic Sans MS}${if_existing /home/docter/.config/gmusicbrowser/gmusicbrowser.fifo}${goto 950}${execi 5 cat ~/.config/gmusicbrowser/nowplaying.info|grep "Album:"|cut -d":" -f2} (${execi 5 cat ~/.config/gmusicbrowser/nowplaying.info|grep "Date:"|cut -d":" -f2}) $endif
${font Sans:size=8}${if_existing /home/docter/.config/gmusicbrowser/gmusicbrowser.fifo}${goto 950}${execi 2 ~/Scripts/gmusic_custom.sh position} of ${execi 10 ~/Scripts/gmusic_custom.sh total} ${execibar 2 ~/Scripts/gmusic_custom.sh progress}   $endif

```

And a screener...

---

### Post by tromort on 2008-10-15
I recently also started using gmusicbrowser instead of banshee, so far it looks really nice/usefull. As soon as I get home Ill give this a try.

---

### Post by loomsen on 2008-10-15
Good, then I didn't write it for me exclusively at least :)

---

### Post by loomsen on 2008-10-17
I worked around the layout a lil bit.

[[img]http://img361.imageshack.us/img361/9356/screenshot47ho6.th.png[/img]](http://img361.imageshack.us/img361/9356/screenshot47ho6.png)

```

${goto 1050}${execi 5 cat ~/.config/gmusicbrowser/nowplaying.info|grep "Album:"|cut -d":" -f2|cut -d"(" -f1} ${alignr}${execi 5 cat ~/.config/gmusicbrowser/nowplaying.info|grep "Date:"|cut -d":" -f2}  
${goto 1050}${color black}${font PizzaDude Stars:size=25}${execi 10 ~/Scripts/gmusic_custom_2.sh sterne}$font ${voffset -10}${font Comic Sans MS}${execi 2 ~/Scripts/gmusic_custom_2.sh position} - ${execi 10 ~/Scripts/gmusic_custom_2.sh total} ${voffset 5}${execibar 2 ~/Scripts/gmusic_custom_2.sh progress}  
${else} ${alignr}${font Comic Sans MS:size=7}no music played  $endif

```

---

### Post by jjgomera on 2008-10-27
good script, and great idea to add other information to standard output of gmusicbrowser, i use a [similar script]("http://ubuntuforums.org/showpost.php?p=5524548&postcount=3175") same time ago, but i didn't know how to add more information.

> 
[[img]http://img361.imageshack.us/img361/9356/screenshot47ho6.th.png[/img]](http://img361.imageshack.us/img361/9356/screenshot47ho6.png)

Is the picture at the bottom the cover of album? How do you draw in desktop?

---

### Post by loomsen on 2008-10-27
Thanks, glad you like it :)

Well, actually it's kind of a workaround. I created a layout containing the cover only, using compiz to have it undecorated, sticky and placed.

What I didn't figure out tho, maybe you know...
Is there a possibility to call fwd through dbus/fifo somehow? Only play/stop is what I figured out so far...
And second, is it possible to change the popup for click on cover?
Actually, I'd like to change the album window into some kind of control window if I click on the cover. Hard to explain, did you get me? :)

Added the only cover and my custom layout...

[[img]http://img355.imageshack.us/img355/5002/screenshot08zf5.th.png[/img]](http://img355.imageshack.us/img355/5002/screenshot08zf5.png)[[img]http://img201.imageshack.us/img201/5806/screenshot07wr4.th.png[/img]](http://img201.imageshack.us/img201/5806/screenshot07wr4.png)
[[img]http://img291.imageshack.us/img291/2473/screenshot10rg7.th.png[/img]](http://img291.imageshack.us/img291/2473/screenshot10rg7.png)[[img]http://img233.imageshack.us/img233/3601/screenshot09tk1.th.png[/img]](http://img233.imageshack.us/img233/3601/screenshot09tk1.png)

---

### Post by loomsen on 2008-10-28
OK,

forget it. Figured out (by reading the howto ^^) and integrated it with compiz deskmenu, which is a quite nice solution imho.

Rightclick on my desktop gives me this menu:

[[img]http://img206.imageshack.us/img206/3607/screenshot18la5.th.png[/img]](http://img206.imageshack.us/img206/3607/screenshot18la5.png)

Lovin' it, now I can easily switch through different layouts if I feel like, and have all main controls just one click away :)

Here's the part to add to ~/.config/compiz/deskmenu/menu.xml, to the bottom of it, right before the last </menu>
```

<menu name="gmusicbrowser">
    <item type="launcher">
      <name>Show/Hide</name>
      <command>gmusicbrowser -remotecmd ShowHide</command>
      <icon>gmb-playlist</icon>
    </item>
    <item type="launcher">
      <name>Next</name>
      <command>gmusicbrowser -remotecmd NextSong</command>
      <icon>gtk-media-next</icon>
    </item>
    <item type="launcher">
      <name>Mute/Unmute</name>
      <command>gmusicbrowser -remotecmd TogMute</command>
      <icon>gmb-vol3</icon>
    </item>
    <item type="launcher">
      <name>Previous</name>
      <command>gmusicbrowser -remotecmd PrevSong</command>
      <icon>gtk-media-previous</icon>
    </item>
    <item type="launcher">
      <name>Quit</name>
      <command>gmusicbrowser -remotecmd Quit</command>
      <icon>gmb-turnoff</icon>
    </item>
    <menu name="Layout">
      <item type="launcher">
        <name>big</name>
        <command>gmusicbrowser -remotecmd SetPlayerLayout aaaab</command>
      </item>
      <item type="launcher">
        <name>nur cover</name>
        <command>gmusicbrowser -remotecmd SetPlayerLayout custom_nur-cover</command>
      </item>
      <item type="launcher">
        <name>default</name>
        <command>gmusicbrowser -remotecmd SetPlayerLayout custom default</command>
      </item>
    </menu>
    <menu name="Misc">
      <item type="launcher">
        <command>gmusicbrowser -remotecmd OpenPref</command>
        <name>Preferences</name>
        <icon>gtk-preferences</icon>
      </item>
      <item type="launcher">
        <command>gmusicbrowser -remotecmd ChangeDisplay :1</command>
        <name>Display TV</name>
        <icon>tv_icon</icon>
      </item>
      <item type="launcher">
        <name>Display Laptop</name>
        <command>gmusicbrowser -remotecmd ChangeDisplay :0</command>
        <icon>laptop_icon</icon>
      </item>
      <item type="launcher">
        <command>gmusicbrowser -remotecmd OpenContext</command>
        <name>Context</name>
        <icon>gmb-context</icon>
      </item>
      <item type="launcher">
        <name>Properties</name>
        <command>gmusicbrowser -remotecmd OpenSongProp</command>
        <icon>gmb-prop</icon>
      </item>
    </menu>
  </menu>

```:guitar:

---

### Post by jjgomera on 2008-10-29
Im trying with this other, rough script:

```
#!/bin/bash
# 
# script para mostrar por pantalla la caratula del disco actualmente en escucha por gmusicbrowser
# dependencias: tener instalado el paquete feh de manipulación de imagenes

sleep 10
while [ -e "/home/jjgomera/.config/gmusicbrowser/gmusicbrowser.fifo" ]
do
	killall feh
	longitud=`cat /home/jjgomera/.config/gmusicbrowser/nowplaying | grep "Length" | cut -d"=" -f2`
	estado=`dbus-send --print-reply --dest=org.gmusicbrowser /org/gmusicbrowser org.gmusicbrowser.GetPosition | grep "double" | cut -d" " -f5`
	time=$(($longitud-$estado))
	album=`cat /home/jjgomera/.config/gmusicbrowser/nowplaying | grep "Album" | cut -d"=" -f2`
	caratula=`dbus-send --print-reply --dest=org.gmusicbrowser /org/gmusicbrowser org.gmusicbrowser.GetAlbumCover string:"$album" | grep "string" | cut -d" " -f5- | cut --delimiter='"' -f2`
	feh -x -g "150x150+250+850" "$caratula" &
	sleep $time
done
```
i run this process asociated with gmusicbrowser, disable taskbar, pager, show in all workspace, set always bellow in window manager (openbox) for feh to work like conky

[IMG]http://img112.imageshack.us/img112/1731/pantallazo1sw8.png[/IMG]

---

### Post by loomsen on 2009-06-14
Hi guys.

I've received a few PMs and decided to rewrite the script, should run better now I hope.
Please let me know, I didn't try it in conky yet (shell output, however, does what it is intended to do)

It doesn't need the nowplaying plugin anymore, instead you'll need to save the script to access dbus and get some standard output from 
[url=http://squentin.free.fr/gmusicbrowser/dokuwiki/doku.php?id=dbus_api]
HERE[/url]
Put the path to the perl script on top of mine, you will figure out I think....

```

#!/bin/bash
# gmusicbrowser script by loomsen
# if you want to contact me: loomsen<at>googlemail.com
#
## requires this script to access dbus and get std output:
# http://squentin.free.fr/gmusicbrowser/dokuwiki/doku.php?id=dbus_api
###
## Put path to your tempfile holding the song info here
songinfo=~/tmp/nowplaying.info
## ------- insert path to perl script here
DBUSINFO=~/Scripts/gmusic-dbus.pl
## ------- 
INFO=`perl $DBUSINFO > $songinfo`
time_tot=`awk /length/ $songinfo | awk '{print $3}'`
elapsed=`dbus-send --print-reply --dest=org.gmusicbrowser /org/gmusicbrowser org.gmusicbrowser.GetPosition | grep "double" | awk '{print $2}' | cut -d '.' -f1`
function tmp_cur
{
	MINS=`expr $elapsed / 60`
	REST=`expr $elapsed % 60`
	SECS=`expr $REST % 60`
	printf "%02d:%02d" "$MINS" "$SECS"
}

function tmp_tot
{ 
	MINS=`expr $time_tot / 60`
	REST=`expr $time_tot % 60`
	SECS=`expr $REST % 60`
	printf "%02d:%02d" "$MINS" "$SECS"
}

function progress
{ 
expr $elapsed \* 100 / $time_tot 
}

## here it starts, you may either 
case "$1" in
	cur_pos ) tmp_cur
	;;
	length ) tmp_tot
	;;
	progress ) progress
	;;
 	*) 
	if [ "$1" != "" ];then
		for i in "$@";do
# -----------------		FIXME: uncomment if you prefer RAW values (without tags)
#######                                      &#8595;
			awk /"$i"/ $songinfo #   | cut -d ':' -f2		
# -----------------
		done
	else
# ------------------		FIXME: uncomment if you prefer RAW values (without tags)
#######                            &#8595;
		awk /""/ $songinfo # | cut -d ':' -f2
# ------------------
	fi
	;;
esac 

exit 0

```

[[img]http://www.ubuntu-pics.de/thumb/16454/shot_SU8zaf.png[/img]](http://www.ubuntu-pics.de/bild/16454/shot_SU8zaf.png)

The variables for total length, current position and progress have to be used each as a single option.
Possible values:
foobar.sh cur_pos
foobar.sh length 
foobar.sh progress (this should be useful for a progress bar)

I hope things improved a little bit :)

Enjoy.

---

### Post by abhiroopb on 2009-08-02
Hi,

I am using the script here to show amarok information in Conky ([http://conky.sourceforge.net/amarok-ke49](http://conky.sourceforge.net/amarok-ke49)) -- see attached screenshot (towards the bottom).

How do I use your script to show the album cover?

---

### Post by loomsen on 2009-08-03
Well I'm not familiar with amarok at all, as this thread's title suggests ^^ 

But you can use any program thats capable to show an image and take the path from stdin.
I'm using xloadimage for simple tasks.

xloadimage /path/to/image

Then you just need to figure out how to send a query request to amarok to return the current albums image path... Something like for example

```

_command-to-query-imagepath=$(some amarok command)
_dbus-signal-song-changed=$(dbus command)
_imagefile=

#if song changed signal received
_imagefile=$_command-to-query-imagepath

xloadimage $_imagefile

```

This is just a quick n dirty draft, you will have to modify it (obviously)

---

### Post by aadam12 on 2009-08-12
Hi All, 

Unfortunately, I am not a script writer. I was wondering if any of you could write a script using the Now Playing plugin to send gmusicbrowser song title, artist, album and cover info to NotifyOSD in Jaunty. I'd love to see the NotifyOSD popup on song changes. 

I currently have the gmusicbrowser icon in my top panel and that is where the songchange info is currently displayed.

Also, is there a way to minimize gmusicbrowser to the panel icon?

---

### Post by loomsen on 2009-08-12
> **aadam12 said:**
> 
Also, is there a way to minimize gmusicbrowser to the panel icon?

[http://www.ubuntu-pics.de/bild/21712/shot_12_aW93vZ.png](http://www.ubuntu-pics.de/bild/21712/shot_12_aW93vZ.png)

This should do what you want...

NotifyOSD: good idea, unfortunately I'm currently not running ubuntu, so I can't take a look into it. Shouldn't be to hard to accomplish tho, write quentin a message about how to query the dbus signal song changed and things should get going. Or better, post your question 
[on the sourceforge forum](http://sourceforge.net/projects/gmusicbrowser/)

Quentin usually is very active and answers questions pretty fast. Hope this helped :)

---

### Post by aadam12 on 2009-08-12
loomsen - Thanks for the screenshot. I've tried both checked and unchecked but gmusicbrowser still minimizes to my dock and not to the tray icon. Oh well, no biggie.

I was going to send Quentin and email but I'll post the NotifyOSD question on Sourceforge instead so everyone can see. I'm sure someone will come up with a script.

Thanks again!

---

### Post by quazi on 2009-08-23
I'm a recent convert (from wine+foobar2k) and here's the script that I'm using to display art+info in conky.  
[ATTACH]125990[/ATTACH]
[ATTACH]125991[/ATTACH]

This is more or less a modification of a script written by
_[Subban]("http://ubuntuforums.org/showpost.php?p=7816963&postcount=8742")_ for Rhythmbox.

copyart_popup
```

#!/bin/sh
#
# Better method to use album art in conky?
# by Subban
#
# Previous method of doing it in conky meant that
# every single update forced the image to be copied.
# that is every single second on most peoples conky.
#
# we can then do magical things better on the image, like apply a sepia
# or maybe transform it to apply it to none flat surfaces?
# Add a blur if its behind a opaque glass..
#
#
# This script must go into the path.. ie ~/bin if you have it
#
# NOTE...... this didn't update once after logging in..
# had to manually run copyart from terminal and
# I don't know why must check when I find time.
#
nomusic="$HOME"/.conky/nomusic.png
rawpath="/home/mckitterick/.gmusic.png"
artist="`dbus-send --print-reply --dest=org.gmusicbrowser /org/gmusicbrowser org.gmusicbrowser.CurrentSong|grep artist -A1|tail -1|cut -d '"' -f2`"
file1=$(printf "$rawpath\n"|sed 's/\\//g')
file2=""$HOME"/.album"

if diff "$file1" "$file2" >/dev/null ; then
  exit 0
else
  cp "$file1" "$file2"

#make the album art/reflection
convert "$file2" -alpha on -resize 150x150 \
      -background none -gravity south -extent 200x200 \
      \( +clone  -fill none -colorize 65%  -size 200x200 gradient:  -flip \
         -compose blur -set option:compose:args 20 -composite -compose Over \
      \) -append -trim +repage \
      -size 200x240 xc:none +swap \
      -gravity North -geometry +0+5 -composite  "$HOME"/.album2.png
#make artist text
 convert -background none -fill white \
          -font "$HOME"/.fonts/AllerDisplay.ttf -pointsize 12 label:"$artist" -trim \
           "$HOME"/.popup_artist.png
#make artist text reflection
    convert -alpha on  -font "$HOME"/.fonts/AllerDisplay.ttf -pointsize 12 -gravity west \
            -size 400x55 xc:none -fill grey32 -annotate 0x0+0+0 "$artist" -flip -channel RGBA  -blur 2x2 \
            "$HOME"/.popup_artist-reflection.png

#merge the text/reflection with the album art
composite -geometry +10+210 "$HOME"/.popup_artist.png "$HOME"/.album2.png "$HOME"/.album2.png
composite -geometry +9+205 "$HOME"/.popup_artist-reflection.png "$HOME"/.album2.png "$HOME"/.album2.png

#tit=`conkyRhythmbox --datatype=AR`; convert -size 400x100 xc:none -font "$HOME"/.fonts/GILGON__.ttf  -pointsize 14 -strokewidth 3 -fill white -stroke black -annotate +0+60 "$tit" -blur 0x8 -stroke none  -annotate +0+45 "$tit" "$HOME"/.artist.png

#  convert -sepia-tone 80% "$file2" "$file2"2
fi

exit 0

```

conkyrc:
```

${if_existing /home/mckitterick/.config/gmusicbrowser/gmusicbrowser.fifo}
${exec copyart_popup}
${image /home/mckitterick/.conky/conky_popup/popupframe.png}
${image /home/mckitterick/.album2.png -p 90,0}
${voffset 200}${alignc 20}${exec echo `dbus-send --print-reply --dest=org.gmusicbrowser /org/gmusicbrowser org.gmusicbrowser.CurrentSong|grep title -A1|tail -1|cut -d '"' -f2`}
${else}
${image /home/mckitterick/.conky/conky_popup/popupframe.png}
${image /home/mckitterick/.nomusic.png -p 90,0}
$endif

```

All I need to do now is figure out how to get gmusicbrowser to behave properly with Docky.

EDIT: If you don't like corners, it's not too hard to make the art curvy:
[ATTACH]125994[/ATTACH]

```

convert $file2 -border 2 -format 'roundrectangle 1,1 %[fx:w-2],%[fx:h-2] 20,20' info: > .rounded_corner.mvg

convert $file2 -border 2 -alpha transparent -background none -fill white -stroke none -strokewidth 0 -draw "@.rounded_corner.mvg"    .rounded_corner_mask.png

convert $file2 -matte -bordercolor none -border 2 .rounded_corner_mask.png -compose DstIn -composite .curve.png
```

---

### Post by loomsen on 2009-08-23
Nice.

I haven't been running conky for quite a while, but I like the code. Maybe reusable to add some reflections to gmusicbrowser's GUI itself.

---

### Post by gapo on 2009-11-09
Hey ... this is really brilliant. Things are now a little bit changed now, I hope.

I started of with Banshee. But, things seem really mucked up when I updated to Karmic. The conkyBanshee script is no longer working, due to flawed dbus support ( because of the absence of hal ?#! ).

So, I switched to gmusicbrowser. I used loomsen's script to get values. The code is relatively very simple . To sum up, after you put the conkygmusic.sh script in ~/.scripts. Do a chmod +x . Then add this in your conky.

```
${execi 2 ~/.scripts/conkygmusic.sh title}
${execi 2 ~/.scripts/conkygmusic.sh artist}
${execi 2 ~/.scripts/conkygmusic.sh album}
${execibar 2 ~/.scripts/conkygmusic.sh progress}
```

Thanks for the great work you have put in this !

The point is now with Conky 1.7's image tag support , what is the basic syntax to get the albumart ? Or where should I look ? Or what should I do ?

---

### Post by Pott on 2009-12-04
Hey all,

I'm using Rhythmbox right now because of the script that works with Conky but I miss gmusicbrowser that I used with Jaunty.

I read the whole thread but I'm still not 100% on what to do to make it work... is there a quick sum-up somewhere, step by step...? I'm not too advanved with Ubuntu, much less scripts...

Thanks!

---

### Post by loomsen on 2009-12-05
> **gapo said:**
> 
Thanks for the great work you have put in this !

The point is now with Conky 1.7's image tag support , what is the basic syntax to get the albumart ? Or where should I look ? Or what should I do ?

You're welcome :)

Just a quick answer, but this solution would require the nowplaying plugin again. I don't know if the URI to the albumcover is reported in dbus... If so, this would be pretty easy, if not, take a look at the setup instructions above, where I described how to modify the nowplaying plugin to also report Rating. Open up the plugin in any texteditor, and you'll see which options may also be used in commented text at the bottom of the script iirc.

I'll take a look into this if i find some more time.

---

### Post by Pott on 2009-12-09
Ok I tried following the instructions on this thread, putting some things together from other info but it's not working at all. The best I get is 'No music playing' on my Conky even though it definitely IS playing... not sure what's going on...

---

