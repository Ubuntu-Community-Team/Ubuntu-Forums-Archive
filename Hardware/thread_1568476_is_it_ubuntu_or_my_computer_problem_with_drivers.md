---
title: "is it ubuntu or my computer? problem with drivers"
date: 2010-09-05
forum: Hardware
---

### Post by abelito8 on 2010-09-05
I am using an AAO 160 GB 11.6 screen and running Ubuntu 10.4 and have a very curious set of related problems

1) the brightness of the screen is the lowest by default...ok this has been discussed BUT I can adjust it in a very singular way

I log in, suspend and resume....if it resumes then it does it with maximum brightness 

what makes me suspect there is something wrong with the computer is that the brightness is lowest also when booting windows (I have kept a dual boot for Skype does not always work)

IF it resumes because, when I touch the switch button it resumes but does not switch on the screen X_X...upon suggestion from this forum learned I have to type Ctrl Alt and F1, F2 etc...until it fully resumes (my rate of success is around 75%, otherwise I have just to switch it off and on again)

When it resumes from suspend the sound (and video players) will work once out of two times...for instance I try to play some music, open rhythmbox and the application refuses to play a song....then I suspend again, resume (if possible) and I can enjoy my music....

It sounds like my computer has an autonomous life....does it sound like a driver problem or I should contact ACER assistance? (the computer is still in warranty)

thank you

---

### Post by Lateralis on 2010-09-05
Hi abelito. 

1) The laptop screen brightness should be configurable.  System -> Preferences -> Power Management.  Under the "On Mains Power" tab you can select how bright your screen should be (when plugged in) and on the "On Battery Power" you can chose to have Ubuntu reduce the brightness from its maximum setting.  You can also add a screen brightness applet to the Gnome panel: right click the panel -> Add to panel -> select Brightness Applet.  

2) When I switch back on from suspend the screen is black too.  But, that's just a power saving option.  When I touch the mousepad or press any key the screen lights back up again.  Can you confirm that this is not the case and that nothing you do will show you a password prompt or your desktop.  

3) I've had problems with Skype in the past in Linux, where it says something about only allowing one instance of Skype to run at a time.  I forget the exact message unfortunately.  If that sounds like your issue, then the simple solution is to delete (or if you prefer, move/rename) the .Skype directory in your home directory.  If that's not the problem then I'm sure we can help with that.

4) The sound and video is more perplexing.  What do you mean by "rhythmbox ... refuses to play a song."  Does the song actually "play" just with no sound?  Do you get an error message?  Or does Rhythmbox just do nothing?  

Have you noticed any of these things in Windows after a suspend?

---

### Post by abelito8 on 2010-09-05
Thank you for your detailed reply Lateralis

1) the laptop brightness is not configurable in ubuntu (nor in Windows). I have an applet on my top bar and when I click on it, it says that ubuntu cannot control it. The same when I go through System >> Preferences

2) when I resume my screen is black and no mouse movements is of any help. Simply the monitor is off and I do not know what miracle the Control - Alt F(1-12) buttons do but they normally do the trick...still, it is weird

3) skype do I simply have to remove/rename/delete a folder? My only problem with skype is my microphone. The Acer default one (the little hole in the computer) does not work and I have to plug an external mic but sometimes the level of background noises is higher than my voice and my interlocutor cannot hear me clearly

4) sound and video: I simply open an application (rhythmbox but could be anything, VLC, Movie Player, Amarok etc...) and click on a file (song/film) it shows it's playing the file but no sound (video) comes out and the cursor (the arrow that moves from left to right showing how much has been played) remains on 0. As I said if I simply suspend and resume then the application starts immediately playing a song/movie, the arrows moves and everything is as it should...still, it's a mystery the relationship between resume from suspend and the video and audio cards isn't it?

windows works normally bad as it should otherwise

---

### Post by Lateralis on 2010-09-05
First of all... interlocutor is a very underrated word!  I like it!  

As for everything else, I have to admit that I'm not sure I can help you much.  At least, there is nothing that I can think of at the moment.  Inspiration might strike me later, but at the moment everything to me just sounds pretty strange. :P  

Unconfigurable screen brightness for a laptop just sounds bizarre.  Not sure why Acer would not allow you to change the screen brightness... 

My solution for my Skype issue definitely will not help with yours.  I took a punt at what your issue might be but it is different from mine!  Anyway, the microphone not working in Skype could be related to sound drivers or, more probably, the setup of your sound card.  I might be able to help with that but will need to dig out some info I've got saved somewhere when I had issues with my sound card and webcam on my laptop. 

The laptop not waking from suspend properly... dunno.  As a check, which kernel version are you using?  If you don't know, type 

[code]
uname -r
[/code

into a terminal.  That will tell us.  

As for the sound/video issue, can I just get clarification.  You say that sound/video files doesn't play but then you suspend and resume and then they do.  Do you then mean that if you load up the laptop from scratch you can't play sound and video files, but suspend and resume once makes everything OK?  And you can suspend/resume as often as you like and you can always play on those subsequent occassions?

---

### Post by abelito8 on 2010-09-06
I also like interlocutor :)

the kernel version is
2.6.32-23-generic

as for the sound it works like this: I switch my computer on, the sound works but the brightness is low. I go to suspend and resume and the brightness is ok (not modifiable but ok) but 80% chances the sound does not work (I can open skype, try to play some music or any other audio device, it won't work)

then I have to suspend again, then resume and this time sound and brightness will be ok

I might want to suspend it for a while (if I go out or have to take the computer somewhere), then on resume the sound will not work....will have basically to resume twice!!!

...if, meanwhile, the computer does not decide not to resume from suspend mode...in which case I simply have to press the start button until it shuts down and then restart....

it works like an old car, with all problems that you learn to manage after a while...but ehi, I bought this computer in January!!!

That's why I started thinking it could be a hardware problem...

---

