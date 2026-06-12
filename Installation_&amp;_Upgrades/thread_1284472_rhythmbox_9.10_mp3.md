---
title: "rhythmbox 9.10 mp3"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by fields2grand on 2009-10-06
Hey Yall
I've posted here a couple times before and got great support so I thought after my two day quest to get this to work I would ask for your help.

My Rhythmbox won't play my music anymore after upgrading to 9.10.  The great part about 9.10 is all my sound features work now without any work.  Even the keyboard shortcuts to volume up and down and mute work now!  Great news.  The problem is that now Rhythmbox won't play any of my music.  Let me tell you what I have done so far to try to fix the problem.

I've gone into Synaptic and reenabled a repository called "main restricted universe multiverse".  I also followed the script from Medibuntu to reinstall the repository and followed their directions to update.  I've sudo apt-get update and everything updated.  I've installed the gstreamer plugins including the ones that gave me troubles in the past.  I've also done the script to download restricted extras.

SO when I try to play a song in Rhythmbox it says it doesn't have the necessary plugins to play the song and give me a GStreamer element autoaudiosink as the requested plugin but cannot find it. 
I'm not sure if this will help but Flash video as well as VLC player plays audio fine.  I've spent quite a lot of time on this and can't get Rhythmbox to play my audio.  I'm sure some of you knowledgeable people can help a noob out with this.  I installed Jaunty about 2 months ago cold turkey from windows and haven't looked back.  This forum is the only reason why I haven't gone back to Windows.  It can be tricky sometimes but your help makes it much better.   Thanks EVERYONE for responding and helping me with this issue.  I will check this post regularly until the problem is fixed.

---

### Post by jmwink on 2009-10-06
I'm not sure that I have helpful suggestions, but I have a question that might be helpful:

Will Rhythmbox play music that is encoded in a format other than MP3 such as ogg or FLAC?

---

### Post by fields2grand on 2009-10-06
I'm sorry Jmwink but the only audio I have is mp3.  I dont have any ogg or flac.  I USED to until my windows machine flatlined and now i'm starting my media collection from scratch with Ubuntu.  Unfortunately I don't have those formats but maybe down the road someone will look at this post and want to know what your suggestion is who may have ogg or flac files.

I feel like I've updated and reinitiated so many files that I've gotten lost in the mix somewhere and don't know where I have or have not been.  I install something and logout and back in and forget what I did three steps ago.  I'm not sure EXACTLY what I've done and what I haven't done.  It's semi frustrating.  I used to troubleshoot software and hardware problems working for the geek squad (please no flames) and this linux stuff is getting the best of me for sure.

---

### Post by Xupit3r on 2009-10-06
jmwink, I am sure you have already discovered this, but Rhythmbox certainly does play .ogg and .flac file.  As a matter of fact, it is less of a hassle dealing purely with those file types as Rhythmbox plays them out of the box.

---

### Post by fields2grand on 2009-10-06
> **Xupit3r said:**
> jmwink, I am sure you have already discovered this, but Rhythmbox certainly does play .ogg and .flac file.  As a matter of fact, it is less of a hassle dealing purely with those file types as Rhythmbox plays them out of the box.


Do you have a suggestion Xupit3r?  I just uninstalled and reinstalled Rhythmbox but it still asks for the "GStreamer element autoaudiosink" plugin.  Thank you!

---

### Post by bshosey on 2009-10-06
go to synaptic and search for gstreamer bad and ugly and if installed remove. Then reinstall them. My have to restart computer.

---

### Post by fields2grand on 2009-10-06
Ok, I just did that and it didn't work.  Rhythmbox is still asking for the GStreamer element autoaudiosink plugin.

---

### Post by bshosey on 2009-10-06
OK. Try reinstalling GStreamer Good Plugins

---

### Post by fields2grand on 2009-10-06
Ok I reinstalled the good plugins and that didn't work either.  I installed Amarok and it won't play audio either.  Thanks for helping.

---

### Post by bshosey on 2009-10-06
are you still getting the error? and does it not play any audio?

---

### Post by bshosey on 2009-10-06
OK let try this. type gstreamer-properties in terminal. for audio choose pulse audio

---

### Post by fields2grand on 2009-10-06
Ok I changed to Pulse Audio and I'm still having the same problem

Yes I'm still getting the same error.  Flash in Firefox audio works fine.  I just can't play any of my mp3's.  Thanks for the help!

---

### Post by bshosey on 2009-10-06
Also make sure you have gstreamer0.10-pulseaudio installed.

---

### Post by bshosey on 2009-10-06
try to open mp3 in totem ( video player ) and see if you get the same error.

