---
title: "Help me with my Win2008 -&gt; Ubuntu transition"
date: 2009-10-01
forum: Installation &amp; Upgrades
---

### Post by IvanIvan on 2009-10-01
Hello!

I got an idea today of replacing my Win2008 home server (file server,download machine, media server, etc.) with Ubuntu.
Reasons? Well, security, "freeware-ness", modularity, etc.
However, I'm not ready to initialize any move until my specific requirements are checked.

[SIZE="3"]**1. The machine itself**[/SIZE]

The hardware consists of:

**_MBO:_** 
ASUS M2N-MX with latest v1004 BIOS installed. [_*link*_]("http://www.asus.com/product.aspx?P_ID=0pKBwEIE8tqMT4j7&templete=2")

**_CPU:_** 
AMD Sempron 64 (AM2) 3200+ (Manila@1.8GHz)

**_RAM:_** 
2GB DDR2@800MHz

**_GPU:_** 
GeForce 6100 (integrated)

**_audio:_** 
none, disabled in BIOS, no need for it.

**_HDD: _**
system drive would be SAMSUNG HD161HJ (160GB, SATA-II, 7200rpm).
I plan to install Ubuntu on this hard drive with only two partitions (root & swap).
Also, stuff that's downloaded will be there in the beginning, and then moved on to...

**_HDD2:_**
...Samsung HD501LJ (500GB, SATA-II, 7200rpm). This is where 90% of the stuff sits.

**_DVD:_**
Pioneer DVR-212D DVD-RW

**_Printers:_**
two of them.
The first one is a laser HP LaserJet 1020.
The second is inkjet HP DeskJet 5150.

These printers need to be accessible via the network (eg. in the role of network printers).

**[SIZE="3"]2. The network environment[/SIZE]**

My home network consists of:
- 3 PC's: two desktop, one laptop, all of them running Windows Vista (stop laughing! :))

- HTPC also running Windows Vista (Media Center)

[B][COLOR="Red"]All of these computers must be able to access the server without problems. For the three PCs that mostly means file copying, backup, etc. _and they must be able to use both printers_
For HTPC it means seamless streaming of video (SD and 1080p HD) and audio.
The network switch and all interfaces are **_1Gbps_, which means 1080p streaming should work like a charm as it does now**.[/COLOR][/B]

Also, the computers must be able to access the computer (via VNC or something like that) because the server is headless (I'll connect the monitor for the initial installation of course).

And now, the main questions are:

1. Currently there are a lot of files on Win2008 server. It's a NTFS partition of course and I was planning to copy all the relevant files to a third drive (external, not in the server, also NTFS) and then after the installation of Ubuntu, reformat the server's HDDs to ext3/4 and then copy back the files from the third drive.
**[COLOR="Red"]Will this work? Will I lose files (NTFS->ext3/4 copying)?[/COLOR]**

2. What's the best way to set up file sharing/access? samba? On what do I need to pay attention?

3. I need linux-equivalent software for these Windows applications:
- torrent client like uTorrent
- powerful download manager like Free Download Manager
- a DVD/CD burning tool (like BurnAware free)
- archiver (like 7zip)

4. HTPC. My HTPC (that is, the Media Center in it) needs to see and add the server's HDD as it's "library" (music,video,etc.) for streaming. How is this done? via samba?

5. Remote control (inter-VLAN, not over WAN). How do I get access to the server with GUI. No "simple" command-line SSH is not an option. FreeNX, some VNC client? And how does that work in Ubuntu/Windows environment?

6. Security. Computer is on 24/7, connected to the switch witch is connected to a router (Thomson Speedtouch 780WL, firewall and IDS enabled). What's the best way to secure the server against possible port scans, intrusion attempts, etc.

That's it. It's a long post, but it's not a small thing so I was detail enough in order to give you people enough information so we can discuss about this...

Thanks for reading,
let's try and make this work.

---

### Post by Lars Noodén on 2009-10-01
> 
1. Currently there are a lot of files on Win2008 server. It's a NTFS partition of course and I was planning to copy all the relevant files to a third drive (external, not in the server, also NTFS) and then after the installation of Ubuntu, reformat the server's HDDs to ext3/4 and then copy back the files from the third drive.
Will this work? Will I lose files (NTFS->ext3/4 copying)?


It should work.  NTFS is not exactly a great file system, technically, but it should be usable for transfer.  If you have the space, I'd recommend a *second* backup that you put somewhere else till this is all over.  

You might look at JFS depending on your planned usage.  In some situations EXT3 or EXT4 might be better.  In others JFS might be better.

Do you have lots of file?  Are they large, small, etc?  Is the directory layout 'deeper' or 'wider'?

---

### Post by IvanIvan on 2009-10-01
> **Lars Noodén said:**
> Do you have lots of file?  Are they large, small, etc?  Is the directory layout 'deeper' or 'wider'?
around 500 GB. mostly video and music files along with some archives. The directory structure is not deep, three or four folders most...

---

### Post by gordintoronto on 2009-10-01
1.  I think you mean that you will format the server's drives to EXT3 *during* installation of Ubuntu.  (And I do suggest EXT3, it's very robust and proven.)  You should not lose any files unless you smack yourself in the head and say, "oh darn, I forgot to copy folder xxxx."

