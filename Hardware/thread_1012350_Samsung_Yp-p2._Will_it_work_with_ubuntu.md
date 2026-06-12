---
title: "Samsung Yp-p2. Will it work with ubuntu?"
date: 2008-12-15
forum: Hardware
---

### Post by TheJoke on 2008-12-15
I have ubuntu 8.1 and i want to get a P2 because my itouch is useless atm and i'm going to sell it.

What i have to ask, is will the P2 work with ubuntu?

[http://www.anythingbutipod.com/archives/2007/11/samsung-yp-p2-review.php](http://www.anythingbutipod.com/archives/2007/11/samsung-yp-p2-review.php)

About the device.:p

---

### Post by jhulf on 2008-12-16
Have a look at this thread: 

[http://ubuntuforums.org/showthread.php?t=692745&highlight=samsung+p2](http://ubuntuforums.org/showthread.php?t=692745&highlight=samsung+p2)
and here:
[http://www.anythingbutipod.com/archives/2007/11/samsung-yp-p2-review.php](http://www.anythingbutipod.com/archives/2007/11/samsung-yp-p2-review.php)

Surely it's a nice gadget, but it has its limitations. For example this one:

# Supported Audio: MP3, WMA
# Supported Video: SVI 480x272 @ 30FPS / WMV9 SP 320x240 or 480x272 @ 30FPS
# Other Supported Formats: TXT, JPEG

---

### Post by ericwait on 2009-04-29
I have a P2 and really like it, but there were some things that needed to be done to make it interact with Ubuntu like one would expect.

First you need to update a hal file for usb music devices located here:

```
$ /usr/share/hal/fdi/information/10freedesktop/10-usb-music-players.fdi
```

If anyone knows how to submit this next section upstream, let me know.

Add the following somewhere in the Samsung section.  Be careful that you don't accidentally embed it into another device.  It should be placed after a 
```
</match>
``` that is indented in the farthest.  (once you look at the .fdi it will become more clear) ;)

Here is the code to paste:

```
<!-- Samsung YP-P2 -->
          <match key="@storage.originating_device:usb.product_id" int="0x5082">
           <addset key="portable_audio_player.access_method.protocols" type="strlist">storage</addset>
           <append key="portable_audio_player.output_formats" type="strlist">audio/x-ms-wma</append>
           <append key="portable_audio_player.output_formats" type="strlist">application/ogg</append>
           <append key="portable_audio_player.output_formats" type="strlist">audio/mpeg</append>
           <append key="portable_audio_player.output_formats" type="strlist">audio/mp3</append>
           <append key="portable_audio_player.input_formats" type="strlist">application/ogg</append>
	   <append key="portable_audio_player.audio_folders" type="strlist">Music/</append>
	   <append key="portable_audio_player.playlist_format" type="strlist">audio/x-mpegurl</append>
	   <append key="portable_audio_player.playlist_format" type="strlist">audio/x-scpls</append>
	   <append key="portable_audio_player.playlist_path" type="strlist">Playlists/</append>
          </match>
```

Then follow this website.  I changed mine to EU and UMS.  I hate that companies think that blocking features is a good thing (thanks Best Buy!:confused:) 

[http://www.anythingbutipod.com/forum/showthread.php?t=25784](http://www.anythingbutipod.com/forum/showthread.php?t=25784)

**Don't forget to restart to reload your hal settings.

After that, I was able to use the P2 with Banshee with no problems!  And I love that this player will work with ogg (audio) files.  Go Open Source\\:D/

********************************************************************

Would you like to take your own videos and load them onto the P2?

Get mencoder 
```
$sudo apt-get mencoder
``` 

Save this code to a file in your mplayer directory, like this:
(you can also see this at [http://ubuntuforums.org/showthread.php?t=651894](http://ubuntuforums.org/showthread.php?t=651894)
```
$ gedit ~/.mplayer/mencoder.conf
```

Paste this:

```
[svi]
fps=30
srate=44100
mc=0.1
oac=mp3lame=true
lameopts=cbr=true:br=128
ovc=xvid=true
xvidencopts=fixed_quant=4:max_bframes=0:quant_type=h263
profile-desc="fps=30 srate=44100 mc=0.1 oac=mp3lame=true lameopts=cbr=true:br=128 ovc=xvid=true xvidencopts=fixed_quant=4:max_bframes=0:quant_type=h263"
```

Save the file.

Now all you have to do is run this command to convert your mpgs to svi: (myvid.mpg is the source and myvid.svi is the destination)

```
$mencoder myvid.mpg -o myvid.svi -profile svi -vf scale=320:240,harddup
```

Now copy the .svi file to the Video directory on your P2 and enjoy!

---

