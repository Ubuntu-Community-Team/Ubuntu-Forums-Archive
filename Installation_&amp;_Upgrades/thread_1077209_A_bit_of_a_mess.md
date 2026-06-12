---
title: "A bit of a mess"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by c3tb0x on 2009-02-22
Hi!
So recently I installed Xubuntu 8.10 while I was running Vista Ultimate (Windows)..
I used to wubi.exe file to "make" Xubuntu and I started it up, and installed it (after selecting Xubuntu in the boot menu) and I ran Xubuntu fine. So I shut it down for the night and yesterday when I tried to run Xubuntu it took ages to log in and then it logged me out after 5 seconds of being logged in, and I could start over by entering username and password. So I decided to run Vista, go to my D drive where I installed Xubuntu and deleted all files and extracted the ISO file again and ran the wubi.exe, but it stopped working.. Is there a way to "remove" the Xubuntu from the system so it doesn't pop up when you start the computer and wants you to select the OS?

Thank you
Regards,
c3tb0x

---

### Post by Partyboi2 on 2009-02-22
To edit the boot menu you can use  EasyBCD.

---

### Post by c3tb0x on 2009-02-22
Thank you, it helped but it didn't fix my problem on why the wubi.exe file stops running when its settting up Xubuntu.. I'm currently deleting old files and extracting them again from the ISO file..

---

### Post by Partyboi2 on 2009-02-22
Make sure that the [[COLOR=Blue]md5sum[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") matches for the iso file. Then stick the iso file and wubi.exe in the same folder and start the wubi install process.

---

### Post by c3tb0x on 2009-02-22
The md5sum are diffrent.. Might cause it! I'll get out and download another Linux, is there any that you could recommend? 
That also comes with an IRC client, bittorrent etc?

---

### Post by Partyboi2 on 2009-02-22
If you used a torrent to download the ubuntu iso you should be able to recheck the torrent and it will download any missing bits.
Or you can download a fresh iso 
[http://www.xubuntu.org/get](http://www.xubuntu.org/get)
[URL="http://releases.ubuntu.com/hardy/"]
[/URL]

---

### Post by c3tb0x on 2009-02-23
I downloaded a new ISO file, and the md5sum started out diffrent! 
And I also tried to install it with the wubi.exe, that failed..
Should I burn it and boot from it?

---

### Post by Partyboi2 on 2009-02-23
You need to get a iso file that md5sums match first. Are you downloading using a torrent? I would suggest using a torrent to download the iso file if you haven't been.

---

### Post by c3tb0x on 2009-02-24
Okay I will do that, thanks!

---

