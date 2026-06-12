---
title: "[SOLVED] How to schedule a file download"
date: 2008-07-17
forum: General Help
---

### Post by oliwally on 2008-07-17
Is it possible for me to schedule a file download at a specific time?

For example: I've found a large file to download (perhaps the latest kubuntu 8.04.1 iso) but I don't want to download it now, I want my computer to start downloading it at 1.30am in the morning.

Is there linux software that can do this? If so, how do I set it up?

---

### Post by strikegold on 2008-07-17
quite interesting question.looking forward to some sensible answers too.:popcorn:

---

### Post by kunixos on 2008-07-17
If you're using a torrent file to download Kubuntu, then KTorrent will allow you to schedule when to download/use-more-bandwith. It also has neat features that make it so it won't use as much ram or processing power so you can still use it while you're on.

If you're downloading directly from a mirror you can use DownloadThemAll! ([found here]("http://mirrors.us.kernel.org/ubuntu-releases/8.04.1/ubuntu-8.04.1-alternate-i386.iso")) which is a firefox extension that allows you to pause/resume downloads. Or add gwget to Ubuntu for similar usability (pause/resume).

As far as scheduling, however I would have to point you back to the KTorrent utility.

Check K/X/Ubuntu's complete list of mirrors to find torrent files for your downloads and then schedule away!


Hope this helps!

---

### Post by mbeach on 2008-07-18
possbibly could use a combination of 'at' and 'wget'.

man at
[http://www.computerhope.com/unix/uat.htm](http://www.computerhope.com/unix/uat.htm)

man wget

---

### Post by phaid on 2008-07-18
You could use crontab and wget.  Crontab allows you to specify a schedule to run a command and wget allows you to download files from the web

to see the full details for crontab type in: 
man 5 crontab


crontab -e will let you edit the configuration.  So you could add a line like the following to crontab
15 2 * * * wget [http://ubuntu.media.mit.edu/ubuntu-releases/8.04/ubuntu-8.04.1-desktop-i386.iso](http://ubuntu.media.mit.edu/ubuntu-releases/8.04/ubuntu-8.04.1-desktop-i386.iso)

Which would download the iso image at 2:15 AM.  Once the file downloads, make sure to remove the line from crontab, otherwise it would run the command every day.

---

### Post by oliwally on 2008-07-18
> **kunixos said:**
> 

As far as scheduling, however I would have to point you back to the KTorrent utility.

Hope this helps!

Thanks for that. I do remember seeing that KTorrent had a scheduling facility. That's a good option for torrents. But I'm more interested in non-torrent files. Ordinary sort of files that are not available as a torrent.

I've got DownThemAll installed and have used it a lot, but how do I tell it to jump into action at a specific time?

---

### Post by mbeach on 2008-07-18
for an example:
```

echo 'wget http://ubuntuforums.org/customavatars/avatar26311_1.gif' | at 01:30
```

---

### Post by oliwally on 2008-07-18
> **mbeach said:**
> for an example:
```

echo 'wget http://ubuntuforums.org/customavatars/avatar26311_1.gif' | at 01:30
```

Hmmm.. very interesting. I'll have to experiment with that one. 

Is there a gui for wget? (I like guis....)

What about ktimer and KCron? Could they be useful in this? (I've never used them)

Thanks for all the input so far!

---

### Post by mbeach on 2008-07-18
this fella doesn't like 'at'
[http://lateral.netmanagers.com.ar/stories/BBS43.html](http://lateral.netmanagers.com.ar/stories/BBS43.html)

gui for wget
[http://www.gnome.org/projects/gwget/](http://www.gnome.org/projects/gwget/)

apologies if this posts twice - thought I already posted it, then looked back and it wasn't there.

---

### Post by oliwally on 2008-07-18
I think I've found something useful - the KGet Download manager is some kind of wrapper for wget and allows for timed downloads. It even integrates with Konqueror (although I'm using Firefox). I'm guessing it's similar to gwget.

Once the file is dropped into the KGet interface, it is possible to pause it and then set a time to complete downloading.

I've tried it a few times and it works! Download resumes at the scheduled time! 

Thanks for the help folks - would have never found KGet without pointing me to wget.

All we need now is someone to build that functionality into DownThemAll or similar Firefox Add-on. Although, KGet works without having a browser open - that's quite neat too!

---

