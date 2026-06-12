---
title: "mic problems"
date: 2009-05-15
forum: Hardware
---

### Post by m4rc1n on 2009-05-15
Hello, so i've used ubuntu for a couple of days now and love it BUT in ubuntu my microphone is realy low. no one can hear me in skype. i've tried to edit the mic loudness in the volume control but i can't move it. It's just stuck at the bottom and  i can't  move it. Help! :P  
[[IMG]http://img40.imageshack.us/img40/8683/skrmbildvolymkontrollhd.th.png[/IMG]]("http://img40.imageshack.us/my.php?image=skrmbildvolymkontrollhd.png")

---

### Post by connorh123 on 2009-05-15
I'm thinking this could be a problem with aumix.. Because that's how I fixed mine.
Type this into terminal.
```
sudo apt-get aumix
```
When it's done, you should get a picture like the one below.
The line where it says <Mic, turn it all the way to the right by using the right-arrow key.
Tell me what happens after that.

---

### Post by m4rc1n on 2009-05-15
> **connorh123 said:**
> I'm thinking this could be a problem with aumix.. Because that's how I fixed mine.
Type this into terminal.
```
sudo apt-get aumix
```When it's done, you should get a picture like the one below.
The line where it says <Mic, turn it all the way to the right by using the right-arrow key.
Tell me what happens after that.

well, mine doesn't look like that at all :(
umm... in mixer i can higher the volume of the mic to full but as soon as i answer in skype it turns to 0

---

