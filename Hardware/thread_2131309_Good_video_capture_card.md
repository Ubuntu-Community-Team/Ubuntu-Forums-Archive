---
title: "Good video capture card"
date: 2013-04-01
forum: Hardware
---

### Post by Phil Binner on 2013-04-01
I have an ubuntu machine attached to my TV and I want to use it for video capture.  It is running 12.04 and has a Saphire 2gb HDMI card  I couldn't say which one without being able to interrogate the system, and I don't know how to do this in Ubuntu.  No matter, it doesn't do video capture.  I have 3 free pci express slots.

Can anyone reccommend a good video capture card I can use which has a track record with Ubuntu.  I wouldn't say cost is no object, but I do want good quality.

If anyone can reccommend good software too this would be a great help.

Thanks in advance.  Phil Binner

---

### Post by gordintoronto on 2013-04-01
Mythbuntu seems to be the popular way to do video capture and media-centre PC. However, you might find the setup difficult. In any case, the Myth project is your best bet for finding an appropriate video capture card. Note that geography influences what is appropriate.
[http://www.mythtv.org/wiki/Video_capture_card](http://www.mythtv.org/wiki/Video_capture_card) 

If you open terminal and enter the command: lspci
you'll get about 14 lines of interesting output. One of them will contain the string "VGA" and that is your HDMI card.

To get a detailed blow-by-blow description of your computer, use this command:
sudo lshw -html > Desktop/myconfig.htm
It will put a file on your desktop. Double-click on it, and it will open in your browser, with a nicely formatted description of your computer hardware.

---

### Post by Phil Binner on 2013-04-03
Thanks for that. I'm away for a couple of days but i'll try that when i get back. 

I have looked at mythbuntu before and did manage the setup ok after a while. I still have the notes. That was more for recieving broadcast tv though. I'm looking to save recorded video fron HDMI in. I didn't like actual mythbuntu because it took over everything else, but myth tv within Ubuntu was ok. 

Thanks anyway. I'll look on, their forum.

---

### Post by gordintoronto on 2013-04-03
Sorry, HDMI in is a completely different story, to the best of my knowledge.

---

