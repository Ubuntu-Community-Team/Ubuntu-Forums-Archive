---
title: "Several Problems (maybe Im new they may be features)"
date: 2008-09-17
forum: General Help
---

### Post by Nitefang on 2008-09-17
Ok I am brand new to Linux. I have used it for the past few days with no bugs (lots of problems but thats cause I'm new and can't figure it out). Today though several weird things have been happening. 

  Every so often Firefox will freeze and then gray scale, almost black and white for several seconds and then returns to normal, once it crashed. 

 My computer seems to be slower, sometimes. It slows down and works harder for a few seconds and then returns to normal. This happens randomly and sometimes even when no programs are running. Does Ubuntu run a lot of things in the background without informing you?

  The help and support closes after 10 seconds of opening. 

 This just started today but became a lot worse and more frequent after I fooled around with some of the "Compiz" features like paint fire and rain.

  I am running a quad-core 2.1GHz(pretty sure it is 2.1) with 3Gb of ram. I have a 8800GTS nVidia Graphics card at 512mb. This is a DELL and I mention that only because there is a whole section on Dell support. Do Ubuntu and Dell not mix well? 

  Like I said I am new at this so if this will require a lot of configuring please explain things in detail. I understand people are busy so you don't need to help me yourself, a point in the right direction (such as a website) will be fine.

  Thank you very much!

---

### Post by Nitefang on 2008-09-17
Ok, I know a few people have looked at my post, so thank you for doing that atleast.

  Any information would make my life a whole lot easier. Thank you for your time and effort!

---

### Post by bobsmith2 on 2008-09-17
Nitefang, as a Linux newbie myself I can't help much, but I will tell you this. My specs are quite a bit less then yours, and I have no problems of the type you're describing. It might help if you tried shutting off some of the eye-candy to see if the problem goes away. Right click on your desktop and click Change Desktop Background > Visual Effects > None.

Also, I found the whole video driver thing to be confusing and found that a program called "Envy" automates the process beautifully. It basically determines what you need and installs it for you. If you haven't tried that, it may be worth a try:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Nitefang on 2008-09-17
O so that's what it does. I know where to find that I just never really fooled with it. Thank you.

---

### Post by mb_webguy on 2008-09-17
> **Nitefang said:**
> I am running a quad-core 2.1GHz(pretty sure it is 2.1) with 3Gb of ram. I have a 8800GTS nVidia Graphics card at 512mb. This is a DELL and I mention that only because there is a whole section on Dell support. Do Ubuntu and Dell not mix well? 

The reason there is a forum devoted to Ubuntu on Dells is not that Ubuntu doesn't work well on Dell computers (an I should know, since I have two Dell laptops and two Dell desktops all running Ubuntu), but rather because Dell sells laptops with Ubuntu pre-installed instead of Windows.

As for your other problems, let's take them one at a time.  Really, you'd get better responses if each problem was in a post of its own with a descriptive subject, like "Firefox stops and turns gray".

Ok, first, the Firefox issue.  When a program stops responding, the window will turn gray to let you know.  This isn't necessarily a bad thing -- the program could be waiting on a response from another program, or for data to be read from the hard drive, or for a response to a request for data over the Internet.  The program window should return to normal within a few seconds.  However, if this is a recurring problem with a specific application, such as you're describing with Firefox, then there's likely a problem somewhere.  I'd be willing to bet that when Firefox hangs, it's on pages with Flash content.  Installing the most recent Flash plugin from the backports repository should fix the problem.  You can find instructions on how to do this by following the "Installing Flash 10 on Hardy Heron" link in my signature.

As for the system slow-downs, this sounds like it could be a video card issue.  Bobsmith2's suggestion of Envy to install the most recent driver for your video card might be worth a try.  However, without knowing exactly what is slowing down your system, it's not possible to provide a solution.  You can use the System Monitor (System->Administration->System Monitor) to monitor your system resource usage to attempt to determine the source of the slow-down.

Another way to monitor your system activity (and the preferred way to do so if you continue to have this problem and need to post to the forum for help) is to open a terminal and type "top".  This will give you a more detailed and accurate look at your system activity than the System Monitor will provide.  Since "top" is text-based, you can easily post the output here if someone asks you to do so.

---

