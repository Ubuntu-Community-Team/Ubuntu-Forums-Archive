---
title: "dv6500 Sound Problems with Feisty"
date: 2007-07-01
forum: Hardware &amp; Laptops
---

### Post by zanelightning on 2007-07-01
Hi, I recently received my dv6500t notebook from HP and have put a fresh install of Feisty (x86 release) and worked through troubles with the nVidia video card and recently got the 4965agn wifi card working through ndiswrapper. However, I am (and always was) unable to hear any sound through either the speaker or the audio jacks.

The touch-sensitive buttons for volume function as they should, and the mute button does too (although the actual button is always red which is supposed to indicate that the sound is muted). I ran into some trouble when trying to compile the latest alsa driver and figured I should check here to see if anyone had any suggestions. 

Here's what I get for audio when I run **lspci -v**
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at f8500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

```

I haven't run into any errors; everything appears that it should be working fine, but there is no sound. Thanks in advance for any help.

---

### Post by Scotty562 on 2007-07-02
I have the same issue with my dv6500. I finally got mine booted to the live cd though so you're a bit ahead of me. I'm really looking forward to hearing what has to be said about the sound issue.

---

### Post by zanelightning on 2007-07-02
Hey Scotty, I was just able to get the sound working, I found the solution here: [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3165](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3165) . Just sign in as guest to view the forum.

Kentrosaurus gives his solution and links to where he found it...download the newest alsa driver, utils, and lib (I used 1.0.14rc4), replace hda_proc.c and patch_realtek.c from realtek10.tar.gz (on the page Kentrosaurus linked to, pshou explains how to do this).

Insert the line "options snd-hda-intel model=toshiba" on the end of /etc/modprobe.d/alsa-base. Finally, compile the driver using the directions here: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) .

If you have any questions, just ask!

Edit: Interestingly, though, the mute button is now always lit up blue, and it seems to only mute the front audio jacks. On the volume control, the "headphone" slider seems to affect both the headphone and line-out jacks, while "front" affects the built-in speaker. Also, at this point, the speaker does not automatically turn off when headphones are inserted, it needs to be manually muted.

---

### Post by bsawler on 2007-07-02
Hi, 

I too have a HP dvxx with very similar specs with no sound.  

I am very new to linux, so any help would be greatly appreciated.  For example I am stuck on the first instruction.  In installing realtek10.tar.gz?? I can't even find this.  I looked at realteks site but it is not the same for unix/linux.  So I did not download.  The next thing would be where to extract this file too? 

Pretty basic questions, but that is where my level is at.  I will keep plugging away.  Any "linux for dummies" help would be great. 

Thanks in advance.
Bradley

---

### Post by bsawler on 2007-07-03
Ok a good 5 hours tackling this to no avail. 

I have a HP Pavillion dv2000 and here are the steps that I took. But I cannot get the sound to work. 

1. Did everything according to the following first:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
I even added the following line as per this page:
options snd-hda-intel model=3stack

2. Downloaded realtek10.tar.gz
[https://bugtrack.alsa-project.org/alsa-bug/file_download.php?file_id=2057&type=bug](https://bugtrack.alsa-project.org/alsa-bug/file_download.php?file_id=2057&type=bug)
Extracted the 2 files and overwrote them into the following directory:
../alsa-driver-1.0.14/alsa-kernel/pci/hda/

3. Changed the model from '3stack' to 'toshiba' as explained in step 1 above.
Reboot > did not work

4. Changed the model from 'toshiba' to 'hp' as explained in step 1 above.
Reboot > did not work

Here are some outputs.

```
lspci -v 
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
        Subsystem: Hewlett-Packard Company Unknown device 30b2 
        Flags: bus master, fast devsel, latency 0, IRQ 23 
        Memory at d6400000 (64-bit, non-prefetchable) [size=16K] 
        Capabilities: <access denied> 

```
cat /proc/asound/card0/codec\#* 
```
Codec: Conexant CX20551 (Waikiki) 
Address: 0 
Vendor Id: 0x14f15047 
Subsystem Id: 0x103c30b2 
Revision Id: 0x100000 
Default PCM: 
    rates [0x40]: 48000 
    bits [0x2]: 16 
    formats [0x1]: PCM 
Default Amp-In caps: N/A 
Default Amp-Out caps: N/A 

