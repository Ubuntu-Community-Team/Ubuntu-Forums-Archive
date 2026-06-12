---
title: "Screen resolution on toshiba, 10.10"
date: 2010-12-20
forum: Hardware
---

### Post by mrnettles on 2010-12-20
Hello, total beginner Ubuntu user, more or less successfully installed for first time.

Main problem is the display does not fill the screen and monitor options only go up to 800x600. I tried entering some code into the text editor from another similar thread but the only result was that on restart I ended up in command line, not knowing how to start the graphical environment.

Please help as this is the first time I have (almost) successfully installed Ubuntu after trying several different versions on two different machines.

Thanks!

---

### Post by mrnettles on 2010-12-20
Noticed quite a few people seem to have this problem.

---

### Post by davidmohammed on 2010-12-20
can you post a link (or copy and paste) to the instructions here.

What graphics card do you have?  Have you installed any graphics drivers for it?

type in a terminal

lspci | grep VGA

copy and paste the results here.

---

### Post by mrnettles on 2010-12-20
Thanks for your reply.

01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XP4m32 (rev 91)

I have not installed any additional drivers.

---

### Post by davidmohammed on 2010-12-20
does the suggestion in [this link]("https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-trident/+question/121083") fix your issue?

---

### Post by mrnettles on 2010-12-20
Yes it did, instantly and completely! Thanks!!

I only wish I understood what I just did...

---

### Post by davidmohammed on 2010-12-20
normally ubuntu can detect what resolutions your monitor/screen supports.  Occasionally it cant - It needs a little bit of help.

That help is in the "xorg.conf" file you have just created.

---

### Post by padfootpak on 2011-01-22
can this help me with my Dell inspiron N5010? i am using Ubuntu 10.10

---

