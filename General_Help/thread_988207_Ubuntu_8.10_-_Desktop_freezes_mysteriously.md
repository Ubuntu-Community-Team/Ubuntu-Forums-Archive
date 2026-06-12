---
title: "Ubuntu 8.10 - Desktop freezes mysteriously"
date: 2008-11-20
forum: General Help
---

### Post by jadhav333 on 2008-11-20
Sometimes my desktop just freezes. and there are some vertical blue dotted streaks across the screen. The mouse works but nothing on the desktop can be clicked.

Assuming some compatibility error due to any recently installed software, I did a clean install of the OS. But the proble still persists.

Though it occurs randomly, it usually occurs while I am using firefox browser 3.0.3.

This is the first time since I am using ubuntu (since version 6.06) that I am encountering an issue like this. 

I am unable to give a screenshot becoz even the print scrren functionality doesnot work during the freeze.

[B]Has anybody come across a similar problem?
Can anybody suggest a solution?
[/B]

 
**My Spec**
[COLOR="Navy"]Quadcore intel cpu Q6600@2.4Ghz, 4 Gb ram
Ubuntu 8.10 Intrepid Ibex 64bit
Partition Info:
\-------------------Root------------10GB
\Home-----------Home----------10GB
\Media\Sda3---Data folder--400Gb[/COLOR]

---

### Post by jadhav333 on 2008-11-20
see how the screenlooks during the freeze.. (refer to blue streaks) err.. oops.. the streaks did not get captured in printscreen. 
pls ignore this post..

---

### Post by jadhav333 on 2008-11-20
The problem now persists across installations. I tried booting off a live CD 7.04 / 8.10 still the blue streaks and desktop freeze occurs.

**One possible solution: I tried booting 8.10 in recovery mode and there was an option to fix X server (which overwrites xserver configuratiosn with default values) then resuming normal boot and voila the blue streaks went away..**

Its too early to say whether the desktop freeze wont repeat but it seems the problem has to do with the default video drivers from ubuntu specifically nvidia based.

Any else can try this out and reply back with their feedback.

---

### Post by omikun on 2008-11-21
Yeah mine does too but without any streaks. The keyboard doesn't work on terminal but works on firefox or other applications. I can't ctrl+alt arrow to change desktops or click on any OS toolbars or folders on the desktop. I just have to relogin to fix it. It happened when I upgraded to 8.10 from 8.4 through the alternate.iso and it just happened again after I tried to play a movie on vlc. This is really annoying.

---

### Post by asearle on 2008-11-22
Yesterday I installed Kubuntu 8.10 with KDE 4.1 on two of my PC's:  one an older desktop with 1,2Gz & 500Mb RAM PC and a newer ASUS Z92 laptop with 1.8Gz & 2GB RAM.  I then installed all updates and a few packages (e.g. Firefox)

On both machines the installation went fine and I was/am very impressed with both the speed and the functionality.

However, both machines freeze up randomly and causing me to need to power-down and re-boot.  The slower PC completely freezes (including the mouse) and the laptop freezes but the mouse is still available (although I can't click on anything).

The installations have taken several hours and basically I am very impressed with Kubuntu but, if it continues freezing, then I will have to wipe it.  Arrrggghhh!

Is this a known problem?  Will it be fixed in an update soon?  (I hope so)  Or is this a hardware problem indicating that Kubuntu 8.10 isn't for my PC?

Many thanks on any tips that you can give.

Regards,
Alan Searle

---

### Post by jadhav333 on 2008-11-22
some common factors:

1) similar issues are happening at the same time across users.

2) mostly affects user with nvidia / ati display cards

3) in my case: the problem repeats even with clean installs of prev versions. which suggest it could be a hw problem not related to ubuntu.

---

### Post by ywilliams12345 on 2008-11-22
I have had the same problem:
display, keyboard, mouse freezing after 1 to 10 minutes.
I have to do a hard reboot.
I do not have any graphics card.
My graphics is from my system board.
I could find the details if necessary.
It has been stable for 10 minutes now, maybe fixed
after the last update???

AMD64
8.10

---

### Post by jadhav333 on 2008-11-23
I have curr installed 8.10 in safe graphics mode. of course the display sucks.. but atleast i am able to access my machine and surf the net. 

I strongly believe this is a nvidia related compatibility error which may arise in conjunction with wifi/wimax network access.. 

I think the linux community got to address this compatibility issue. I have raised a query on the launchpad site.. 

