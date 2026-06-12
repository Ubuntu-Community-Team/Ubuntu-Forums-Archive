---
title: "avi to iso conversion via Devede"
date: 2008-08-26
forum: General Help
---

### Post by teeleef on 2008-08-26
Hi everyone....especially those who like writing scripts. 

I have loaned my friends Father a decent computer so he can use Linux.  It is the first PC he has ever used and is blown away by it :)

He is in his seventies and is struggling a little using the Devede program in order to convert avi files into an iso format so it can then be burnt to a dvd so he can watch the media (tv programs or films for example) through his dvd player linked to his tv.

Clicking through the devede gui is proving a tad vexing and he forgets the sequence.  Are they any scripts which would complete the devede 'avi to iso' process?

I realise its a long shot but I am aware that most gui's are a frontend for command line actions.


Teeleef

---

### Post by LateNiteTV on 2008-08-26
```
growisofs -speed=YourSpeed -Z /dev/cdrom -dvd-video /place/where/the/dvd/files/are
```

---

### Post by mb_webguy on 2008-08-26
> **LateNiteTV said:**
> ```
growisofs -speed=YourSpeed -Z /dev/cdrom -dvd-video /place/where/the/dvd/files/are
```

That's not going to help if he doesn't have the dvd files....

Really, DeVeDe is about as easy as it gets when it comes to converting an avi to dvd.  

However, you *could* write a script to take as input an avi file, create a generic iso, and burn it to a DVD.  You could then set it as a Nautilus action so all he has to do is right-click on an avi and select something like "Burn to DVD".

I'm a bit rusty at writing scripts, but [this page]("http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/AVI_to_DVD") should give you an idea of the necessary commands...

---

### Post by teeleef on 2008-08-27
Thanks for the comments so far.   The chap concerned is downloading torrents using Deluge.  They then reside in his /home/torrents folder awaiting processing by Devede.   It is this process I'd like to automate....

eg. 

convert   /home/torrents/tvprogram.avi   to  /home/completed/tvprogram.iso  

then 

burn /home/completed/tvprogram.iso to /media/dvdburner

Thanks again


Teeleef

---

