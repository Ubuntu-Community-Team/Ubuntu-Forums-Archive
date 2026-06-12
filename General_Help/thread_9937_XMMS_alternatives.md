---
title: "XMMS alternatives"
date: 2005-01-03
forum: General Help
---

### Post by nocturn on 2005-01-03
After going to some issues, I got XMMS working on Ubuntu.
Now, I've been using XMMS for years now, and I've always loved it, but lately I've been under the impression that development kinda stopped (or is very, very slow).

So I'm looking at alternatives for it, but none that really suit my need.  Ideally, I would like XMMS with GTK2 support and the ability to load newer winamp skins.

I looked at Beep (XMMS fork to GTK2), but it does did not work very well for me.
I wanted to try Rhythmbox, but it  wanted to search through my music directories (which takes forever so I killed it).

Are there any others that I'm not aware of?  I'm not looking for something with indexing capabilities like Rhythmbox.

---

### Post by nocturn on 2005-01-03
[QUOTE=nocturn]After going to some issues, I got XMMS working on Ubuntu.
Now, I've been using XMMS for years now, and I've always loved it, but lately I've been under the impression that development kinda stopped (or is very, very slow).

So I'm looking at alternatives for it, but none that really suit my need.  Ideally, I would like XMMS with GTK2 support and the ability to load newer winamp skins.

I looked at Beep (XMMS fork to GTK2), but it does did not work very well for me.
I wanted to try Rhythmbox, but it  wanted to search through my music directories (which takes forever so I killed it).

Are there any others that I'm not aware of?  I'm not looking for something with indexing capabilities like Rhythmbox.[/QUOTE]
 I was just looking at Zinf too (seems GTK...)
I'll try it tonight if I find the time.

---

### Post by pmshoop on 2005-01-04
[QUOTE=nocturn]After going to some issues, I got XMMS working on Ubuntu.


Ok question, I'm tryin real hard to get XMMS up and running on Ubuntu.  What am I missing?  I've tried installing all dependencies and XMMS but I can't ./configure anything... keep getting 'no acceptable C compiler found at $Path'.  I am trying to install through a root terminal.  Any ideas?

---

### Post by nocturn on 2005-01-04
[QUOTE=pmshoop][QUOTE=nocturn]After going to some issues, I got XMMS working on Ubuntu.


Ok question, I'm tryin real hard to get XMMS up and running on Ubuntu.  What am I missing?  I've tried installing all dependencies and XMMS but I can't ./configure anything... keep getting 'no acceptable C compiler found at $Path'.  I am trying to install through a root terminal.  Any ideas?[/QUOTE]

I just installed it from Universe (or multivers, not quite sure).
Works perfectly.

If you have an nvidia card, you need to get an extra lib.

---

### Post by zeroK on 2005-01-04
[QUOTE=nocturn]After going to some issues, I got XMMS working on Ubuntu.
Now, I've been using XMMS for years now, and I've always loved it, but lately I've been under the impression that development kinda stopped (or is very, very slow).

So I'm looking at alternatives for it, but none that really suit my need.  Ideally, I would like XMMS with GTK2 support and the ability to load newer winamp skins.

I looked at Beep (XMMS fork to GTK2), but it does did not work very well for me.
I wanted to try Rhythmbox, but it  wanted to search through my music directories (which takes forever so I killed it).

Are there any others that I'm not aware of?  I'm not looking for something with indexing capabilities like Rhythmbox.[/QUOTE]
 Have you already tried the Music Player Daemon (with client) ?
