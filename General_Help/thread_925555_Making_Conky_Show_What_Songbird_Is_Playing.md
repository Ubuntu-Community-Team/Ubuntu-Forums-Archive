---
title: "Making Conky Show What Songbird Is Playing"
date: 2008-09-20
forum: General Help
---

### Post by KeybladeSephi on 2008-09-20
Hello, everyone. I use Songbird as my default music player, but don't know how to get Conky to show what it's playing. Does anyone know how? Thanks =D

---

### Post by parm289 on 2008-11-27
I hate to dig up old posts, but:

Songbird has an extension called DBusBird that interfaces Songbird with DBus.  Would it be possible to make a conky script to display Songbird info through DBus?

---

### Post by rudihawk on 2008-11-27
I have mine setup to work with rythmbox

```
${color #1EDA12}${alignc}:::CURRENT SONG INFO :::
${if_running rhythmbox}${color #1EDA12}Artist: ${color #1EDA12}${goto 50}${exec rhythmbox-client --no-start --print-playing-format %ta}
${color #1EDA12}Title: ${color #1EDA12}${goto 50}${exec rhythmbox-client --print-playing-format %tt}
${color #1EDA12}Album: ${color #1EDA12}${goto 50}${exec rhythmbox-client --no-start --print-playing-format %at}
${color #1EDA12}Genre: ${color #1EDA12}${goto 50}${exec rhythmbox-client --no-start --print-playing-format %ag}${goto 130}${color #1EDA12}Year: ${color #1EDA12}${exec rhythmbox-client --no-start --print-playing-format %ay}
${color #1EDA12}Position: ${color #1EDA12}${exec rhythmbox-client --no-start --print-playing-format %te}${goto 130}${color #1EDA12}Length: ${color #1EDA12}${exec rhythmbox-client --no-start --print-playing-format %td}${color #28AF63}$else${color #1EDA12}${alignc}${font sans:size=6:bold}No Activity${font}$endif
```

---

### Post by parm289 on 2008-11-27
It seems that rythmbox is easier to monitor than songbird.  Songbird, afaik, does not have such a simple command-line monitoring system, hence why DBus is required.  All we need to monitor songbird is a simple python script using Dbus - if I knew python, I would write the script...but I don't.

BIG EDIT: Seems like I found a way to display the current title and artist:

1.  Download/Install LiveTweeter extension for songbird
2.  Go to Tools->Addons->LiveTweeter->Preferences
3.  Click on messenger tab
4.  Check "Activate Text File"
5.  In the text box right below "Activate text file," type
```
~/songbird.txt
```
6.  Open your .conkyrc file
7.  Type this into the TEXT section:
```
${execi 1 tail -n3 ~/songbird.txt | fold -w50}
```
****The "1" after execi means the info will refresh every second - edit as needed.******
8.  Save your .conkyrc file and start conky!

Hope this helps anyone who is wondering how to do this!  A screenshot of this in action is attached.

---

### Post by Zularan on 2008-11-30
> **parm289 said:**
> It seems that rythmbox is easier to monitor than songbird.  Songbird, afaik, does not have such a simple command-line monitoring system, hence why DBus is required.  All we need to monitor songbird is a simple python script using Dbus - if I knew python, I would write the script...but I don't.

BIG EDIT: Seems like I found a way to display the current title and artist:

1.  Download/Install LiveTweeter extension for songbird
2.  Go to Tools->Addons->LiveTweeter->Preferences
3.  Click on messenger tab
4.  Check "Activate Text File"
5.  In the text box right below "Activate text file," type
```
~/songbird.txt
```
6.  Open your .conkyrc file
7.  Type this into the TEXT section:
```
${execi 1 tail -n3 ~/songbird.txt | fold -w50}
```
****The "1" after execi means the info will refresh every second - edit as needed.******
8.  Save your .conkyrc file and start conky!

Hope this helps anyone who is wondering how to do this!  A screenshot of this in action is attached.

