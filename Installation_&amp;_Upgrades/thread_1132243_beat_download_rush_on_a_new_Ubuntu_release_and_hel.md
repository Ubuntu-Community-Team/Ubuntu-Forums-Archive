---
title: "beat download rush on a new Ubuntu release and help others download faster, as well"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by vigyani on 2009-04-21
[B]How to beat download rush on a new Ubuntu release and help others download faster, as well.
[/B]
Ubuntu 9.04 "Jaunty Jackalope" shall release tomorrow i.e. 23rd April 2009. There is going to be a mad rush for downloading the release version. In fact you need not wait till final release is announced. In all probability daily build available now would become the final release (if not there would be only minor modifications).

Daily build are available on: [http://cdimage.ubuntulinux.org/](http://cdimage.ubuntulinux.org/)

daily-live contains the live CD image
daily contains the alternate CD image and
dvd contains the DVD image

daily-live and daily have not changed since 20th Apr. that means these would become final release in all probability (this can be confirmed by md5sum check, once final release is available). DVD is still changing.

What are different options for download?

**1. Jigdo:**
If you already have a CD or DVD image of earlier version of Jaunty then jigdo is the best option.

Jigdo is a download utility for the Debian and other distributions of GNU/Linux that downloads pieces of CD/DVD images from several mirrors/ sources (already down-loaded CD/DVD images/ cached repositories i.e. /var/cache/apt/archives/) in order to build an optical disk image. "jigdo-lite" can be used to download Ubuntu.

Given the  URL of a &#8216;.jigdo&#8217; file, jigdo-lite first downloads pieces of administrative data (contained in the &#8216;.jigdo&#8217; file and a corresponding  &#8216;.template&#8217; file). Then it asks you to provides already downloaded CD/DVD so that it can scan and find-out files/packages required for the download image. Then it asks you to select Ubuntu mirror having rest of the files. Once you give the mirror, it down-loads the remaining files to re-construct the image of CD/DVD. If you already down-loaded an image of a CD/DVD of RC or Beta, then use it to reduce the download.

You can loop mount .ISO CD/DVD images (no need to write to Disc) using Gmount-iso.

In short: 
i) jigdo can use earlier downloaded Cd/ Dvds to look for common packages.
ii) If you Jaunty installed on your system and keeping it updated then you can use even packages in you apt-cache available at /var/cache/apt/archives/

Ubuntu mirrors are located at the following locations:

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)
 
[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)
 
Mirror at ANL has good bandwidth i.e. 15GB; you may chose it as one of the mirrors.

[http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/)

To install jigdo use the following command:

```
sudo apt-get install jigdo-file


```

To start downloading; open a terminal; change to dir where you want to store the iso image; use the following command:

jigdo-lite "url of .jigdo file" 

e.g.: 
```
jigdo-lite http://cdimage.ubuntulinux.org/daily/20090420.1/jaunty-alternate-i386.jigdo
```

This command will download the .jigdo file then ask for CD/DVD to scan and download .template file and scan the CD/DVD or loop mounted directory. You can give more than one CD/DVD/directory. After scanning is over press enter and it would ask for Ubuntu mirror (two of them). Chose a mirror location near you and it shall start to download the required packages and create the image and verify the md5sum.


**2. Next best method is to use bit-torrent:**
I would suggest that download the image using jigdo and use Bit-torrent to seed so that other users may download it faster. (I used this method seeding for Jaunty RC DVD).

Bittorrent is a peer-to-peer, one of the most common protocols for transferring large files. Being a peer-to-peer download/ upload protocol one server is not overloaded as load is distributed. BitTorrent sometimes enables higher download speeds and more reliable downloads of large files. This is one of the best way to download large files.

If you already have a part of the file then Bit-torrent can repair a damaged or incomplete file(s). What it means is if you have downloaded a file by using any other means, you can use bittorrent to repair/ complete the file. Incomplete file (downloaded using some other method) can always be completed using bittorrent.

