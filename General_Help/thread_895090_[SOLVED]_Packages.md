---
title: "[SOLVED] Packages?"
date: 2008-08-19
forum: General Help
---

### Post by Yezinki on 2008-08-19
Hi there,

How can I install Kubuntu, Xbuntu, MythBuntu packages in Ubuntu?

What are the commands??

Thanks!

---

### Post by Sorivenul on 2008-08-19
Pretty much all of the packages are universal from the repository.  Is there something in particular you want to install?  Check in Synaptic Package Manager.  Dependencies should be resolved automatically.  It may be a bit more confusing than Add/Remove but is much more powerful as well.  Good luck.

---

### Post by Yezinki on 2008-08-19
Thanks & sorry for asking simple queries.

I want to merge MythBuntu, Kbuntu, Xbutntu to Ubuntu Hardy Heron 8.04.....as they have the same platform.

Regards!

---

### Post by unca.paka on 2008-08-19
You can install em all in Synaptic, just search for Mythbuntu, Kubuntu, and Xubuntu, and install the -desktop packages. Synaptic will grab all the dependencies and programs included in those flavors.
Your install is gonna get pretty bloated though, so you could just install KDE, and XCFE, and the Myth packages. Then grab whatever programs you need from there.

---

### Post by cariboo on 2008-08-19
An way easier way to install everything that you want is to go to System-->Administration-->Synaptic Package Manager-->Edit-->Mark Packages by Task. This will bring up a list of options to install various servers and desktops.

Jim

---

### Post by Yezinki on 2008-08-19
Hi there thanks,

One query.......after Edit etc & checking the needed ones.....it shows some to removed.....coz they have a chance to cause conflict?

Regards!

---

### Post by Yezinki on 2008-08-19
To summarize I want Ubuntu, MythBuntu, Kubuntu & Xbuntu all merged in one envoirment............any suggestions??

---

### Post by unca.paka on 2008-08-19
Man Cariboo, that is easy. Thanks for the tip. And Yezinki, some packages may conflict, and some may not be needed at all. Thats my understanding anyway, correct me if I'm wrong.

---

### Post by Yezinki on 2008-08-19
> **cariboo907 said:**
> An way easier way to install everything that you want is to go to System-->Administration-->Synaptic Package Manager-->Edit-->Mark Packages by Task. This will bring up a list of options to install various servers and desktops.

Jim

What would you mark by task to use Kubuntu, Xbuntu, MythBuntu & Ubuntu?

Thanks again!

---

### Post by Yezinki on 2008-08-19
> **unca.paka said:**
> Man Cariboo, that is easy. Thanks for the tip. And Yezinki, some packages may conflict, and some may not be needed at all. Thats my understanding anyway, correct me if I'm wrong.

Ok ......so which to install & which not to create conflicts.

---

### Post by mcduck on 2008-08-19
I suppose Edubuntu & Ubuntu desktops are the only ones that could have a conflict. They are both using Gnome desktop. All the others should work fine together.

But Synaptic should actually tell you which packages have conflicts and with what packages..

---

### Post by Yezinki on 2008-08-19
Thanks........I aint installing Edubuntu.

Should I remove those packages listed to removed by synaptic after I have checked what I need??

---

### Post by mb_webguy on 2008-08-19
All Ubuntu variants use the same repositories and packages, so you shouldn't have conflicts by installing the different variants over each other.  You'll just have the desktop managers, themes and applications of all of the installed variants available to you.

---

### Post by Yezinki on 2008-08-19
Thanks mb_webguy........from web md lol.........i'll keep bothering ya!

---

### Post by mb_webguy on 2008-08-20
No problem. :wink:

The only "problem" you're going to have by installing Ubuntu, Kubuntu, Xubuntu, and Mythbuntu is that you'll have all three desktop managers on your system, and all of the software packaged with each of the four variants, which means you're going to have a fairly bloated install.

You can only use one desktop manager at a time, though you'll have the choice of which to use when you log in.

Regardless of which desktop manager you use, you'll have up to three different programs for each task available to you.  You'll have Brasero, K3B, and Xfburn for burning a CD.  You'll have Nautilus, Dolphin, and Thunar for file management (though which is the default will be determined by your choice of desktop manager).  You'll have both Evolution and Kontact.  You'll have both Rhythmbox and Amarok, etc., etc., etc.  Basically, you'll have a lot of redundant stuff, and a lot of stuff you won't have any use for.

