---
title: "How to Install XDVDShrink"
date: 2005-11-19
forum: General Help
---

### Post by Drifter on 2005-11-19
After downloading XDVDShrink, how do u install it.  Is There a how to anywhere on this.

---

### Post by manicka on 2005-11-19
It's available in the repos

sudo apt-get install dvdshrink

---

### Post by rcerreto on 2005-11-19
[QUOTE=manicka]It's available in the repos

sudo apt-get install dvdshrink[/QUOTE]

Some repository has to be added I presume.
I'm using the standard (breezy) ones + universe + multiverse + some other
and I can't get it
Could it be that it hasn't been ported into breezy repositories?

---

### Post by Kokanee on 2005-11-19
It is not in the repos but can be installed easilily. You will need to download it from their website and then use alien to convert the RPM to a DEB.

1. [Download the RPM from their website]("http://dvdshrink.sourceforge.net/").

2.  Get Alien

```
sudo apt-get install alien
``` 
3. Convert RPM to deb

```
sudo alien dvdshrink-2.6.1-3mdk.noarch.rpm
``` 
4. Install

```
sudo dpkg -i dvdshrink_2.6.1-4_all.deb
``` 
5. Make menu item

```
sudo gedit /usr/share/applications/xdvdshrink.desktop
``` 
then paste this into the file and save it..

```
[Desktop Entry]
Name=DVD Shrink
Comment=Make and shrink copies of DVDs
Exec=xdvdshrink.pl
Icon=/usr/share/pixmaps/gnome-cd.png
Terminal=false
Type=Application
Categories=Application;AudioVideo;
StartupNotify=true
```

---

### Post by artinla on 2005-11-19
Hey mods.. somebody.. can we add this to the howto?

---

### Post by manicka on 2005-11-19
[QUOTE=manicka]It's available in the repos

sudo apt-get install dvdshrink[/QUOTE]

Sorry, my bad. I should have checked properly.

It is a package I aliened using a similar method to the above, except I just used smeg to make the menu entry.

---

### Post by Drifter on 2005-11-19
Where do I get Alien

---

### Post by manicka on 2005-11-19
[QUOTE=artinla]Hey mods.. somebody.. can we add this to the howto?[/QUOTE]
I've added this how-to, to the 
Ubuntu Document Storage Facility

---

### Post by Kokanee on 2005-11-19
[quote=Drifter]Where do I get Alien[/quote]

Step #2 was...

```
sudo apt-get install alien
```

---

### Post by Kokanee on 2005-11-19
[quote=manicka]It is a package I aliened using a similar method to the above, except I just used smeg to make the menu entry.[/quote]

_*I think*_ using SMEG will only create the menu item for the existing user that created it.  Manually making the .desktop file will create the entry for all users that log on.

---

### Post by Drifter on 2005-11-19
Thanks I got Alien.

---

### Post by Drifter on 2005-11-19
When I try to burn with XdvdShrink I get this error or what ever:



________________________________________________________

   DVDShrink 2.6.1 - Aug 26, 2005
   Rick Saunders (ozzzy1@gmail.com)
________________________________________________________


   There appears to be no readable DVD in /dev/hdc/

   Place the source DVD in /dev/hdc/ and hit any key to continue...














________________________________________________________

   DVDShrink 2.6.1 - Aug 26, 2005
   Rick Saunders (ozzzy1@gmail.com)
________________________________________________________

Error!
/usr/bin/dvdsfunctions: line 497: $LOGFILE: ambiguous redirect
/usr/bin/dvdsfunctions: line 498: $LOGFILE: ambiguous redirect
/usr/bin/dvdsfunctions: line 500: $LOGFILE: ambiguous redirect
/usr/bin/dvdsfunctions: line 500: $LOGFILE: ambiguous redirect

   DVDShrink has failed!
   Error:
      -> dd could not read the Volume ID from the DVD!
   Command run:
      -> dd if=/dev/hdc/ bs=1 skip=32808 count=32

   Check all your files etc. If it appears that the problem is
   ephemeral restart the script with 'dvdshrink --restart'

   See the log file at  for more information.
   Exiting!


   Thank you for using OzWare!


Hit any key to close terminal and exit!

---

### Post by manicka on 2005-11-19
Is hdc your dvd drive? You may need to configure the app to read your drive properly.

go to

File-->Configure 

and enter the location of your reader and writer.

I use 

/dev/dvd 

for both

---