Nice find there, I was getting a headache trying to figure this one out.
The tweeter thing works fine. It's also possible to have long lines scroll in Conky with the ${scroll} tag so you don't have to worry about long texts and fold. Not in the documentation I found it by accident.

```
${scroll 30${alignr} ${execi 1 cat ~/scripts/conky/songbird.txt}}
```

---

### Post by eightmillion on 2008-12-01
I was looking for a way to get information from songbird for my [conky lyrics script]("http://code.google.com/p/lyricsdownloader/downloads/list") and I came across this thread. I implemented that and threw together a quick python script to interact with dbusbird and get the now playing info(literally less than ten minutes of work). Right now it outputs Artist - Album - Track. I'll add support for command line switches to format the output if anyone is interested. You need to have python-dbus installed to use it.


Edit: New version. It supports command line arguments in the form of %aa%tt%nn%bb where aa is artist, tt is track title, nn is number, and bb is album title. Calling it without arguments outputs Artist - Album - Title.

Examples:
$ ./songbird.py %nn%tt%bb
1 - Windowpane - Damnation

$ ./songbird.py %aa%tt
Opeth - Windowpane

$ ./songbird.py %bb%nn
Damnation - 1

---

### Post by parm289 on 2008-12-01
YES!  I was hoping this thread would get the attention of someone willing to hack up a python script...thanks a bunch for the script and I'm glad I was able to spark the idea.

---

### Post by anxiousdog on 2008-12-07
So being a little new... how can I add this to my current conky file? This is the bit that I use to show Rhythmnbox: 

```
${font Print Bold:size=14}${color2} Title:  ${color1}${exec conkyRhythmbox --datatype=TI}${font}
${font Print Bold:size=14}${color2} Duration:  ${color1}${exec conkyRhythmbox --datatype=PT}/${exec conkyRhythmbox --datatype=LE}${font}
${color1}${execibar 1 conkyRhythmbox --datatype=PP}
```

---

### Post by eightmillion on 2008-12-07
> **anxiousdog said:**
> So being a little new... how can I add this to my current conky file? This is the bit that I use to show Rhythmnbox: 

```
${font Print Bold:size=14}${color2} Title:  ${color1}${exec conkyRhythmbox --datatype=TI}${font}
${font Print Bold:size=14}${color2} Duration:  ${color1}${exec conkyRhythmbox --datatype=PT}/${exec conkyRhythmbox --datatype=LE}${font}
${color1}${execibar 1 conkyRhythmbox --datatype=PP}
```

Hi anxiousdog. You're not going to be able to do exactly the same thing with songbird as you do with rhythmbox. Dbusbird doesn't make the song position available to outside applications, only the total song length. You should be able to do something like this:

```
${font Print Bold:size=14}${color2} Title:  ${color1}${exec songbird.py %tt}${font}
${font Print Bold:size=14}${color2} Duration:  ${color1}${exec songbird.py %ll}
```

This will only display the track name and length. You'll have to grab this new version that returns the track length too.

---

### Post by anxiousdog on 2008-12-08
> **eightmillion said:**
> Hi anxiousdog. You're not going to be able to do exactly the same thing with songbird as you do with rhythmbox. Dbusbird doesn't make the song position available to outside applications, only the total song length. You should be able to do something like this:

```
${font Print Bold:size=14}${color2} Title:  ${color1}${exec songbird.py %tt}${font}
${font Print Bold:size=14}${color2} Duration:  ${color1}${exec songbird.py %ll}
```

This will only display the track name and length. You'll have to grab this new version that returns the track length too.

Thanks for this! I added the new version and the code:

> ${font Print Bold:size=14}${color2} Title:  ${color1}${exec ~/Conky/songbird.py %tt}${font}
${font Print Bold:size=14}${color2} Duration:  ${color1}${exec ~/Conky/songbird.py %ll}

Unfortunately I am getting an error

