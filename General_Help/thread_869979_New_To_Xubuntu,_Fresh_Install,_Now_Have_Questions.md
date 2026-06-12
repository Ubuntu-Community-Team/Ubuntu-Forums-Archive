---
title: "New To Xubuntu, Fresh Install, Now Have Questions"
date: 2008-07-25
forum: General Help
---

### Post by s1mp13m4n on 2008-07-25
Hello everyone.  I installed Xubuntu 7.10 Alternate yesterday via advice from this forum.  Now I have the PC up and running and even connected wirelessly, not bad for a newbie.  Here is what I have:

HP Pavilion 6633C
500Mhz Celeron
128MB RAM
20GB HDD
12MB shared video
no NIC
using Blitzz USB wireless G stick
15in crt monitor

The system is slow but I guess it will be with these specs.  I am new to Linux and want to know what do I do now?  Are there "safe" and easy to do tweaks to speed things up a bit?  If the machine has to access the hard drive the machine comes to a stand still and you wait and wait.  I can load basic html pages such as [www.google.com](www.google.com) pretty well.  However trying to load my google home page at [www.google.com/ig](www.google.com/ig) take forever, mainly because of gmail.  
     I do not really know how to use the terminal yet, however when I try and access it through the application drop down menu the PC thinks a bit, then I get strange virtical lines on my monitor then I get logged out back to the GUI username screen.  I am trying to locate some PC100 RAM locally on [www.craigslist.com](www.craigslist.com).  The PC will handle two 128MB sticks for a total of 256MB RAM, and I know that should help a bit.  
     Thanks for your advice and tweaks, remember I am a newbie, heck I still can not figure out how to get Flash Player to install with firefox.  LOL  :)

---

### Post by overdrank on 2008-07-25
PM me I have some memory. I maybe can help out. :)

---

### Post by snowpine on 2008-07-25
Flash player is easy, just open a terminal and type: ```
 sudo apt-get install flashplugin-nonfree
```

More RAM is probably the #1 thing you can do to speed up that computer. Good luck!

ps Flash video might be a little choppy with that system, though.

---

### Post by LowSky on 2008-07-25
Firefox has a built in program editor that can help reduce how much of the system it uses.

follow these instructions they may help
[http://forevergeek.com/open_source/make_firefox_faster.php](http://forevergeek.com/open_source/make_firefox_faster.php)

---

### Post by GreenN00b on 2008-07-25
Go to System\Preferences\Session and disable all startup programs except, this should free up a bit of memory.

Go to System\Preferences\Appearance and disable visual effects

Go to System\Administration\Services and disable the ones you are sure you don't need, eventually ask somebody if you don't know for sure if you need them. Some examples of services that can be disabled are: "Bluethoot ...", "CPU Frequency manager", "Folder sharing service", "Power management", "Printing ..."

I hope this helps ...

---