2.  I have file sharing set up and it works fine from my desktop (not server) system -- but I forget the details.  Searching in the forums should tell you all you need to know.  If you want remote admin by GUI, I suggest you set up desktop, not server.

3. Ubuntu comes with Transmission torrent client, which seems to work OK.  I don't know what a download manager does.  Brasero burns CDs and DVDs.  There are several archivers.

4. Sorry, can't help.

5. TightVNC should work fine.  I assume you will install Ubuntu with a monitor, keyboard and mouse attached.

6. Linux is much more secure by design than Windows.  I have no firewall, but I'm behind a router.  In two years, there hasn't been a hint of anything amiss.

---

### Post by sloppyc on 2009-10-01
Yes, Samba is the answer to numbers 2 and 4.  When you share with Samba, Windows will see the share in the same way it would if it were a shared folder on a Windows machine.  That means, yes, you will be able to map network drives on your Windows clients.  It also means you could easily do your file management from any client machine, making the need for an archiving tool or CD burning package on the server unnecessary.

If you're going to have a GUI installed anyway, uTorrent works pretty well with Wine (I just can't make it connect to https trackers).  I mention this because I know what a hassle it is to re-add a large list of torrents to a client.  With uTorrent, just copy the contents of your %APPDATA%/uTorrent folder, put them together with the utorrent.exe and it will pick up right where it left off next time you run uTorrent (for this reason I keep a uTorrent folder with uTorrent.exe and all of my .torrents on a partition separate from my system... this way, if I have to reinstall, all I need do is run the executable and it's immediately up and running, torrents all loaded.  Great for dual-boot situations, too).

---

### Post by Lars Noodén on 2009-10-01
> 
2. What's the best way to set up file sharing/access? samba? On what do I need to pay attention?


If you still have a lot of Windows clients, then Samba might be most appropriate.  OpenAFS might be considered in addition, if you have several geographic locations to consider.

> 
3. I need linux-equivalent software for these Windows applications:
- torrent client like uTorrent
- powerful download manager like Free Download Manager
- a DVD/CD burning tool (like BurnAware free)
- archiver (like 7zip)


The package transmission-daemon gives you a daemonized torrent that you can run on the server. 

Have no idea what 'Free Download Manager' would be a copy of.  How is it used?   Most web browsers have built-in download managers, but that is not a server topic.

On the server, for CD burning,: wodim. 
On the desktop, hands-down choice is K3b

You have 7zip, gzip, and bzip2 available to name just a few.  Do you mean a GUI or a shell interface?   Or do you mean a file manager like thunar or doplhin?

---

### Post by Lars Noodén on 2009-10-01
> **IvanIvan said:**
> Hello!
5. Remote control (inter-VLAN, not over WAN). How do I get access to the server with GUI. No "simple" command-line SSH is not an option. FreeNX, some VNC client? And how does that work in Ubuntu/Windows environment?


Don't underestimate the usefulness of the shell.  GUIs are usually a subset of the normal, shell based tool.  Anything you do in the shell can usually be cut-n-paste into a script and thus automated.  GUIs are often dependent other pieces and more vulnerable to murphy. 

If your connection is fast, you can connect graphically via SSH to run GUI-based programs:
[indent]
   ssh -Y -l melogin 127.8.9.10
[/indent]

Anyway, to explicitly answer the VNC question, you can run tightvncserver on your server and connect from VNC clients.  There are several others, you might wish to compare them.  During a test, I was able to get a Windows-user on another continent to connect, but the main test was against another Linux machine.  

krdc is the client I have used most, but I don't use much VNC.  There is also vinagre, gtkvncviewer, gvncviewer, xtightvncviewer, xvnc4viewer.

---

### Post by Lars Noodén on 2009-10-01
> **IvanIvan said:**
> Hello!
4. HTPC. My HTPC (that is, the Media Center in it) needs to see and add the server's HDD as it's "library" (music,video,etc.) for streaming. How is this done? via samba?


Those are usually some kind of linux.  So you could use NFS, but if you are going to be running Samba, then you might as well do without NFS and use Samba for that, too.  

You can do streaming from your Ubuntu server using Icecast2 or, when you are ready for some shell action, the Darwin Streaming Media Server.  The latter is not packaged yet for Ubuntu, so I would recommend Icecast2 for right now.

---

### Post by IvanIvan on 2009-10-01
> **gordintoronto said:**
>  1.  I think you mean that you will format the server's drives to EXT3 *during* installation of Ubuntu.  (And I do suggest EXT3, it's very robust and proven.)  You should not lose any files unless you smack yourself in the head and say, "oh darn, I forgot to copy folder xxxx." 