---

### Post by fields2grand on 2009-10-06
Yeah it worked in movie player!  So how do I transform that to rhythmbox or amarok?  THANKS FOR THE HELP!

---

### Post by bshosey on 2009-10-06
OK. Then I would not think it is a gstreamer issue. Totem uses gstreamer. OK. try this type this in the terminal

sudo apt-get remove rhythmbox

then type this.

sudo apt-get install rhythmbox

---

### Post by fields2grand on 2009-10-06
Ok I uninstalled rythmbox and reinstalled.  still no change.  Audio files are still playing in totem though.

I would like to mention that I'm logging off and back on after every suggestion.  I don't know if I'm supposed to.

---

### Post by bshosey on 2009-10-06
OK. try this

sudo apt-get remove --purge rhythmbox

then 

sudo apt-get install rhythmbox

---

### Post by fields2grand on 2009-10-06
Ok I did the purge uninstall and it was still a no go.  Neither Amarok or Rhythmbox worked but totem still does.

---

### Post by bshosey on 2009-10-06
OK. I am looking at something else. Don't give up.

---

### Post by fields2grand on 2009-10-06
Oh believe me I am not going to give up as long as you are here.  I really appreciate the help.

---

### Post by bshosey on 2009-10-06
OK. this is a long shot. type this in terminal
gconf-editor

then navigate to /system/gstreamer/0.10/audio/global

in there make sure then right click on the key and make sure mp3 is listed.

---

### Post by fields2grand on 2009-10-06
Yup mp3 is listed.

---

### Post by bshosey on 2009-10-06
OK in rhythmbox if you go to preferences do and click on the music tab in the preferred format can you choose mp3?

---

### Post by fields2grand on 2009-10-06
Yes I can.  I selected it but it still doesnt play.

---

### Post by bshosey on 2009-10-06
make sure libtag1-vanilla is installed.

---

### Post by fields2grand on 2009-10-06
Yup it was installed.  I just reinstalled it.

---

### Post by bshosey on 2009-10-07
Sorry I lost internet connection and it was late. I will try to think up some stuff to help. Sorry I was not much help last night.

---

### Post by bshosey on 2009-10-07
Try running this command and the restart the computer

gst-register

---

### Post by fields2grand on 2009-10-07
Thanks for coming back.  I thought you had gone.  I tried your command but it's not found.

---

### Post by bshosey on 2009-10-07
Well I am at work now. When I get some free time I will look some more.

---

### Post by fields2grand on 2009-10-07
Well Bshosey we may have found a solution.  I can't get rhythmbox to work but Amarok now plays mp3 after doing this  [http://www.linuxforums.org/forum/ubuntu-help/106850amarok-wont-play-mp3.html](http://www.linuxforums.org/forum/ubuntu-help/106850amarok-wont-play-mp3.html)   It suggests installing **libxine1-ffmpeg **via synaptic.  That made Amarok play mp3's.  Which is great news.  Looks like I might be an Amarok user from now on!  You Bshosey have been a great help and are the reason why people don't throw their installs out the window and go back to windows.  Thank you very much.

---

### Post by bshosey on 2009-10-07
I bet if you did a new install not an upgrade that would work. But I do not want to recommend that because this should be an easy fix. I will continue to research this problem. Amarok is probably the best sound player for KDE. But I would prefer rhythmbox just because of gnome. Nothing wrong with Amarok. I just prefer gnome. Nothing wrong with KDE either.

---

### Post by bshosey on 2009-10-07
OK got an idea go to ubuntu software center and search for pulse. install PulseAudio Volume Control.

reboot computer and try to play the mp3.

---

### Post by bshosey on 2009-10-07
Also make sure gstreamer0.10-ffmpeg is installed.

---

### Post by andi666 on 2009-10-07
I had the same problem with two user accounts on my system after updating to ubuntu 9.10 beta. Fixed it by deleting gstreamers settings for each user. I dont know if it was neccessery but I did it in an xterm and not a gnome session, and then relogged into a gnome session.


rm -rf ~/.gconf/system/gstreamer
rm -rf ~/.gstreamer-0.10

---

### Post by bshosey on 2009-10-07
Interesting. I do not have those directories on my 9.10 install but mine is not an upgrade. Good ketch. I hope this works for him.

---

### Post by andi666 on 2009-10-07
Are you sure?
They were even newly created for each user after deleting the directories and logging in a gnome session. 

in my previous post I forgot to mention that they exist in each users home directory

~/.gconf/system/gstreamer
~/.gstreamer-0.10

---

