---
title: "opening torrents with opera"
date: 2005-11-14
forum: General Help
---

### Post by pickarooney on 2005-11-14
This is perhaps not strictly an Ubuntu question, but hopefully someone can help me with this. 
When I click on a .torrent file on a webpage with Opera, I get the option to open or save the torrent. If I choose to open it, the wrong version of bitttorrent opens (I have 4.16 installed via apt-get and 4.17 source package unpacked to a directory - I want to use 4.17).
In Opera's preferences, advanced, downloads section, I have files of type .torrent associated with version 4.17 (complete path given), but still version 4.16 opens.

Also, if torrents have non alphanumeric characters in their names, the files cannot be opened, as the filenames are parsed and a file called **linux iso - cd1** gets interpreted as two files, linux iso and cd1.

Basically, what I need to do is tell Opera to open torrent files with version 4.17 and to encompass the filename in quotes, so nothing gets incorrectly parsed.

---

### Post by bionnaki on 2005-11-14
I dont use opera, but is there is way to choose the default applications in the preferences? just change how your browser opens the files...point it towards the other client.

---

### Post by aysiu on 2005-11-14
What bittorent program are you using? I couldn't find any in the Ubuntu repositories with version 4.16 (see screenshot).

In any case, what I would do is symlink the new version to /usr/***--preferably with the same name as the version you're trying to replace.

So let's say the program you're using is bittorrent (which it obviously isn't, because bittorrent is in version 3.4.2 in the Ubuntu repositories, not 4.16). You probably have it in /usr/share or /usr/bin. Using ```
gksudo nautilus
``` find the launching place for the 4.16 version. Then, open a new ```
gksudo nautilus
``` window and middle-click-drag the 4.17 version of the launcher to /usr/share or /usr/bin and then select **link here**. It will ask if you want to replace the other one. Say "yes."

---

### Post by bionnaki on 2005-11-15
he's referring to the bittorrent beta 4.1.7
found here: [http://sourceforge.net/project/showfiles.php?group_id=33044&package_id=25125](http://sourceforge.net/project/showfiles.php?group_id=33044&package_id=25125)

I highly recommend it.

---

### Post by aysiu on 2005-11-15
[QUOTE=bionnaki]he's referring to the bittorrent beta 4.1.7
found here: [http://sourceforge.net/project/showfiles.php?group_id=33044&package_id=25125](http://sourceforge.net/project/showfiles.php?group_id=33044&package_id=25125)

I highly recommend it.[/QUOTE] What confused me was > I have 4.16 installed via apt-get The only Bittorrent I could see that was available via apt-get was version 3.4.2.

---

### Post by pickarooney on 2005-11-15
mea culpa, I think now I installed 4.16 via dkpg, not apt-get.
I'm a little confused about the simlinking via nautilus. 

version 4.16 is launched with

/usr/bin/bittorrent

version 4.17 is launched with

/usr/lib/BitTorrent-4.1.7/bittorrent.py

The file open preference is set in Opera as so:

[http://img476.imageshack.us/my.php?image=screenshot9ra.png](http://img476.imageshack.us/my.php?image=screenshot9ra.png)


I had to upload this elsewhere as
a) gnome-screenshot only seems to take PNG files
b) screenshots are invariably bigger than the allowed attachment size

How do other people get around this?

---

### Post by bionnaki on 2005-11-15
good to see that you were able to change opera's preferences...

as for .png & uploading,
use gimp to compress the image.
file>save as>.jpeg

if I am not mistaken, .png is uncompressed
like .wav is uncompressed...
obviously .wav is far too large for common music file useage (digital players, p2p, etc)
so people compress the files to ogg or mp3...
same with image files.

---

### Post by pickarooney on 2005-11-15
I looked again at Opera's preferences, and there was a second entry called x-bittorrent, which pointed to the wrong client. I edited that, and I think it should work now.

Hmm, I isntalled ksnapshot to test it, and it takes screenies in multiple formats. I'd prefer not to use it with GNOME, but it's a bit handier.

Thanks.

---

### Post by pickarooney on 2005-11-15
Still have that one snag with the torrents, with files containing spaces, dashes etc. Is there normally some kind of command like
**/path/to/application "$1"** ? (that syntax itself doesn't work).

---

