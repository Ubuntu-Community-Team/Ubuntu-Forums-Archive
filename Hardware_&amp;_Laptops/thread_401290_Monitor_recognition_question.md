---
title: "Monitor recognition question"
date: 2007-04-04
forum: Hardware &amp; Laptops
---

### Post by Mr. Eddy on 2007-04-04
Hi,

I'm a ubuntu user for more than a year now, and I love it.

What I was wondering when I was installing feisty, why can't ubuntu detect my monitor properly. I always have to edit my xorg.conf for vert sync, horiz sync and add the right resolutions. Why is detecting a monitor sometimes so difficult?

If it is sometimes difficult:
Isn't it possible to make a tool to select your type of monitor, so xorg is edited automatically for that monitor.

Or like in suse linux interprise edition, there was a tool for importing the windows .inf file.

Or can I add my monitor in some hardware database so my monitor would be recognized the next release?

[the monitor I'm talking about:]("http://www.monitorworld.com/Monitors/vobis/highscreenms1795p.html") 
Highscreen MS 1795P 
H freq 30-82
V freq 47-120

Another question, can ubuntu detect if another monitor is connected? and so automatically edit xorg?

everyone who knows something, please answer. I want to learn :guitar:

---

### Post by futz on 2007-04-04
> **Mr. Eddy said:**
> What I was wondering when I was installing feisty, why can't ubuntu detect my monitor properly. I always have to edit my xorg.conf for vert sync, horiz sync and add the right resolutions. Why is detecting a monitor sometimes so difficult?
Auto monitor detection is something that should have been working years ago. But even in windows it doesn't work - you have to plug in the CD and give it the "driver", which is not a driver, but just a capability list. If windows gets it right without the CD, it's only because it has a list of monitors and auto-detects at least the monitor's make/model number, so it can use a so-called "driver" out of the list.

It's something that should have been fixed long ago, but hasn't been done for whatever reason.

---

### Post by Mr. Eddy on 2007-04-04
aha, but why are some monitors recognized and others not?

If it's not a driver, but just a capability list, why can't linux use the same driver CD that windows users use?

---

### Post by futz on 2007-04-04
> **Mr. Eddy said:**
> aha, but why are some monitors recognized and others not?
Probably the same deal as windoze, there's a list of some of the more common monitors, but it's far from complete.

> If it's not a driver, but just a capable list, why can't linux use the same driver CD that windows users use?
Someone would have to write the software to do it. Pretty simple stuff, but beyond my simple programming skillz.

---

### Post by Mr. Eddy on 2007-04-04
Does someone know If I can add my monitor to the "monitor list"? Or could someone do it for me?

thanks for the explanation futz!!

If someone has to ad something, go ahead.

---

### Post by Mr. Eddy on 2007-04-04
Suse uses SaX2 to configure diplay/monitor setting and other stuff. It's also with this tool you can configure your monitor with the .inf file of your monitor. Ubuntu should have a similar graphical tool to configure xorg.conf. Why shouldn't ubuntu use SaX to configure the xorg.conf?

---

### Post by futz on 2007-04-04
> **Mr. Eddy said:**
> Suse uses SaX2 to configure diplay/monitor setting and other stuff. It's also with this tool you can configure your monitor with the .inf file of your monitor. Ubuntu should have a similar graphical tool to configure xorg.conf. Why shouldn't ubuntu use SaX to configure the xorg.conf?
That question has been asked before. Nobody seems to know the answer, or they aren't telling. Sax would be ok, but I think a better utility could be made.

There are a few people working on solutions to the monitor/xorg.conf settings problem. I don't think we'll have to wait too much longer.

I even started writing a tool in Python to do it, but got side tracked with too much work and haven't got back at it. The skeleton is there - I just have to put together all the detail code (that's the hard part :mrgreen: ).

EDIT: Just went digging for sax2 source and finally found the website [http://sax.berlios.de](http://sax.berlios.de)
Maybe I'll tinker with compiling that for Ubuntu and see how it goes. The site mentions that the guy has tried to get it working on Debian, but doesn't say if he was successful. I'll let y'all know what happens.

EDIT2: I think it might be beyond my capabilities. After getting a bunch of dependencies installed and the compiler finally agreeing to start, I've run into tons of errors. I'm probably missing the libsax library or something. I've downloaded it, but don't know how to install it. It's an RPM. I'm not giving up quite yet, but it doesn't look good.

---

### Post by Mr. Eddy on 2007-04-05
Cool to hear you're searching for asolution too :). Maybe I should make a feature request.

Or If you haven't given up (I know you haven't ;) ): 
you have to convert rpm files to debs with alien. Here's the wiki guide: [https://help.ubuntu.com/community/RPM/AlienHowto?highlight=%28rpm%29]("https://help.ubuntu.com/community/RPM/AlienHowto?highlight=%28rpm%29")

If I had some skill's of programming/compiling, I would try it myself. But I haven't...

EDIT: Here are the packages that are needed to compile the source [ftp://ftp.berlios.de/pub/sax/README]("ftp://ftp.berlios.de/pub/sax/README") (But you already knew that)

greets

---

### Post by futz on 2007-04-05
> **Mr. Eddy said:**
> Or If you haven't given up (I know you haven't ;) ): 
you have to convert rpm files to debs with alien. Here's the wiki guide: [https://help.ubuntu.com/community/RPM/AlienHowto?highlight=%28rpm%29]("https://help.ubuntu.com/community/RPM/AlienHowto?highlight=%28rpm%29")
I already knew about alien, and that's my next step for getting that lib installed. Thanks.

I found a post from last summer from a guy who sounded like he was better at compiling stuff than me. He pounded away at it and got it compiled, sorta, but it still wouldn't work. Too many missing parts or something. The thread faded away, so I guess he gave up.

---

### Post by aln on 2007-11-16
Lets revitalize this thread!
I might be wrong, but long time ago in the times of Hoary 5.04 and Breezy 5.10 "dpkg-reconfigure xserver-xorg" command recognized not only the sync ranges of monitor but also it's model! Nowdays if I want to have the proper model name, insted of "generic monitor" in xorg.conf I have to type it in. I wonder if this functionallity was lost during the development of xorg and ubuntu? But that is only if my memory servs me well :-k

---