5. Downloaded realtek11.tar.gz
[https://bugtrack.alsa-project.org/alsa-bug/file_download.php?file_id=2063&type=bug](https://bugtrack.alsa-project.org/alsa-bug/file_download.php?file_id=2063&type=bug)
Extracted the 1 files and overwrote them into the following directory:
../alsa-driver-1.0.14/alsa-kernel/pci/hda/

6. Re-compiled the installed as per:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
Reboot > Still no sound.

---

### Post by zanelightning on 2007-07-03
bsawler, I'm in no way an expert, I can just tell you what worked for me...if you actually did things in that order, that may be your problem. I believe you need to extract the two files into the source *before* you compile the driver, so it is compiled in with it, otherwise the files are just sitting in the source doing nothing. I'd say try replacing the files, then going ahead with the compile, that just might work.

---

### Post by zanelightning on 2007-07-03
I have just recently noticed this problem, and was wondering if anyone else was experiencing it with the same notebook: my dvd drive is not detected by Feisty. It works fine with Vista, and I was able to install Ubuntu using the drive, but after it was installed, Ubuntu has been unable to use the drive. In fstab, it is listed as /dev/hda, but I have no such device and am completely unable to locate what might be my drive, it is as if it doesn't exist at all. I don't know if this is a kernel issue or what, I just want to know if I'm alone in this or not.

---

### Post by Scotty562 on 2007-07-03
I installed the newest drivers, inserted those  two files, added that one line, and compiled and still nothing. What could I hav e done differently zanelightning? We have the exact same card!

Also, do you have a howto that got your wireless going? I've  been trying the guide for the native 4965 drivers but that's not going so well either. I'm starting to think ubuntu isn't quite ready for these machiens yet.

---

### Post by bsawler on 2007-07-03
Scotty562,

Check this tread out about boot up and subsequent wireless loading. 

[http://ubuntuforums.org/showthread.php?p=2958693#post2958693](http://ubuntuforums.org/showthread.php?p=2958693#post2958693)

---

### Post by Scotty562 on 2007-07-03
I just spoke too soon. I tried recompiling just for the hell of it and it worked!

Thanks for the link bsawler, I'll check that out right now.

---

### Post by l-fever on 2007-07-06
Scotty562, can you give me brief step by step how to on how you got your sound working? I have the 3945 wireless card, so my wireless worked right out of the box. TIA!

Steve

---

### Post by bsawler on 2007-07-06
After giving up and formatting my drive and reinstalling xp... I wasted no time reinstalling ubuntu shortly afterwards, cause I did not want to give up without a bit of a fight. 

I was able to get my sound working by the following:

1. Did everything according to the following first:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

For this I used "laptop-hp" 
options snd-hda-intel model=**laptop-hp**

---

### Post by Scotty562 on 2007-07-06
I'm at work right now but I'll write a howto up when I get some free time. My weekend is completely booked so it might not be until Monday night that I can write it. 

Basically go to [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) and follow the part where it says to download the latest version of alsa-driver, alsa-lib, and alsa-utils.

Go to [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3104](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3104) and download realtek10.tar.gz.
Extract to ../alsa-driver-1.0.14/alsa-kernel/pci/hda/

Follow the compile part of [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto). 

Reboot

Edit /etc/modprobe.d/alsa-base and insert "options snd-hda-intel model=toshiba" at the end of the file.

Reboot again.

It should work at this point. It did for me anyways. Good luck!

---

### Post by bsawler on 2007-07-06
Non related question. 

How do you post a new thread?? I am lost on this one.  I cannot find the option anywhere.

---

### Post by zanelightning on 2007-07-06
bsawler, just go to a category (e.g. Hardware & Laptops) and at the top and bottom of the thread list is a button that says "Make New Post." That's all!

Scotty and bsawler, I would like to know how all the aspects of your sound works now, like whether the mute and volume buttons on the laptop change the correct output (mine changes the headphone volume, not the speaker) and if the mute button light changes colors. Also, my speaker doesn't automatically mute when headphones are inserted (I don't care too much about this one, I'm just wondering if the different options change these things).

EDIT: Wow, I'm dumb...the option for which track the keyboard volume keys affects is in sound preferences. BUT, has anyone gotten the mic to work?

---

### Post by l-fever on 2007-07-06
> **Scotty562 said:**
> I'm at work right now but I'll write a howto up when I get some free time. My weekend is completely booked so it might not be until Monday night that I can write it. 

Basically go to [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) and follow the part where it says to download the latest version of alsa-driver, alsa-lib, and alsa-utils.

Go to [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3104](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3104) and download realtek10.tar.gz.
Extract to ../alsa-driver-1.0.14/alsa-kernel/pci/hda/

Follow the compile part of [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto). 

Reboot

Edit /etc/modprobe.d/alsa-base and insert "options snd-hda-intel model=toshiba" at the end of the file.

Reboot again.

It should work at this point. It did for me anyways. Good luck!

Thanks guys! 

 That worked! I didn't put the patched files in place before the compile! All is good now! Have the nvidia driver,sound and Beryl, and the wireless card is working now. This is great fun!

---

### Post by bsawler on 2007-07-06
zanelightning - thanks for the info. I'll give a go. 

Now for my sound.... I was excited to get sound out at first.  Now after getting sound I have noticed it is all a bit messed up. 

The master volume does not do anything.  If you right click on the speaker and open the Volume control: HDA Intel (Alsa Mixer), if mute the "Master" it does nothing.  The volume is controlled by the "PCM" sliders.  This is same for speakers & headphones. 

If you play music via Rythmbox etc. the volume control works on these applications.  

If you select the volume controls on the laptop itself, a horizontal slider will quickly show the screen with system beeps as you touch the controls.  The meter moves but the volume does not change (both speaker & headphone). 

If you select the mute control on the laptop, it changes from blue to red, but does nothing with the actual volume. (speaker & headphone). 

Ok I just noticed that the laptop controls (volume +/- and mute) control the "master" volume correctly of the Alsa Mixer, but as I said above the "master" does not work, as the volume is controlled by the PCM.  Therefore, guessing here, if we can change the control from PCM to Master then the laptop controls would work.  

Now for the mic.  I have an built-in mic (2 locations) on the screen on either side of the webcam.  When I went to sound recorder, it was set as "ExtMic" and it worked fine.  I did a skype test call, and it worked fine.  I did nothing for the mic.  I don't care about the mic cause I use a usb phone cause the feedback for others on skype is always a problem with mics hences I went to the usb phone 6 months back.

I'll have a look later, but for now, I need to get the sound controller to make my usb phone to work... grr. That is why I want to post  a new thread.

---

### Post by l-fever on 2007-07-07
Now that I have my sound working I need to do some testing with the volume controls. I can't seem to get my mic to work either.

---

### Post by bsawler on 2007-07-07
run: alsamixer

and make sure something isn't muted.

---

### Post by l-fever on 2007-07-07
> **bsawler said:**
> run: alsamixer

and make sure something isn't muted.

I can adjust the volume inside applications with the mixer but the slider buttons on the laptop and my mic are still not working. The slider graphics display on the screen but do nothing.

---

### Post by l-fever on 2007-07-07
> **zanelightning said:**
> I have just recently noticed this problem, and was wondering if anyone else was experiencing it with the same notebook: my dvd drive is not detected by Feisty. It works fine with Vista, and I was able to install Ubuntu using the drive, but after it was installed, Ubuntu has been unable to use the drive. In fstab, it is listed as /dev/hda, but I have no such device and am completely unable to locate what might be my drive, it is as if it doesn't exist at all. I don't know if this is a kernel issue or what, I just want to know if I'm alone in this or not.

Which cd did you use to install? I had the same thing happen to me when I used the i386 alternate cd full text install. I couldn't mount the cd/dvdrom drive after the install. I then installed with the i386 7.04 live cd with Scotty562's suggestion pressing f6 when booting the live-cd and adding all_generic_ide kernel boot option,and got the cd/dvdrom back.

---

### Post by zanelightning on 2007-07-07
Yeah, I did use the alternate install disk, thanks for the heads-up, though I'm not sure whether I really feel like reinstalling my system right now.

---

### Post by l-fever on 2007-07-07
Yeah, I hear ya, after 5 attempts, I'm finally feeling pretty good now. Just got to get the mic and the laptop slider volume controls to work. So far everything else is sweet!

---

### Post by zanelightning on 2007-07-08
l-fever, I was thinking of trying to reinstall using the livecd, but I wasn't able to boot it, it hangs, mentioning something about tty. My question is, what options did you have to get the cd to boot?

---

### Post by l-fever on 2007-07-08
Press f6 when starting the live cd and enter all_generic_ide to the end of the boot line and press enter. If you get an xserver error let me know.

---

### Post by zanelightning on 2007-07-08
Thanks l-fever, It worked like a charm! I reinstalled the system, and my drive was recognized with no problem...getting sound and wireless to work again was a bit of a pain, but not so bad after doing it once before. Thank god for my /home directory on a separate partition, that saved a lot of configuration and tweaking!

Also, does anyone else have this quirk...after disabling the touchpad (using the little button on the top of it), when I re-enable it, the Ubuntu Help Center is opened. It's mildly annoying at worst, I just thought it was funny (and a bit random!) :)

---

### Post by l-fever on 2007-07-08
> **zanelightning said:**
> Thanks l-fever, It worked like a charm! I reinstalled the system, and my drive was recognized with no problem...getting sound and wireless to work again was a bit of a pain, but not so bad after doing it once before. Thank god for my /home directory on a separate partition, that saved a lot of configuration and tweaking!

Also, does anyone else have this quirk...after disabling the touchpad (using the little button on the top of it), when I re-enable it, the Ubuntu Help Center is opened. It's mildly annoying at worst, I just thought it was funny (and a bit random!) :) 

Cool! I'm glad you are up and working! My touchpad button does the same thing! lol:)

---

### Post by torrent478 on 2007-07-25
I recently got the dv6500 and I'm having some of the same problems. I have wifi working but thats about it.  I havnt gotten my sound or Nvidia drivers/Beryl working... I havnt spent too much time on sound so I might be able to figure that out.

What I really need help with is the video, Some of you said you got it working with beryl so any help would be appreciated.


nvm, got it working with envy... audio is the last thing and then im set :)

---

### Post by l-fever on 2007-07-26
> **torrent478 said:**
> I recently got the dv6500 and I'm having some of the same problems. I have wifi working but thats about it.  I havnt gotten my sound or Nvidia drivers/Beryl working... I havnt spent too much time on sound so I might be able to figure that out.

What I really need help with is the video, Some of you said you got it working with beryl so any help would be appreciated.


nvm, got it working with envy... audio is the last thing and then im set :)