But you shouldn't have any conflicts with installing the different variants on top of each other.

---

### Post by Yezinki on 2008-08-20
Thanks mb_webguy for your positive & encouraging thoughts!

Does doesn't Ubuntu variants have a defragger like Perfect Disk 8.0 for Vista...to make it less bloated?

Regards!

---

### Post by mb_webguy on 2008-08-20
"Bloated" in this sense doesn't have anything to do with defragmentation (which isn't required in Linux, since Linux filesystems don't get fragmented in the first place unless you're close to 95% capacity of your hard drive).

When I and other posters have been saying "bloated", we mean having lots of packages installed that you won't need or likely will never use.  Such as having multiple desktop managers (and all of the libraries those desktop managers require) installed, when you only ever use one of them.  Such as having multiple different applications that do the exact same thing.

As I said above, installing the various variants of Ubuntu means installing those variants' applications and desktop managers.  To reduce the "bloat" of your system after you install the various *buntu-desktop packages, simply uninstall anything you don't want or need.  You can use the Add/Remove Programs utility if you don't want to concern yourself with specific packages.

Also, if you're never going to use certain desktop managers, there's really no need to install that *buntu-desktop package.  For example, if you never plan to use the Xcfe desktop manager, then don't install xubuntu-desktop.  You can still install all of the software that comes with Xubuntu individually, without installing the desktop manager.  Likewise, if you're never planning on using the KDE desktop manager, there's no real reason to install kubuntu-desktop.  You can still install Amarok and the other software that comes with Kubuntu without installing KDE.

Remember, the only thing that differentiates the different variants of Ubuntu is the desktop manager and the applications used.  If you don't want the desktop manager, just install the applications you want.  I use Ubuntu, but replaced Rhythmbox with Amarok, and installed K3B as an alternative to Brasero.  You can even replace Nautilus as your default file manager with Dolphin, Konqueror, or Thunar, if you want.  Don't think you have to install Kubuntu to get the Kubuntu applications.  Only install Kubuntu/Xubuntu if you want the option of using KDE/Xfce instead of Gnome.

---

### Post by Yezinki on 2008-08-20
Thanks for clarifying........as earlier said I want to use initially all 4 variants......than as I get more familiar, as you said uninstall the unrequired ones.

Btw which are the better working utilities like e.g Burning softwares, Music, Videos, Photo editing  etc that you personally recommend.

How does one encrypt a drive?

How can one take snap shot of the Ubuntu based system & windows?

Hoping to hear as always,

Regards!

---

### Post by Yezinki on 2008-08-20
Some screen shots of synaptic packages for your comments!

Regards!

---

### Post by mb_webguy on 2008-08-20
> **Yezinki said:**
> Thanks for clarifying........as earlier said I want to use initially all 4 variants......than as I get more familiar, as you said uninstall the unrequired ones.
Sure.  The choice of whether to use Gnome, KDE, or Xfce is essentially a personal preference -- each has its advantages and disadvantages, but none is necessarily "better" than the others -- but the only way you can decide which is *your* preference is to try each of them for yourself.  I personally prefer Gnome, though the newest version of KDE looks interesting, and if I had an older, slower system I'd definitely use Xfce.
> **Yezinki said:**
> Btw which are the better working utilities like e.g Burning softwares, Music, Videos, Photo editing  etc that you personally recommend.
For burning CDs and DVDs, Brasero and K3B are both very good.  K3B may have a few more features (which you may or may not ever use), but Brasero has a simpler and easier interface.

For playing music, I personally don't think there's anything better than Amarok.

For playing videos, once you install the [necessary packages]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_install_multimedia_support_on_Hardy_Heron"), either Totem or MPlayer will do the job.  But personally, I prefer the VLC media player.  It will play practically any format you're likely to come across (and without using any external codecs), and has a lot of nice features.

For editing audio, I use Audacity.  For editing video, I use Avidemux for simple things, and am still trying to decide between KdenLive, Cinelerra (which is unfortunately not in the Ubuntu repositories), and Open Movie Editor for the more complex stuff.

