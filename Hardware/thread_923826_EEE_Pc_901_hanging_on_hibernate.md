---
title: "EEE Pc 901 hanging on hibernate"
date: 2008-09-18
forum: Hardware
---

### Post by cr4z3d on 2008-09-18
Hello,

I recently purchased the ASUS EEE Pc 901 and have installed [link="http://www.ubuntu-eee.com/index.php5?title=Main_Page"]Ubuntu EEE[/link] and followed this tutorial specifically to [link="http://www.ubuntu-eee.com/index.php5?title=Fix:_hibernate"]fix hibernate [/link]. However, it seems that it just hangs on s2disk: Snapshotting System and does not appear to do anything. I've let it sit for up to 5 minutes trying to get this to work. This does not use the generic kernel but instead a custom one from [link="http://array.org"]Array.org[/link]. If anyone has some kind of suggestion as to get s2disk working with a separate swap file to limit system writes I would greatly appreciate it.

---

### Post by parsim on 2008-09-20
That happened to me, so I changed the image size line back from "= 0" to what it had been and it worked again. So my /etc/uswsusp.conf looks like:

```

resume device = /dev/sdb2
compress = y
early writeout = y
image size = 483733585
RSA key file = /etc/uswsusp.key
shutdown method = platform
```

---

### Post by parsim on 2008-09-20
Hmm, I take it back, I'm still getting that problem.

---

### Post by cr4z3d on 2008-09-20
It would be nice to get hibernate working.. since for whatever reason I don't get the advertised 7.5 hours using ubuntu yet my friend running Win XP does. Not really sure why though

---

### Post by starcannon on 2008-09-20
Same is happening here on the Asus Eee 8g (702). Hangs on suspend/resume using the lid as well; however, it suspends and resumes fine using the FN+F1 key. My 4g (701)'s all seem to work flawlessly. Am guessing I can figure out which model was tested with lol.

---

### Post by cr4z3d on 2008-09-20
Man if I knew about how Linux did things I'd attempt to fix this myself.. but I'd rather not mess things up since everything works besides hibernate. I got suspend working, but like you said depends how I initiate it. If I click the battery meter and chose suspend it works. If I click "quit" and then suspend it seems to hang then instantly resume. Very strange stuff

---

### Post by starcannon on 2008-09-22
Its the first release of Ubuntu eee (soon to be renamed), and I would expect that there will be patches to address these issues (so long as we all file bug reports with Jon I think his name is).

Anyway, I hear you, and I've never found Hibernate to be a very useful feature anyway; however suspend/resume is an absolute necessity for my laptops as I need those batteries to last as long as possible.

GL and have fun.

---

### Post by parsim on 2008-09-25
Wow, I cannot figure this out! Most of the time (but not always) I get that hang on "Snapshotting system."

I'm very keen to get it sorted out.

Suspend works fine and always has though.

---

### Post by cr4z3d on 2008-09-25
There's some weird things that happen with mine. On shutdown, usually it'll hang with just my wallpaper until I tap the power button. Then it proceeds to shutdown as normal. Sometimes it hangs on a black screen until i hit power once again.

For suspend, if i have it set to suspend on close lid it works fine everytime. But as soon as I click quit > suspend it'll never work. It looks like it will then instantly resumes right away. Some very strange stuff.

---

### Post by mister_pink on 2008-09-29
I have a weird issue. Hibernate seems to work but after its saved the image to disk it just goes to the lock screen dialog.

Suspend only works about half the time. It sometimes won't resume and I have to hard off.

---

### Post by parsim on 2008-09-29
Well I seem to have got mine working, although I'm not totally sure how. I removed uswsusp, so I'm back to kernel hibernation, and made a new 768MB swap partition (about 3 times as big as the one Ubuntu made by default, for 1GB of RAM). I also put everything back the way it was before I started following [this guide](http://www.ubuntu-eee.com/index.php5?title=Fix:_hibernate). So far so good!

---

### Post by mister_pink on 2008-09-30
I really wouldn't recommend having swap on an eee. It will seriously reduce the life of the solid state drive. Thats why theres the whole faff with that guide, it creates swap only for hibernation, not for normal use. 

That said, that guide didn't work for me, and nearly caused me data corruption as I had to hard power off. It saved the data to disk and left me with a blank screen with a flashing cursor in the corner.

---

### Post by parsim on 2008-10-08
I've never seen the machine actually use its swap. I think "swappiness" is set to discourage it.

Anyway, hibernate seems to work about 19 times out of 20 for me now. But that one occasional failure means you can't trust it...

---

