---
title: "Semi-Frustrated New User Needs Some Help! ^_^"
date: 2009-04-26
forum: Hardware
---

### Post by Ripp_Steakface on 2009-04-26
Hello everyone. I just posted a bit ago about a trackpad issue I'm having where it causes the cursor to jump horizontally when you put your finger down onto it. I decided to make a new thread for a few other issues I'm having. I'm new to Linux, so if I have to use Terminal commands, be gentle please :) First, my PC's specs:

Eee PC 900HA
160GB hard drive
1.6GHz Intel Atom
Dual-booting Ubuntu 9.04 Netbook Remix and Windows XP

1. The sound is really low, and I have everything turned up to max. I've tried installing eee-controls, but the Terminal command doesn't want to download it. I'm not sure if this would fix the problem or not.

2. I have two versions of Java - 5 and 6. I had to install them to get some Airport controls to work in Terminal (I was having network issues between Ubuntu and my Apple Airport Extreme base station). I have since worked out the kinks without having to use the Airport controls, but I had previously made Java 5 my default. I tried to make Java 6 my default now, but this brings me to my next issue...

3. Videos barely play in Firefox. I went to view a YouTube video and I was prompted with downloading a codec to play the video. I installed it, but the videos only display a frame every 10 seconds; the sound, however, is fine, but too low volume (see issue 1).In addition, videos don't just display - a large ( I> ) icon is over it, and I click that to display the video, which I must then click the Play icon. The fan on this little netbook flips into high gear as well. This seems really odd because I have no trouble viewing videos in Windows - it isn't the hardware. I have since removed the codecs that were installed. Still the same issue.

EDIT: I fixed this issue. There were two different codecs, one was installed with the OS, the other was optional. The optional one screwed up the playback by "overencumbering" my processor. I can't remember the names of the codecs... if I remember or see them again I'll post to help out anyone searching.

EDIT 2: The issue still isn't fixed. SOME videos work, most don't. I get a prompt to install "GStreamer for mms, wavpack, quicktime, musepack" - when this is installed, all the videos run like molasses.

4. I'm prompted to enter a password to start up my wireless connection upon login, but apparently I made this password different than my universal one that I type for everything else. Is there a simple way to change this wireless password?

I know it's a lot, but I could really use the help. I like Ubuntu a lot, I just want to get it working for myself and my fiance - I need things to work simply for her, or she'll be using Windows instead :( Thanks in advance!

---

### Post by firebirdworks on 2009-04-26
> **Ripp_Steakface said:**
> Hello everyone. I just posted a bit ago about a trackpad issue I'm having where it causes the cursor to jump horizontally when you put your finger down onto it. I decided to make a new thread for a few other issues I'm having. I'm new to Linux, so if I have to use Terminal commands, be gentle please :) First, my PC's specs:

Eee PC 900HA
160GB hard drive
1.6GHz Intel Atom
Dual-booting Ubuntu 9.04 Netbook Remix and Windows XP

1. The sound is really low, and I have everything turned up to max. I've tried installing eee-controls, but the Terminal command doesn't want to download it. I'm not sure if this would fix the problem or not.

2. I have two versions of Java - 5 and 6. I had to install them to get some Airport controls to work in Terminal (I was having network issues between Ubuntu and my Apple Airport Extreme base station). I have since worked out the kinks without having to use the Airport controls, but I had previously made Java 5 my default. I tried to make Java 6 my default now, but this brings me to my next issue...

3. Videos barely play in Firefox. I went to view a YouTube video and I was prompted with downloading a codec to play the video. I installed it, but the videos only display a frame every 10 seconds; the sound, however, is fine, but too low volume (see issue 1).In addition, videos don't just display - a large ( I> ) icon is over it, and I click that to display the video, which I must then click the Play icon. The fan on this little netbook flips into high gear as well. This seems really odd because I have no trouble viewing videos in Windows - it isn't the hardware.

4. I'm prompted to enter a password to start up my wireless connection upon login, but apparently I made this password different than my universal one that I type for everything else. Is there a simple way to change this wireless password?

I know it's a lot, but I could really use the help. I like Ubuntu a lot, I just want to get it working for myself and my fiance - I need things to work simply for her, or she'll be using Windows instead :( Thanks in advance!

Wow, that is quite a lot of problems.  If I were you, I would start from scratch, but I do that alot.

As far as your sound, double click on the sound button to pull up the AlsaMixer config screen.  Make sure that all of those options are up with your sound.

Hope that helps!

---

### Post by Ripp_Steakface on 2009-04-26
Thanks for the reply! Double-clicking the speaker icon in the top right just mutes the sound, but I've checked in the Volume Control and Sound apps and everything seems to be up fully. I'm seeing other threads now asking about sound issues in 9.04, so I assume I'm affected as well until a fix is out.

---

### Post by FirstTimeMan on 2009-05-14
Hi.

no luck with the sound issues currently?

I too have a 900ha with low sound. i just recently completed my second ree-install of UNR  9.04. First was because the file system currupted and second because I could not fix the desktop switcher bug for some odd reason.

Anyways, this was the only thread I could find on the forums concerning 900HA low sound, I was wondering if anyone has sovled this issue as yet?


-FTM

---

### Post by radi0j0hn on 2009-05-14
On my Asus Eee PC I needed to turn up the "line in" volume to get it louder.

---

### Post by FirstTimeMan on 2009-05-18
> **radi0j0hn said:**
> On my Asus Eee PC I needed to turn up the "line in" volume to get it louder.


Thanks, I will try that.

But did your sound become normal, like having normal volume?

-FTM

---

### Post by PumpkinSonnema on 2009-06-22
MSI Wind, same thing.  In the volume control window, "front" needed to be all the way up.  Now it's louder than the windows volume.

---

### Post by vilar on 2009-06-22
Have you tried on terminal console:
 
```
sudo alsamixer
```
 
then crank all the volume up on all specs, you can browse through sound channels by using your arrow keys.
 
It worked for me.

---