[https://answers.launchpad.net/ubuntu/+question/52240]("https://answers.launchpad.net/ubuntu/+question/52240")

but nobody has answered it for the last 6 hrs.

---

### Post by jadhav333 on 2008-11-23
I believe that many people with nvidia cards are having problems desktop freezing issues.

How is it that no solution has been worked out yet?

Nor does it seem to be a critical issue, considering the fact that no major 
thread seems to be considering a resolution.

If this continues for long, I would be left with no choice but to shift to windows. oh nooooooooooo.

come on community.. 

Is there something that i am not aware off..

---

### Post by jadhav333 on 2008-11-24
Help !!

---

### Post by silverglade00 on 2008-11-24
jadhav333, from your launchpad post, I would bet that it is a hardware issue. The fact that Windows freezes up on it confirms it. It gave a pci.sys error, so you might want to try to take the card out and put it back in. Hopefully it has just come loose a little and needs to be reseated in the slot.

---

### Post by jadhav333 on 2008-11-24
Thanks. I had tried that once. But I don't mind giving it a try, once again, to be sure.

Hope it is just that. 

I usually am on my PC for around 12-15 Hrs a day at a stretch.
My eyes are tired of seeing this low (800x600) resolution screen with vertical dotted streaks, for the last two days. :(

---

### Post by jadhav333 on 2008-11-24
Hi silverglade00, and all, the issue resolved by itself. I was planning to re-seat the card next day morning. as suggested by silverglade00. 

I get up in the morning and see that the vertical streaks are gone. huh.

I tested by renaming the xorg.conf files to something else. and doing a 'ctrl+alt+backspace' for a xserver restart. 

The system detected the display properly and I have my screen resolutions back to normal.

In all probability this was a hardware glitch, which spoilt my weekend :) Off I go to update my launchpad report. Thanks for all your support

---

### Post by brodock on 2008-12-11
I have a dell e521 with a Geforce 6150LE and i'm getting lots of system freeze (not evan the keybord lights nor the mouse works)...

So i had to repartition the Hardrive to re-install windows xp and try to make it freeze again, so i can make dell support to go to my house and give me a new motherboard.

But i'm a little afraid that it can be some linux related problem that will not show up on windows (to my suspicious list i have the new Xorg and the nvidia drivers but, i already tryied all the 3 versions available on 8.10, so if i got it not working, i will have to install 7.10 or something like that to proove myself i'm wrong.)

---

### Post by Arup on 2008-12-11
Please try turining off desktop effects in appearance to see if this problem goes away.

---

### Post by nocwage on 2009-01-17
I am having the same problem but I have an ATi video card..
I was about to put in an Nvidia one just to see if it helps but since the rest of you have Nvidia cards I guess it's just me.

I was running Ubuntu 8.04 and everything was fine, I upgraded to 8.10 last weekend and it has frozen 3 times so far.
The desktop is the only thing affected, if I use a serial terminal or ssh to the machine everything is fine, no processes have gone out of control.

With the ATi card I have NOT installed the ATi drivers, I'm going to try it now and see if that makes any difference..

---

### Post by nocwage on 2009-01-17
Oh, I am running vmware server 2.0 on the machine.. I don't know if that matters but someone else mentioned VMware.

---

### Post by walter_j on 2009-01-17
Firefox has an issue re system freezes. Check out this link.

[http://news.softpedia.com/news/Who-Freezes-The-System-Firefox-or-ext3-86242.shtml](http://news.softpedia.com/news/Who-Freezes-The-System-Firefox-or-ext3-86242.shtml)

I find firefox to be very buggy, with many crashes per session. I'm trying Opera until they sort it out. I would use Konqorer if I could figure out how to install the flash player in it.

Walter

---

### Post by jamessnell on 2009-03-12
Howdy, I'm having a problem similar to this - seems that when I come back to my computer after leaving it for a brief time, it will have rebooted on me. I've disabled the power management daemon with no noticeable effect. 

My machine is running fully updated Ubuntu 8.10 AMD64 with an ATI video card.

---

### Post by jswilliams on 2009-03-19
NOOB HERE!!!!

I am having similar problems with my computer. I went cold turkey to Ubuntu 8.10 from winblows. I have been very satisfied so far but in the last few weeks, I have had graphics issues and random HARD lockups.....nothing works except the reset button and/or pulling the cord. The graphics problem shows up as horizontal lines, dots, blocks and other random stuff. They have no pattern and go away when the window is closed and reopened. It happens in all graphical windows. They seem to go hand in hand with the lockups (i.e. more graphic errors the more likely to crash.) I have an ATI card and have been using their "forbidden" drivers but went for a few months with no issues whatsoever. I removed them with no change. The MoBo has NVidia video so switching sounds like it wouldnt do any good. Any suggestions? What error logs should I run (and how) to provide more info?? Thanks for the help!!

---

