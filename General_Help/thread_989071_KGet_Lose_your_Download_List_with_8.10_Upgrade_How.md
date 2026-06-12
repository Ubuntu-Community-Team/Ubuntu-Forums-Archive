---
title: "KGet: Lose your Download List with 8.10 Upgrade?? How to Fix!!"
date: 2008-11-21
forum: General Help
---

### Post by OzzyFrank on 2008-11-21
OK, when you upgrade K/Ubuntu to Intrepid Ibex, **the move from KDE3.5x to KDE4 sort of destroys your download list** - meaning all those things you nearly finished downloading are now inaccessible. This is due to the fact that the markup/code has changed, but with a bit of manual work, you can get your unfinished downloads back. Now, even if you've opened **kget** the old file is still safe, but as soon as you add a new download, it will be written over. So, before you do so, make a copy of this file:

**/home/yourusername/.kde/share/apps/kget/[COLOR="Indigo"]transfers.kgt[/COLOR]**

Basically what you'll be doing is opening that copy and also the new **[COLOR="#4b0082"]transfers.kgt[/COLOR]** that will be created once you add a download, creating copies of that single entry, and pasting in the relevent info from the list of downloads in the backed up file. Or you can just edit the file before starting the new version of **kget** for the first time. In the old file, entries will look like so (including the top of the file):

[B][COLOR="Blue"][Common]
Count=14

[Item0]
CanResume=false
Dest[$e]=file://$HOME/Downloads/ISO/xubuntu-8.10-alternate-amd64.iso
Mode=1
ProcessedSize=15283250
ScheduledTime=2008,10,31,7,51,10
Source[$e]=http://cdimage.ubuntu.com/xubuntu/releases/8.10/release/xubuntu-8.10-alternate-amd64.iso
Status=2
TotalSize=626380800

[Item1]
CanResume=false
Dest[$e]=file://$HOME/Downloads/ISO/ultimalinux-8.4_Desktop-AMD64-LiveCD.iso
Mode=1
ProcessedSize=621367384
ScheduledTime=2008,10,10,0,12,22
Source[$e]=ftp://distro.ibiblio.org/pub/linux/distributions/ultima/ultimalinux-8.4-ISO/ultimalinux-8.4_Desktop-AMD64-LiveCD.iso
Status=2
TotalSize=736796672[/COLOR][/B]

What it should look like now is this (once again, including what goes at the top of the file, as well as the bottom, so as long as you put that there too, you shouldn't need to add a new download just to update the code in the file):

[B][COLOR="Indigo"]<!DOCTYPE KGetTransfers>
<Transfers>
<TransferGroup DownloadLimit="0" Icon="bookmark-new-list" Name="My Downloads" DefaultFolder="" UploadLimit="0" >
<Transfer Dest="file:///home/ozzman/Downloads/ISO/mandriva-linux-one-xfce4-int-cdrom-i586.iso" ElapsedTime="4" UploadedSize="0" DownloadLimit="0" Source="ftp://ftp.gtlib.gatech.edu/pub/mandrake/devel/iso/contrib/2009.0/mandriva-linux-one-xfce4-int-cdrom-i586.iso" UploadLimit="0" TotalSize="663040000" DownloadedSize="121638" />
<Transfer Dest="file:///home/ozzman/Downloads/ISO/xubuntu-8.10-alternate-amd64.iso" ElapsedTime="0" UploadedSize="0" DownloadLimit="0" Source="http://cdimage.ubuntu.com/xubuntu/releases/8.10/release/xubuntu-8.10-alternate-amd64.iso" UploadLimit="0" TotalSize="626380800" DownloadedSize="15283250" />
</TransferGroup>
</Transfers>[/COLOR][/B]

There is a big difference as you can see, but just a bit of copying and pasting and kget will be back to how you had it before the upgrade. All you have to do is have each transfer one after the other between the **TransferGroup** tags, with no empty paragraphs between them. So just start off the new file with:

[B][COLOR="Indigo"]<!DOCTYPE KGetTransfers>
<Transfers>
<TransferGroup DownloadLimit="0" Icon="bookmark-new-list" Name="My Downloads" DefaultFolder="" UploadLimit="0" >[/COLOR][/B]

Paste a bunch of these after it and replace the from/to paths and **TotalSize** and **DownloadedSize** with the source and destination addresses from the old file, and those important numbers from **[COLOR="#4b0082"][COLOR="Blue"]TotalSize[/COLOR][/COLOR]** and **[COLOR="#0000ff"]ProcessedSize[/COLOR]** in the old file:

**<Transfer Dest="[COLOR="Blue"]file:///home/ozzman/Downloads/ISO/mandriva-linux-one-xfce4-int-cdrom-i586.iso[/COLOR]" ElapsedTime="0" UploadedSize="0" DownloadLimit="0" Source="f[COLOR="#0000ff"]tp://ftp.gtlib.gatech.edu/pub/mandrake/devel/iso/contrib/2009.0/mandriva-linux-one-xfce4-int-cdrom-i586.iso[/COLOR]" UploadLimit="0" TotalSize="[COLOR="#0000ff"]663040000[/COLOR]" DownloadedSize="[COLOR="#0000ff"]121638[/COLOR]" />**

Then just finish off the file with:

[B][COLOR="Indigo"]</TransferGroup>
</Transfers>[/COLOR][/B]

... and that's it. When you open **kget**, your transfer list will be there! Hope that helps someone. Cheers

---

