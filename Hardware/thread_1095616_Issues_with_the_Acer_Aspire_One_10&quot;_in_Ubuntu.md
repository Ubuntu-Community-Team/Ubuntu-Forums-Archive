---
title: "Issues with the Acer Aspire One 10&quot; in Ubuntu"
date: 2009-03-13
forum: Hardware
---

### Post by flatland2d on 2009-03-13
I know there are already some threads about the Acer One (8.9") but I am having some different issues with my 10".  I'm trying to get some help in resolving these issues so maybe there could be a wiki for the 10" someday.

I can't get the custom Sickboy kernel to run on this.  I thought the hardware was pretty much the same but it's not working for me.

Sound does not work in 8.10, even after compiling the ALSA drivers myself.  Sound does work in 9.04.

Battery life is not as good in Ubuntu as it is in XP.  I get maybe around 5 hours in Ubuntu.  I haven't used XP for a full charge but other people are reporting 8 hours.  This is with the 5800mAh battery.

The temperature doesn't seem to be reporting correctly.  Likewise, the fan never turns off.  The temp reports 27C all the time.  I've been working with the developer of acerhdf to try and resolve this.

Suspend and hibernate work when manually selected, but I can't get it to suspend when the lid is closed.  All it does is turn the screen off.

Any help would be greatly appreciated!

---

### Post by flatland2d on 2009-03-15
So far testing with 9.04 has been pretty good.  The only thing I'm having trouble with is the touchpad vertical scrolling.  I need to make sure I'm using the same settings as I am for 8.10, but it just seems like I have to press really hard and that the scrolling section of the touchpad is too thin.  There might be a way to change that, but I noticed the xorg.conf file is empty in 9.04.

I tried compiling the 1.0.18rc3 drivers for 8.10 (which do work fine in 9.04 as far as the speakers go, haven't tested mic or headphones) but I still can't get sound to work.  I've made sure all the volumes were turned up.  I may have to do some more testing on this.

At this point I'd be ready to switch to 9.04, but the vertical scrolling thing bugs me too much.  I use this laptop mostly for internet browsing so I need good scrolling.

Any advice would be appreciated.

---

### Post by awy on 2009-03-17
Have you got wired ethernet working with either 8.10 or 9.0x?

---

### Post by flatland2d on 2009-03-17
> **awy said:**
> Have you got wired ethernet working with either 8.10 or 9.0x?

Yes, wired ethernet works for me out of the box with both 8.10 and 9.04.

---

### Post by awy on 2009-03-19
So 8.10 with the -7 kernel is working with wired ethernet for me now.

I have installed the madwifi-hal drivers and ath0 and wifi0 come into existence and I see no error messages in the logs but, somewhat stupidly, I cannot work out what to do to actually get a wireless connection to come up.

As for audio, as you reported, this is not working. I have not yet investigated further.

The fan for me is not running at a constant speed, although I am unsure as to whether it actually turns off. How do you check the temperature?

I had a crash trying to resume from suspend mode. The crash was related to USB and I had removed a wireless-mouse USB dongle while suspended, so I guess it could be that.

For information, I am running with the Xubuntu distribution. I looked at adding in the netbook-remix pieces, hoping for an Atom-optimized build of the kernel and some other pieces (Firefox, Thunderbird) but I don't know if they should be available in that distribution: they don't seem to be and I'm not all that interested in the other additional features.

So for now, my priorities are:
[LIST=1]
[*]Get wireless actually up and running
[*]Get audio (and video -> Skype) working
[*]Atom-optimized builds of key pieces (I have read a report that the Intel complier can yield 35% faster results than gcc at the moment)
[*]Make sure power-saving and the like are operating correctly (suspend on close lid)
[/LIST]

---

### Post by flatland2d on 2009-03-19
Once you have the madwifi-hal drivers installed, you should just have to click on the network manager icon in the top right to select an available wireless network.  That's all I had to do.

After using this some more, the fan speed might be changing some.  It's hard to tell because it's so quiet all the time.  I never really pay attention to it.

As for Skype, it'll complain about your sound not being set up until that can be fixed on this laptop.  In Jaunty, with working sound output, I can complete the test call but the onboard mic doesn't record.  But it does recognize the device being there and doesn't complain.  I checked my volume settings and still nothing.  I don't have an external mic to test with.

I'd also really like suspend with lid closed.  I've gotten s2ram working when given the command to suspend, but can't get this command triggered, even after altering the suspend and hibernate files (I can't remember their exact names).

You might want to give Jaunty a try if you've got an available partition for testing.  So far it's better than Intrepid for this laptop.  Only thing I still can't figure out is the issue with vertical scrolling, but I haven't taken the time to look into it yet, either.

---

### Post by awy on 2009-03-20
I tried 9.04 alpha 6. Wireless and audio (speakers) worked out of the box, although the mic did not seem to work and the speakers did not continue to work after suspend. The problem with the trackpad is still there. Otherwise pretty nice.

Have you opened a bug for the trackpad issue?

I wonder what is different about the audio in the Jaunty build. I (also) tried building alsa (1.0.19) and, although the mixer controls looked more sensible, I still got no sound.

---

### Post by achristoffersen on 2009-03-21
My acer aspire one AOD150 - i.e. the 10.1 inch version has just arrived. Mine is the one with 3g built in (sim-slot just behind the battery).

Does anybody know which distro supports this computer the best´? from the advice above jaunty seams to be the way fwd. But does it support 3g also?

Does anyone have any experiene with kuki, easy peasy or chrunch bang #! ?

---

### Post by achristoffersen on 2009-03-22
Have just played around with live-cd (USB really). Cruchbang #! i super fast an I think this will be my choice. For some reason I can use the FN keys to control volume in ubuntu 8.10, but not in crunchbang. Otherwise the issues were as expected. No sound through speakers (headphone just fine though) and no 3g.

The 3g is my only real concern. Does anyone have some ideas? I have no experience with dmesg etc.

BTW: For some reason in crucnhbang #! the webcam worked via skype - but not cheese... Strange? (didn't test this in ubuntu 8.10)

---

### Post by FoolsRun on 2009-03-22
I've had some luck getting sound to work after suspend in Jaunty by following some instructions on the [community docs](https://help.ubuntu.com/community/AspireOne#Install%20Ubuntu%20Intrepid%20Ibex%208.10%20on%20the%20Acer%20Aspire%20One) originally intended for Intrepid:

> Maybe sound stops working after suspending and then resuming if this happens to you, add the following to the end of /etc/modprobe.d/options
```
# enable sound after suspend on Aspire One LP#249961
options snd-hda-intel model=acer
```

Now in Jaunty this file didn't exist. I created it and added those lines to it, suspended and woke the laptop, and sound worked.

Anecdotal at best, obviously, but it's worth a shot.

Right now suspend-on-lid-close is my highest priority so if anyone finds anything out on that front, please post here.

---

### Post by flatland2d on 2009-03-23
> **awy said:**
> I tried 9.04 alpha 6. Wireless and audio (speakers) worked out of the box, although the mic did not seem to work and the speakers did not continue to work after suspend. The problem with the trackpad is still there. Otherwise pretty nice.

Have you opened a bug for the trackpad issue?

I wonder what is different about the audio in the Jaunty build. I (also) tried building alsa (1.0.19) and, although the mixer controls looked more sensible, I still got no sound.

No I haven't reported this as a bug yet.  I was hoping someone else could confirm this as I spent a good amount of time messing with the built in settings and gsynaptics that I didn't know if I screwed something else.  But if you're also having a hard time with vertical scrolling, we ought to report the bug.  I've never done that before, so if someone wants to take care of it, that's cool.  Else I'll look into doing it when I have more time.

I can now definitely say the fan speed is somewhat being controlled, and not running full speed all the time.  I booted up holding the One to my ear like it was a cell phone, and I could hear the fan changing under different CPU loads.  I have no idea what's controlling this since it doesn't seem like there's any way to monitor the CPU temp itself.

I'm kind of happy that battery life started getting a little better after just lowering the LCD brightness some.  I probably get close to 6 hours now.  I haven't taken any other steps towards power management so I'm sure there's still a lot to be done there.

---

### Post by qedx on 2009-03-26
I just installed a jaunty daily-live from 24/03 and I have wifi, speakers, webcam, headphone jack, mic jack working out of the box. the built-in mic does not work. I haven't tested bluetooth and the card reader.

---

### Post by awy on 2009-03-26
How is scrolling with the trackpad working?

---

### Post by qedx on 2009-03-27
Yeah, I just noticed the thing with the trackpad. It's like the scrolling area on it is really really thin. And sometimes it just doesn't work. I hadn't experienced this issue when I ran mepis.

---

### Post by flatland2d on 2009-03-28
Wifi has been behaving kind of weird for me with Jaunty for about the past week or so.  Seems like any type of data transfer goes very slow when it's acting up.  Sometimes it works just fine.  I've been updating pretty much daily and was wondering if anyone else has noticed this.

I'm back to Intrepid for a while.  Still no sound but better scrolling and more reliable wifi for now.

---

### Post by awy on 2009-03-31
I entered [bug 352179]("https://bugs.launchpad.net/bugs/352179") for the trackpad problem.

---

### Post by FoolsRun on 2009-04-05
I posted in the bug report noted in the previous post, but I'll note it here incase anyone's following this thread:

I ran updates on an Acer Aspire One running Jaunty alpha tonight and the trackpad problem appears to be fixed now. Unfortunately I have no idea what package fixed it or when it was released :)

