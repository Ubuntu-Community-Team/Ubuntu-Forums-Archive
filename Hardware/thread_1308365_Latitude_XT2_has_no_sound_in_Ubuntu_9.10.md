---
title: "Latitude XT2 has no sound in Ubuntu 9.10"
date: 2009-10-31
forum: Hardware
---

### Post by EternalLiberty on 2009-10-31
I've been working on this issue for a few days now but nothing seems to be working for me. I'm using Ubuntu 9.10 installed on the Dell Latitude XT2.

I've tried to change sound settings and tried different output ports with headphones. I also found a thread on changing the /etc/modprobe.d/alsa-base file but I couldn't get it to work. So I find myself asking the Ubuntu community for help.

Here's a link on the information about my configuration.

[http://www.alsa-project.org/db/?f=e74847c51613285ff6296bef5b8fc20519915d25]("http://ubuntuforums.org/newthread.php?do=newthread&f=332")

Any help would be appreciated.

---

### Post by EternalLiberty on 2009-10-31
I found that a lot of people are fixing the issue by using the following commands. This seems to be working for HP computers.

Open Terminal and type the following

```
gksu gedit /etc/modprobe.d/alsa-base.conf
```[FONT=monospace]

Add the following at the end of the file.

[/FONT]```
[FONT=monospace]options snd-hda-intel enable_msi=1[/FONT]
```[FONT=monospace]

If that didn't fix the issue add this line at the end of the file too.

[/FONT]```
[FONT=monospace]model=xxx[/FONT]
```[FONT=monospace]

Replace the xxx with the sound card manufacturer.[/FONT]

---

### Post by EternalLiberty on 2009-10-31
I found a solution at the following URL.

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/428555](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/428555)

All you have to do is open the Alsa configuration file in terminal.

```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

Then add the following code at the end of the file.

```
options snd-hda-intel model=dell-m4-1
```

This worked for my Dell Latitude XT2 running Ubuntu 9.10. Good Luck :D

---

### Post by danielshewchuk on 2009-10-31
it opens a second window then what?

---

### Post by EternalLiberty on 2009-10-31
It opens a configuration file to which you add a line of code.

---

### Post by EternalLiberty on 2009-10-31
Please note, if you are using an older version of Ubuntu use the following command to open the configuration file.

```
gksu gedit /etc/modprobe.d/alsa-base
```

The new version adds .conf to the end.

---

### Post by danielshewchuk on 2009-10-31
so if i use 9.10 i go into terminal and type 
gksu gedit /etc/modprobe.d/alsa-base.conf 

then in the other window that opens i type in what???? THanks




Then in the other window that opens i type

---

### Post by EternalLiberty on 2009-11-14
Make sure the window you are editing is not empty. If it is then you didn't open the correct window. There should be text already in the file you're editing.

All you have to do is add this line of text to the end of the file.

```
options snd-hda-intel model=dell-m4-1
```

---

### Post by swissmade on 2010-01-20
Thank you! It worked for me too

---

