---
title: "Nvidia TNT2 64mb card driver?"
date: 2009-09-14
forum: Hardware
---

### Post by spkenny on 2009-09-14
I have dabbled in linux, specifically xubuntu for a little less than a year now.  As a computer tech, I mainly deal with windows.  For those customers of mine that love eye candy, I could totally sell them on linux once I learn how everything works from installing to code you have to imput.  One issue that remains for me, and keeping me from experiencing beryl, is my friggin video card.  I have a TNT2 Nvidia 64mb card that is working perfectly.  My only issue is getting a proper driver to install.  can anyone start me in the right direction on where to get the driver from and how to install it to begin with?

---

### Post by Whiffle on 2009-09-14
Go to System > Administration > Hardware drivers and see if it detects it.  If it does, it should offer to install the correct drivers.  If not, we'll have to do a little more work.

EDIT: Oh wait you're on xubuntu...I'm not sure if you have that menu. Hmm.

---

### Post by spkenny on 2009-09-14
um...ok.  Not sure what happened, but it says its working fine now.  Understand that I've run into the same whole thing before with setting up the driver, having it automatically download and it appears to be fine, only to pop up that message saying its still using 3rd party software and may not be fully functional blah blah blah.  But that was back when I first looked into xubuntu in 08.  Anyways, now onto step 2.  What do I look for in the synaptic package manager for the beryl?  I did this a while ago already, but forgot how to do some of this.  Oh, and is 64 mb on the vid card enough to run beryl?

---

### Post by Whiffle on 2009-09-14
Well, Beryl is pretty much long gone, now the word you're looking for is compiz.  

If the Intel 915GMA on my laptop can do it, your TNT2 should be able to as well.

here's a blog post on compiz under xubuntu:
[http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/](http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/)

---

### Post by spkenny on 2009-09-15
awesome, thanx for the link I'm reading it now.  I knew that it was either beryl or compiz that had become outdated, just got it backwards.  It's compiz that took over beryl.  A question about commands.  I visited some forums reguarding my video driver problem, and they had commands to put into the terminal to download the drivers etc.  I noticed upon doing so that some (I think they were links to download sites)error messages came up reguarding... well I forget now.  But with everything changing with linux, are links to download certain packages also continually changing?

---

### Post by Whiffle on 2009-09-15
> **spkenny said:**
> awesome, thanx for the link I'm reading it now.  I knew that it was either beryl or compiz that had become outdated, just got it backwards.  It's compiz that took over beryl.  A question about commands.  I visited some forums reguarding my video driver problem, and they had commands to put into the terminal to download the drivers etc.  I noticed upon doing so that some (I think they were links to download sites)error messages came up reguarding... well I forget now.  But with everything changing with linux, are links to download certain packages also continually changing?


Yeah, theres alot of out-of-date information floating around the web, and I would expect plenty of out of date files as well.

