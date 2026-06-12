---
title: "What is this default media player that opens when I click on files?"
date: 2008-08-30
forum: General Help
---

### Post by PsychedelicWonders on 2008-08-30
Alright what is the name of this default player that opens when I double click on music or a movie?

Where can I download a cool skin for it?

Its too plain right now.

---

### Post by mb_webguy on 2008-08-30
It's called Totem, and I don't believe that it can be skinned.  I personally prefer VLC (which can be skinned, and has a lot of other advantages over Totem), though many people like MPlayer (which can also be skinned, and has some uses in command-line transcoding of video files).

---

### Post by PsychedelicWonders on 2008-08-30
> **mb_webguy said:**
> It's called Totem, and I don't believe that it can be skinned.  I personally prefer VLC (which can be skinned, and has a lot of other advantages over Totem), though many people like MPlayer (which can also be skinned, and has some uses in command-line transcoding of video files).

Well I def want to get rid of this default player then.

I may go with VLC, but first explain command-line transcoding is?

Because I may be editing my own videos in the very near future and if this is a great tool to do so, I will start using that program now and become as familar with it as possible.

I have also heard that Ubuntu Studios is really good... is that a media player and editor that is able to be skinned?

---

### Post by mb_webguy on 2008-08-31
When I say command-line transcoding, I mean using commands in the CLI (command-line interface, i.e. terminal or shell prompt) to manipulate video files -- mux and demux them, encode them into various formats, etc.

Various GUI apps (inlcuding VLC) provide the ability to do this sort of thing, but GUIs by necessity and design do not provide all of the options available in the command line (though VLC has more than most).  If you're going to get serious about creating and converting videos, you may eventually want to use CLI commands.  As an example, here's a tutorial on how to [convert an avi to a dvd]("http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/AVI_to_DVD") using the command line.

I do a lot of work with videos on my computer, and I have MPlayer installed largely to use it in the command line.  However, I use VLC as my default media player, and also use it for a lot of file conversions.  I prefer VLC as the default media player because it has more options useful in playing media, it plays most file formats (including some rather obscure ones) without requiring any external codecs, and I like the interface better than that of MPlayer (which uses a separate video window which I hate).  It's default interface isn't necessarily that attractive, but it has some very [nice skins]("http://www.videolan.org/vlc/skins.php") (especially the WMP11 skin).

