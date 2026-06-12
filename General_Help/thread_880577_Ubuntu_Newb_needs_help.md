---
title: "Ubuntu Newb needs help"
date: 2008-08-05
forum: General Help
---

### Post by AlGamer on 2008-08-05
Ive recently built a new computer but couldn't afford to buy a more mainstream O/S so i chose to get my hands on the latest ubuntu cd instead.
Ive figured out the lay out of most of the system but i cant seem to install any of my games it says there is no app installed to open them, also i cant play any of my dvds or multimedia except audio cds it says i need the correct codecs. Please could someone set me on the right path
THANK YOU.

---

### Post by northern lights on 2008-08-05
Your games are most likely Windows binaries, right? Those won't work out of the box.

Check 'wine' or 'vmware'.

For multimedia support:

Navigate to "System > Administration > Software Sources". Enable all repositories but 'proposed' and 'backports'.

Adding medibuntu:```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
Update (synchronize index files w/ sources), install public keyring, update again```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

For DVD playback, run
```
sudo apt-get install libdvdcss2
```To install a player and a ripper, run```
sudo apt-get install vlc dvdrip
```

For wma/wmv support, which is now possible with medibuntu enabled, run```
sudo apt-get install w32codecs
```

For mp3 support, run```
sudo apt-get install ubuntu-restricted-extras
```

For video/flash web content run```
sudo apt-get autoremove totem-mozilla && sudo apt-get install mozilla-mplayer flashplugin-nonfree
```

---

### Post by kirsis on 2008-08-05
For codecs, in the top menu Applications choose Add/Remove ...

Type gstreamer in the search box and install all the gstreamer plugins. A lot of codecs aren't installed by default due to licencing issues.

As for your games, I take it nobody informed you that Windows applications do not run natively in Linux? There is a project called Wine, that allows executing windows apps, but it does not work with all the apps.

Install Wine (from here: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)) and check out appdb.winehq.org/ to see if the games you want to run will work with it. The older a game, the better the chance it'll work.

---

### Post by WRDN on 2008-08-05
To run Windows applications under Linux, you will need WINE (in repos), which provides the libraries for the applications to run. However, it is likely that many games will not work correctly. If you wish, you could use Cedega which allows you to play games under Linux.
As for the audio/ video, open the terminal and type:

```
sudo apt-get install ubuntu-restricted-extras
```

This will install most of the codecs you will need, as well as some fonts.

Now run:

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

DVD's should now work :)

---

### Post by Ryadt on 2008-08-05
Hi..
Concerning your games. First install wine```
sudo apt-get install wine
```
Then install the games in wine.
For your DVDs
```
sudo apt-get install ubuntu-restricted-extras
```
then enable medibuntu repos
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by /////// on 2008-08-05
Some of your games might not work in WINE. If they don't, then your probably screwed because VMWare doesn't support D3d so to play the game you'll most likely have to dual boot with XP or Vista

---

### Post by kirsis on 2008-08-05
If Wine doesn't cut it for you, check out the Cedega app db too
[http://www.cedega.com/gamesdb/](http://www.cedega.com/gamesdb/)

If neither Wine nor Cedega can run a game, then you're out of options and will need Windows to play it.

---

