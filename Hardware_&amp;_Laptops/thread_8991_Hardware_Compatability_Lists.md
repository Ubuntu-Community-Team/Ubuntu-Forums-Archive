---
title: "Hardware Compatability Lists"
date: 2004-12-23
forum: Hardware &amp; Laptops
---

### Post by jakeslife on 2004-12-23
I was wondering if anyone has made any formal documentation on hardware compatability for Ubuntu.  Debian may have an official list (I'm not sure, I haven't checked), but I think it would be beneficial for all Ubuntu users, especially people just starting with it. It would also come in handy for seasoned Ubuntu users when they consider buying extra hardware...it's never fun to play a guessing game whether something will work or not when you purchase it, and it seems to be that some hardware will work on some machines and specific configurations, but not on others. 

I'm sure some Ubuntu users have already thought of this, but I searched the forums and nothing came up. It would definitely be a big project, but it could be divided up among others (a small team for handling hard drives and hard drive configurations, one to handle video cards, one to handle sound cards, network cards, USB peripherals, etc.).

A list that would show users exactly what models work well and which models haven't, and maybe some workarounds that have been proven to help would be great! Something similar to Mandrake's Hardware Compatability list ([http://www.linux-mandrake.com/en/hardware.php3](http://www.linux-mandrake.com/en/hardware.php3)) comes to mind.

---

### Post by techn9ne on 2004-12-23
Thats a great idea. And people can add comments and workarounds for specific pieces of hardware.

---

### Post by Averatec5400 on 2004-12-23
[QUOTE=techn9ne]Thats a great idea. And people can add comments and workarounds for specific pieces of hardware.[/QUOTE]
 Just a wiki page for it would be great.

---

### Post by clasqm on 2004-12-23
This is an old Linux problem, actually, not limited to Ubuntu.

All that info exists already, scattered all over the web. For graphic cards, go see the XFree86 or X.org websites. For scanners, go to the SANE site. For cameras, track down gphoto2. And so on. And if  gphoto2 doesn't see eye-to-eye with your current USB setup, well, then a "supported" camera mysteriously doesn't work. I speak from experience on that last one.

It would be nearly a fulltime job for someone at Canonical to keep track of all of those, note the changes,  and keep a HCL up-to-date. Not impossible, just a **lot** of work. If every piece of hardware actually needs to be tested in combination with every other piece of hardware, well, they might as well set up a separate company for that.

Mandrake was mentioned. They are quite brave: If I have a piece of hardware on the list and it doesn't work, I can call them on it, send long angry e-mails to France or wherever they are these days, asking them why they make false claims of compatibility on their site. If I was American, I would more likely just sue.  Who needs that?

What Ubuntu **could**  do is to set up some links to all those external websites (X.org) and so on, create a whole lot of disclaimers around it, and hope for the best.

---

### Post by ubuntu_demon on 2004-12-23
[QUOTE=clasqm]This is an old Linux problem, actually, not limited to Ubuntu.

All that info exists already, scattered all over the web. For graphic cards, go see the XFree86 or X.org websites. For scanners, go to the SANE site. For cameras, track down gphoto2. And so on. And if  gphoto2 doesn't see eye-to-eye with your current USB setup, well, then a "supported" camera mysteriously doesn't work. I speak from experience on that last one.

It would be nearly a fulltime job for someone at Canonical to keep track of all of those, note the changes,  and keep a HCL up-to-date. Not impossible, just a **lot** of work. If every piece of hardware actually needs to be tested in combination with every other piece of hardware, well, they might as well set up a separate company for that.

Mandrake was mentioned. They are quite brave: If I have a piece of hardware on the list and it doesn't work, I can call them on it, send long angry e-mails to France or wherever they are these days, asking them why they make false claims of compatibility on their site. If I was American, I would more likely just sue.  Who needs that?

What Ubuntu **could**  do is to set up some links to all those external websites (X.org) and so on, create a whole lot of disclaimers around it, and hope for the best.[/QUOTE]
 nice idea to have a link page for hardware compatibility with disclaimers!

A hardware database with disclaimers could also be done. Especially if it would be updated by the community. (people who find stuff is working add it to the database,other confirm it)

I think both should be done. That would rock.

---

### Post by randy on 2004-12-23
I know there are wiki pages for speific laptops hardware support description.

---

### Post by jakeslife on 2004-12-23
> 
This is an old Linux problem, actually, not limited to Ubuntu.

All that info exists already, scattered all over the web. For graphic cards, go see the XFree86 or X.org websites. For scanners, go to the SANE site. For cameras, track down gphoto2. And so on. And if gphoto2 doesn't see eye-to-eye with your current USB setup, well, then a "supported" camera mysteriously doesn't work. I speak from experience on that last one.

It would be nearly a fulltime job for someone at Canonical to keep track of all of those, note the changes, and keep a HCL up-to-date. Not impossible, just a lot of work. If every piece of hardware actually needs to be tested in combination with every other piece of hardware, well, they might as well set up a separate company for that.

Mandrake was mentioned. They are quite brave: If I have a piece of hardware on the list and it doesn't work, I can call them on it, send long angry e-mails to France or wherever they are these days, asking them why they make false claims of compatibility on their site. If I was American, I would more likely just sue. Who needs that?

What Ubuntu could do is to set up some links to all those external websites (X.org) and so on, create a whole lot of disclaimers around it, and hope for the best.



I know it is a general linux issue not pertaining to Ubuntu specifically, and that most of that information is already out there on the web, but if we are to expect "general computer users" (read: Windows folk) to be turned onto linux and OSS, shouldn't we make this information readily accessible to them without telling them to hunt it down for themselves? I think that an open list specifically for hardware (a wiki would be ideal) would be greatly beneficial for Ubuntu. 

And that isn't to say that someone at Canonical has to be in charge of it...this forum has taken off, and many of the users here who think this would be a great idea would probably lend a few hours of their time to help with the project. Even if it is just collating the docs already out there and making it easily accessible to new Ubuntu users, don't you still think it would be worth it?

If we as a community are trying to ready Ubuntu for the average user, I think this is a crucial step, showing them from our experience what works and what doesn't with Ubuntu.

---

### Post by ubuntu_demon on 2004-12-23
[QUOTE=jakeslife]I know it is a general linux issue not pertaining to Ubuntu specifically, and that most of that information is already out there on the web, but if we are to expect "general computer users" (read: Windows folk) to be turned onto linux and OSS, shouldn't we make this information readily accessible to them without telling them to hunt it down for themselves? I think that an open list specifically for hardware (a wiki would be ideal) would be greatly beneficial for Ubuntu. 

And that isn't to say that someone at Canonical has to be in charge of it...this forum has taken off, and many of the users here who think this would be a great idea would probably lend a few hours of their time to help with the project. Even if it is just collating the docs already out there and making it easily accessible to new Ubuntu users, don't you still think it would be worth it?

If we as a community are trying to ready Ubuntu for the average user, I think this is a crucial step, showing them from our experience what works and what doesn't with Ubuntu.[/QUOTE]
 I agree. There must be enough people who like to do this sort of thing.

---

### Post by mark on 2004-12-23
I haven't checked it out in depth, but there is [http://www.ubuntulinux.org/wiki/HardwareSupport](http://www.ubuntulinux.org/wiki/HardwareSupport) - is this the kind of documentation that would be helpful?

---

### Post by jakeslife on 2004-12-23
Somewhat, yes, but with more than 4 items in most of the categories.....

If the wiki is editable, and there are enough volunteers to take on something that would be more comprehensive, we can scoure the forums (especially the recent thread about what hardware specs people run), or send out a mailing on the mailing lists for people to send all their specs, and what works and what doesn't, to an e-mail address, where someone would then then divide up the hardware and send them to specific people to go and edit the wiki with exact model numbers, etc. Hell, I'd even give the volunteers dedicated e-mail addresses on my server (ubuntu-video, ubuntu-sound, ubuntu-mainboard, etc...@thermogenicdesign.com).

---

### Post by saBrEwolf on 2005-03-11
First, I want to say I'm not a programmer, so this may not be of much use...

Isn't this really just another way of looking at HAL's hardware database?
This could be linked to a page on the ubuntu site saying "compatibility list" and give an option to hand over newly working HAL info to the database.
The HAL database would then do the rest of the legwork with drivers and whatnot and maybe even "Bill"; a project I've seen on the forum (can't remember what thread) that would download the relevant software to use the hardware.

Just a thought.

---

### Post by Biffy on 2005-03-11
If you havent seen it, this one is pretty good:

[http://www.linuxquestions.org/hcl/index.php](http://www.linuxquestions.org/hcl/index.php)

---

