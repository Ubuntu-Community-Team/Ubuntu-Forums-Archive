---
title: "Hardware Questions and *buntu Edition Help!"
date: 2008-08-01
forum: Hardware
---

### Post by flatline on 2008-08-01
Hi,

So I am setting up a home server.  I need a little guidance though, as A) This is my first DIY computer, and B) My linux experience is limited to basic desktop use.

The hardware I have coming in is this:
[LIST]
[*]_[Asus P5E WS PRO Server Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131244")_
[*]4GB (2x2) Kingston DDR2-800 ECC RAM
[*]Xeon E3110 3.0GHz Wolfdale dual-core CPU
[*]2x 1TB Western Digital GP HDDs
[/LIST]

I saw on newegg that someone had 8.04 running on this mobo, so I am hoping that it will work.  [_Unfortunately, I saw an older thread on here that suggested that the RAID controller built-in prevents Ubuntu from installing_]("http://ubuntuforums.org/showthread.php?t=751457")... *fingers crossed*  If this mobo doesn't work, I will probably trade it in for the [_Asus P5BV-C_]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131242").

Here is what I want to use it for:

[LIST]
[*]File Server - My house uses Macs and XP (Samba?)
[*]Torrent Server - Using uTorrent or something similar, provide a Web-based GUI that I can set to download torrents.
[*]Print Server - Provide a tether for printing from laptops (CUPS?)
[*]Media Streaming - This is the tricky part.  I want to be able to stream media to my X-Box 360/1080p TV.  I am hoping Fuppes works, because I like the on-the-fly transcoding.
[/LIST]

I know I said that I am setting up a home server, but I'm wondering if Server Edition of Hardy is the right way to go, since I'm probably going to want a GUI.  Yes, it will be running headless most of the time, but when I remote into it I would prefer to have an actual desktop.  Also, I might be doing virtualization now and then.  **So the question is, Desktop or Server Edition?**  Followon: Should I stick with the 32-bit edition?  I'm afraid I'll run into issues trying to get Fuppes running as it is, 64-bit compatibility seems like asking too much.

All (constructive) comments appreciated!

Matt

---

### Post by Rocket2DMn on 2008-08-01
Assuming you have checked that your hardware is compatible with the other components you are purchasing (e.g. the processor and RAM fits on the board), you should be OK.  Some people have trouble with SATA and RAID controllers during install, but there are typically ways to work around this, often by using the correct kernel boot options.

RE: the computer's purposes, it sounds like you have done some research and are pretty much up to speed.  I don't know much about media streaming though.

The server edition should be just fine, and you can always install a desktop environment on it after the initial installation.  The desktop edition will also suffice since you don't seem to be setting up things like LAMP.

For 32bit vs 64bit see [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607) - in general you are probably OK with 64 bit (you can always try, and if it fails, go to 32 bit).  You may get a touch more out of those Xeons using 64 bit and you certainly have the RAM to spare.

---

### Post by evets25 on 2008-08-01
On the torrent server thing, I should mention that ktorrent is a wonderful torrent client that I use, and it has a web gui plugin which allows you to access ktorrent and control it remotely using your browser. It's pretty easy to set up, and even easier to use. You could use it to log in to the computer from another computer on the network, and start and stop downloads. Ktorrent also has a robust bandwidth manager that can start and stop at different times on a schedule, or even slowly scale down the speed in stages. It's really neat. :)

---

