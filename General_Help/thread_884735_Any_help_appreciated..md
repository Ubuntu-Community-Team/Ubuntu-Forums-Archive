---
title: "Any help appreciated."
date: 2008-08-09
forum: General Help
---

### Post by Blackrhythms on 2008-08-09
Hi there - I've been using Ubuntu Linux for years now, but never registered on the forums til now. I have a very strange problem with Mozilla Firefox, that even my computer genius brother couldn't help me with!:lolflag:

It started yesterday afternoon - when I turned on the pc and clicked on the Firefox symbol, same as I always do, to connect to the internet. A page opened up, as normal, but it was completely blank. At first I thought that I wasn't connected to the internet, but I was - Firefox seems to have forgotten everything!! No home page, no browsing history - nothing. I have to type in the web address on each individual page I open up. That's not a problem as such - every page is opening as normal - what's really weird is, I have no Back, Forward, Stop, Reload buttons - they remain in shadow. All Bookmarks I had saved are also gone. Also, when I type in a web address and the page opens, rather than getting, for example: [http://ubuntuforums.org/newthread.php?do=newthread&f=331](http://ubuntuforums.org/newthread.php?do=newthread&f=331) - I just get what I typed in - i.e. [www.ubuntuforums.org](www.ubuntuforums.org) and that remains there without changing, no matter what the page is!

I apologise if I haven't been very clear here. I've described the problem as best I could. It just seems really odd and I've never seen anything like it before. At the moment I'm using Epiphany to browse the web, but it's just not the same - I miss Firefox!!:lolflag:

Any help at all would be greatly appreciated!:guitar:

---

### Post by hyper_ch on 2008-08-09
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

### Post by Blackrhythms on 2008-08-09
Gah!!! Sorry!! That would help I guess - d'oh!!:( This forum is different to others I've used - total noob I guess!:lolflag::oops:

---

### Post by sisco311 on 2008-08-09
what is the output of:
```
ls -lR ./.mozilla/
```

---

### Post by silkstone on 2008-08-09
This may be due to doing an update while Firefox was running. That shouldn't matter normally, but people have had problems with this. 

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/238876](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/238876)

Things to try...

It may be that a rogue instance of FF is running. Quit FF and in a terminal...

sudo killall firefox
sudo killall firefox-bin

You can also run FF in safe mode...

firefox -safe-mode

and that will disable any plugins that may be causing a problem.

If that doesn't help, you may have to remove and reinstall Firefox. You will also need to delete the xxx.default folder in ~/.mozilla/firefox/ which will lose your bookmarks and configuration.

---

### Post by Blackrhythms on 2008-08-09
> **sisco311 said:**
> what is the output of:
```
ls -lR ./.mozilla/
```

As I said - total noob - I ran that but couldn't explain to you what it put up! I got a big long list of stuff, that means nothing to me tbh! :oops:

> **silkstone said:**
> This may be due to doing an update while Firefox was running. That shouldn't matter normally, but people have had problems with this. 

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/238876](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/238876)

Things to try...

It may be that a rogue instance of FF is running. Quit FF and in a terminal...

sudo killall firefox
sudo killall firefox-bin

You can also run FF in safe mode...

firefox -safe-mode

and that will disable any plugins that may be causing a problem.

If that doesn't help, you may have to remove and reinstall Firefox. You will also need to delete the xxx.default folder in ~/.mozilla/firefox/ which will lose your bookmarks and configuration.

Yes that's exactly what happened! When I get the update notification, I just click it and let it update and I always have FF running at the time! I did install updates yesterday and it was after that the problem started!

Thank you very much - I'll go give all that a go and hopefully I'll get it sorted! Thank you!:)

---