But, as for installing software, here's a couple of good resources for general ubuntu know-how:
[http://www.psychocats.net/ubuntu](http://www.psychocats.net/ubuntu)

[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)

---

### Post by spkenny on 2009-09-15
hey sweet.  You've been a huge help.  When I started back in october last year, I wasnt getting much help.  I really appreciate this.  Can I private message you with any more questions, or just post again if something else comes up?

---

### Post by spkenny on 2009-09-15
ok, another problem.  Everything seems to be going ok up to the part where he says "Beneath the Effects heading, click window decoration.  In the command input field, enter the window decorator you prefer (emerald if you installed that, xfwm4 if not)
I have emerald installed, but am not sure what command to type into that field.  I tried just typing emerald, but nothing happened.

---

### Post by Whiffle on 2009-09-15
> **spkenny said:**
> hey sweet.  You've been a huge help.  When I started back in october last year, I wasnt getting much help.  I really appreciate this.  Can I private message you with any more questions, or just post again if something else comes up?

Eh its usually better just to post a new thread, I'm not always around.

---

### Post by Whiffle on 2009-09-15
> **spkenny said:**
> ok, another problem.  Everything seems to be going ok up to the part where he says "Beneath the Effects heading, click window decoration.  In the command input field, enter the window decorator you prefer (emerald if you installed that, xfwm4 if not)
I have emerald installed, but am not sure what command to type into that field.  I tried just typing emerald, but nothing happened.

Hmm, emerald should do it.  If you type "emerald" into a terminal and hit enter, does it give back any errors?

---

### Post by spkenny on 2009-09-15
OMG!!!!!! I am so pulling my hair out!  Nothing but video card issues once again.  Basically, I was reading everything I could find on installing compiz.  With a few variances here and there, they turned out to be the same in explanation.  I had put emerald in, but when I ran it to test, it wouldnt do anything at all.  Just the desktop as is, nothing popping up.  I did go to screen savers to check them out, and interestingly enough not all of them are showing in preview mode.  Even went through my video cards (5 of them) to see what might work.  Put in an Xabre 200-64 to try, and the resolution went to lowest availiable.  Obviously not working, I put the TNT2 back in and now it wont get out of low resolution mode.  Not sure what I screwed up, but I just know with the 2 cards I described, I have had no trouble using them in windows at all.  Perhaps I need to start from square 1, and make sure I have the driver installed properly.  So far I have let the automatic driver installation do it's thing for Nvidia Proprietary drivers.  Starting to remember why I got so frustrated doing this months ago.

---

### Post by spkenny on 2009-09-15
here is a thread I found concerning nvidia. [http://ubuntuforums.org/showthread.php?t=1159489&highlight=Nvidia+TNT2](http://ubuntuforums.org/showthread.php?t=1159489&highlight=Nvidia+TNT2)

Does this mean my TNT card wont work?

---

### Post by Whiffle on 2009-09-15
Does it say which version of the nvidia drivers you've got?  I think the drivers that went with jaunty when it originally came out may not be compatable, but there are new ones that have been released since that should work.

See here:
[http://ubuntuforums.org/showpost.php?p=7869601&postcount=5](http://ubuntuforums.org/showpost.php?p=7869601&postcount=5)


And if all else fails, take a break.  Being frustrated sucks.

---

### Post by spkenny on 2009-09-15
ok, so I've reinstalled Xubuntu.  Might as well start from scratch eh?  But also because I wanted to dual boot with my xp pro.  So, with the vid card should I follow the link on your last post on what to install reguarding a driver?  Because the automated installation obviously isnt working.  I need to take this much slower, so I'll wait for your response :-)

---

### Post by Whiffle on 2009-09-15
Thats what I would try.  Those three commands in that post should install the latest driver available for that video card.

---

### Post by spkenny on 2009-09-15
ok, finally got everything back on.  Had a couple issues with the installation, but everything appears fine now with a 3rd attempt.  Anyways, I ran the compiz check, and in the description it says Error: nv driver in use.

The nvidia drivers that are listed to look for in the package manager, I cannot find.  There is a driver on the nvidia site itself, but I cannot figure out how to install it manually from the download.

---

### Post by spkenny on 2009-09-15
you know what?  I'm gonna put this on the back burner for a bit until I can get a video card with a lot less issues.  So as  final question, have any suggestions on what to look for?

---

### Post by spkenny on 2009-09-16
Update:  It seems there is a driver download for the TNT2 card on the nvidia site.  I downloaded the file, but am unable to figure out how to execute and install it.  The specific instructions are: 

Type "sh NVIDIA-Linux-x86-1.0-9639-pkg1.run" to install the driver, then edit your X config file as appropriate.

After keying that in, it cant seem to locate the file (even though its right there on my desktop).  And I have no idea what an X config file even is.  Somebody help me?

---

### Post by gordintoronto on 2009-09-16
> **spkenny said:**
> Update:  It seems there is a driver download for the TNT2 card on the nvidia site.  I downloaded the file, but am unable to figure out how to execute and install it.  The specific instructions are: 

Type "sh NVIDIA-Linux-x86-1.0-9639-pkg1.run" to install the driver, then edit your X config file as appropriate.

After keying that in, it cant seem to locate the file (even though its right there on my desktop).  And I have no idea what an X config file even is.  Somebody help me?

When you start a terminal session, you will be in your Home folder/directory.  To go to the desktop,

cd Desktop

Note the capital "d".  Linux pays attention to case.

Then you can enter the "sh" command.

I don't know where the X config file is, but I suspect you can use a GUI tool such as Preferences/Display.

---

### Post by Whiffle on 2009-09-16
Here's a howto:

[http://forums.nvidia.com/index.php?showtopic=99513](http://forums.nvidia.com/index.php?showtopic=99513)

---

### Post by spkenny on 2009-09-16
Cool, I'll have to try that once I get home.  However, I dont quite understand step 5 if you could help me with that.

---

### Post by Whiffle on 2009-09-16
In step 5 he is saving the driver in one place, and then creating a link to it in another place.  I've never actually had to do that, but I don't see any reason it would hurt anything.

Also make sure you use the legacy drivers you downloaded from nvidia, not the ones that they tell you to download in that howto.

---

### Post by spkenny on 2009-09-17
Ok, so I've gotten all of the explanation done, up until where I have to open the Nvidia driver and install it.  I am unable to move it to another folder location (it was automatically saved to the desktop).  I then changed the settings in firefox to save in /usr/src just like the description.  But when I save to the new location, the new download does not appear to be saving.  It is still however on the desktop.  Can you just show me how to open and install a .run file from the desktop?

---

### Post by Whiffle on 2009-09-17
sure.

```

chmod +x ~/Desktop/the_file.run
sudo sh ~/Desktop/thefile.run

```

---

### Post by spkenny on 2009-09-17
Whiffle,

I would like to thank you for all your help.  I got the proper driver installed for the card, however I still cannot get it working with compiz.  This is my last post for this thread, as I will just work with xubuntu when I get a better video card installed.  This particular one is just too much hassle, and wearing on my patience.  I'll keep you in mind if I have any more questions :-)

---