Taken from page 2 of this thread from Scotty562's reply:

Basically go to [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) and follow the part where it says to download the latest version of alsa-driver, alsa-lib, and alsa-utils.

Go to [https://bugtrack.alsa-project.org/al...ew.php?id=3104](https://bugtrack.alsa-project.org/al...ew.php?id=3104) and download realtek10.tar.gz.
Extract to ../alsa-driver-1.0.14/alsa-kernel/pci/hda/

Follow the compile part of [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto).

Reboot

Edit /etc/modprobe.d/alsa-base and insert "options snd-hda-intel model=toshiba" at the end of the file.

Reboot again.

It should work at this point. It did for me anyways. Good luck!
__________________

---

### Post by Scotty562 on 2007-07-27
Just for future reference for anyone trying to get the nvidia graphics drivers installed. You can use this little trick to get envy to work on gutsy. It will get the nvidia drivers installed for you. Compiz-Fusion DOES NOT WORK. Well, I should say it doesn't work for me at least. You guys are more than welcome to try it, and if you get it working please let me know.

[http://blog.chaoz.org/?p=6](http://blog.chaoz.org/?p=6)

Hey did any of you guys get your mic working? That's the only problem I still have with the sound.

---

### Post by l-fever on 2007-07-27
> **Scotty562 said:**
> Just for future reference for anyone trying to get the nvidia graphics drivers installed. You can use this little trick to get envy to work on gutsy. It will get the nvidia drivers installed for you. Compiz-Fusion DOES NOT WORK. Well, I should say it doesn't work for me at least. You guys are more than welcome to try it, and if you get it working please let me know.

[http://blog.chaoz.org/?p=6](http://blog.chaoz.org/?p=6)

Hey did any of you guys get your mic working? That's the only problem I still have with the sound.

I got Compiz/Fusion working great on Feisty. I have given up on the mic though. The envy script works great for the nvidia drivers. At least it does on my laptop.

---

### Post by Scotty562 on 2007-07-27
When I was on Feisty it worked well too. It has been an entirely different experience with gutsy though. Not like I don't expect some problems with alpha software though :). I'm glad to hear you have things working though.

---

### Post by l-fever on 2007-07-28
> **Scotty562 said:**
> When I was on Feisty it worked well too. It has been an entirely different experience with gutsy though. Not like I don't expect some problems with alpha software though :). I'm glad to hear you have things working though.

Oh, I misunderstood your post. I have been having all kinds of weird fun with gutsy. I have a backup image of my feisty install. I had trouble with the wireless drivers, sound, and video with gutsy, so I agree with you. I will continue trying out gutsy when I get some more energy!

Cheers!

---

### Post by l-fever on 2007-07-28
> **Scotty562 said:**
> Just for future reference for anyone trying to get the nvidia graphics drivers installed. You can use this little trick to get envy to work on gutsy. It will get the nvidia drivers installed for you. Compiz-Fusion DOES NOT WORK. Well, I should say it doesn't work for me at least. You guys are more than welcome to try it, and if you get it working please let me know.

[http://blog.chaoz.org/?p=6](http://blog.chaoz.org/?p=6)

Hey did any of you guys get your mic working? That's the only problem I still have with the sound.

Scotty562, did you use the same method to install the alsa drivers on gutsy as we did in feisty?

---

### Post by Bingulim on 2007-07-30
I am too unable to use the mic.

I could pass through the **painful** path for installing/booting/nvidia/speakers/wireless process (took me the whole weekend plus friday), but the mic and the webcam are still a problem.

I happen to use a dv6575us notebook.

Any news or advise are gladly welcome.:D:D:D

---

### Post by Bingulim on 2007-07-30
Oops.
Just one more.
The card reader doesn't work too.
:-(

---

### Post by Scotty562 on 2007-07-30
> **l-fever said:**
> Scotty562, did you use the same method to install the alsa drivers on gutsy as we did in feisty?

I actually didn't use Feisty at all. I started right with gutsy. I'm a risk taker like that ;).

---

### Post by l-fever on 2007-07-30
> **Scotty562 said:**
> I actually didn't use Feisty at all. I started right with gutsy. I'm a risk taker like that ;).


I like a challenge as well! And I have a really short attention span!

---

### Post by l-fever on 2007-07-30
> **Scotty562 said:**
> I actually didn't use Feisty at all. I started right with gutsy. I'm a risk taker like that ;).

BTW, I got compiz/fusion running on a fresh install of gutsy tribe 3. Did you get 'er going yet?

---

### Post by Scotty562 on 2007-07-31
Nope, I gave up on that. How did you install your graphics drivers? After that how did you install compiz-fusion?

You've given me hope :D.

---

### Post by l-fever on 2007-07-31
> **Scotty562 said:**
> Nope, I gave up on that. How did you install your graphics drivers? After that how did you install compiz-fusion?

You've given me hope :D.

You know this is the weird part.I used your trick on the envy script to install the nvidia driver. The only change that I made was to change the default depth to 24 in the xorg.conf and I added the compiz plugins and compiz manager through synaptic package manager and restarted and opened the compiz manager changed the default settings and compiz is up and running. I did do a fresh install of tribe 3 though. I did the usual compiling of the alsa stuff to get the sound working and that's were I'm at right now. If I remember anything else I will let you know. 

Steve

---

### Post by Scotty562 on 2007-07-31
Hmm... A fresh install... I don't really have the bandwidth to redownload all the updatees again :(. I did uninstall everything compiz related in Synaptic and then reinstalled it but I still can't get it working. this is with the new 22.9 kernel too. Makes me sad knowing someone else with the same hardware got it working though. My nvidia drivers are installed and workign fine. I can play 3d games and things like that. Maybe I'll get lucky and it'll be a bug that gets fixed tomorrow :).

---

### Post by l-fever on 2007-07-31
> **Scotty562 said:**
> Hmm... A fresh install... I don't really have the bandwidth to redownload all the updates again :(. I did uninstall everything compiz related in Synaptic and then reinstalled it but I still can't get it working. this is with the new 22.9 kernel too. Makes me sad knowing someone else with the same hardware got it working though. My nvidia drivers are installed and working fine. I can play 3d games and things like that. Maybe I'll get lucky and it'll be a b,ug that gets fixed tomorrow :).