For photo editing, you can't get much better than GIMP, though it's can be intimidating for beginners.

For text editors, I prefer GEdit over Kate, though both are good.  (And yes, you *will* be using text editors in Linux, so make sure you find one you like.)

For file managers, I prefer Nautilus or Konqueror over Dolphin, though I'd be happy enough with Thunar if I were using the Xfce desktop manager.

For bittorrent clients I highly suggest Deluge (particularly the most up-to-date version from the [Deluge website]("http://deluge-torrent.org/downloads.php")).

For IM clients, Pidgin will do just about everything.
> **Yezinki said:**
> How does one encrypt a drive?
Well, I know you can do it [using the alternate install disc]("http://news.softpedia.com/news/Encrypted-Ubuntu-7-10-68383.shtml") during installation, but other than that I'm not sure.  I've never done it myself.  I've never felt it necessary, since I don't keep any incriminating evidence on my laptop...
> **Yezinki said:**
> How can one take snap shot of the Ubuntu based system & windows?
Try xvidcap.  It's primarily intended to take video screencaptures from your desktop, but it can also take still images.

---

### Post by Yezinki on 2008-08-20
> **cariboo907 said:**
> An way easier way to install everything that you want is to go to System-->Administration-->Synaptic Package Manager-->Edit-->Mark Packages by Task. This will bring up a list of options to install various servers and desktops.

Jim


Hi Jim,

I was doing as you suggested but near completion by dsl got dcd....may be due to the storm & heavy down pour.

Now when I try to do the same it stuck/ hangs......the circle keeps going.

After I am into System > Synaptic > Edit> Mark packages by Task......I check, in the pop up window...but than when I click on install it hangs.

Thanks & sorry to have bothered!!

---

### Post by Yezinki on 2008-08-20
How do I start downlaoding packages again.......my bad luck they were almost done.....94% downloaded.

---

### Post by Yezinki on 2008-08-20
Kindly have a look!

Thanks.

---

### Post by niyonk on 2008-08-20
To be quite honest I really do not see the reason you want to mix/have all of these packages together.

What I mean is, what programs do you really want from Edu/Xu/Ku/buntu?.
All of those use the same repository i believe just change your software sources accordingly.

As for the above error, there is clearly a package missing that the program you want to install depends on, what program is is?

Take a look at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and make sure all dependencies are satisfied :)

---

### Post by Yezinki on 2008-08-20
Want to merge Ubuntu, Kbuntu, MythBuntu, & Xbuntu!

Thanks alot!

---

### Post by niyonk on 2008-08-20
So, then my question was....why exactly :D
Well, i have never heard or mixing them. Like i said unless you got programs from the other ones that you want to install.

How about you try to install kde, xfce and their programs instead.
Sorry, i do not have any idea of mixing packages :(

---

### Post by Yezinki on 2008-08-21
Installed all at Atlast .

But I like KDE 4, Ubuntu & MythBuntu the best,

Its the best OS, only think it lacks messenger & live caming!

Regards & Thanks!!

---

### Post by Yezinki on 2008-08-21
Wish Yahoo made a messenger like for Mac...............

---

### Post by Sorivenul on 2008-08-21
> **Yezinki said:**
> Wish Yahoo made a messenger like for Mac...............

Pidgin is more than capable of handling Yahoo messaging.

---

### Post by Yezinki on 2008-08-21
> **Sorivenul said:**
> Pidgin is more than capable of handling Yahoo messaging.

Hi there,

Really.........would you care to elaborate?

I can't even log in to yahoo via Pidgin..........only MSN?

Their is no cam option in Pidgin?

Regards!!

---

### Post by Sorivenul on 2008-08-21
Pidgin can be used for most major messenger services.  
If you start the program and are logged into your MSN, just go to Accounts (also available from right-clicking the Pidgin icon in the system tray) and click accounts.  You should be able to add your MSN account.  Also, make sure it is updated, as the MSN protocol recently updated if I recall.  Not sure how that affects Pidgin, but it can't hurt.  Also, never tried them myself, but aMSN or emesene may suit your needs better for an MSN client.  As far as cam chat goes, I'm at a loss as I don't have a cam set up - no need for one.  Good luck.  I'll leave it there since the original issue of this thread is resolved.

---