Of course, MPlayer will play most files as well -- as long as you have the codecs installed.  And it is also [skinnable]("http://www.mplayerhq.hu/design7/dload.html") (though none of the skins I've tried get rid of the annoying detached video window).

---

### Post by PsychedelicWonders on 2008-08-31
Good arguement, you sold me on VLC.

So how do I go about getting it installed, getting new skins for it and then making it my default media player?

---

### Post by kostkon on 2008-08-31
> **PsychedelicWonders said:**
> So how do I go about getting it installedYou can do it from *Applications -> Add/Remove*
> **PsychedelicWonders said:**
> getting new skinsFrom its website, I assume.
> **PsychedelicWonders said:**
> for it and then making it my default media player?*System -> Preferences -> Preferred Applications*

---

### Post by mb_webguy on 2008-08-31
You might also want to take a look at [this]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_VLC_Media_Player"), especially if you want to set VLC to play dvds.

---

### Post by PsychedelicWonders on 2008-08-31
alright everything is going along smoothly, I'm working at moding the dvd player and got to this point...

Replace the above line with one of the following: 
1. (all you really need) 
   Exec=vlc %f
2. (recommended settings from ubuntuforums for better dvd playback) 
   Exec=vlc --vout-filter deinterlace --deinterlace-mode blend --volume 512 %f
3. (recommended settings from ubuntuforums for better dvd playback and automatic full screen playback) 
   Exec=vlc --vout-filter deinterlace --deinterlace-mode blend --volume 512 --fullscreen %f

I did suggestion #3.  Is that alright?

Does it really matter?

I figured #3 seems like the one with the most bells and whistles and automation.

---

### Post by PsychedelicWonders on 2008-08-31
Alright everything seems to be installed and I verified the dvd player is set as the default via their walk-thru.

Now I tried to make VLC my main player by default under system>preferences>preferred applications

And the only thing listed is 

Rhythmbox
Totem

So how do I get vlc listed under that menu?

---

### Post by mb_webguy on 2008-08-31
There should be an option of "Custom", which lets you type in the command.  Type "vlc" in the text box (or in my case, "vlc --volume 384", since I want the volume to be initially set at 384/1024, or 3/8 of full volume).

As for which command to use for the vlc-dvd.desktop file, it just depends on whether you want it to start fullscreen or not.  Deinterlacing does make dvds look better, so you definitely want that.  The volume line depends on your computer volume settings and personal preference.

As for skins, the [VLC website]("http://www.videolan.org/vlc/skins.php") has instructions on installing them.  To have VLC start using the skinned interface, open VLC and go to Settings->Preferences, then Interface->Main Interfaces, and in the Interface Module select "Skinnable Interface".  Save your preferences, then close and reopen VLC.  You should now be looking at the (moderately unattractive) skinned interface.  Right-click somewhere around the border, and choose Select Skin, and pick the skin you downloaded (assuming you put it in the correct folder).

Of course, while the skinned interface can look very nice, it comes at a price.  You lose easy access to some of the nicer features, such as found on the Extended GUI (particularly the contrast and brightness controls, which I've seen on few other media players and come in extremely handy when a movie or scene is a bit too dark to make out details).  Of course, if you want to use these features, just right-click somewhere on VLC and choose Switch Interface->wxWidgets.

---

### Post by PsychedelicWonders on 2008-08-31
When I do custom, do I want to click "run in terminal"?

I like the 3/8 volume idea, I will use that code.

but say I want it a little higher... should I do like 550 or so to have it a little over half volume?

---

### Post by kostkon on 2008-08-31
> **PsychedelicWonders said:**
> When I do custom, do I want to click "run in terminal"?
No.

---

### Post by mb_webguy on 2008-08-31
> **PsychedelicWonders said:**
> When I do custom, do I want to click "run in terminal"?

I like the 3/8 volume idea, I will use that code.

but say I want it a little higher... should I do like 550 or so to have it a little over half volume?

Like I said, it's personal preference.  On my system, the default sound level in VLC was a bit loud, and I got tired of turning it down a bit every time I started the program.  I played around with it a bit, and decided that 384 (which as I said is 3/8 max volume, since VLC internally uses 1024 as max volume) was about right for me.  (And just so you know, the wxWidgets interface and possibly the skinnable interface uses 512 rather than 1024 as the max volume, so you can only make it so loud using the volume slider.  If that's not loud enough, the hotkey Ctrl-Up will let you go all the way to 100%.)

You might also want to play around with the equalizer.  On my laptop, the Headphones preset sounds wonderful.  Unfortunately -- and this is one of my few gripes about VLC -- the equalizer is currently not persistent (even though there is an option in both the Preferences the command-line to set it), so you have to select it every time you open VLC.  This is a well known bug/deficiency, and will probably/hopefully be fixed/implemented in future releases of VLC.

---

### Post by PsychedelicWonders on 2008-09-01
Alright I hit custom, entered vlc and did not click "run in terminal"

I've logged out, rebooted, everything and still vlc isnt my default player?

---

### Post by mc4man on 2008-09-01
> Alright everything seems to be installed and I verified the dvd player is set as the default via their walk-thru.
If you did that then vlc should be default. What happens when you insert a dvd?

> Now I tried to make VLC my main player by default under system>preferences>preferred applications
Not where the setting is made. You set, change in file management -> media
(needs to be enabled in main menu -> preferences or go places -> home folder -> edit -> preferences -> media.

While the method you followed is a perfectly good way (I use similar to enable additional player like mplayer, smplayer, ect. the launch command is wrong, it should be set to vlc %m.

---

### Post by PsychedelicWonders on 2008-09-01
Alright I got to the place you told me, but when I try to change CD Audio & music player defaults, VLC is not listed to be selected?

DVD player is set to VLC though.

I have not tried a dvd yet no.

---

### Post by mc4man on 2008-09-01
> Alright I got to the place you told me, but when I try to change CD Audio & music player defaults, VLC is not listed to be selected?
You only added vlc for dvds -  > x-content/[COLOR="Red"]video-dvd[/COLOR]=vlc-dvd.desktop;totem.desktop;

Now while it would be  possible to add vlc as a default cd... player I'm pretty sure vlc would only open upon cd insert but not start playing. You'd have to find a launch command that caused autoplay (vs. autostart)

The only music player I've found that can be set as a default and **autoplay** upon media insert is Amarok. (haven't tried vlc though

edit : part of the problem (autoplay for cd's) is in 8.04 the location of cd files has changed from gutsy. It's now .gvfs/ cdda mount on scdx. This doesn't 'jive' to well with available launch comm. to cause autoplay. (again not meaning autostart

---

### Post by PsychedelicWonders on 2008-09-01
> **mc4man said:**
> You only added vlc for dvds -  

Now while it would be  possible to add vlc as a default cd... player I'm pretty sure vlc would only open upon cd insert but not start playing. You'd have to find a launch command that caused autoplay (vs. autostart)

The only music player I've found that can be set as a default and **autoplay** upon media insert is Amarok. (haven't tried vlc though

edit : part of the problem (autoplay for cd's) is in 8.04 the location of cd files has changed from gutsy. It's now .gvfs/ cdda mount on scdx. This doesn't 'jive' to well with available launch comm. to cause autoplay. (again not meaning autostart

I'm mostly looking for a program that will play music files already on my computer, and can be skinned but I would like a program like Windows Media Player that kind of does it all.

Ideas?

So do I not want VLC?

---

### Post by mc4man on 2008-09-01
For a music player vlc is less than ideal though some may like it. Amarok suits me fine, may not others. You should try several players and use the one you like best.
Banshee, Rhythmbox, Exaile, XMMS, Audacious, Songbird to name a few others

---

### Post by PsychedelicWonders on 2008-09-02
Honestly that is jsut too many choices.

Can anyone suggest an all around media player to set as my default?>

Should I go with Armarok?

How do I delete this VLC thing then?

---

### Post by mc4man on 2008-09-02
> How do I delete this VLC thing then? 
There's no reason to delete vlc.
Rhythmbox is installed by default - try it and see if you like it.
If not then you'll have a better idea of what your looking for.

Personally i think Amarok is great. I don't use playlists, collections and such. All my music is stored in folders and subfolders as artist, albums, with some misc. mixes and loose files laying around.

So I use Amarok because I can control it thru right click actions (load and play, append, queue) and a couple of custom file associations (double left click). (executed on folders and files directly.
 Also because it can autoplay cd's.

I never even see the main gui, playlist box which suits **me** fine.

---

### Post by PsychedelicWonders on 2008-09-02
I would like to be able to set up playlists etc.

What program allows me to do that?

---

### Post by mb_webguy on 2008-09-02
If you want to play music, I second Amarok.  Since you've been saying "media player", we've all been thinking you've been wanting something to play videos and music.  VLC will play almost anything, and is particularly great for videos, but it's not a specialized music player and doesn't have the advanced library features you would expect of one.  If you want to play music and have an easy-to-organize collection with playlists, you can't do much better than Amarok.

BUT... Amarok is just a music player, though very good one.  It will play many formats of music, but it won't play videos.  If you want to play videos (or music, since it will play most media formats), VLC is still the best, IMO.

---

### Post by PsychedelicWonders on 2008-09-02
alright, what should I type to insall Armarok?

I have an HTPC, so I would really like a program that does it all like Windows media player... there isnt anything that will be default of everything, be able to be skinned and have playlists etc?

I'm asking a little too much for a single program?

---

### Post by mb_webguy on 2008-09-02
If it's an HTPC, you need to look into Mythbuntu.  It's a version of Ubuntu specialized for HTPCs using MythTV.  While I think it might use VLC to play media, it also handles your media library.

---

### Post by PsychedelicWonders on 2008-09-02
So do I delete Ubuntu and install Mythbuntu?

Or is it a program I add onto Ubuntu?

---

### Post by mb_webguy on 2008-09-02
Weeellll...  If all you're going to use the computer for is as an HTPC, then I think I'd probably do a fresh install, as there's a lot of stuff in Ubuntu that's unnecessary for an HTPC.

On the other hand, you could just install the mythbuntu-desktop package ("sudo apt-get install mythbuntu-desktop"), which will add all of the Mythbuntu packages to your current Ubuntu installation.

You can read all about it at the [Mythbuntu web site]("http://www.mythbuntu.org/").

---

### Post by PsychedelicWonders on 2008-09-02
No I am def going to be using it for many other things other than just an HTPC, so I suppose installing the desktop package is best for me.

Thanks.

Once I install it using that code, how will I find the media player?

Do I need to go to file>home folder>edit>prefernces>media again to set it as default?

---

### Post by mb_webguy on 2008-09-03
Ooookaaayyy....

I think we're having a slight communication problem, here.  Watching movies and listening to music on a PC doesn't make it an HTPC.  If you're hooking it up to one or more televisions and a nice set of speakers so that the computer takes the place of things like the DVD player and stereo, then it's an HTPC.

If you're just going to use the computer as a computer, and occasionally watch movies or listen to music, then you need a multimedia player or two, but not an HTPC system like MythTV.  There are a number of media players available for Linux, and which one(s) are right for you depend on your needs and personal preference.

[LIST]
[*]VLC -- Multimedia player that will play almost any audio and video format, has lots of nice and powerful features, has some limited playlist capability, and is skinnable, but lacks a media library browser
[*]Totem -- The default multimedia player for Ubuntu, will play a wide variety of audio and video formats using external codecs and has limited playlist capabilities, but no media library
[*]MPlayer -- A multimedia player which can play a wide variety of audio and video formats using external codecs, has some playlist capability, can be run from the command line with no GUI, and has many command-line options that make it useful for encoding video
[*]Rhythmbox -- The default music player for Ubuntu, has a media library and full playlist functionality, and can play the most common audio formats (but not video)
[*]Amarok -- A full-featured music player with full media library and playlist features, which can play most audio formats (but not video)
[/LIST]

Basically, there are some really nice music players available with media libraries and full playlist support, and then there are some really nice multimedia players that will play audio and video, but have no media library and only limited playlist support.  An then there are HTPC suites that turn your computer into a combination DVD player, DVR, and stereo, but do so at the expense of using your computer *as* a computer while you're using it as a home theater center.

Linux software tends to be more specialized than Windows software, because the people who create it tend to create it initially for themselves to fulfill a specific need.  There are very few Linux applications that do everything, but many that do one thing very well.  This means that a multimedia player application on Linux will probably do a great job at playing media, but might not have all of the extra features that commercial Windows applications might add to them.  Likewise a music player will probably do a really good job at playing music and organizing your music library, but probably won't be able to play video.  It's not necessarily better or worse than the way things are in the Windows world, it's just different.

Which means that there's probably not one particular media player to suit all of your needs, but there is probably a combination of two or three of them that will.

---

### Post by PsychedelicWonders on 2008-09-06
Alright I am  eventually going to get into Mythbutuntu, but for now just want a media player that can be skinned.

I think Amarok is what I need.

How do I go about getting this installed?

Thanks for the help.

---

### Post by mb_webguy on 2008-09-07
Type "sudo apt-get install amarok" in the terminal.

---

### Post by PsychedelicWonders on 2008-09-07
awesome, seems to be downloading now.

How do I make this my default player when I click on a song on my computer?

Where can I go to get skins?

Does this Amarok also come with a mini-visual screen like the default player or windows media to have some trippy stuff playing?

---

### Post by mb_webguy on 2008-09-07
Amarok isn't skinnable, as far as I know, though it is customizable as far as colors and fonts.  If you're using the KDE desktop environment, Amarok should follow your KDE theme.

Amarok has several visualization plugins, which you can select from the Tools menu.

To use Amarok to open music files, right-click on a music file and select Preferences, the Open With tab, and select Amarok.

---

### Post by PsychedelicWonders on 2008-09-07
hmm.  I was really looking for a program that I could give a wild and cool skin.

What program will allow me to skin it, have playlists and will play all music files on my computer?

---

### Post by mb_webguy on 2008-09-07
> **PsychedelicWonders said:**
> hmm.  I was really looking for a program that I could give a wild and cool skin.

What program will allow me to skin it, have playlists and will play all music files on my computer?

Rolling Stones: "You can't always get what you want"
Meatloaf: "Two out of three ain't bad"

I can suggest several applications (e.g. VLC, MPlayer, etc.) with the first and third features in that list, and several (e.g. Amarok, Rhythmbox, etc.) with the second and third, but I'm afraid I'm coming up blank on one that has all three.

---

### Post by PsychedelicWonders on 2008-09-07
haha alright, so if I was just looking for one that can be skinned with really cool skins and will play all music on my computer... which way am I leaning now?

Lets take out the playlists (I mean I can still choose so many songs and allow them to auto-play one after another right?)

---

### Post by 3rdalbum on 2008-09-07
Audacious has playlists and skins, and should play all music files.

Are skins really that important to you??

---

### Post by PsychedelicWonders on 2008-09-07
yeah I really want them to have a skin because there are some really cool skins to get in general.

What about this Audacious?  Seems to have all 3...exactly what I'm looking for... how do I go about getting this installed?

---

### Post by MaxIBoy on 2008-09-07
I'd also like to suggest Audacious as a good player for sound files (not video.) It's very minimalistic (takes up very little screen space,) but it's pretty full-featured. It's also skinnable.

---

### Post by Lacrimstein on 2008-09-07
sudo apt-get install audacious

^_^

---

### Post by PsychedelicWonders on 2008-09-07
alright, now that seems to be installed.

So how do I go about getting it set as my default music player and then find some cool skins for it?

---

### Post by Lacrimstein on 2008-09-07
1) Same way as for Amarok (except select Audacity)
2) Google it! There is plenty, plus (if my memory serves me correctly) it supports WinAmp skins.

---

### Post by PsychedelicWonders on 2008-09-07
I just know how to right click and open with... but I want to sent the main preferences to Audacious as the default... where do I do that?

This seems to be what I'm looking for, thanks.

Are playlists easy to set in this program?

---

### Post by PsychedelicWonders on 2008-09-07
also where do I download the skin file to so that I can selete it?

---

### Post by Lacrimstein on 2008-09-07
Go to System->Preferences->Preferred Applications, click on Multimedia tab, select Audacious from the list, or, if its not there, enter "audacious" in the textbox. That should do it.

As for the playlist, there is a button on the player that opens the playlist window; You can drag+drop files into it, and save/load playlists.

Also, you should do the following if you want to be able to play mp3's:

sudo apt-get install audacious-plugins-extra

as for the skins: Right-click on the player, select Preferences..., and in Appearance you should be able to drag-and-drop the themes.

Finally, Audacious did not work with PulseAudio for me, so you may have to change it to ALSA in Audio (also in Preferences)

---

### Post by PsychedelicWonders on 2008-09-07
hmm, as you can see, I have done what you told me, but it still opens with the Ubuntu default player when I try to play a song?

Also, it seems that I cant drag this player from workspace to workspace... what is limiting me from doing so?

As for the skins, here is a complete screen shot of what I'm working with.

The intruder.wal is the file, i opened it and you see what files are inside of the main file.

Now do I drag and drop the entire file or a file inside of the file?

Regardless what I do, I've tried dragging them into the skin section in apperance and nothing happens?

---

### Post by PsychedelicWonders on 2008-09-07
alright I found another thread where someone suggested putting the skin files here:

/usr/share/audacious/Skins

I found it, dragged and dropped the two main skin files into that folder, right clicked preferences on the player went to appearance and they are not under the skin section?

Is it because I downloaded the wrong kind of file?

It was a winamp file to begin with.

---

### Post by MaxIBoy on 2008-09-07
That's odd, a winamp skin should work.


Could I have a screenshot of that skin folder plus a screenshot of the preferences window?

---

### Post by PsychedelicWonders on 2008-09-07
here you go...

---

### Post by Lacrimstein on 2008-09-07
I have found that some themes do not work, and some do. This one, for example, does:

[http://gnome-look.org/content/show.php/Vortigo+++(+3D%2BVU%2BBeryl%2BDock+)?content=55440](http://gnome-look.org/content/show.php/Vortigo+++(+3D%2BVU%2BBeryl%2BDock+)?content=55440)

---

### Post by MaxIBoy on 2008-09-07
Sorry, that wasn't the preference window I meant.


If you have to, post multiple shots so I can see the entire list of skins.



Have you tried reloading the skins?

---

### Post by PsychedelicWonders on 2008-09-07
ok here you go...

Now for some reason when I right click and try to open with audacious, it brings up a screen that wants me to open a file... everything is in the screenshot...

---

### Post by MaxIBoy on 2008-09-07
/usr/bin/audacious.


Also definitely gnome-look.org is great for finding skins and stuff.

---

### Post by PsychedelicWonders on 2008-09-07
> **MaxIBoy said:**
> /usr/bin/audacious.


What exactly are you telling me here?

---

### Post by MaxIBoy on 2008-09-07
That screen that wants you to open a file: (assuming it popped up when you clicked a sound file not when you clicked on audacious itself) go to /usr/bin/audacious.

---

### Post by PsychedelicWonders on 2008-09-07
I set it to what you told me, and now it still opens, but this time right to 

/usr/bin

I've tried it a couple of times, closed out of audacious, and opening a file via open with and it keeps prompting me.

I want to get this issue cleared up, but I also want to get this audacious set as my default player so I can just double click on any music file I want.

---

### Post by MaxIBoy on 2008-09-07
Try right-clicking the file, go to "open with." Note that you'll need to do this separately for each file extension (once for mp3, once for ogg, once for wav, you get the idea.)

---

### Post by mc4man on 2008-09-07
> audacious set as my default player so I can just double click on any music file I want.

for that you would pick one example of a file type (mp3,flac,whatever) and r. click -> properties -> open with.
At that point the progression is - look in the first list, if not there go **add**  and look in that list. If not there use custom command. From there either browse to audacious or enter probably just audacious or audacious %U  (not installed here

That will open audacious when you d.click on each filetype you've set this way with the default launch command. If you don't see it in the first list the first time you set a file type it'll probably be there afterwards for others.



What may be also useful to have is some r. click nautilus actions. They work on files and files inside folders, subfolders. There are 3 useful ones I saw

see here, some available commands in post 8
[http://ubuntuforums.org/showthread.php?p=5282367#post5282367](http://ubuntuforums.org/showthread.php?p=5282367#post5282367)

It's also good to set a player as a default choice for cd audio. Setting audacious as up as default will be easy, though it may or may not start autoplaying the cd. (autostart vs. autostart and play
Will give it a try tomorrow

---

### Post by PsychedelicWonders on 2008-09-07
I guess I'm confused.

I've followed everything you guys told me to and it is still opening the default ubuntu player instead of audacious.

I've right clicked, used, "Open with" and chosen audacious several times when it prompts me what file to open.

Nothing has changed, audacious is not the default.

Why is this so difficult?

---

### Post by mc4man on 2008-09-07
While i don't particularly like audacious you can make it work fairly well with everything but auto playing audio cds

I think your using 'default player' too broadly
There are 2 ways to to define 'default' (in this instance

First as the default player for any **particular filetype** (mp3, wma, wav, flac, ect. (**known as file association** 
That is only useful for the double left click on an individual file
To do that you do as described above, take **one** example of a particular filetype, right click on it -> **properties** -> open with -> yada yada

The result then is when you d. left click on any file of the same type audacious will open, create a **new playlist and play.** **Period** . If you d. l. click on another file the same thing. In other words, 1 song only at a time

If you wanted to d. l. click on files and have them added to existing playlist you'd need to create a 'custom' file association that used a different launch command.
To avoid confusion won't describe how now.

The other default is as the default for audio cd's, ie. you put a cd in the drive and the player opens.

Audacious appears to be unsuitable for that, at best inserting a cd will open audacious and a file box opens. Even if it auto finds the cd the tracks will not be loaded into a playlist. ( and are not recognized properly) See screen 1

Choosing 'audio cd from the left side will reload the files properly (screen 2) but you'd still need to 'shift/select all of them before clicking 'open'. see screen 3

The best way to play an audio cd in audacious is from the gui, right click on bottom of audacious or playlist box -> Plugin service -> add cd.


If you want to be able to add a folder with all tracks inside and play, set it up like this

R. click on a folder -> open with audacious
If audacious is **not available there** choose  -> open with other application
At this point you'll probably see audacious in a list, **ignore**
Choose - Use a custom command  
Enter audacious as command
From that point on audacious will be available immediately from main r. click -> open with menu.

Again the behavior is the same as the single file,  audacious will create a **new play list**, load all the songs in the folder in the order they're listed and start playing.


note: **For future use** -  The custom command box is where you can alter the launch command to affect how audacious behaves in **that situation**  - the 3 decent choices are in the nautilus action thread (removing the %M)
In other words **any of those commands** can be used as the command for both 'file associations' and for 'opening folders' as well as nautilus actions 

[http://ubuntuforums.org/showthread.php?p=5282367#post5282367](http://ubuntuforums.org/showthread.php?p=5282367#post5282367)

---

### Post by PsychedelicWonders on 2008-09-07
Alright I want to be able to double click any music file at any point and have it open up in Audacious.

I dont want to have to right click and open with Audacious every time because I have thousands of songs.

Is there no way to set it that when you double left click on a file audacious automatically opens and becomes your music player?

Not this default Ubuntu one that currently opens?

---

### Post by mb_webguy on 2008-09-07
Right-click on a music file, and select Properties.  Go to the Open With tab and click the radio button next to Audacious, and close the window.

---

### Post by PsychedelicWonders on 2008-09-07
YES!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!


SUCCESS!!!!!

haha, finally, thanks guys.

Now I just gotta figure out how to apply the skins I have downloaded...

any ideas on that one?

Also, why doesnt Audacious allow me to drag it to another workspace?

---

### Post by PsychedelicWonders on 2008-09-08
still not able to apply skins.

Also, when I go to create new playlist, nothing opens for me to create one?

Anyone know what I'm doing wrong?

---

### Post by mc4man on 2008-09-08
> Also, why doesnt Audacious allow me to drag it to another workspace?
preferences -> appearances , check box 'show window manager decoration'
> Also, when I go to create new playlist, nothing opens for me to create one?


In the detached  playlist editor box click the add button or with focus on it or the player, 'f' on keyboard

---

### Post by PsychedelicWonders on 2008-09-08
Alright, got the drag to other windows down, thanks,

But where exaclty do I find the Detatched playlist Edititor?

I hover my mouse on audacious, and hit F, but it seems to just get an "Add Files" box... is this what you are referring to?

How do I set up individual playlists?

---

### Post by mc4man on 2008-09-09
> But where exaclty do I find the Detatched playlist Edititor

see screen, click on what's inside circle


> How do I set up individual playlists? 

Don't use this player but ck out buttons on the playlist editor, add, list seem to be about right. To add to current list use add, use list to save ect, misc. to modify.

---

### Post by PsychedelicWonders on 2008-09-09
ahh alright figured out the playlist thing.

Thanks.

For some reason, some of the songs only list the band and not the name of the song... what do I need to edit in the song to make the songs show up?

See the screenshot...

---