### Post by bshosey on 2009-10-07
/home/bshosey/.gconf/system/gstreamer/0.10
/home/bshosey/.gstreamer-0.10

I do have these. I must have miss read or typed. Sorry you where right. I really hope that fixes his issue. I would hate for him to have to be forced to use Amarok. Now if he wants to use that then that is great. But if he does not it would be sad. Thanks for helping us resolve this issue for him.

I thought it was odd that he could play them in totem. Inless he has totem-xine installed.

---

### Post by fields2grand on 2009-10-09
> **andi666 said:**
> I had the same problem with two user accounts on my system after updating to ubuntu 9.10 beta. Fixed it by deleting gstreamers settings for each user. I dont know if it was neccessery but I did it in an xterm and not a gnome session, and then relogged into a gnome session.


rm -rf ~/.gconf/system/gstreamer
rm -rf ~/.gstreamer-0.10


I don't know what it means to run it in xterm and not gnome.  Can you elaborate?  Also, I can not find these files.

---

### Post by fields2grand on 2009-10-09
BShosey I installed Pulse audio volume control.  Didn't work and gstreamer0.10-ffmpeg is installed.  Thanks for the help!

---

### Post by bshosey on 2009-10-10
To delete the file just go to Click on Places. Then click on Home Folder, Then click on View, then put a check mark in Show Hidden Files. Then you will be able to find the files. 

xterm is Command Line. Click on Applications, Accessories, Terminal. That will get you in the command line.

---

### Post by fields2grand on 2009-10-10
LOL!  I deleted .gstreamer-0.10 out of my home folder after enabling hidden files.  Restarted and now rhythmbox plays mp3s!  thanks alot guys!  Hopefully this thread will help others!

---

### Post by bshosey on 2009-10-10
I am glad it worked!

---

### Post by johnyhoffman on 2009-10-19
Thanks for doing the work here guys. Had identical problems and after about 10 minutes of google mining came up with this gem! Thanks again!

---

### Post by The Thug on 2009-10-26
Music was playing perfectly in Songbird but wouldn't in Rythymbox.

After removing the necessary files/directories I have it now working.

Thanks for the help.

---

### Post by sleepynate on 2009-11-01
andi, thank you kindly for your suggestion. I can confirm this worked for me (aplay would produce sound, nothing in the gstreamer->pulseaudio pipeline would.)

---

### Post by tjpoe on 2009-11-02
> **andi666 said:**
> Are you sure?
They were even newly created for each user after deleting the directories and logging in a gnome session. 

in my previous post I forgot to mention that they exist in each users home directory

~/.gconf/system/gstreamer
~/.gstreamer-0.10

This worked great for me. thanks.

---

### Post by Alienhunter2010 on 2009-11-02
> **andi666 said:**
> I had the same problem with two user accounts on my system after updating to ubuntu 9.10 beta. Fixed it by deleting gstreamers settings for each user. I dont know if it was neccessery but I did it in an xterm and not a gnome session, and then relogged into a gnome session.


rm -rf ~/.gconf/system/gstreamer
rm -rf ~/.gstreamer-0.10

It works for me too! Thanks to all, guys!

Karmic Koala R.O.C.K.S.!

---

### Post by gigaforce1111 on 2009-11-04
> **Alienhunter2010 said:**
> It works for me too! Thanks to all, guys!

Karmic Koala R.O.C.K.S.!
I upgraded from 9.04 and had the same problem.
It worked for me also!!!
BTW you can install Gstreamer later it still works.

---

### Post by yasitya on 2009-11-13
Originally Posted by **andi666** 					[[IMG]http://www.uluga.ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://www.uluga.ubuntuforums.org/showthread.php?p=8068661#post8068661") 				
 				[I]I had the same problem with two user accounts on my system after updating to ubuntu 9.10 beta. Fixed it by deleting gstreamers settings for each user. I dont know if it was neccessery but I did it in an xterm and not a gnome session, and then relogged into a gnome session.


rm -rf ~/.gconf/system/gstreamer
rm -rf ~/.gstreamer-0.10

THIS WORKED FOR ME! Success!
[/I]

---

### Post by Snyder.4000 on 2010-03-29
> **andi666 said:**
> I had the same problem with two user accounts on my system after updating to ubuntu 9.10 beta. Fixed it by deleting gstreamers settings for each user. I dont know if it was neccessery but I did it in an xterm and not a gnome session, and then relogged into a gnome session.


rm -rf ~/.gconf/system/gstreamer
rm -rf ~/.gstreamer-0.10
  Thanks a lot, i have the same problem and this fixed, thank you :D

---

