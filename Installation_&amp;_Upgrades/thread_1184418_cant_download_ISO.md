---
title: "cant download ISO"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by t-cave77 on 2009-06-11
Hi,
I downloaded 9.04 a few days ago and it worked fine. I just tried today and when I run the exe in window the log produces the following error:
 
06-11 09:33 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-amd64.metalink](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-amd64.metalink) > D:\ubuntu\install
06-11 09:33 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-amd64.metalink](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-amd64.metalink) err=[Errno 4] IOError: 
 
is this an issue at your end?
 
Tony.

---

### Post by Sef on 2009-06-11
What exactly are you trying to do?  If you have successfully burned it to a live cd, then you need to have your boot check the cd tray before the hard drive.

---

### Post by t-cave77 on 2009-06-11
> **Sef said:**
> What exactly are you trying to do? If you have successfully burned it to a live cd, then you need to have your boot check the cd tray before the hard drive.
 
Sorry, I was not very specific here. I just donwloaded wubi 9.04, so I can install from Windows. When I did this the exe ran and down loaded the ISO, unbunto installed when I rebooted (I was great, just worked). Now I am trying to do exactly the same on a different PC, the wubi.exe complains it can not get the ISO and I find the above error in the log.
 
I was just wandering if the link ito the ISO has moved.
 
Regards,
Tony.

---

### Post by Sef on 2009-06-11
make sure that windows is properly closed down...if it is not, then wubi will not start up.

---

### Post by t-cave77 on 2009-06-11
> **Sef said:**
> make sure that windows is properly closed down...if it is not, then wubi will not start up.
 
Its not getting to that stage. I am at the stage of running the window exe (wubi.exe) to download the ISO.
 
Can someone check the link wubi.exe is trying to download is accessable: 
_[COLOR=#800080][cdimage.ubuntu.com/daily-live/current/jaunty-desktop-amd64.metalink]("http://cdimage.ubuntu.com/daily-live/current/jaunty-desktop-amd64.metalink") [/COLOR]_[[COLOR=#444444][/COLOR]]("http://releases.ubuntu.com/9.04/ubun...amd64.metalink")
 
When I try to open it in a browser it is saying access denide...
 
Tony.

---

### Post by t-cave77 on 2009-06-11
> **t-cave77 said:**
> Its not getting to that stage. I am at the stage of running the window exe (wubi.exe) to download the ISO.
 
Can someone check the link wubi.exe is trying to download is accessable: 
_[COLOR=#800080][cdimage.ubuntu.com/daily-live/current/jaunty-desktop-amd64.metalink]("http://cdimage.ubuntu.com/daily-live/current/jaunty-desktop-amd64.metalink") [/COLOR]_
 
When I try to open it in a browser it is saying access denide...
 
Tony.
 
 
Its ok, my works firewall was blockinh access to the .xsl page... Downloading now ;-) Sorry to waste your time.
 
Tony.

---