---

### Post by flatland2d on 2009-04-05
It's fixed for me, too.  Very cool.  Makes it much more usable for me.

So what next?  Suspend with lid closing?  Is that considered a bug or are there other workarounds for that?

---

### Post by FoolsRun on 2009-04-05
> **flatland2d said:**
> It's fixed for me, too.  Very cool.  Makes it much more usable for me.

So what next?  Suspend with lid closing?  Is that considered a bug or are there other workarounds for that?
The lack of suspend on lid-close is the only major hole remaining in my daily use now that the trackpad scroll is working again.

---

### Post by awy on 2009-04-06
Well I still have two other problems, although I have not tried te very latest Jaunty yet:
[LIST=1]
[*]Bulitin microphone (for Skype)
[*]Wireless networking seems to forget keys/passwords
[/LIST]

I also get the impression that I'm getting crashes in various suspend/hibernate modes from time to time. I realise that this seems to be a general issue with Jaunty. The trouble is that it is not consistent. I suspect that hibernate is the more troublesome.

---

### Post by flatland2d on 2009-04-06
> **awy said:**
> Well I still have two other problems, although I have not tried te very latest Jaunty yet:
[LIST=1]
[*]Bulitin microphone (for Skype)
[*]Wireless networking seems to forget keys/passwords
[/LIST]