yes, exactly. :)

> **gordintoronto said:**
> 2.  I have file sharing set up and it works fine from my desktop (not server) system -- but I forget the details.  Searching in the forums should tell you all you need to know.  If you want remote admin by GUI, I suggest you set up desktop, not server.

that's why I meant. I now that server is more robust and configurable, etc. but I really need the GUI.

> **gordintoronto said:**
> 3. Ubuntu comes with Transmission torrent client, which seems to work OK.  I don't know what a download manager does.  Brasero burns CDs and DVDs.  There are several archivers.

4. Sorry, can't help.

5. TightVNC should work fine.  I assume you will install Ubuntu with a monitor, keyboard and mouse attached.

Yes, but only during the install and initial setup.
After that it will run headless (no monitor,keyboard or mouse...)

> **gordintoronto said:**
> 6. Linux is much more secure by design than Windows.  I have no firewall, but I'm behind a router.  In two years, there hasn't been a hint of anything amiss.

though so, but I wanted to be sure. :)

> **sloppyc said:**
> Yes, Samba is the answer to numbers 2 and 4.  When you share with Samba, Windows will see the share in the same way it would if it were a shared folder on a Windows machine.  That means, yes, you will be able to map network drives on your Windows clients.  It also means you could easily do your file management from any client machine, making the need for an archiving tool or CD burning package on the server unnecessary.

If you're going to have a GUI installed anyway, uTorrent works pretty well with Wine (I just can't make it connect to https trackers).  I mention this because I know what a hassle it is to re-add a large list of torrents to a client.  With uTorrent, just copy the contents of your %APPDATA%/uTorrent folder, put them together with the utorrent.exe and it will pick up right where it left off next time you run uTorrent (for this reason I keep a uTorrent folder with uTorrent.exe and all of my .torrents on a partition separate from my system... this way, if I have to reinstall, all I need do is run the executable and it's immediately up and running, torrents all loaded.  Great for dual-boot situations, too).

Thanks for the NFO, but I think that transmission will suffice. 

> **Lars Noodén said:**
> Have no idea what 'Free Download Manager' would be a copy of.  How is it used?   Most web browsers have built-in download managers, but that is not a server topic.

I meant a program called Free Download Manager:
[IMG]http://actualdownload.com/pictures/screenshot/free-download-manager-6672.gif[/IMG]

AFAIK, the most similar thing is multiget, right?

> **Lars Noodén said:**
> You have 7zip, gzip, and bzip2 available to name just a few.  Do you mean a GUI or a shell interface?   Or do you mean a file manager like thunar or doplhin?
GUI based would be really nice.

---

### Post by Lars Noodén on 2009-10-01
> **IvanIvan said:**
> 
6. Security. Computer is on 24/7, connected to the switch witch is connected to a router (Thomson Speedtouch 780WL, firewall and IDS enabled). What's the best way to secure the server against possible port scans, intrusion attempts, etc.


K.I.S.S.  -- if it is not there it can't break, install as few packages as you can get away with.  
Don't run PHP or GUI.  

Read the do's and don'ts of the services you have chosen to run.  Security is an effect of good design, and an ongoing process.  

Once you have it up and running, then you should scan the thing yourself from another, non-Windows machine.  **zenmap** is a good option for the basic scan, though it shows only which ports are open, not what's there on those ports.  Later, during the holidays, a separate project might be to learn to do vulnerability scans with OpenVAS or set up snort as an IDS.

fwbuilder is a GUI for building IPTables rules, but my strong recommendation would be to look at using IPTables via a regular shell script.

Having open ports are not in and of themselves are not a problem, having insecure programs listening is: if your application cannot survive without a firewall, then it has no business being on the net.  

Advanced: Divide the filesystem up into partitions that either can execute programs XOR are writeable.  That's a bit harder.  /dev, /proc, /sys, /var, and /home should be writeable.

---

### Post by IvanIvan on 2009-10-01
> **Lars Noodén said:**
> Don't run PHP or GUI.
as I said above, I need the GUI. I'll be installing the desktop version not the server.

---

### Post by Lars Noodén on 2009-10-01
> **IvanIvan said:**
> 

I meant a program called Free Download Manager:

AFAIK, the most similar thing is multiget, right?

GUI based would be really nice.

Firefox, Opera and Konqueror all have some form of download manager.  There are also a lot of [download add-ons](https://addons.mozilla.org/en-US/firefox/search?q=download") for firefox.  One of them might be worth something.  Unfortunately, it's a foreign concept to me.  If you do test multiget and find that it was or wasn't what you were looking for, please write something so that others can find out.  

Regarding compression, thunar seems to be good at figuring out how to decompress or unpack files.  So that may be the GUI you are looking for.  Konqueror does a good job, too.  I wish there were more articles describing the innerworkings, because is is very well designed.

---

