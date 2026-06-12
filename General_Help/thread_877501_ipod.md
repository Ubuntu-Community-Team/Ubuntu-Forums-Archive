---
title: "ipod"
date: 2008-08-01
forum: General Help
---

### Post by Th3Professor on 2008-08-01
If someone purchased a brand new ipod nano (current version, "3rd gen" I suppose), and the only operating systems they ran were Linux and Unix... could they transfer audio/video back and forth?

Or, would they be required to use either Windows or Mac?

I've seen some ipod-related posts in here, so it looks like it works... but does it work right out of the box? Or does the person have to initially set up the ipod on either a win or mac OS, prior to using it with *nix?

Are there any important points one should be aware of prior to using ipod with a *nix-only computer?

Are there any common issues that arise from using ipod with *nix that one should be aware of?

Thank you!

---

### Post by dark_phantom on 2008-08-01
I have an ipod video color (4th or 5th version, I forget), but I can upload songs just like any other external hard drive.  Or if you need iTunes to transfer your vids/songs then you can use wine and do it that way.

---

### Post by Th3Professor on 2008-08-01
Are ipods limited to itunes for transferring audio/video back and forth?

---

### Post by dark_phantom on 2008-08-01
No, I don't use itunes at all.

---

### Post by Th3Professor on 2008-08-01
okay cool...

Someone who owns an ipod said you have to have either windows or mac to move any audio/video files back and forth, so that left me skeptical about it.

I'll guess that you are not required to use itunes for all the ipods (not just ipod video).

Is it basically just "plug n play"?

Like, you hook the ipod up to the computer, say one running Ubuntu, and you simply move audio and/or video files back and forth.

Is any software required?

I'm concerned that there will be a conflict in either format, drivers, or similar.

As far as format, there's the file system (win-based or mac-based) and actual file formats (I don't know the actual audio/video formats it uses), I'm hoping both of those would be compliant between an ipod nano and *nix system (at least Ubuntu).

Thanks again! :-)

---

### Post by fhmanas on 2008-08-01
The apps in linux do hook up with the ipod, but I have yet to see an app which will actually sync with the ipod.  Meaning, transfer to and fro your ipod will be strictly a manual thing.  Also, I haven't successfully created a playlist and transferred to the ipod.

---

### Post by Th3Professor on 2008-08-02
> **fhmanas said:**
> The apps in linux do hook up with the ipod, but I have yet to see an app which will actually sync with the ipod.  Meaning, transfer to and fro your ipod will be strictly a manual thing.  Also, I haven't successfully created a playlist and transferred to the ipod.

Okay, these are good to know things...

So manually transferring audio/video is literally 1 file at a time, where syncing is all at once?

Can you manually transfer all at once?

That's not incredibly important, as long as they can go both ways (and actually work on the ipod).

If ipod doesn't have a playlist once you transfer all the audio and video over, how do you access the "list" to "play"? (...confused on taht one...)

Or do you mean strictly play list created on the computer then moved over to the ipod?

Can you still create playlists once the audio/video files are on the ipod, only actually create them directly on the ipod?

Which apps would one use, in linux/ubuntu/etc., to transfer audio/video to and from the ipod?

Thanks again! :)

---

### Post by ubuntu27 on 2008-08-02
This might help you:

[http://www.psychocats.net/ubuntu/itunes](http://www.psychocats.net/ubuntu/itunes)

---

### Post by dentaku65 on 2008-08-02
The ipod nano 3rd generation it works out of the box, but you have to do a little hack described here
[http://ubuntuforums.org/showpost.php?p=4898179&postcount=7]("http://ubuntuforums.org/showpost.php?p=4898179&postcount=7")
Then you can manage the music and other content with your favorite player like amarok, rhythmbox, gtkpod or many others..

Please be sure to have installed the ipod library:
```
sudo apt-get install libgpod3

```
in order to be able to use ipod.

---

### Post by chitresh4u on 2008-08-02
I got an ipod classic, 6th generation working on ubuntu using gtkpod ... I could transfer music to ipod and copy music from ipod. I think the same can be done for 3rd generation nano. 

I followed the steps as described [here]("http://ronnietucker.co.uk/blog/2008/01/18/black-80gb-ipod-classic/"). Though I have a little problem with photos. I could view them but I cannot successfully transfer photos to ipod.

---

### Post by Th3Professor on 2008-08-03
how about floola?

it looks like floola has the most all-around features, including photo and video transfers between the devices.

---

### Post by mb_webguy on 2008-08-03
> **Th3Professor said:**
> Okay, these are good to know things...

So manually transferring audio/video is literally 1 file at a time, where syncing is all at once?

No, syncing means that the iPod and your computer automatically updates your music collection as soon as you plug in the iPod.  You cans still transfer multiple files at once.  You simply have to do it manually, rather than it automatically happen when you plug in the iPod.

> If ipod doesn't have a playlist once you transfer all the audio and video over, how do you access the "list" to "play"? (...confused on taht one...)

A playlist is a list of songs you create that you can select to play rather than simply playing from the entire list of songs on the iPod.  For example, suppose you have a few hundred songs on your iPod, but only a couple of dozen of those songs are jazz, and sometimes you just want to listen to jazz.  You can make a playlist of just those songs.  iTunes lets transfer playlists you've created in iTunes to your iPod.

> Which apps would one use, in linux/ubuntu/etc., to transfer audio/video to and from the ipod?

Amarok might be best the best media player to use with an iPod, and allows you to sync and create playlists.  gtkpod is a simpler and specialized program specifically for managing your iPod.  If you want to transfer videos to your iPod Video, you'll need gtkpod.  Rhythmbox (which comes preinstalled with Ubuntu) works well with older iPods, but I don't know how well it works with the newer ones, and to my knowledge doesn't allow syncing or playlist creation.  Of course, you can also use Wine to install the Windows version of iTunes, if you want.

Here are a couple of resources that might be helpful:
[Using an iPod with Ubuntu]("https://help.ubuntu.com/community/PortableDevices/iPod")
[Using an iPhone or iPod Touch with Ubuntu]("https://help.ubuntu.com/community/PortableDevices/iPhone")

---

### Post by thrice upon a time on 2008-08-03
When did iTunes become useable under wine? :confused:

---

### Post by mb_webguy on 2008-08-03
> **thrice upon a time said:**
> When did iTunes become useable under wine? :confused:

Don't know when, but it seems to be working for people...
[URL="http://www.wine-reviews.net/applications/itunes-73-on-linux-with-wine.html"]
http://www.wine-reviews.net/applications/itunes-73-on-linux-with-wine.html[/URL]
[http://mikesubuntu.blogspot.com/2007/10/itunes-great-with-wine-yep-its-true.html]("http://mikesubuntu.blogspot.com/2007/10/itunes-great-with-wine-yep-its-true.html")

---

### Post by Th3Professor on 2008-08-03
> **mb_webguy said:**
> You cans still transfer multiple files at once.  You simply have to do it manually, rather than it automatically happen when you plug in the iPod.

That's not a bad deal. While syncing has some great advantages, not having that feature, yet still having the ability to transfer multiple audio/video files at once, still seems pretty effective. It doesn't seem like it'd be some kind burden.

If someone had to transfer... one... file... at... a... time... then, wow, that would be pretty crazy. Transferring a thousand (or thousands) of songs? ha! ;)


> **mb_webguy said:**
> You can make a playlist of just those songs.  iTunes lets transfer playlists you've created in iTunes to your iPod.

Could someone create playlists on the ipod?

Or optionally, perhaps better, could someone create playlists in one of the *nix apps?

> **mb_webguy said:**
> Amarok might be best the best media player to use with an iPod, and allows you to sync and create playlists.

Ah, that answers the playlist question... though you can actually sync with it?

I was under the impression syncing only works with itunes, though if that's not true then that's great news.

> **mb_webguy said:**
> gtkpod is a simpler and specialized program specifically for managing your iPod.  If you want to transfer videos to your iPod Video, you'll need gtkpod.

Does ipod nano (or I suppose any ipod) only support 1 audio file format and 1 video file format? Any ideas which ones are supported?

If someone gets an ipod nano, 3rd gen, with smaller storage (the "4GB: 1,000 Songs" version), how many video files could they place on it?

Maybe, at least 1 full-length movie (approx. 2 hrs.)?

(I'm not sure the video format, which I'm guessing might determine possible limitations in it's lossy compression rate.)


> **mb_webguy said:**
> Rhythmbox (which comes preinstalled with Ubuntu) works well with older iPods, but I don't know how well it works with the newer ones, and to my knowledge doesn't allow syncing or playlist creation.

Good to know as a back-up/alternative.

> **mb_webguy said:**
> Of course, you can also use Wine to install the Windows version of iTunes, if you want.

Wine seems a bit sketchy with some applications, though on the other hand it does work really well with others.

Any idea on how wine works, in effectiveness (like, "solid" vs "buggy") with ipod/itunes?

There's also the alternative of running VMware, or similar.

If a member of the family, or a friend - someone I purchase an ipod for as a gift, for example - if they run only Linux or Unix (*bsd or sysv), yet if they don't want to install Windows, either at all or within a vmware-type app, and would like to use itunes, then it sounds like wine would be the way to go.

On the other hand, if I ever decide to actually purchase an ipod for myself ;) - I'm currently running various *nix systems, with all kinds of pseudo "cross-over" applications - it looks like it would all work quite well. My Ubuntu Studio set-up appears to have some default ipod apps installed, although I could just install whatever else would be needed. I'm running VMware server, as well, with the old WinXP. Though...

Could someone use hardware/devices, such as plugging an ipod (usb or firewire?) into a computer, along with a vmware server running winxp?

On another note, can Mac OS X run inside *nix, such as through vmware?

Or could one actually dual-boot between Mac & *nix on a "non-mac" computer?

> **mb_webguy said:**
> 
Here are a couple of resources that might be helpful:
[Using an iPod with Ubuntu]("https://help.ubuntu.com/community/PortableDevices/iPod")
[Using an iPhone or iPod Touch with Ubuntu]("https://help.ubuntu.com/community/PortableDevices/iPhone")

...will definitely check out that 1st link...

A colleague recently received an iphone (for work), it is pretty slick!

There seem to be several programs that work with ipod with varying degrees of functionality. A previous reply in this thread had a link to a page comparing the different apps... of those apps the one that seemed the most promising for all-around functionality seemed like "floola".

Any ideas how well "floola" works with *nix+ipod?

The webpage comparing the apps says that floola can, for "transfer features", do the following:

[LIST]
[*]Copy music
[*]copy videos
[*]copy "smart" playlists
[*]copy album artwork
[*]extract drm-free music
[*]extract drm-free videos
[*]extract playcounts
[*]extract playlists.
[/LIST]
A couple others do all of these too, from that page at least, like gnupod, though floola appears to also have the following "miscellaneous" features:


[LIST]
[*]download podcasts
[*]rebuild ipod database
[*]portable
[*]6th gen firmware
[*]photo support
[/LIST]
The other apps didn't seem to have as many of these features, including gnupod or any other *nix-based app.

Anyway, another question came to mind after doing a little digging into various pros/cons of ipods...

If someone had an ipod without an extended warranty - that is, without a warranty beyond the default one that comes with purchase - and if the battery dies, which appears irreplacable...

Would they be better off having someone replace it for them or actually getting a new ipod?

How many months are ipod batteries (such as ipod nano) known to last before they finally lose their rechargable capacity?

Thanks again! :)

---

### Post by Th3Professor on 2008-08-04
bump hoping for suggestions, recommendations, etc.

thank you!

---

### Post by pi.boy.travis on 2008-08-04
You could use Rockbox, which is an open source firmware replacement for iPod, etc.

Check it out!

[http://www.rockbox.org/](http://www.rockbox.org/)

---

### Post by Seti on 2008-08-04
How about a howto on formatting an iPod if its disk isn't FAT?

???


:confused:

---

### Post by Seti on 2008-08-04
OK, scratch that. I am not wasting another minute monkeying around with this stupid thing. I have this nice little RCA Lyra, and it suits my needs just fine. It plays all my mp3's perfectly, and holds a charge very well. As far as I am concerned, Mac, iPhone, iThis and iThat and all things Apple are garbage. They are nice little toys unto themselves, but forget about having an easy time getting them to operate with other computers/devices. 
Tomorrow I am returning this iPod to the person who gave it to me. 
Not interested. I'd like to kick Steve Jobs in the balls right now for the 2 hours I just wasted with his fancy little **** gadget.

---

### Post by Th3Professor on 2008-08-05
Okay... anyway...

> **pi.boy.travis said:**
> You could use Rockbox, which is an open source firmware replacement for iPod, etc.

Check it out!

[http://www.rockbox.org/](http://www.rockbox.org/)

Sure thing... will definitely check that out. :D

Are you familiar with floola?

Does rockbox work well and without any hitches/problems on Ubuntu?

---

### Post by /////// on 2008-08-05
I have an iPod Video 30GB Gen 5.5 and I can easily add playlists and put songs on with Rhythmbox Music Player (Should come pre-installed with Ubuntu). Putting videos on with Ubuntu, you have to use gtkpod (just download with synaptic). You can just drag and drop videos and music to the iPod, theres no need to put you things on one by one and if nothing works for you, you can always install a Virtual Machine where you can install iTunes. Don't try putting things on the iPod with iTunes in Ubuntu under WINE as WINE doesn't support USB connections, so although iTunes will run fine, it will not detect your iPod.

Hope this helps.

---

### Post by pi.boy.travis on 2008-08-05
> **Th3Professor said:**
> Okay... anyway...



Sure thing... will definitely check that out. :D

Are you familiar with floola?

Does rockbox work well and without any hitches/problems on Ubuntu?

I just copy and paste from my music library on my computer that I manage with Rhythmbox.  Places-Music-Copy-Paste-Done!

Rockbox will work on any OS that supports USB mass storage devices.

I have never used floola.  You only need a file manager to use Rockbox.

Hope this helps!

---

### Post by dentaku65 on 2008-08-07
> **pi.boy.travis said:**
> I just copy and paste from my music library on my computer that I manage with Rhythmbox.  Places-Music-Copy-Paste-Done!

Rockbox will work on any OS that supports USB mass storage devices.

I have never used floola.  You only need a file manager to use Rockbox.

Hope this helps!

The ipod nano 3rd gen is not (yet) compatible with Rockbox, due to different hardware.

---

### Post by Th3Professor on 2008-08-07
i saw a time table for the release dates of each generation of all the different models of ipods, it looks like - if they stick with the pattern they've used so far for release dates - they might be coming out with a 4th gen (at least 4th g. nano) sometime soon (next couple/few months).

does anybody have any ideas what the word is on the next generation?

this might determine when to purchase one. ...not sure...

---

### Post by LitusMayol on 2008-08-07
I recommend you **Amarok**.

With videos it doesn't works me (yet!) but with audio it run its better. On video... no idea...! :S

Sorry.

---

### Post by Th3Professor on 2008-08-11
So far, it looks like "floola" and "rockbox" might be the best options for apps.

Someone else commented on rockbox working well.

Though, has anybody used floola?

---