### Post by manicka on 2005-11-19
[QUOTE=Kokanee]_*I think*_ using SMEG will only create the menu item for the existing user that created it.  Manually making the .desktop file will create the entry for all users that log on.[/QUOTE]

Yes, that's right, I'll add this to the how-to on [doc.gwos.org]("http://doc.gwos.org/index.php/Xdvdshrink")

---

### Post by Drifter on 2005-11-19
Yes that is my drive, I have them both set the same to use one drive as reader and burner.  How do u change the drive names if I need to do that.

---

### Post by manicka on 2005-11-19
[QUOTE=Drifter]Yes that is my drive, I have them both set the same to use one drive as reader and burner.  How do u change the drive names if I need to do that.[/QUOTE]
Click in the relevant field/s in the configure panel and change them

---

### Post by adhuvi on 2005-12-06
Great step by step Kokanee, thanks a lot! Hope some day i can be like u guys.

---

### Post by BLTicklemonster on 2005-12-10
I've got it burning right now, thanks. Seems easy enough, but I wonder, is there any document I can edit? It doesn't see that I have a dvd rom and a dvd rw. I must have dweebeled out when I installed it.

Also, I'd like to change it so that I can keep the iso on the hd for later use, how can I do that?


*edit:

It shows /dev/dvd/ for read and write. I want the write to be /dev/dvd/ for sure, but I want /dev/dvd1/ to be read. I tried editing this:

```
# This hash holds the main configuration items
#-----------------------------------------------------
my %config = (
   SCOMMAND       => "dvdshrink",
   WDEVICE        => "/dev/dvd",
   RDEVICE        => "/dev/dvd1",
   MULTIDRIVE     => 0,
   SPEED          => 1,
   BASEDIR        => "/tmp",
   RMFILES        => 0,
   AUTOBURN       => 0,
   TERMINAL       => "none",
   DELETELOGS     => 0 );

&readconfig;
```

in sudo gedit /usr/bin/xdvdshrink.pl but it didn't make any difference.


I did notice in dvdshrink configure that it wants the devices named. Koff koff, I named the Frank and Arnold, bought them matching little flea collars, but it didn't help. What do I name them? (as a noob, I might mention that "name them" is a bit vague)

---

### Post by Zelut on 2005-12-25
can anyone give me pointers on specifying widescreen vs standard when copying a DVD?  I just did my first one but apparently it took the widescreen and cut it off so it looks a little goofy...

---

### Post by tabinin on 2006-02-18
This howto was great for getting xdvdshrink installed with alien.  Thank you for that.

I had some problems running it after it was installed.  Seems I needed a few other packages, so check to see if you have all of these:

transcode dvdauthor mjpegtools subtitleripper gocr mkisofs libgtk2-perl

if you get this:

```
x@x:~$ xdvdshrink.pl
Can't locate Gtk2.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/bin/xdvdshrink.pl line 17.
BEGIN failed--compilation aborted at /usr/bin/xdvdshrink.pl line 17.
```

---

### Post by Hocktwoie on 2006-02-24
[QUOTE=tabinin]

I had some problems running it after it was installed.  Seems I needed a few other packages, so check to see if you have all of these:

transcode dvdauthor mjpegtools subtitleripper gocr mkisofs libgtk2-perl

[/CODE][/QUOTE]

Thanks to all of you for the tips on install, etc. The above was what I needed to get it to actually work after I installed, so Thank you again.

---

### Post by ardchoille on 2006-02-24
From what I have heard from people who know the author, [xdvdshrink]("http://dvdshrink.sourceforge.net/") is not maintained anymore. However, here are some good links:

[xdvdshrink homepage]("http://dvdshrink.sourceforge.net/")
[Introduction]("http://dvdshrink.sourceforge.net/intro.html")
[The gui]("http://dvdshrink.sourceforge.net/xdvdshrink.html")
[Download]("http://sourceforge.net/project/showfiles.php?group_id=133818")
[Project changelog]("http://dvdshrink.sourceforge.net/changelog.html")

**xdvdshrink dependencies:**
The transcode package and it's required codecs (ripping etc),
the mjpegtools package (re-multiplexing),
the mkisofs package (creating ISO images),
the subtitleripper package (converting subtitles),
the gocr package (for subtitles),
the dvd+rw-tools package (burning), and
the dvdauthor package (authoring DVDs).

Many of the people who were loyal to the xdvdshrink project now use [k9copy]("http://k9copy.free.fr/").

