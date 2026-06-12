---
title: "keys nonstop pressing malfunctioning, ubuntu 11.10"
date: 2012-05-07
forum: Hardware
---

### Post by p3rry on 2012-05-07
I have set up Ubuntu 11.10 on my new Dell Vostro and I noticed a strange  issue.  After a while (~ some hours of work) I experience that the cursor freezes  while I try to move it by nonstop pressing of arrow keys. I have to  press the key once more to make it move again. It happens also with the  other keys, for example if I keep pressed "l" key I get:
llllllllllllllllllllll
And it stops after a while. I also noticed that the screen blinks slightly   when the key freezes. I cannot understand if it's linked to some hardware or software issues. 

Is there some way to monitor what's happening while I type? Just to understand a  little more what goes on when such a boring behavior shows. 

Thank you for your help, you can imagine how boring is such an issue while you try to write and correct a paper...

---

### Post by p3rry on 2012-05-14
Anybody?

I tried something but still the problem persists.
I switched to a fresh 12.04, just recovering my home directory.
I was thinking it's related to hybrid ati-intel graphics issues so I tried this solution: [http://ubuntuforums.org/showthread.php?t=1930450&page=2](http://ubuntuforums.org/showthread.php?t=1930450&page=2)
I tried to look at some error logs but really I do not know where to start and, as far as I can understand, I didn't find anything strange.
I unset some graphical effects I was using (eg wobbly windows) and it seemed to work but just for sometime. 
Anyway I have also windows 7 and it doesn't give me such kind of troubles...

---

### Post by p3rry on 2012-05-22
Here's something more, which maybe can help

Each time the issue occurs Xorg.0.log displays:

[ 17364.264] (II) fglrx(0): EDID vendor "SEC", prod id 21569
[ 17364.264] (II) fglrx(0): Printing DDC gathered Modelines:
[ 17364.264] (II) fglrx(0): Modeline "1366x768"x0.0   76.69  1366 1414 1446 1618  768 770 775 790 +hsync -vsync (47.4 kHz)
[ 17364.264] (II) fglrx(0): Modeline "1366x768"x0.0   48.22  1366 1414 1446 1526  768 770 775 790 +hsync -vsync (31.6 kHz)

So it's related to the video driver...any idea?

---

