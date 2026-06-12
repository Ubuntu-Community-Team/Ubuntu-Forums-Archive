---
title: "Hardware Acceleration? Drivers? Whats wrong?"
date: 2010-02-08
forum: Hardware
---

### Post by Jooder492 on 2010-02-08
Everything on my Ubuntu seems to be running kinda...slugish.  My youtube videos lagg, even my mouse curser kinda lags when i type a URL in.  Would the be due to hardware acceleration or drivers?  How would i fix this?  I have used Ubuntu before but never as a primary OS like i am trying now so im kinda new.

---

### Post by Merlinson on 2010-02-08
Well, one thing to try is to install mesa-utils so that you can see if your opengl acceleration is working.  It will give you two commands to try:  glxinfo, and a little demo called glxgears.

---

### Post by Merlinson on 2010-02-08
Another thing to look at is System > Administration > Hardware Drivers.  That will tell you if there are some proprietary video card drivers available.

---

### Post by Jooder492 on 2010-02-08
ok im not sure were to find mesa-utils but i have tryed the hardware drivers list and nothing is there.  I also tryed restarting and looking again and still nothing.  Do i try and download the drivers of the manufactures website?  i haven't tried but there not linux.. there windows so i haven't tried yet

---

### Post by Merlinson on 2010-02-08
Hi,

You can install mesa-utils by going to System > Administration > Synaptic Package Manager.  Enter your password and then type mesa-utils in the entry box.  Select the little box on the left and choose Mark for Installation.  Then select Apply.  To see the glxgears, open a terminal and type that in the command line.

If there is no proprietary driver available, you are probably using an Intel chip like me.  I would just let it go at this time.  Installing special drivers might cause problems and it's too soon to do that, lol.

Good luck.

---

### Post by pi/roman on 2010-02-08
You could look at errors and warnings in your xorg.log
```
grep "^(EE)" /var/log/Xorg.0.log
grep "^(WW)" /var/log/Xorg.0.log
```

---

