---
title: "General Application File Location"
date: 2008-08-02
forum: General Help
---

### Post by ricksterinps on 2008-08-02
Hello all.

I have been using Ubuntu since Edgy and I haven't had any real problems that I couldn't figure out myself.  I can't for the life of me figure out where the programs are installed in Linux.  I know I figured it out before, but I can't seem to place it now.

Here is what I am trying to do.  I installed Deluge for bittorrent through Synaptic and left everything alone and didn't do any fancy settings with it. For some reason Firefox is still wanting to use the default that was installed in Hardy.  When I go to change the application settings in Firefox I can't remember where to direct it to use deluge.  Can anyone point me in the right place?  Thanks

---

### Post by drs305 on 2008-08-02
Not specifically for deluge, but in general you can find app file locations by typing: 
For command:
```
which appname
```

For files:
```
whereis
```

You can also look up information on apps in the /usr/share/menu/ folder.

---

### Post by rune0077 on 2008-08-02
A round-about way to do it. Rigth-click the torrent link, select "save link as" and save it to your desktop. Now right click the file you just saved, select "Open with", select the "use a custom command" and type

```
deluge
```

into the field, and this should now be the default application for torrents.

---

### Post by ricksterinps on 2008-08-03
Thanks Guys.  That helps.

---

### Post by mb_webguy on 2008-08-03
> **ricksterinps said:**
> I have been using Ubuntu since Edgy and I haven't had any real problems that I couldn't figure out myself.  I can't for the life of me figure out where the programs are installed in Linux.  I know I figured it out before, but I can't seem to place it now.

Believe it or not, there is a method to the madness of the Linux directory structure, but it's completely different from that of Windwos.  This might help: [Filesystem Hierarchy Standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard")  

Executables are located in directories called *bin*, and support files are located in directories called *share* in the same parent directory as the bin directory.  User applications are installed in the */usr* and */usr/local* directories.

As to your issue with Deluge, in Firefox go to Edit->Preferences, the Applications tab, find the entry for "BitTorrent seed file", and change the action to Deluge.

---

