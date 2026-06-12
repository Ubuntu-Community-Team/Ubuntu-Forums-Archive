---
title: "Digital Camera on ubuntu?"
date: 2008-07-25
forum: General Help
---

### Post by Kyle FTW on 2008-07-25
I have a Canon PowerShot SD600 and I want to be able to upload photo's and videos to my computer. It's not showing up on my desktop when I plug it in. Help?

---

### Post by Kyle FTW on 2008-07-25
Bump.

---

### Post by bhankins on 2008-07-25
This isn't really straight-forward help but I had a similar issue with a newly released Samsung S860.  I had to go into f-spot and run the import thing to get it to detect the camera, it has worked just fine when I plug it in from the desktop since then.

---

### Post by Sef on 2008-07-25
> Bump

Don't bump your posts until 24 hours have gone by.  Otherwise you can get an infraction for it.  Since all are volunteers here, sometimes your posts are answered fast and sometimes slow.

---

### Post by russo.mic on 2008-07-26
Plug your camera in, and right after open a terminal and type

dmesg | tail

Post the output.

Russo

---

### Post by Taxman415a on 2008-07-26
Some cameras don't show themselves as USB mass storage devices. Then you have to open a photo management program first. Though typically they automatically run for you if you have it set that way. As noted above F-spot will probably work, and if not, I found a post that said KDE's digiKam works fine with that camera. digiKam is in the repositories, but you'd need broadband to download all the needed kde dependencies if you haven't already installed them for something else.

A general tip is google for your device and add Linux or Ubuntu. So in this case Canon PowerShot SD600 linux made a good search that found what you needed.

---

### Post by hansdown on 2008-07-26
> **Kyle FTW said:**
> I have a Canon PowerShot SD600 and I want to be able to upload photo's and videos to my computer. It's not showing up on my desktop when I plug it in. Help?

Hi kyle FTW. I have a smsung and rather than figure out how to connect it, I read off of the memory card. Hopefully you have a memory card reader. Hope this helps.

---

### Post by ronocdh on 2008-11-01
> **hansdown said:**
> Hi kyle FTW. I have a smsung and rather than figure out how to connect it, I read off of the memory card. Hopefully you have a memory card reader. Hope this helps.
This does indeed seem like the best quickfix, but it's frustrating, because I don't want to drop money on a card reader when I know that my camera works just fine with my computer, just not in KDE4! Argh. =)

---

### Post by cofko on 2008-11-07
I've found the reason for this seemingly odd behaviour (F-spot sees the Camera, but Ubuntu doesn't recognize the device as block device, so you can't mount it) with the help of another post ([http://ubuntuforums.org/showthread.php?t=952378](http://ubuntuforums.org/showthread.php?t=952378)) . 
Quick answer is that you can't transfer files to/from this kind of Camera by traditional file manipulation, but only through a specific protocol. What F-spot sees is really not a filesystem, it just creates a view of a filesystem like tree using this protocol :

[http://en.wikipedia.org/wiki/Media_Transfer_Protocol](http://en.wikipedia.org/wiki/Media_Transfer_Protocol)
[http://en.wikipedia.org/wiki/PTP](http://en.wikipedia.org/wiki/PTP)

---