[http://www.musicpd.org/](http://www.musicpd.org/)

---

### Post by jbh on 2005-01-04
[QUOTE=nocturn]I wanted to try Rhythmbox, but it  wanted to search through my music directories (which takes forever so I killed it).[/QUOTE]

? I have around 3500 mp3's on my machine and Rhythmbox doesn't take any time loading up. I like it because it's alot like iTUNES, you can just index search right away instead of screwing around with playlists.

---

### Post by crun on 2005-01-04
A possible alternative for XMMS (with the same kind of GUI) is Beep Media Player

[http://www.sosdg.org/~larne/w/BMP_Homepage](http://www.sosdg.org/~larne/w/BMP_Homepage)

Deb package on [this page](http://www.sosdg.org/~larne/w/Packages)

---

### Post by jbh on 2005-01-04
[http://www.imendio.com/projects/jamboree/](http://www.imendio.com/projects/jamboree/)  I found this too, a 'lightweight' indexing mp3 itunes-like prog for Gnome

---

### Post by nocturn on 2005-01-04
[QUOTE=jbh]? I have around 3500 mp3's on my machine and Rhythmbox doesn't take any time loading up. I like it because it's alot like iTUNES, you can just index search right away instead of screwing around with playlists.[/QUOTE]

Maybe it does not like that my files are on an NFS server (on a 100MBit link)

I tried it again last night, and it stood there for 3 hours 'loading songs'.

---

### Post by hashimoto on 2005-01-04
[QUOTE=nocturn]Maybe it does not like that my files are on an NFS server (on a 100MBit link)

I tried it again last night, and it stood there for 3 hours 'loading songs'.[/QUOTE]
 I don't think this is the reason. My music folder is on the same HD as the system (a normal dekstop) and the Rhythmbox does not load all the songs. And I don't have that many gigs of music. I gave up and loaded xmms

Hashimoto

---

### Post by Ste on 2005-01-04
[http://savannah.nongnu.org/projects/xmms2/](http://savannah.nongnu.org/projects/xmms2/)

I couldn't get it to install tho.

---

### Post by jbh on 2005-01-04
[QUOTE=hashimoto]I don't think this is the reason. My music folder is on the same HD as the system (a normal dekstop) and the Rhythmbox does not load all the songs. And I don't have that many gigs of music. I gave up and loaded xmms

Hashimoto[/QUOTE]

According to the Rhythmbox faq, the reason this happens is because of a GStreamer bug that doesn't recognize some mp3 types. I don't even know if development for Rhythmbox is still going on

---

### Post by X-fact0r on 2005-01-17
[QUOTE=nocturn]I just installed it from Universe (or multivers, not quite sure).
Works perfectly.

If you have an nvidia card, you need to get an extra lib.[/QUOTE]

What is the name of that extra lib for nvidia card users?
I'm having a hard time getting xmms to work in Ubuntu....

Thanks,

---

### Post by nocturn on 2005-01-17
[QUOTE=X-fact0r]What is the name of that extra lib for nvidia card users?
I'm having a hard time getting xmms to work in Ubuntu....

Thanks,[/QUOTE]

I thought libmikmod or something...
If not, try searching the forums, you'll find it quickly.

---

### Post by Error1312 on 2005-01-18
amaroK is also a very good audio player. It's a bit like iTunes for Mac or Windows.

---

### Post by tomchuk on 2005-01-19
You might want to try [Muine](http://muine.gooeylinux.org/) which is now in Gnome CVS. It's a little dependancy-heavy, but a great app. I haven't used it in a while but, I'm compiling it now and maybe I'll post a .deb if I get around to it.

Edit: Maybe not, the deps are ugly and SourceForge is down for maintenance (as usual) so I can't even grab the gtk# libs. Looks like I'll wait for it in hoary or the backports (wink, wink jdong).

---

### Post by duff on 2005-01-19
Take your pick ... [http://www.gnomefiles.org/subcategory.php?sub_cat_id=2](http://www.gnomefiles.org/subcategory.php?sub_cat_id=2)

**edit**: and that thing about rhythmbox taking forever.  It hangs quite often for me when importing my enitre music collection, so I have to import parts at time (individual artist directories).

---

### Post by TravisNewman on 2005-01-19
Muine rocks, it's probably my favorite.

Rhythmbox might be hanging because you have other files in your music folders. Images, text files, etc, will cause it to hang.

Zinf is pretty nifty as well, but I like Muine and Rythmbox the best because of their lightweightedness (no that's not a word)

---

### Post by nocturn on 2005-01-20
[QUOTE=panickedthumb]Muine rocks, it's probably my favorite.

Rhythmbox might be hanging because you have other files in your music folders. Images, text files, etc, will cause it to hang.

Zinf is pretty nifty as well, but I like Muine and Rythmbox the best because of their lightweightedness (no that's not a word)[/QUOTE]

There are .ram files and playlists in those dirs...
And someone said that certain mp3's will cause gstreamer to bail out.

I tried zinf (I really liked freeamp way back), but it's display does not come out nice.  The info in the display (title, ...) is not fully displayed (top cut off).  I tried changing the fonts, but no luck.
I have it working fine on my WinXP at work though...

---

### Post by hashimoto on 2005-01-20
Thanks! Got to start testing...

Hashimoto

---

### Post by nicholaspaul on 2005-01-20
A real newbie question here, altho i hate that word. Anyway, I decided to give Muine a look and downloaded a folder of 'stuff' 
So..er... what do i do with it now?!

---

### Post by HetIsLarsje on 2005-01-20
[QUOTE=nicholaspaul]A real newbie question here, altho i hate that word. Anyway, I decided to give Muine a look and downloaded a folder of 'stuff' 
So..er... what do i do with it now?![/QUOTE]

Had the same problem. Look at the file included in your download, called 'INSTALL'. Open it with an editor, and you will find installation instructions.

Do make sure you've got all the requirements stated in the 'README' file. W/out these you will run into problems.

Before you think, I'm a newbie too, and have not yet installed it myself. 'Make' and compilation in general still are mysteries for me (how I love apt, though).

---

### Post by machiner on 2005-01-21
If you like to also take advantage of your mysql you might find these 2 apps useful:

mp3kult
prokyon3

---

### Post by ctt1wbw on 2005-01-22
[QUOTE=nocturn]I just installed it from Universe (or multivers, not quite sure).
Works perfectly.

If you have an nvidia card, you need to get an extra lib.[/QUOTE]


That would be what I need.  What file is it that I have to download?

---

### Post by ctt1wbw on 2005-01-23
[QUOTE=nocturn]After going to some issues, I got XMMS working on Ubuntu.
Now, I've been using XMMS for years now, and I've always loved it, but lately I've been under the impression that development kinda stopped (or is very, very slow).

So I'm looking at alternatives for it, but none that really suit my need.  Ideally, I would like XMMS with GTK2 support and the ability to load newer winamp skins.

I looked at Beep (XMMS fork to GTK2), but it does did not work very well for me.
I wanted to try Rhythmbox, but it  wanted to search through my music directories (which takes forever so I killed it).

Are there any others that I'm not aware of?  I'm not looking for something with indexing capabilities like Rhythmbox.[/QUOTE]

Issues, like what?  I can't get xmms to play either.  It crashes upon launch.  Is there a set of files or something that I need that I'm not aware of?

I've downloaded and installed and uninstalled xmms twice now and still it won't work...

---

### Post by ReiKn on 2005-03-01
[QUOTE=nocturn]
Are there any others that I'm not aware of?  I'm not looking for something with indexing capabilities like Rhythmbox.[/QUOTE]

[Sonance](http://sonance.aaronbock.net/) might become something good, at least now development seems to be rapid. Downside are the dependencies at the moment.

---

### Post by nocturn on 2005-03-02
[QUOTE=ctt1wbw]Issues, like what?  I can't get xmms to play either.  It crashes upon launch.  Is there a set of files or something that I need that I'm not aware of?

I've downloaded and installed and uninstalled xmms twice now and still it won't work...[/QUOTE]

If you have an Nvidia card, you will need to get libmikmod 
If fonts are tiny, you will have to install non-truetype fonts that match your resolution too.

---

### Post by Phosphoros on 2005-03-02
I hear amaroK is nice but since I'm a linux newbie, I don't know if I can run KDE programs on a gnome system.  :?

---

### Post by NeoChaosX on 2005-03-02
It's possible, it's just going to look ugly unless you want to install the rest of KDE, that's all.

---

### Post by kassetra on 2005-03-02
I personally use beep, but I also have zinf installed ... muine and rhythmbox have always been dog slow and prone to crashing with my music... zinf is a nice alternative to xmms though.  :)

---

### Post by neville_lobo on 2005-03-03
Source for Muine and Tomboy 

deb [http://www.stud.uni-karlsruhe.de/~ut8g/ubuntu/]("http://www.stud.uni-karlsruhe.de/%7Eut8g/ubuntu/") warty-updates main universe 

Neville

---

### Post by HungSquirrel on 2005-03-03
[QUOTE=ReiKn][Sonance](http://sonance.aaronbock.net/) might become something good, at least now development seems to be rapid. Downside are the dependencies at the moment.[/QUOTE]
 I'll say.  I'm trying to build it now and it breaks looking for 'gst-sharp' libraries.  I assume 'gst' stands for gstreamer?  I tried installing libgstreamer0.8-dev, but no dice.

Edit: just tried Beep Media Player (*sudo apt-get install beep-media-player* from universe).  You can get more skins for it by installing xmms-skins from universe, opening /usr/share/xmms/Skins in your file browser, and dragging the *.tgz files into the Preferences -> Appearance -> Skin pane.

I've been wishing for XMMS' reliability (i.e. not crashing when adding media!) with GTK2 menus, and this is doing the trick.  Thanks for the tip.   8-)

---

### Post by ubuntu_jazzbach on 2008-05-03
Check this page:

[http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html]("http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html")

It helped me a lot to compile and run xmms

XMMS FOREVER !!!

---

