---
title: "Sony Vaio Nightmare with Lucid"
date: 2010-10-16
forum: Hardware
---

### Post by skew on 2010-10-16
I don't know what's going on, or even who is to blame, but I've encountered nothing but headaches getting my new Sony Vaio F series to work at anything close to the full functionality that this Vaio is capable of with Lucid.  

In any case, with my Vaio I have had and still have many problems. Here are some of them:

 First is video driver issues. I'm using the Nvidia proprietary driver. I use this driver (ver 195.36.24) since the native Ubuntu driver does not have 3D capability with my card (310m). I don't expect help with this on this forum since it's a Nvidia proprietary driver and the blame for it failings falls on their shoulders. It is after all their hardware and drivers. I only mention it here as MANY MANY Ubuntu users use proprietary drivers.  

  The problems here are many. First Nvidias drivers don't function as well as their previous drivers did. Second the install procedure to update the drivers from their web site is almost impossible to do because linux's nouveau drivers seem to have locked themselves onto my system and are impossible to remove without some dire warnings. Third after installing these drivers with ubuntus ***hardware driver utility*** I've been unable to enter the terminal mode (Ctrl-Alt-Fn). This catch-22 means that I can't install their updated drivers from Nvidias web site even if I wanted to. I did try using some outside repositories that I found which had updated drivers but their installation left me with a blank screen (ver. 260). 

 Eventually After much research I finally got what I wanted by using xorg.conf. Now both my external monitor and laptop screen function as I wanted BUT after a rebooting, the system reverted to the way it had been previously, even though the corrected xorg.conf was still intact and available in /etc/X11/ (why?). Anyway it's only partially working.
	
 Next, My Firewire port does not work. I have a Firewire external optical drive which is now useless. (FireWire (IEEE 1394): Ricoh Co Ltd Device e832)  Nothing from the research I've gathered has worked nor does any of the suggestions on this and other forums work for anyone else either. FWIW, the wire in my previous laptop did function perfectly. Final result, it's not working.

 For those of you who want to know why I bought a Vaio in the first place it was because I read that they are second in customer support after Apple and miles ahead of the next best PC manufacturer.  However, from what I've read after my purchase in the many forums which I reviewed in search of assistance, that support does not apply to Linux users. I have read that Sony won't even give you the time of day if you call and claim to have Linux on your computer. Therefore it would appear that you should not even bother contacting them for hardware support if you use Linux. From what I've read, if you require warranty repair work you should remove linux/s from your system and restore the system to the way it was when you purchased it before returning it to them. If it's your hard drive that goes you're up the proverbial creek.

 Next BIOS, wait WHAT BIOS! Sony has apparently locked users out from making all but the most rudimentary changes to their BIOS. One of the few things I can change is the boot order, so I changed it to the following; external drive, optical drive, internal hard drive.  Guess what, the system won't boot if my HP printer is attached to a usb port with that boot order. Remove the printer cable or change boot order back to default and it works again. why...who knows. FWIW My Vaio has the latest system drivers installed

 Next the sound system. From the start the laptop speakers and mic didn't work however the plug-in jacks for microphone and headphones did work. I upgraded the Alsa drivers and was thrilled to find that the sound & mic on the laptop worked but once again that success was short lived as now the microphone and headphone jacks didn't work! As it stands now I can either get either one set or the other to function but not both. At present I have removed the newest alsa drivers and have had to settle with only the headphone and microphone jacks working. 

 Next the Alps touchpad didn't work after installing Lucid. That I did get fixed after some research but I have a multi boot system and that fix only worked with the last Linux OS I installed. It didn't work with my first linux OS I install. I did eventually get that working with some help from a member of this forum. The fix was made by adding aa menu entry in the /etc/grub.d/40_custom file. Even then the results were strange but acceptable. Strange in that my custom menu entry didn't show up in the grub2 boot menu like it should have yet the problem was rectified just the same. So that is sort of fixed.  

 There may be more things that pop up in the future as I haven't had a chance to look over all the other system ports & functions like the eSata & pcmcia port.  

  The only bright side is that the network wired & wireless ability functioned out of the box and the webcam works albeit without the microphone.

  For the past few years, since I stated using Ubuntu with Dapper, I've notice a creeping regression in the operation of my systems with each new upgrade. Why is their this wide spread regression? Are Ubuntu releases being rushed to market before they are ready. Or is this simply a matter of you get what you paid for. Is it the hardware manufacturers fault?

Any one else having big issues with their Vaio or this creeping regression? 

