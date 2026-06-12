---
title: "Some Questions"
date: 2008-07-29
forum: General Help
---

### Post by allyant on 2008-07-29
Hey there, I decided to stop bashing linux and finding reasons why windows is better and give ubuntu a go to see if it can change my mind.

I have got it up the way I want it (Theme, bookmarks, email etc).

But I Would like to know what I could do with these situations. 

1. Make thunderbird start when I log in (Easy to do, add it to the season), but I want it to start minimized to the tray.
In windows I use the MinimizeToTray(Enhancer) extension, but it doesn't support linux. 

2. I have a windows shared smb folder on the network, linux mounts this fine, how to I get it to mount on startup?

3. Everything in ubuntu seems big, for example the update manager takes up 3/4 of the screen, no way to make windows(elements) smaller? Yes I have the proper screen resolution set. 

4. In firefox in windows I can press the scroll wheel on my mouse and move my cursor down making the page go down, it doesn't seem to work that way in ubuntu..
Thanks for any help.

---

### Post by ibuclaw on 2008-07-29
1) I don't use Thunderbird, but there may be a commandline argument which prevents it from opening up.
Check it's manpage
```
man thunderbird
```

2) Add a line to your fstab file
```
sudo gedit /etc/fstab
```
And something like
```
//192.168.1.2/folder  **/path/to/folder**  smbfs  defaults 0 0
```
I will have to verify that as soon as I get on my Desktop though...

3) Do you mean the font size?

4) I just use the scroll wheel, I find it less of a hassle, but alas, there is probably a way somewhere, I just don't know...

Regards
Iain

---

### Post by kool_kat_os on 2008-07-29
4. i have the same problem

---

### Post by cariboo on 2008-07-30
I'll answer question 4. In firefox go to Edit-->Preferences-->Advanced, under Browsing check autoscrolling.

Jim

---

### Post by Nepherte on 2008-07-30
Question 1: Install alltray:
```
sudo apt-get install alltray
```
and change the command of the launcher of thunderbird to
```
alltray -st -na thunderbird %u
```
You can see all the extra options of alltray by typing:
```
man alltray
```

---

### Post by hyper_ch on 2008-07-30
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by rossjman1 on 2008-07-30
> **cariboo907 said:**
> I'll answer question 4. In firefox go to Edit-->Preferences-->Advanced, under Browsing check autoscrolling.

Jim

Thanks so much! This always worked by default in Windows, so I just figured it didn't work in Ubuntu.

---

### Post by derrick81787 on 2008-07-30
There is a Thunderbird extension that enables it to be minimized to the system tray in Linux, as well, because I have it installed.  Unfortunately, I can't remember the name of it and I'm at work right now.  As previously mentioned, AllTray should do the job though.

I think the name of the extension is something deceptive like "New Mail Icon" or something like that, but it's best feature is minimizing to the system tray (in my opinion).

- Derrick

---

### Post by allyant on 2008-08-06
Thanks, everything seems to be fine now :)

---

### Post by lisati on 2008-08-06
> **allyant said:**
> 

4. In firefox in windows I can press the scroll wheel on my mouse and move my cursor down making the page go down, it doesn't seem to work that way in ubuntu..

I'm not sure why this may be, it seems to work ok on my machine. Perhaps rossjman's suggestion might be of some help.

---

### Post by allyant on 2008-08-06
> **lisati said:**
> I'm not sure why this may be, it seems to work ok on my machine. Perhaps rossjman's suggestion might be of some help.
I think it may be because I am using a laptop, with an external mouse, rossjman's method sorted it tho.

---