---

### Post by cvmostert on 2006-05-24
[QUOTE=Kokanee]It is not in the repos but can be installed easilily. You will need to download it from their website and then use alien to convert the RPM to a DEB.

1. [Download the RPM from their website]("http://dvdshrink.sourceforge.net/").

2.  Get Alien

```
sudo apt-get install alien
``` 
3. Convert RPM to deb

```
sudo alien dvdshrink-2.6.1-3mdk.noarch.rpm
``` 
4. Install

```
sudo dpkg -i dvdshrink_2.6.1-4_all.deb
``` 
5. Make menu item

```
sudo gedit /usr/share/applications/xdvdshrink.desktop
``` 
then paste this into the file and save it..

```
[Desktop Entry]
Name=DVD Shrink
Comment=Make and shrink copies of DVDs
Exec=xdvdshrink.pl
Icon=/usr/share/pixmaps/gnome-cd.png
Terminal=false
Type=Application
Categories=Application;AudioVideo;
StartupNotify=true
```[/QUOTE]


Thanks for the desktop link info, i was wondering how I got the GUI the previous time I installed xdvdshrink.

Cheers man!

---

### Post by BLTicklemonster on 2006-12-17
After being away from ubuntu for 6 months, I came back and just got around to putting dvdshrink on and here's the problems I'm having.


First off, I installed it from the repos, and my launcher in apps didn't launch it at all. So I launched it from the terminal, and got set up just fine and ripped a dvd. Couldn't have gone any faster! But it has no selections when I try to watch it. It just starts the movie and plays. Not good. I like to pick though if there's something I want to watch later. Then there's another problem. The dvd I ripped starts lagging towards the end. It will stop, then pick up again. The image freezes and the movie keeps going in the background, and suddenly, I'm at a point later than where it froze. I wonder why it does that? I have my burn speed set to 8, so I don't think I'm burning too fast.

So anyway, I removed it and went here 

[http://dvdshrink.sourceforge.net/](http://dvdshrink.sourceforge.net/)

and downloaded that (when I extracted it, the file name was . so I added a folder to put that one in, and lo 

 and behold there's a usr and a bin file) and I have to run the dvdshrink.pl file in the /bin folder to get an interface. What's up with that? No installer, either, it just pops up and starts wanting to run.

So what am I missing here? Some weird stuff for sure. I want to be able to rip dvds in linux so I don't have to keep booting to windows, but at this time, that's the only thing available to me for sound solid ripping of dvds.

If anyone could guide me in how to make a dbd with the option to remove what I don't want, that would be nice. (kinda like the win32 dvdshrink)

I tried dvdrip and other linux stuff, but they are way to over the top technical for me. k9copy, by the way, it has the same problem when I burn a dvd. It stutters once you get towards the end of a movie. No dvd I burn in windows has this problem. I've tested it with a dvd from linux, and one from windows to be sure.

---

### Post by crjackson on 2007-11-03
Excellent thread.  Thanks, worked like a charm.

---

### Post by mastergunner on 2007-11-09
........

---

### Post by mastergunner on 2007-11-09
I am having the same problem as ticklemonster but in K9 copy. the main menu just doesnt work and when you put the DVD into a player it begins to play just the movie. What gives?

---

### Post by Alfred_McGee on 2007-12-23
Is there any advantage to using xdvdshrink when you can use k9copy and k3b? I was initially interested in xdvdshrink because k9copy and k3b are for KDE and I use the Gnome desktop, but k9copy seems to work fine in Gnome and it has a GUI that puts any dvdripper I've seen to shame. It was around 75MB to apt-get install. I tried xdvdshrink first, but it seems to only be available through Automatix, which gives an antiquated version from before the subtitle bug was fixed. Downloading xdvdshrink direct from sourceforge gets you the latest version, but the installation is not just your standard make + make install. It looks like a bit of a headache, and once I had tried k9copy, I didn't feel motivated to go back and mess with xdvdshrink anymore. The backup DVD that I created with k9copy seems to have subtitles switched on, but won't display them, though I don't think that has anything to do with Gnome. Dvd::rip is good, but it doesn't have that wonderful option of making what it rips into a nice .iso file of manageable, burnable size. Dvdbackup is nice and fast, but again, unless you feel like investing in a bunch of pricey DVD-DLs, you're going to have to figure out how to manually shrink stuff down, then put it into an .iso, and so on.

---

