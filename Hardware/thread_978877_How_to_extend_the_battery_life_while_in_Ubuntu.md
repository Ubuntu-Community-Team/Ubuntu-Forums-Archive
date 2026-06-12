---
title: "How to extend the battery life while in Ubuntu?"
date: 2008-11-11
forum: Hardware
---

### Post by Indrid on 2008-11-11
Hello there!
So after reinstalling Ibex on my Dell Latitude D620 I am falling in love all over again with Ubuntu.
But heres my question! I have the regular 6 cell battery on my computer, and it's a fairly new machine at onlyl a few months old, and I'm really sad because i only get about two hours and ten minutes battery life on  full charge :( For reference in XP (dual booti) i get about four and a half hours
So my question is how do i extend the battery life as much as possible without sacrficing too much functionality.
Does anyone have any tips from personal experience? Or is Ubuntu/Ibex just a powerhungry beast by nature?
If you need to i can post the specs of my laptop if it helps
Thanks in advance!!!!!


In Him,
~Indrid

---

### Post by transmition on 2008-11-11
Are you using Conky? I noticed that when you lower it's refresh rate, or disable it altogether, it does improve battery life somewhat. 

I also believe that disabling fancy desktop effects affects battery consumption.

As for your question regarding Ubuntu's energy efficiency, I think that this is due to that when you get a computer, it is usually optimized for the operating system it comes with. When I first got my macbook, I had around four and half hours in OS X, and around three hours in windows XP. When I later installed ubuntu 8.04, I had slightly less useful battery life. When I upgraded to Ibex, that went up to around three and a half hours. (Bearing in mind that these are all approximate values)

I could be wrong, but this is what I have noticed from personal experience.

---

### Post by Valde_91 on 2008-11-15
Hi Indrid!
Do you use laptop-mode on battery power?

For knowing if laptop-mode is active when you unplug the AC cable type this line in a terminal

```
 cat /proc/sys/vm/laptop_mode
```

If the answer is 0 the laptop-mode isn't activated. If the answer is a number above 0 then laptop-mode is activated.

If your laptop-mode isn't activated, you can set it up to run when you unplug the AC cable. 

1. open a terminal
2. Type ```
sudo gedit /etc/laptop-mode/laptop-mode.conf

```
3.then go to this line
```
ENABLE_LAPTOP_MODE_ON_BATTERY=0
``` 
and change 0 with 1
4. Save and close
5. Unplug the cable and check if laptop-mode active by typing in terminal
```
cat /proc/sys/vm/laptop_mode
```
Now, normally you must have a number above 0 as answer. thats means that laptop-mode now turns on when you unplug your AC cable

You can also control manually laptop-mode:

if you type in a terminal
```
sudo laptop_mode start
```
you turns laptop-mode on

if you code 
```
sudo laptop_mode stop
```
you turns laptop-mode off

bye bye Valde_91

---

### Post by sdennie on 2008-11-15
Though not specific to your model, you may find the information and links in this thread useful: [ HOWTO: XPS m1330 power savings]("http://ubuntuforums.org/showthread.php?t=847773")

---

### Post by Ryan2009 on 2008-11-24
Hey all, great tip, however, mine doesn't seem to be working as it should...

I checked the conf file and it shows:
ENABLE_LAPTOP_MODE_ON_BATTERY=1

when I'm on battery and I run 'cat /proc/sys/vm/laptop_mode' it shows 0

any ideas?

edit:  found a fix here:

[http://ubuntuforums.org/showpost.php?p=6087297&postcount=5](http://ubuntuforums.org/showpost.php?p=6087297&postcount=5)

---

### Post by iggykoopa on 2008-11-24
if you don't mind helping me test it out you can use the gui I'm working on here .. [http://ubuntuforums.org/showthread.php?t=988309](http://ubuntuforums.org/showthread.php?t=988309) .

---