> sh: /home/anxiousdog/Conky/songbird.py: Permission denied


I seem to remember this being something with the exec command...? Not sure what to do!

---

### Post by eightmillion on 2008-12-08
> **anxiousdog said:**
> Thanks for this! I added the new version and the code:



Unfortunately I am getting an error



I seem to remember this being something with the exec command...? Not sure what to do!

Did you make it executable first? Try 'chmod +x ~/Conky/songbird.py'. You might want to grab this new version too, since the old one isn't exiting properly when songbird isn't running.

---

### Post by anxiousdog on 2008-12-08
> **eightmillion said:**
> Did you make it executable first? Try 'chmod +x ~/Conky/songbird.py'. You might want to grab this new version too, since the old one isn't exiting properly when songbird isn't running.

Ah the executable was it. Of course it's not throwing the error anymore, but it's not showing the song data now. :(

---

### Post by eightmillion on 2008-12-08
> **anxiousdog said:**
> Ah the executable was it. Of course it's not throwing the error anymore, but it's not showing the song data now. :(

Did you install the dbusbird extension? If so, could you post the output of this command?

```
dbus-send --dest='org.mozilla.songbird' --print-reply /org/mozilla/songbird org.mozilla.songbird.getStatus
```

---

### Post by anxiousdog on 2008-12-09
> **eightmillion said:**
> Did you install the dbusbird extension? If so, could you post the output of this command?

```
dbus-send --dest='org.mozilla.songbird' --print-reply /org/mozilla/songbird org.mozilla.songbird.getStatus
```

I am using Songbird 1.0 and when I navigate to the add-ons page to see if I can install [DBusbird]("http://addons.songbirdnest.com/addon/181"), the install option isn't available. I think that this was built into the latest version...? That or it hasn't been updated to work with 1.0. Maybe I need to wait a little longer?

Here is the output:

> anxiousdog@ubuntu1:~$ dbus-send --dest='org.mozilla.songbird' --print-reply /org/mozilla/songbird org.mozilla.songbird.getStatus
Error org.freedesktop.DBus.Error.ServiceUnknown: The name org.mozilla.songbird was not provided by any .service files


---

### Post by eightmillion on 2008-12-09
> **anxiousdog said:**
> I am using Songbird 1.0 and when I navigate to the add-ons page to see if I can install [DBusbird]("http://addons.songbirdnest.com/addon/181"), the install option isn't available. I think that this was built into the latest version...? That or it hasn't been updated to work with 1.0. Maybe I need to wait a little longer?

Here is the output:

You're right that it doesn't work with 1.0, but it wasn't built into the newest version (although it should be). Apparently the author isn't working on it right now either, so you may be waiting a while. :(

---

### Post by bobt39 on 2008-12-10
gah i hope they make it work for 1.0 or someone comes out with another fix.

does anyone know why ${if_running songbird} doesnt work? I replaced "songbird" with "firefox" and that worked fine. Does songbird have another name or something?

EDIT - I answered my own question, its songbird-bin

---

### Post by parm289 on 2008-12-11
Ok guys, it's true that this script does not work with Songbird 1.0.  However, the LiveTweeter extension HAS been updated to 1.0, and therefore them method outlined in my earlier post will still work.  For a refresher:

> 1. Download/Install LiveTweeter extension for songbird
2. Go to Tools->Addons->LiveTweeter->Preferences
3. Click on messenger tab
4. Check "Activate Text File"
5. In the text box right below "Activate text file," type
Code:

~/songbird.txt

6. Open your .conkyrc file
7. Type this into the TEXT section:
Code:

${execi 1 tail -n3 ~/songbird.txt | fold -w50}

****The "1" after execi means the info will refresh every second - edit as needed.******
8. Save your .conkyrc file and start conky!

This is working for me but only currently displays Title and Artist.

---

### Post by KuruOujou on 2008-12-19
Just so everyone knows, I think dbusbird has been updated for 1.0 now. I was able to install it, at least, and I'm running songbird 1.0.

---

### Post by eightmillion on 2008-12-19
> **KuruOujou said:**
> Just so everyone knows, I think dbusbird has been updated for 1.0 now. I was able to install it, at least, and I'm running songbird 1.0.

Thanks for the update. Here's a new version of my script. The old version still works. This one eliminates a few bugs (and probably introduces some new ones :)) There's also some new switches -s or --status returns &#9654;, &#10074;&#10074;, or &#9632; depending on whether songbird is playing, paused, or stopped. -l or --long-status outputs Playing, Paused or Stopped. 

This is the full list of formatting options:

        %aa           Artist
        %bb           Album
        %tt           Track Title
        %ll           Track Length
        %nn           Track Number
        %br           Bitrate
        %dd           Date
        %ff           File Path


Here's a screenshot of Mira Multi conky configured to work with it:
[IMG]http://e.imagehost.org/0439/mira.png[/IMG]


[DOWNLOAD LINK]("http://lyricsdownloader.googlecode.com/files/songbird.py")

---

### Post by Wylkar on 2008-12-21
eightmillion,
I am using your script in songbird 1.0. I have dbusbird installed, but I still get no song data.
Thanks

---

### Post by eightmillion on 2008-12-21
> **Wylkar said:**
> eightmillion,
I am using your script in songbird 1.0. I have dbusbird installed, but I still get no song data.
Thanks

Ok, let's try a few things. Could you run these commands and post the output?

First make sure that the execute bit is set for the script.
```
chmod +x /path/to/script/songbird.py
```

Then run the script from the command line and see what the exit code is:
```
./songbird.py
echo $?
```

Then, try these out:

This one should have a lot of output.
```
dbus-send --dest='org.mozilla.songbird' --print-reply /org/mozilla/songbird org.freedesktop.DBus.Introspectable.Introspect

```

```
pgrep songbird
```

```
apt-cache policy python-dbus
```

---

### Post by Wylkar on 2008-12-21
I already made it an executable, the output for running it in the command line was 
'william@william-laptop:~$ ~/scripts/songbird.py
william@william-laptop:~$ echo $?
1'
    this is all I got for the one you said should have a lot of output:
'william@william-laptop:~$ dbus-send --dest='org.mozilla.songbird' --print-reply /org/mozilla/songbird org.freedesktop.DBus.Introspectable.Introspect
Error org.freedesktop.DBus.Error.ServiceUnknown: The name org.mozilla.songbird was not provided by any .service files'
    For the second to last command I got:
'william@william-laptop:~$ pgrep songbird
18753
18758' 
    For the last command I got:
'william@william-laptop:~$ apt-cache policy python-dbus
python-dbus:
  Installed: 0.82.4-2
  Candidate: 0.82.4-2
  Version table:
 *** 0.82.4-2 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
        100 /var/lib/dpkg/status'

---

### Post by eightmillion on 2008-12-21
> **Wylkar said:**
> william@william-laptop:~$ dbus-send --dest='org.mozilla.songbird' --print-reply /org/mozilla/songbird org.freedesktop.DBus.Introspectable.Introspect
Error org.freedesktop.DBus.Error.ServiceUnknown: The name org.mozilla.songbird was not provided by any .service files

This is the problem. Songbird still isn't making itself known on the session bus. You might try reinstalling dbusbird and restarting songbird.


The output of that command should look like this:

```
method return sender=:1.83959 -> dest=:1.88245 reply_serial=2                                                                            
   string "<!DOCTYPE node PUBLIC "-//freedesktop//DTD D-BUS Object Introspection 1.0//EN"                                                
"http://www.freedesktop.org/standards/dbus/1.0/introspect.dtd">                                                                          
<node>                                                                                                                                   
  <interface name="org.freedesktop.DBus.Introspectable">                                                                                 
    <method name="Introspect">                                                                                                           
      <arg name="data" direction="out" type="s"/>                                                                                        
    </method>                                                                                                                            
  </interface>                                                                                                                           
  <interface name="org.freedesktop.DBus.Properties">                                                                                     
    <method name="Get">                                                                                                                  
      <arg name="interface" direction="in" type="s"/>                                                                                    
      <arg name="propname" direction="in" type="s"/>                                                                                     
      <arg name="value" direction="out" type="v"/>                                                                                       
    </method>                                                                                                                            
    <method name="Set">                                                                                                                  
      <arg name="interface" direction="in" type="s"/>                                                                                    
      <arg name="propname" direction="in" type="s"/>                                                                                     
      <arg name="value" direction="in" type="v"/>                                                                                        
    </method>                                                                                                                            
    <method name="GetAll">                                                                                                               
      <arg name="interface" direction="in" type="s"/>                                                                                    
      <arg name="props" direction="out" type="a{sv}"/>                                                                                   
    </method>                                                                                                                            
  </interface>                                                                                                                           
  <interface name="org.mozilla.songbird">
    <method name="getStatus">
      <arg name="q_status" type="s" direction="out"/>
    </method>
    <method name="getFile">
      <arg name="q_file" type="s" direction="out"/>
    </method>
    <method name="getLength">
      <arg name="q_length" type="s" direction="out"/>
    </method>
    <method name="getBitrate">
      <arg name="q_bitrate" type="s" direction="out"/>
    </method>
    <method name="getDate">
      <arg name="q_date" type="s" direction="out"/>
    </method>
    <method name="getTrack">
      <arg name="q_track" type="s" direction="out"/>
    </method>
    <method name="getAlbum">
      <arg name="q_album" type="s" direction="out"/>
    </method>
    <method name="getTitle">
      <arg name="q_title" type="s" direction="out"/>
    </method>
    <method name="getArtist">
      <arg name="q_artist" type="s" direction="out"/>
    </method>
  </interface>
</node>
"
```

---

### Post by Wylkar on 2008-12-21
I tried reinstallation and it did not work. Thanks for the help.

---

### Post by eightmillion on 2008-12-21
> **Wylkar said:**
> I tried reinstallation and it did not work. Thanks for the help.

Sorry I couldn't help. You could try contacting the dbusbird guy.

---

### Post by irfan9727 on 2009-01-26
Ok, I got this runninng, but why this script only accept only 1 argument at one time?

---

### Post by eightmillion on 2009-01-26
> **irfan9727 said:**
> Ok, I got this runninng, but why this script only accept only 1 argument at one time?

That's just the way I wrote it. You should download this new version. It's much more flexible in accepting formatting arguments. Here's some examples:

```

$ ./songbird.py
A Perfect Circle - Mer de Noms - 3 Libras

$ ./songbird.py %ll -  %tt -  %aa -  %bb
04:48 - Orestes - A Perfect Circle - Mer de Noms

$ ./songbird.py "Length: %ll      Title: %tt     Artist: %aa     Album: %bb"
Length: 03:39      Title: 3 Libras     Artist: A Perfect Circle     Album: Mer de Noms

$ ./songbird.py %ls
Playing

$ ./songbird.py %ss
&#9654;


```

---

### Post by irfan9727 on 2009-01-27
Okay, thank you very much!

---

### Post by cros13 on 2009-03-03
Thanks for the script eightmillion.
The only issue I have is when characters such a ' or " are in the tags nothing is output.

---

### Post by eightmillion on 2009-03-03
Does this happen if you run it on the command line too, or just conky?

---

### Post by cros13 on 2009-03-03
I get:
Traceback (most recent call last):
  File "/home/cros13/bin/songbird.py", line 110, in <module>
    print ' - '.join(info)
UnicodeEncodeError: 'ascii' codec can't encode character u'\u2019' in position 19: ordinal not in range(128)

---

### Post by cros13 on 2009-03-03
also is there any way to output elapsed time?

---

### Post by eightmillion on 2009-03-03
> **cros13 said:**
> I get:
Traceback (most recent call last):
  File "/home/cros13/bin/songbird.py", line 110, in <module>
    print ' - '.join(info)
UnicodeEncodeError: 'ascii' codec can't encode character u'\u2019' in position 19: ordinal not in range(128)
Try changing that line to: 
```
    print u' - '.join(info)
```
This way, I don't think it will try to reencode the unicode strings.
> **cros13 said:**
> also is there any way to output elapsed time?

No, unfortunately that's not information that dbusbird makes available.

---

### Post by cros13 on 2009-03-03
Same error. I replaced both instances of "print ' - '.join(info)" and still no change.

---

### Post by eightmillion on 2009-03-03
Try change the line at the top:
```
# -*- coding: latin-1 -*-
```
to:
```
# -*- coding: utf-8 -*-
```

---

### Post by cros13 on 2009-03-03
Still the same issue... My console coding is set in my kernel to utf8 if that makes any difference.

---

### Post by eightmillion on 2009-03-03
Well I think I'm about out of options on getting that character to display. I could write a function the strips out any problem characters. Would that be an acceptable solution?

---

### Post by cros13 on 2009-03-03
Sure, that would be great.

---

### Post by eightmillion on 2009-03-03
Cool, because I already wrote it. :)

Give this version a try and cross your fingers.

Edit:
If you want, you can even add characters that you know work to the validChars variable.

---

### Post by cros13 on 2009-03-03
Thanks so much for your help eightmillion.
It was the lack of anything displayed at all that was getting on my nerves.

---

### Post by eightmillion on 2009-03-03
No problem. I'm glad we found a solution.

---

### Post by Ryuki_NdranC on 2009-05-24
First of all, thanks for the time you are putting into this script. I got a question though. I saw a few post backs a screeny with Mirav2 conky "now playing", and i was wondering if it is possible to make work the duration bar with your script. That would be ubberly awesome.

Thanks again man, and great work.

---

### Post by eightmillion on 2009-05-25
> **Ryuki_NdranC said:**
> First of all, thanks for the time you are putting into this script. I got a question though. I saw a few post backs a screeny with Mirav2 conky "now playing", and i was wondering if it is possible to make work the duration bar with your script. That would be ubberly awesome.

Thanks again man, and great work.

Thanks. Unfortunately dbusbird only returns the total length of the song and not the elapsed time, so it's not possible to make the duration bar work.

---

### Post by Ryuki_NdranC on 2009-05-25
> **eightmillion said:**
> Thanks. Unfortunately dbusbird only returns the total length of the song and not the elapsed time, so it's not possible to make the duration bar work.


Oh well, i guess i could live without it. ^^ Thx...

---

### Post by Ryuki_NdranC on 2009-05-25
Does someone know if dbusbird is ever gonna get updated? Because i can't install it from the add-on website... The install button is grayed out. I think it's because the fact that has two month without an update.

---

### Post by devildoc5 on 2009-07-05
dbusbird seems to not be up working for version 1.02 as of yet.....

---

### Post by maslic68 on 2010-01-15
[http://addons.songbirdnest.com/addon/1626]("http://addons.songbirdnest.com/addon/1626")

MPRIS extension is maintained and can do pretty much the same as Dbusbird, so it would be nice if someone could rewrite the script here to be used with it. I tried it but I'm no programmer so i failed mireably.

Well not exactly failed... I managed to make theese 5 little scripts . The function is pretty obvious (SBstatusIMG.py returns status in form of Webdings symbol for play,pause,stop), but I bet any of you can do it better :D

---

### Post by vanepelw on 2010-02-24
I've taken the scripts that maslic68 provided and put them into a single script, entirely based on the conkyExaile.py script that you can find at conky hardcore ([http://conky.linux-hardcore.com/?page_id=849](http://conky.linux-hardcore.com/?page_id=849)) and within these forums ([http://ubuntuforums.org/showthread.php?t=926041](http://ubuntuforums.org/showthread.php?t=926041)).

The updated script allows you to get a specific item returned based upon command line or template, and also includes a trick to get the local location of the coverart for the song.  I only implemented the few items that I use, not everything that MPRIS provides, so with very little effort this could be expanded and improved upon greatly.  This is hacked together at best...

I've attached the script. My template (.conkySongbird.template):

```

${image [--datatype=CA] -s 50x50 -p 1140,25}
${goto 1210}${voffset -60}[--datatype=AR]
${goto 1210}[--datatype=TI]
${goto 1210}[--datatype=AL]

```

My conky config file:

```

use_xft yes
xftfont Liberation Sans:size=11

update_interval 1
total_run_times 0
double_buffer yes
text_buffer_size 2048

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

minimum_size 1440 80


default_color 171717
draw_shades no

color0 white
color1 white
color2 919FB8

alignment bottom_left
gap_x 0
gap_y -153

no_buffers no
net_avg_samples 2

override_utf8_locale yes

no_buffers yes

imlib_cache_size 0

TEXT
${image ./pix/cwb2.png -s 1440x70 -p -0,15}${image ./pix/cbg.png  -s 64x64 -p 1133,18}${voffset 15}${execpi 10800 ~/.tonky/sh/conkyForecast.py -l USMN0178 -w -t ~/.tonky/conkyForecast.template} ${image ./pix/System/Task_Manager.png -s 64x64 -p 270,18}${image ./pix/System/Memory.png -s 64x64 -p 470,18}${image ./pix/System/Clock2.png -s 64x64 -p 670,18}${image ./pix/System//wlan100.png -s 70x70 -p 870,10}
${goto 350}${voffset -78}Cpu1:${goto 420}${cpu cpu1}%${goto 551}Hd:${goto 620}${fs_used_perc /}%${goto 750}${time %H:%M}${goto 960}Signal:${goto 1020}${wireless_link_qual wlan0}%
${goto 350}Step:${goto 420}${freq_g}${goto 550}Ram:${goto 620}${memperc}%${goto 750}${time %A} ${goto 960}Bitrate:${goto 1020}${wireless_bitrate wlan0}
${goto 350}${goto 550}Swap:${goto 627}${swapperc}%${goto 750}${time %d. %B}${goto 960}Local:${goto 1020}${addr wlan0}
${goto 686}${voffset -44}${font aClock:style=_Hour:size=30}${color2}${execi 120 python ~/.tonky/sh/conkyClock_h.py}${color}${font}
${goto 686}${voffset -36}${font aClock:style=_Min:size=30}${color2}${execi 60 python ~/.tonky/sh/conkyClock_m.py}${color}${font}
${execpi 10 ~/.tonky/sh/conkySongbird.py --template=~/.tonky/.conkySongbird.template }

```

  The conky theme is the 'Tonky' theme that can be found here:  [http://bigrza.deviantart.com/art/Tonky-Desktop-v0-5-135697944](http://bigrza.deviantart.com/art/Tonky-Desktop-v0-5-135697944)

I've also attached a screenshot with the result.  Hope you enjoy!

---

### Post by dopple on 2010-03-10
Hey. Nice Job. In order to use this I had to change conkySongbird.py coverart output line to the following

```
output = str(self.musicData.coverart).replace("resource://sb-artwork/", "~/.songbird2/h658bh2j.default/artwork/")
```

---

### Post by Spike-X on 2010-04-10
> **eightmillion said:**
> Cool, because I already wrote it. :)

Give this version a try and cross your fingers.

Edit:
If you want, you can even add characters that you know work to the validChars variable.

I'm using the version of the script you posted there, but with the following line changed as per the MPRIS page:

```
songbird = bus.get_object('org.mpris.songbird', '/Player')
```

I'm calling the script with the following line in my conky.rc

```
${exec songbird.py %tt}$
```

But all that shows up is    ${}

What am I doing wrong? Even though Songbird is being discontinued for Linux, it's really sticking in my craw that I can't get this to work!

---

### Post by matias_tati on 2010-10-07
> **vanepelw said:**
> I've taken the scripts that maslic68 provided and put them into a single script, entirely based on the conkyExaile.py script that you can find at conky hardcore ([http://conky.linux-hardcore.com/?page_id=849](http://conky.linux-hardcore.com/?page_id=849)) and within these forums ([http://ubuntuforums.org/showthread.php?t=926041](http://ubuntuforums.org/showthread.php?t=926041)).

The updated script allows you to get a specific item returned based upon command line or template, and also includes a trick to get the local location of the coverart for the song.  I only implemented the few items that I use, not everything that MPRIS provides, so with very little effort this could be expanded and improved upon greatly.  This is hacked together at best...

I've attached the script. My template (.conkySongbird.template):

```

${image [--datatype=CA] -s 50x50 -p 1140,25}
${goto 1210}${voffset -60}[--datatype=AR]
${goto 1210}[--datatype=TI]
${goto 1210}[--datatype=AL]

```

My conky config file:

```

use_xft yes
xftfont Liberation Sans:size=11

update_interval 1
total_run_times 0
double_buffer yes
text_buffer_size 2048

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

minimum_size 1440 80


default_color 171717
draw_shades no

color0 white
color1 white
color2 919FB8

alignment bottom_left
gap_x 0
gap_y -153

no_buffers no
net_avg_samples 2

override_utf8_locale yes

no_buffers yes

imlib_cache_size 0

TEXT
${image ./pix/cwb2.png -s 1440x70 -p -0,15}${image ./pix/cbg.png  -s 64x64 -p 1133,18}${voffset 15}${execpi 10800 ~/.tonky/sh/conkyForecast.py -l USMN0178 -w -t ~/.tonky/conkyForecast.template} ${image ./pix/System/Task_Manager.png -s 64x64 -p 270,18}${image ./pix/System/Memory.png -s 64x64 -p 470,18}${image ./pix/System/Clock2.png -s 64x64 -p 670,18}${image ./pix/System//wlan100.png -s 70x70 -p 870,10}
${goto 350}${voffset -78}Cpu1:${goto 420}${cpu cpu1}%${goto 551}Hd:${goto 620}${fs_used_perc /}%${goto 750}${time %H:%M}${goto 960}Signal:${goto 1020}${wireless_link_qual wlan0}%
${goto 350}Step:${goto 420}${freq_g}${goto 550}Ram:${goto 620}${memperc}%${goto 750}${time %A} ${goto 960}Bitrate:${goto 1020}${wireless_bitrate wlan0}
${goto 350}${goto 550}Swap:${goto 627}${swapperc}%${goto 750}${time %d. %B}${goto 960}Local:${goto 1020}${addr wlan0}
${goto 686}${voffset -44}${font aClock:style=_Hour:size=30}${color2}${execi 120 python ~/.tonky/sh/conkyClock_h.py}${color}${font}
${goto 686}${voffset -36}${font aClock:style=_Min:size=30}${color2}${execi 60 python ~/.tonky/sh/conkyClock_m.py}${color}${font}
${execpi 10 ~/.tonky/sh/conkySongbird.py --template=~/.tonky/.conkySongbird.template }

```

  The conky theme is the 'Tonky' theme that can be found here:  [http://bigrza.deviantart.com/art/Tonky-Desktop-v0-5-135697944](http://bigrza.deviantart.com/art/Tonky-Desktop-v0-5-135697944)

I've also attached a screenshot with the result.  Hope you enjoy!

Thank you very much work for my Songbird 1.2. But I have this problem: the characther Ñ doesn't work. Some idea?

---