I know what you mean, on my first attempt, I upgraded from feisty to gutsy and I manually removed all the compiz stuff, and I could not get it to work. I gave up and decided to do a clean install. So many updates! Fun stuff! All of my 3d stuff is working great right now as well. Compiz is pretty cool! I can always mail you a cd! Let me know!

---

### Post by Scotty562 on 2007-08-03
I ended up cheating :(. I reinstalled Feisty and did all the updates. I installed the nvidia drivers and then I used the guide here: [http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974) .
That brought my kernel up to the brand new gutsy kernel which had my wireless drivers built into it. Now I just have to figure out the sound. The guide we used for gutsy doesn't work the same on Feisty for some reason. I'll give it another whack tonight most likely.

And you are right, this is great fun! I love tinkering with this stuff until it finally works. When you finally have everything working the way you want it a new version comes out and the whole process repeats itself. Good times.. Good times..

---

### Post by dawg on 2007-08-27
im stuck on the extraction of the realtek driver.  "Extract to ../alsa-driver-1.0.14/alsa-kernel/pci/hda/"  i keep getting an error.  the error is...

Error while copying to "/usr/src/als...rnel/pci/hda".
You do not have permissions to write to this folder.

i tried changing the permissions on the folder, but it wont let me.  I tried using "mv" to try to move it that way but i got  "overriding mode 0644"  any ideas anyone?

---

### Post by l-fever on 2007-08-27
do a sudo cp source destination or you can use sudo nautilus to copy/extract the files.

---

### Post by dawg on 2007-08-27
you are a genius.  audio is working too.

---

### Post by torrent478 on 2007-09-02
ok guys, everything has been working fine, ive been using sound for a couple months now, but after an update today the sound is no longer working... is this a problem with just our laptops? or is it a problem as a whole with ubuntu? any of you guys have the same problem

---

### Post by kanna1620 on 2007-09-02
> 
Edit /etc/modprobe.d/alsa-base and insert "options snd-hda-intel model=toshiba" at the end of the file.


WHAT IS THIS MODEL???? HOW CAN I KNOW MY MODEL???? PL SOMEBODY HELP ME

---

### Post by torrent478 on 2007-09-02
seems like a lot more people are having the sound problem after the update too. 

I tried doing what they suggested which was re-compiling ALSA but that didnt work for me. 

[http://ubuntuforums.org/showthread.php?t=540296&page=2](http://ubuntuforums.org/showthread.php?t=540296&page=2)

I'm going to try the steps I used to initially get the sound working on this. 

I'll let you  know how it turns out

---

### Post by torrent478 on 2007-09-02
repeating the steps to get sound working on this thread did it for me just in case anyone else has this problem

---

### Post by sundarb on 2007-09-06
Hey Guys,
I'm new to Linux and Feisty is the first OS that I had installed on my new HP DV6500T laptop. Thanks to the Ubuntu forums, I've been able to fix most of the issues (CD/DVD, video, audio) and got a working OS up and running. Thanks a lot you guys!

Cheers,
Sundar

---

### Post by aldeby on 2007-09-07
> bingulim wrote: 
[...] but the mic and the webcam are still a problem.
I happen to use a dv6575us notebook.


with ubuntu gutsy gibbin tribe 6 released on 6 sep 2007 webcam works out of the box with ekiga, simply choose V4L2 as Video plugin in Video Devices in Ekiga Preferences, you should be able to see the preview in the main window of ekiga!
cheers

---

### Post by mooseboy on 2007-09-10
2.6.22-11 just hit the updater for me in my gutsy image at work. Apparently [this update to the kernel]("http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-ubuntu-modules-2.6.22/linux-ubuntu-modules-2.6.22_2.6.22-11.28/changelog") fixes a pile of hda-intel bugs. I'll check it when I'm home from work on my dv6500t to see if that resolves the no sound issue on the stock kernel.

---

### Post by FuturePilot on 2007-09-10
> **mooseboy said:**
> 2.6.22-11 just hit the updater for me in my gutsy image at work. Apparently [this update to the kernel]("http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-ubuntu-modules-2.6.22/linux-ubuntu-modules-2.6.22_2.6.22-11.28/changelog") fixes a pile of hda-intel bugs. I'll check it when I'm home from work on my dv6500t to see if that resolves the no sound issue on the stock kernel.

If you could report back on your findings please:) I've also tested out Gutsy on my dv6500t and with the 2.6.22-10 kernel there is no sound out of the box. I'm hoping the -11 kernel fixes this.

---

### Post by mike984 on 2007-09-10
I have the same laptop and with a clean install of Tribe 5 and then all the updates, I can say all the buttons on the laptop work, the Intel 4695AGN wireless worked out of the box with with my router - D-Link DIR-655 except it communicates only in g mode - not n.  

Only things not working - sound and built in card reader.

---

### Post by mooseboy on 2007-09-10
> **FuturePilot said:**
> If you could report back on your findings please:) I've also tested out Gutsy on my dv6500t and with the 2.6.22-10 kernel there is no sound out of the box. I'm hoping the -11 kernel fixes this.