I also get the impression that I'm getting crashes in various suspend/hibernate modes from time to time. I realise that this seems to be a general issue with Jaunty. The trouble is that it is not consistent. I suspect that hibernate is the more troublesome.

Add to that no sound after suspend, unless you guys have found a fix for that.  I can't remember if I've tried the fix for the 8.9" regarding this.  I think it had a similar problem.

Also, power management is something that needs to be worked on.  8 hours battery life for XP and 5.5 hours for Ubuntu is not good.  What kind of battery life are you guys getting?

---

### Post by Noblacktie on 2009-04-13
I have the 5200mAH battery (the 6-cell from the 8.9") that Jaunty seems to report as 4 hours and 45 minutes max. I know I can get more than 6 hours with Wifi on because, well, I've run it for over 6 hours and still had 6 or 7% of the battery left.

Fedora, however, reports my battery life as 6 hours 30 mins.

So my problem is not actual run-time but the accuracy of the battery monitor.

As for suspend on lid close, it used to work in Intrepid by creating a lid.conf file in /etc/acpi/events/ but that no longer seems to work.

In any case, suspend seems to work on sporadically and seems to break from kernel to kernel. Worked with 38, borked with 39, worked with 40, now borked again with 41.

---

### Post by micdhack on 2009-06-12
What about the video with the UNR? Im experiencing some interfiernce while watching videos. In my big laptop i fixed this problem by disabling ubuntu's windows effects but in the UNR is already disabled. Any ideas?

---

### Post by Kimos on 2009-06-16
I'm running 9.04 Netbook Remix on an Acer Aspire One D150 and I get some pretty destructive behavior with the closed lid as well. It locks up after about half an hour of the lid being closed.

I've found no solution or even suggestions of a workaround. I don't mind having to suspend manually, just as long as the laptop continues to function with the lid closed!

---

### Post by ZackM on 2009-06-16
I've actually had the same problem with that myself. I'm not sure why it does it either, but I have been looking into it. If I find anything, I'll let you know.

---

### Post by Kimos on 2009-06-16
Cross post to here:
[http://ubuntuforums.org/showthread.php?p=7465964](http://ubuntuforums.org/showthread.php?p=7465964)

I started that thread before I had a good understanding of what my problem actually was. There are some links to bug reports.

I'm going to try a few things when I get home, but it looks like it's just a flood of events that aren't getting properly handled.

---

### Post by lucmv on 2009-08-26
Hello, fellow AOD150 owners! I just got this notebook (this isn't a "netbook" is it?) and installation of Jaunty went so well that I thought I was going to love this machine, but I ran into a huge showstopper: the keyboard layout. 

I am using KDE and set my keyboard as "Generic 105-key intl" on Kcontrol. Mind you, I am Brazilian and my native language is full of accented characters: é, õ, à, ç etc. For some reason, I can type those characters very easily into Kedit. The tilde works on all the vowels I need and the ' quote character acts as dead keys for the other vowels. It even combines with c to make the cedilla ç.

However, none of these keys work on Konsole or OpenOffice. That is quite a tragedy. This notebook will be *useless* to me without all the proper character typing unless I fall back to XP. Ugh!

Can someone please share a tip about how to get the correct keyboard layout and accented characters? Any help is desperately appreciated.

---

### Post by lucmv on 2009-08-27
Hello. No one? Sorry about upping the post, but I can't get any work done. I am really desperate here! :-(

---

### Post by ianmillington on 2009-08-27
Dont know whether this helps.. perhaps it's relevant, perhaps not, but hope so

[http://kubuntuforums.net/forums/index.php?topic=3103940.0](http://kubuntuforums.net/forums/index.php?topic=3103940.0)

---

### Post by lucmv on 2009-08-27
Thanks, ianmillington. That page didn't have the answer, but put me in the right track. It lead me to other places until I eventually ran into this tip: edit the /usr/bin/soffice script and add this near the end of the file:

LANG=en_US
LC_ALL=en_US
LC_CTYPE=ISO-8859-1
LC_COLLATE=POSIX
LESSCHARSET=latin1
export LANG LC_ALL LC_CTYPE LC_COLLATE LESSCHARSET

It works.

The proper way to do it would probably be to fix the system's locale. But how? I found recipes on the Internet, none of them worked. The 'locale' command would always return a lot of empty strings.

That's why I really hate Debian sometimes. They make it so complicated and even change the damn things often, so we never know, we are left in the dark all the time. Very disrespectful IMO.

Anyway, I just added those lines to /etc/profile and now 'locale' returns everything correct, and accents work even in OpenOffice (the only application where they still refused to work).

Thank you!

---

### Post by leorolla on 2009-11-19
Hi lucmv

I have the same laptop but I run gnome instead of kde, in Karmic

Here's what I did:

System -> Preferences -> Keyboards -> Layouts
Keyboard model: Acer Laptop
Layout: Add -> USA -> International (with dead keys)
Select other layouts, delete.
Apply Systemwise

Now you will probably get c-acute instead of ç when you type 'c

Follow the steps at
[http://ubuntuforums.org/showthread.php?t=1330912](http://ubuntuforums.org/showthread.php?t=1330912)

to get ç back.

This should work with every application.

My solution is for gnome.

For Kde in Hardy I went to

System Settings -> Personal -> Regional and Language -> Keyboard Layout

and did a similar procedure.

---