Theoretically, you can update a Beta or RC ISO image to final release (but I am not sure how much saving you would have).

Ubuntu has a pre-installed Bit Torrent client (Applications--> Internet --> Transmission; though I still continue to use azureus). Download the torrent file corresponding to the CD image and open it with the bit-torrent client. Download shall start.

How to complete/ repair already downloaded ISO image file. Copy the file to the location where bittorrent client would store the file. Rename it to the target file and then start the Bittorrent client. It would recognize the already available file; **[COLOR="Red"]_do the forced checking and then start downloading_[/COLOR]** and it will download parts missing or with errors; complete the ISO image and start seeding. 

Do remember to seed after you have finished downloading. 


**3. Download using a http or ftp client (last option):**
Daily-live does not have torrent or .jigdo option (though release would have torrent file). You can download the ISO image file using "wget" or "Gwget". Install it using Add/Remove.

Change to the directory where you want to store the image file and Use the following command:

wget -t 0 "Url of .ISO image"


For example:

```
 wget -t 0 http://cdimage.ubuntulinux.org/daily-live/20090420.1/jaunty-desktop-i386.iso 
```
 

Once you have the file run md5sum and confirm image is good.

To seed this file using bittorrent:

1. Rename this file to "ubuntu-9.04-desktop-i386.iso"

2. Copy it to the location bittorrent client would store the file.

3. Download the .torrent file of corresponding final release (only after final release is available at [http://releases.ubuntu.com/](http://releases.ubuntu.com/))  seed it using Bittorrent client.


All the instructions may not be clear, as time was too short to prepare this post. 

**Comments / suggestions welcome.**

---

### Post by dudeskeeroo on 2009-04-22
> **vigyani said:**
> 
**3. Download using a http or ftp client (last option):**
Daily-live does not have torrent or .jigdo option (though release would have torrent file). You can download the ISO image file using "wget" or "Gwget". Install it using Add/Remove.

Change to the directory where you want to store the image file and Use the following command:

wget -t 0 "Url of .ISO image"


For example:

```
 wget -t 0 http://cdimage.ubuntulinux.org/daily-live/20090420.1/jaunty-desktop-i386.iso 
```
 

Once you have the file run md5sum and confirm image is good.

To seed this file using bittorrent:

1. Rename this file to "ubuntu-9.04-desktop-i386.iso"

2. Copy it to the location bittorrent client would store the file.

3. Download the .torrent file of corresponding final release (only after final release is available at [http://releases.ubuntu.com/](http://releases.ubuntu.com/))  seed it using Bittorrent client.


All the instructions may not be clear, as time was too short to prepare this post. 

**Comments / suggestions welcome.**

I'm not sure this will work.  Each .torrent file knows the checksum of all the chunks and if the daily build is any different to the final release, you will be seeding "corrupt" data chunks to the swarm.

Thankfully the other clients in the swarm will detect this problem and delete the chunks that fail the checksum.

Sounds dodgy.

I may be wrong, anyone else with more nous willing to pitch in?

---

### Post by Daniel591992 on 2009-04-22
You can also go to Administration > Software Sources and change the mirror to a local university. :P

---

### Post by oc3an on 2009-04-23
Does anyone know where the jigdo file for [http://cdimage.ubuntulinux.org/daily-live/current/jaunty-desktop-amd64.iso](http://cdimage.ubuntulinux.org/daily-live/current/jaunty-desktop-amd64.iso) can be found?

-Patrick

---

### Post by Spearhead666 on 2009-04-23
For Bittorrent:
After adding the bittorrent file _**[COLOR=DarkRed]do a forced check[/COLOR]**_, it would find if there are any changes in file, it would first download the missing/ changed data and then start seeding.

---

### Post by vigyani on 2009-04-23
Finally release is there. If you run the md5sum on the daily-live and daily of 20th April and DVD of 21st April; it is the same as release MD5SUMs.

I am happy to see lots of seeds just after release is announced.

Happy Jaunty-ing.

---