Sadly, this hasn't fixed it -- you still have to go through all the alsa hackery to make sound work :(

---

### Post by FuturePilot on 2007-09-10
> **mooseboy said:**
> Sadly, this hasn't fixed it -- you still have to go through all the alsa hackery to make sound work :(

Yes, I also tested this, and still no sound.:(

---

### Post by dreadlocks1221 on 2007-09-15
Ive been looking all around and I can't find any working way for me to install Ubunutu 7.04, I'm new to linux and I heard good things and so far its been a nightmare. I have an HP DV6500T with Intel T7300, 4GB Ram, 200GB Hard Drive, Vista Ultimate 64 bit, and  GeForce 8400M GS. I am panning on dual booting and I can't even get Ubuntu to install correctly. 

When  I first start to install it says failure to allocate mem resource

then I'll get the Busy box version info and itll say unable to access ttyl: job control turned off

sometimes when I go to safe vga mode or enter in something in F6, itll tell me that startx cant load or something goes wrong with gnome. either way it won't install

---

### Post by FuturePilot on 2007-09-15
> **dreadlocks1221 said:**
> Ive been looking all around and I can't find any working way for me to install Ubunutu 7.04, I'm new to linux and I heard good things and so far its been a nightmare. I have an HP DV6500T with Intel T7300, 4GB Ram, 200GB Hard Drive, Vista Ultimate 64 bit, and  GeForce 8400M GS. I am panning on dual booting and I can't even get Ubuntu to install correctly. 

When  I first start to install it says failure to allocate mem resource

then I'll get the Busy box version info and itll say unable to access ttyl: job control turned off

sometimes when I go to safe vga mode or enter in something in F6, itll tell me that startx cant load or something goes wrong with gnome. either way it won't install

As far as I know that error about failed to allocate mem resource is harmless, but it's a known issue
[https://bugs.launchpad.net/linux/+bug/54294]("https://bugs.launchpad.net/linux/+bug/54294")
As for getting dumped to Busy Box, see this thread, I was having the same issue.
[http://ubuntuforums.org/showthread.php?t=527280]("http://ubuntuforums.org/showthread.php?t=527280")
Put the CD in and when you see the screen come up with all the boot options, press F6 and add```
all_generic_ide
``` to the end and press Enter.
There's also some other good info in that thread about getting Feisty installed and working.

---

### Post by dreadlocks1221 on 2007-09-15
It loads up fine, but when it goes to the installer startx fails to start and it says no screens found and then it freezes when trying to start blue tooth services

---

### Post by aldeby on 2007-09-17
Sir, these are all known problems of Feisty with recent HP pavilion notebooks.
I suggest you to use most recent builds of Gutsy, even if I must tell you it is still under development it is already very well usable. You can download the bootable cd from here: 
```
[http://cdimage.ubuntu.com/daily-live/current/]("http://cdimage.ubuntu.com/daily-live/current/")
```

I also suggest you to carefully read this thread since it helped me a lot: 
[http://ubuntuforums.org/showthread.php?t=512059]("http://ubuntuforums.org/showthread.php?t=512059")

---

### Post by dreadlocks1221 on 2007-09-17
Whats the difference between Gutsy and Fiesty?

---

### Post by Scotty562 on 2007-09-19
Welp, I reinstalled tribe 5 and did all the upgrades. Gutsy is deff coming along. I was able to install the video drivers through the restricted drivers manager and then install the compiz manager and bam, eyecanly everywhere.

Anyway, I think it updated to the .12 kernel and I still don't have sound. Rather than screwing it up again :) I'm just going to do the updates until the sound does work. When that day comes there will be much rejoicing :).

---

### Post by Scotty562 on 2007-09-20
Ok, I couldn't help it and I found some more info and I tried it and it works!

This is the guide nille posted and it is what worked for me, You can find his original post [here]("http://ubuntuforums.org/showthread.php?p=3395008#post3395008").

> **nille said:**
> 

Install dependencies:
```
sudo apt-get install libncurses5-dev build-essential ncurses-dev gettext linux-headers-`uname -r`
```

Download the files needed (this is version 1.0.15rc2):
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc2.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc2.tar.bz2)
[ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15rc2.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15rc2.tar.bz2)
[ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15rc1.tar.bz2)

I save mine on separate home-partition first (in case of reinstall) to a directory called ~/ALSA/1.0.15rc2 and then I do the following:

```
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/ALSA/1.0.15rc2/* .
sudo tar xjf alsa-driver-1.0.15rc2.tar.bz2
sudo tar xjf alsa-lib-1.0.15rc2.tar.bz2
sudo tar xjf alsa-utils-1.0.15rc1.tar.bz2
```

Then compile (I'm not sure if the --with-oss=yes is needed):
```
cd alsa-driver-1.0.15rc2/
sudo ./configure --with-cards=hda-intel --with-oss=yes
sudo make
sudo make install
cd ../alsa-lib-1.0.15rc2/
sudo ./configure
sudo make
sudo make install
cd ../alsa-utils-1.0.15rc1/
sudo ./configure
sudo make
sudo make install
```

Then edit alsa-base in /etc/modprobe.d:
```
sudo vim /etc/modprobe.d/alsa-base
```

And add the following line at the end:
```
options snd-hda-intel model=toshiba
```



Then I followed this suggestion:

> **sebastiansjoberg said:**
> The problem I had was that the module in /lib/modules/2.6.22-11-generic/ubuntu/media/snd-hda-intel conflicted with the one I had built from alsa. So I just moved it to /tmp and ran "sudo depmod -a" and then it worked. Step by step:
```

sudo mv /lib/modules/2.6.22-11-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko /tmp
sudo depmod -a

```

Then I rebooted. After I rebooted I was able to unmute the sound and it worked!

Nothing else worked for me, hopefully this can help the rest of you guys that are still having problems.

---

### Post by aldeby on 2007-09-22
Just to point out that Realtek has released drivers for our chipset.

They are available here: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2")

Note that nille's procedure actually works, and Realtek drivers in part cover the same points, however they come with an integrated installer that eases things a lot. 

Cheers.

---

### Post by FuturePilot on 2007-09-22
> **aldeby said:**
> Just to point out that Realtek has released drivers for our chipset.

They are available here: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2")

Note that nille's procedure actually works, and Realtek drivers in part cover the same points, however they come with an integrated installer that eases things a lot. 

Cheers.

I've tried that and it does not work. All it really is, is the ALSA 1.0.14 drivers with a script that automates the install by compiling it automatically. And that version of ALSA had a problem with the Intel HDA ICH8 family chipset which is why the sound doesn't work out the box. It has been fixed in the latest development version of ALSA 1.0.15rc2

---

### Post by sanitys on 2007-09-28
> **Scotty562 said:**
> Ok, I couldn't help it and I found some more info and I tried it and it works!

This is the guide nille posted and it is what worked for me, You can find his original post [here]("http://ubuntuforums.org/showthread.php?p=3395008#post3395008").



Then I followed this suggestion:



Then I rebooted. After I rebooted I was able to unmute the sound and it worked!

Nothing else worked for me, hopefully this can help the rest of you guys that are still having problems.

Worked like a charm. Dont forget to ./configure lib or utils, if you forget to do this it will not work. Also the realtek install didnt work. only takes 5 min to recompile and it works. Hopefully we get a working out the box solution before release.  Again thanks everyone. 

fresh Gutsy tribe 5 32bit
installed all updates
wireless works outta the box
installed alsa driver, lib, utils (newest, rc3) (i didnt have to add the realtek driver part)
added the toshiba bit.
flash works just by updating through firefox (i couldnt get sound to work with fiesty 64, only video)
now to test the webcam, although i probably wont use it.
also have not tested the mic
finger print reader...cant really ever see myself using it.
I

---

### Post by jhvillegas2 on 2007-11-21
> **zanelightning said:**
> Hey Scotty, I was just able to get the sound working, I found the solution here: [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3165](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3165) . Just sign in as guest to view the forum.

Kentrosaurus gives his solution and links to where he found it...download the newest alsa driver, utils, and lib (I used 1.0.14rc4), replace hda_proc.c and patch_realtek.c from realtek10.tar.gz (on the page Kentrosaurus linked to, pshou explains how to do this).

If you have any questions, just ask!



Where do I download the newest also driver, utils, and lib (1.0.14rc4)?

Thanks,
John Villegas

---

### Post by jhvillegas2 on 2007-11-21
Never mind that question, I already found them.

---

### Post by jhvillegas2 on 2007-11-21
When running the 

apt-get install ncurses-dev

command I get a message saying that the package cannot be found.

I have "ncurses-dev_5.4-r8_arm.ipk" on my Desktop.  Is that the right one?  If it is not, where can I get the correct one?  If it is the right one, how do I prepare the file for installation, and how do I install it?

Thanks,
John Villegas

---

