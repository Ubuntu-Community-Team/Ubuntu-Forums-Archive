---
title: "How to start bittorrent on command line"
date: 2008-09-11
forum: General Help
---

### Post by satimis on 2008-09-11
Hi folks,


I have no problem to start bittorrent to download file on Gnome desktop by clicking the *.torrent.  Bitorrent will take care of the rest.  If on headless server how can I start it on command line to download file similar to rtorrent?  TIA


B.R.
satimis

---

### Post by Pro-reason on 2008-09-11
It&#8217;s simply &#8220;bittorrent&#8221;.
[I]
Edit: oops, that's the name of the package, not the command; see below.[/I]

---

### Post by satimis on 2008-09-11
> **Pro-reason said:**
> It’s simply “bittorrent”.
Hi Pro-reason,


Thanks for your advice.  I tried before.  It did not work.


On terminal

1)
# bittorent```

bash: bittorent: command not found

```

Both as root and user.


2)
# bittorrent Desktop/debian-40r4a-i386-DVD-1.iso.torrent ```

bash: bittorrent: command not found

```


However "rtorrent" works on step 2)

---

### Post by lovinglinux on 2008-09-11
You could simply create a folder for your .torrent files and configure the bittorrent client to auto download from that folder. So, instead of clicking the .torrent file to start it, you simply save it on your torrent folder. Next time you open the bittorrent cilent it will grab the .torrent file and start it automatically.

I don't know rtorrent, but Deluge is capable of doing that and it is the best client for Linux in my opinion.

```
sudo apt-get install deluge

```

---

### Post by satimis on 2008-09-11
Hi lovinglinux,


Ubuntu 7.10


Thanks for your advice.

> **lovinglinux said:**
> You could simply create a folder for your .torrent files and configure the bittorrent client to auto download from that folder. So, instead of clicking the .torrent file to start it, you simply save it on your torrent folder. Next time you open the bittorrent cilent it will grab the .torrent file and start it automatically.

Could your please explain in more detail how to configure bittorrent client to do the job?  Thanks.


> 
I don't know rtorrent,.... 

It is very simple.  On terminal;

$ rtorrent *.torrent

then it starts to download the file.


Unforturnately I can't install rtorrent because of dependencies problem.


> 
but Deluge is capable of doing that and it is the best client for Linux in my opinion.
```
sudo apt-get install deluge

```
deluge is NOT on repo.  I tried to install it before posting.


B.R.
satimis

---

### Post by lovinglinux on 2008-09-11
> **satimis said:**
> Could your please explain in more detail how to configure bittorrent client to do the job?  Thanks. 

That depends on the torrent client. Deluge has this option in the first configuration tab. It is called "Autoload". Just select the folder you want and you are setup. Save torrent files on that folder and Deluge will get them when it starts. It is really a handy feature.

> **satimis said:**
> deluge is NOT on repo.  I tried to install it before posting

It should be, unless there is differences between 8.04 and 7.10 repositories. I guess you also need to enable "universe" repository. If this doesn't make it show up, you can download the deb file from [http://download.deluge-torrent.org/ubuntu/gutsy/](http://download.deluge-torrent.org/ubuntu/gutsy/). I recommend version [[COLOR="DarkRed"]**0.5.9.4**[/COLOR]]("http://download.deluge-torrent.org/ubuntu/gutsy/0.5.9.4/"), because the 0.9.x branch is still Release Candidate and has bugs.

---

### Post by Pro-reason on 2008-09-11
> **satimis said:**
> Hi Pro-reason,


Thanks for your advice.  I tried before.  It did not work.


Ah, sorry.  I gave the wrong information there.

Type &#8220;bt&#8221; on the command line (with no space or enter!) and then press Tab.  You'll get a list of all the bittorrent terminal commands.   &#8220;btdownloadcurses.bittorrent&#8220; is probably the relevant one.

In future, to get a list of all the commands provided by an installed package, do this:

```

dpkg -L *bittorrent* | grep /bin/

```

Replacing &#8220;*bittorrent*&#8221; with the name of the package.

---

### Post by satimis on 2008-09-12
> **Pro-reason said:**
> Ah, sorry.  I gave the wrong information there.

Type “bt” on the command line (with no space or enter!) and then press Tab.  You'll get a list of all the bittorrent terminal commands.   “btdownloadcurses.bittorrent“ is probably the relevant one.

Hi Pro-reason,


I tried before;

$ which bt
$ which btorrent
$ which bittorrent
etc.

All without printout


> 
In future, to get a list of all the commands provided by an installed package, do this:

```

dpkg -L *bittorrent* | grep /bin/

```

Replacing “*bittorrent*” with the name of the package.
Thanks.


$ dpkg -L bittorrent | grep /bin
```

/usr/bin/btcompletedir.bittorrent
/usr/bin/btdownloadcurses.bittorrent
/usr/bin/btdownloadheadless.bittorrent
/usr/bin/btlaunchmany.bittorrent
/usr/bin/btlaunchmanycurses.bittorrent
/usr/bin/btmakemetafile.bittorrent
/usr/bin/btreannounce.bittorrent
/usr/bin/btrename.bittorrent
/usr/bin/btshowmetainfo.bittorrent
/usr/bin/bttrack.bittorrent

```
Which of them shall I use;

1)
fresh download

2)
resume download


TIA


B.R.
satimis

---

### Post by Pro-reason on 2008-09-12
Don't ask me.  I've never used it before.

Read the manuals.  

```

man bittorrent-downloader.bittorrent
man bittorrent-multi-downloader.bittorrent

```

---