Does anyone have any fixes to the above that don't require a Masters in computer science to fix? 

Thx

---

### Post by unitron6991 on 2010-10-16
What ubuntu are you running? I have 10.04 and I found a tutorial that really was quite painless to use for the Nvidia. It worked on my vaio.

[http://www.gaanza.com/blog/installing-nvidia-driver-on-ubuntu-10-04/](http://www.gaanza.com/blog/installing-nvidia-driver-on-ubuntu-10-04/)

Does your eSata port have a usb port inside of it? I know that usb works, however I have not tried the eSata yet.

Can you give a link to the touchpad idea?

Good luck.:grin:

---

### Post by skew on 2010-10-16
> **unitron6991 said:**
> What ubuntu are you running? I have 10.04 and I found a tutorial that really was quite painless to use for the Nvidia. It worked on my vaio.

[http://www.gaanza.com/blog/installing-nvidia-driver-on-ubuntu-10-04/](http://www.gaanza.com/blog/installing-nvidia-driver-on-ubuntu-10-04/)

Does your eSata port have a usb port inside of it? I know that usb works, however I have not tried the eSata yet.

Can you give a link to the touchpad idea?

Good luck.:grin:

Thanks. I'll check out your link.

My OS'es are Win7/lucid32bit/lucid32bit<--soon to be changed to 10.10 64bit

I have three USB ports one of which is the dual eSata/usb2.0 type.
All USB ports do work although I haven't benchmarked their throughput 
yet.

Here's my link for the touchpad issue.

[http://ubuntuforums.org/showthread.php?p=9960626#post9960626](http://ubuntuforums.org/showthread.php?p=9960626#post9960626)

You can also google these terms as well:  i8042 touchpad Ubuntu vaio
and you'll find lots of info.

By the way have you noticed issues with any of the other topics I mentioned above?

---

### Post by skew on 2010-10-16
Finally, Some SUCCESS!Thanks to your link I now have the 256.53 drivers running and in the manner I wanted, even after several reboots. Thank you VERY much **unitron6991**.  =D>=D>

  The process I took though was a little round about in order to get there first though. The first thing I tried was reinstalling the 260 drivers again from the X-stat repository (before I read unitron6991's post) and that got me nowhere. On a whim I loaded an earlier rescue kernel from the grub menu and was now able to get access to a console (Ctrl-Alt_Fn), where I wasn't able to do this with the newer kernel. Then I used the instructions in the link provide above and struggled through a few issues where the driver kept saying that the x-server was still active even though the command line showed it to be stopped. Eventually something took and the driver installed perfectly and the rest is, as they say history. 

 However (I really hate to add this) the Ctrl-Alt_Fn keys still fail to bring up a console or terminal mode from within X (gdm). Doing so shows a blank screen with nothing, no cursor. The monitor and laptop screens are actually turned off as indicated by a loss of signal notification on my external monitor and no backlight on the laptop screen. However Ctrl-Alt_F7 does bring me back into a functioning gdm. Oh well, I'll mark today as a large, yet partial success. 

  Now lets hope I and other Vaio sufferers can get some success with the other problems including the still missing console ability.

---

### Post by unitron6991 on 2010-10-16
> **skew said:**
> Finally, Some SUCCESS!Thanks to your link I now have the 256.53 drivers running and in the manner I wanted, even after several reboots. Thank you VERY much **unitron6991**.  =D>=D>

  
You're welcome!

I fixed the sound before, but I don't remember how I did it! :D

Thanks for the touchpad link. It works now. I had been lugging around a usb mouse, but I can still use that to play Portal.

Yes, I agree with you on the BIOS thing. I found that out when I tried to make a Hackintosh. (partial fail, osx works in virtual box)

I don't know about the firewire, cuz I don't have any.

Have you got Wine to work?

Just wondering, does your vaio get hot right of the touchpad?
> **skew said:**
> 
Oh well, I'll mark today as a large, yet partial success. 
  
This was a triumph.
I'm making a note here:"HUGE SUCCESS"
It's hard to overstate my satisfaction.

(whoops, just geeked out for a minute there):rolleyes:

---

### Post by unitron6991 on 2010-10-16
And one more thing....
Sometimes I have the mysterious problem of the keyboard not working in grub...

---

### Post by skew on 2010-10-16
One good turn deserves another...or some such thing. Glad to hear you got the touchpad working.

> **unitron6991 said:**
> And one more thing....
Sometimes I have the mysterious problem of the keyboard not working in grub...

Hot on the touchpad huh? Mines slightly warm yes, hot no.(**knock on wood**). It's warmer on the right than left, but nothing that concerns me, like I need another problem to contend with.  Are you frying eggs on yours? :wink:

I have had the keyboard issue a couple of times. Mostly I use my Laptop as a desktop replacement with external keyboard so I'll be keeping an eye on that one. We'll just add it to the the list. Which I was hoping was gonna get shorter not longer.

 If you remember, or come across that sound fix in your surfing I'd be appreciative if you give me a heads up on that.  It's not super critical but I would like to get it working since I did pay for it.

The terminal mode issue appears to be a unresolved bug. There are reports of it all over the place. I guess I'll just have to wait on that one. Damn pity though as it's a major bug.  There is nothing like the having access to the trusty terminal mode when things go haywire in X. 
Ah well, C'est la vie.

Ya, I've got wine installed but haven't used it yet ...why??? [-o<

---

### Post by unitron6991 on 2010-10-16
[http://ubuntuforums.org/showthread.php?t=1452089](http://ubuntuforums.org/showthread.php?t=1452089)

That was the sound.

Never mind the Wine. That's why I kept Windows. :D  (and dosbox)

I guess you're in orbit now, but not on the moon (yet).

I'll try to post if I find anything else...

---

### Post by skew on 2010-10-17
> **unitron6991 said:**
> [http://ubuntuforums.org/showthread.php?t=1452089](http://ubuntuforums.org/showthread.php?t=1452089)

That was the sound.

Never mind the Wine. That's why I kept Windows. :D  (and dosbox)

I guess you're in orbit now, but not on the moon (yet).

I'll try to post if I find anything else...


LOL:P   Ah... I'm too much of a pragmatist to jump that far ahead. If we are gonna throw around analogies I guess I've left the building and am sitting on the launch pad. maybe.  

Then again, my mission number so far seems to be "Vaio 13" so where does that get me..heh heh.

I did try the newest Alsa drivers with limited success, as you can read in my first post. Do you have both your output jacks and speakers and mics working?

---

### Post by skew on 2010-10-18
**Firewire Update:**

Partial success with the firwwire port. I got it to function with a dv camera. using the directions offered by the Kino web page listed below.

[http://www.kinodv.org/article/archive/13/](http://www.kinodv.org/article/archive/13/)

However I was still unable to use the Firewire port with my optical drive until I read the last post int the following forum from LJ50.

[http://club.myce.com/f91/gsa-5163d-firewire-will-not-work-163721/](http://club.myce.com/f91/gsa-5163d-firewire-will-not-work-163721/) 

Now the drive works w/ Firewire in the same manner as he describes but it's a bizarre outcome. I'll see how it works after a reboot.:confused:

**Update:**

 After many warm & cold boots and with the drive both on and off and disks in the tray and empty during these subsequent tests the Firewire port continues to work. 

Why, ya got me, I'm just happy that it's now working and that's another problem off my list. :)

Now If I could just get that terminal mode to work.

---

### Post by unitron6991 on 2010-10-18
> **skew said:**
> 
I did try the newest Alsa drivers with limited success, as you can read in my first post. Do you have both your output jacks and speakers and mics working?

I didn't get the mike working, but I don't think I need it.

I think I am pretty happy with the way its working.


working on the terminal thing.

=/\=

---

### Post by skew on 2010-10-20
**Update Firewire**

  I jumped the gun on the Firewire port operation. The port failed to operate again in the morning after I had turned the system off for the night.  

It appears a short cold boot is OK but a longer duration shutdown kills the port. ...sigh :(

---

### Post by unitron6991 on 2010-10-20
got the dvd player to work

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by skew on 2010-10-24
> **unitron6991 said:**
> got the dvd player to work

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Mines a Blu-Ray/DVD player and there is not a simple solution to that working currently (Blu-ray that is). I've never had trouble with DVD players in the past but now you mention it I'll check it out and confirm that that continues to be the case w/ this Vaio

---

### Post by skew on 2010-11-01
Two things:

First, I can't get the built in blue-tooth device to find my blue-tooth enabled phone. Has anyone have any issues with Blue-tooth with their Vaio or Lucid? 

Finally, has anyone experienced an intermittent, high-pitched, barely audible tone from their fan?  It usually occurs when the fan operates between 48c and 60c CPU temps. I work in a quiet environment and it very noticeable in that environment and very aggravating. The fan is essentially white noise and not an issue for me but this sound is maddening. I called Sony about it. They said send it in. It's less than a month old.:mad:

---

