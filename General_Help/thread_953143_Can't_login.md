---
title: "Can't login"
date: 2008-10-19
forum: General Help
---

### Post by sirdouglas on 2008-10-19
Sorry to continue posting my problems here, but now things got even worse and I can't even log onto Ubuntu.  Let me state that I am quite the beginner and don't know what I'm doing typing in the terminal window.  I think that's what got me to this mess actually.

Well, I was trying to connect my laptop to a TV through S-Video, and naturally I wasn't having much luck.  After browsing the internet for a solution, I tried a number of terminal commands that people offered to others for connecting S-Video.  Eventually I thought I had changed the settings through an easy configuration window and a logout was necessary for changes to take place.

My computer started booting up normally, but then it went quite slowly listing different text on a black background, and instead of the fancy login screen asked for my login name just on the black background.  I type it in, which was followed by text including,

"Last login... etc, The programs included with the Ubuntu system are free softwareç the exact distribution terms for each program are described in the individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.
sirdouglas@sirdouglas-laptop:~$"

... something like that, maybe I didn't type it out perfectly, but besides that fact, can someone please help get past this and let me know if I need to change some settings, etc to prevent it from happening again?  I'm afraid I permanantly changed some settings, but who knows.

Thanks once again,

Doug

---

### Post by niccholaspage on 2008-10-19
Type startx and see if you get a graphical environment.

---

### Post by sirdouglas on 2008-10-20
Typing "startx" brought another line of texts including:

"Fatal server error:
no screens found
XI0: fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining."

Yup, looks like I must have changed something with the screen settings trying to make S-Video work.  Ugh.  Any ideas?

Thanks,

Doug

---

### Post by AndyCooll on 2008-10-20
You could try re-running through the configuration process (choosing the VESA option if it fails first time):
```
sudo dpkg-reconfigure xserver-xorg
```

:cool:

---

### Post by mkvnmtr on 2008-10-20
This won't help you much fixing you problem but it sounds like you don't remember the exact commands you used. When I was starting with Ubuntu I messed up my system maybe 15 times. Like you I didn't remember enough of what I had done to ask for help to fix it. I just reinstalled and started over messing up my system. I finally got enough practice that my system has been stable for several months. It only takes about an hour to reinstall. I would recomend you don't put any important data on your system without backing up right away. Try to remember or write down everything you do to set up and it will be easier to get help.

---

### Post by sirdouglas on 2008-10-20
Yup, looks like I might have to reinstall from the beginning.  I tried re-running through configuration process, but eventually I think it just finished and I was left with "sirdouglas@sirdouglas-laptop:~$".. and then I'm stuck.

My installation DVD is version 1.4 (ultimate) which is the main reason I would like to avoid reinstalling as installing all the software updates and updating to 1.7 can be a long process (I spent half the weekend on updating alone).

Any other ideas before I give this one quits and start over?  I wish I could be more specific with which commands I entered to get into this mess.  I used a bunch of commands from a long tutorial on setting up s-video with Ubuntu.  (I think I used this website: [https://wiki.ubuntu.com/X/Config).]](https://wiki.ubuntu.com/X/Config).])

Do I really have to re-install my Ubuntu 1.4 or can someone save me?

Thanks,

Doug

---

### Post by sirdouglas on 2008-10-20
Woohoo, after rebooting once again, it allowed me to login as normal.  The configuration process must have worked.  Thank you sooo much Ubuntu community!  It's the little things in life I tell ya... as a beginner you'll be hearing lots of little problems and be able to feel good about yourself giving little simple answers which in return will make me really happy.  :)

I'll be back:)  (I promise I always try searching before posting though!)

Doug

---

### Post by sirdouglas on 2008-10-20
I'm back:)

Okay, well now that my computer is back and running, I still have issues trying to connect my S-Video.  I searched throughout google and the forums, but there are many choices using different ways to do it.  Why can't this just be an easy task?

So I tried using "Screens and Graphics" but the option for extending my desktop/clone wasn't able to be enabled.  I don't know which Video Card I have either (how can I find out?), but when I try to apply the Nvidea or Ati drivers with Envy an error appears saying "There was an error in the installation process. You can see the log file /var/log/envy-installer.log."  I'm guessing this is a prerequisite to the process.

Where is the best how-to guide (for dumb beginners like me) to make S-Video work from my laptop to TV?  Any tips?  I'm using Ubuntu 7.10.  Thanks in advnace!

DOug

---

