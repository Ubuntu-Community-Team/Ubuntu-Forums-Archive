---
title: "Repository of Downloaded Plugins and support files"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by germantechie on 2009-01-22
I am using KUbuntu Hardy Heron 8.04 LTS on my Dell Inspiron 1525.
There were many softwares which did not work out of the box, one small example would be the Amarok player not playing .mp3 files, or Kaffine not playing .avi files.
I had to download their plugins and support files. Fine here. But i was not informed where the files are being downloaded.(Layman terms, where on my HDD did it save itself, which folder?)

Hence i would like to know,
1> What all packages, support files, plugins did i download in   the past 3 months.
2> Where did it get saved on my HDD? and how to backup these?
3> If i want to erase my HDD and install the same OS again, then will these saved downloads be used to make the broken softwares run correctly?
4> Is there any way i can know the file size being downloaded before the download starts, because based on that, i can decide whether to download or not? Amarok just started downloading without enquiring if i wanted to download or not.

Please visit my blog for some more info about my problem.
[http://kubuntu-hardy-heron.blogspot.com/2008/10/experiencing-kubuntu-on-dell-inspiron.html#links](http://kubuntu-hardy-heron.blogspot.com/2008/10/experiencing-kubuntu-on-dell-inspiron.html#links)

---

### Post by Ng Oon-Ee on 2009-01-22
I'll give this a try...

1> That depends. Most application related stuff goes to /usr/local or /usr/share.
2> See (1). You should not back up these files (explanation to come)
3> Instead of manually backing up, I'd suggest either a complete system backup (then you don't even need to reinstall the OS) or downloading the .deb files from packages.ubuntu.com.
4> Amarok, as well as other media players (WMP also, for that matter), will automatically look for the codecs to download. This is a useability 'feature', so that the 'grandma' portion of society doesn't have to think about what's going on behind the scenes.


So, if you want a full system backup, there's HOWTOs somewhere around (search the forums). There should not be a need for a full reinstall unless you like running alpha/beta software or you mess around a lot with your system (like I do). This isn't Windows, you don't need to reformat every 6 months just to get things running properly again. At worst, all you need to do is create a new user with a new home directory, if you've screwed up some user-specific settinsg. The big 'but' here is xorg and boot-related stuff, if you're playing with that then you need to know what to do about it.

If you still want to reinstall, you can search packages.ubuntu.com for the exact packages being downloaded. I think kubuntu-restricted-extras will provide all the necessary. If you download the .deb file for your architecture, its basically an archive containing the files you need and instructions on where to put them.

---

