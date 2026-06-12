---
title: "Problems installing 7.10"
date: 2008-04-16
forum: Georgia Team - US
---

### Post by Eric Weir on 2008-04-16
I posted on this on the Ubuntu installation forum, and thought I'd try here, too. 

I've been using Ubuntu almost exclusively -- actually, Kubuntu -- for about eight months now. A techie friend installed it on a 10 GB hard drive on a machine that I wasn't using. Needless to say, with only 10 GB the system eventually got excruciatingly slow.

This past weekend I cannibalized two 40 GB hard drives from my Windows desktop and tried to do a fresh install of Kubuntu by myself. Initially, the install hung up very early in the process in the "Busy-Box" terminal with looked like a command in parentheses -- "(initramfs)" -- in the display. I couldn't tell that anything was happening, although the lights on my modem and router were flashing like crazy. I assumed it was downloading updates to the system.

However, after four hours of waiting for the "downloading" to stop I took my techie friend's advice did a Ctrl-Alt-Del, after which the installation process started up again and seemed to go through to completion. However when I tried booting without the CD in the drive the system wanted to boot from the CD; it wouldn't move on to the HD. I restarted the system and checked the BIOS settings, which showed the two CDs as first and second alternate boot drives and the two hard drives as "not installed." Changing that to autodetect had no effect. [The drives were detected by the Live CD, including the correct make and model number for each.]

My techie friend suggested I change the jumper settings on the second hard drive and then try installing again. Again, the process hung up in the "Busy-Box" terminal with "(initramfs)" displayed. I tried Ctrl-Alt-Del several times, thinking the installation process would eventually start and go through to completion the way it did on the first install attempt, but it never did.

Any ideas what's going on and what I need to do to get the installation to go through to completion?

For what it's worth this system has a Pentium IV 1.6 Ghz with 512 MB of Ram.

Thanks,

---

### Post by s4rams on 2008-04-16
hi to all,
i was feeling happy to join with u people.as i was virgin to this ubuntu
i was stucked at drivers installation....i am not getting sound effects
can anyone help me about this problem

---

### Post by siafulinux on 2008-04-17
> **Eric Weir said:**
> I posted on this on the Ubuntu installation forum, and thought I'd try here, too. 

I've been using Ubuntu almost exclusively -- actually, Kubuntu -- for about eight months now. A techie friend installed it on a 10 GB hard drive on a machine that I wasn't using. Needless to say, with only 10 GB the system eventually got excruciatingly slow.

This past weekend I cannibalized two 40 GB hard drives from my Windows desktop and tried to do a fresh install of Kubuntu by myself. Initially, the install hung up very early in the process in the "Busy-Box" terminal with looked like a command in parentheses -- "(initramfs)" -- in the display. I couldn't tell that anything was happening, although the lights on my modem and router were flashing like crazy. I assumed it was downloading updates to the system.

However, after four hours of waiting for the "downloading" to stop I took my techie friend's advice did a Ctrl-Alt-Del, after which the installation process started up again and seemed to go through to completion. However when I tried booting without the CD in the drive the system wanted to boot from the CD; it wouldn't move on to the HD. I restarted the system and checked the BIOS settings, which showed the two CDs as first and second alternate boot drives and the two hard drives as "not installed." Changing that to autodetect had no effect. [The drives were detected by the Live CD, including the correct make and model number for each.]

My techie friend suggested I change the jumper settings on the second hard drive and then try installing again. Again, the process hung up in the "Busy-Box" terminal with "(initramfs)" displayed. I tried Ctrl-Alt-Del several times, thinking the installation process would eventually start and go through to completion the way it did on the first install attempt, but it never did.

Any ideas what's going on and what I need to do to get the installation to go through to completion?

For what it's worth this system has a Pentium IV 1.6 Ghz with 512 MB of Ram.

Thanks,

**Eric**

I had a similar situation with the Busy Box terminal while installing 8.04 Beta, but after blowing hard into the CD-Drive the problem seems to be corrected. Still I expect problems with a Beta, but not so much with 7.10. Maybe it was just a fluke when I blew into the drive, but since then it works fine. But your case sounds a little different.

Check your BIOS again plugging each drive in separately from the other. Make sure BIOS picks each drive up separately and that  one of the drives is not bad.

If it picks them both up independently, try installing with one hard drive by itself and see if that sorts it out. If so, it may just be that one of the drives are set up incorrectly as your friend had alluded to. You need to have one primary, one secondary or both set to "cable select".

If BIOS is not picking up the drives at all, make sure the cables are all plugged in correctly. I've done it myself, messing around in my boxes and after getting the cover screwed on I find I had accidentally unplugged a cable just ever so slightly from the motherboard. Double check everything! Though I don't think this is your problem.

When installation is complete, remove the CD! If your BIOS is set to boot from CD first and then hard drive and a CD is in the drive, it will boot from this. If I'm not mistaken though, the CD has an option to boot from hard drive. So if it boots to CD look for this option and see if it begins booting from the HDD instead of the CD, but I would just remove it after install.

Let me know if you were able to figure it out.
JC

> hi to all,
i was feeling happy to join with u people.as i was virgin to this ubuntu
i was stucked at drivers installation....i am not getting sound effects
can anyone help me about this problem

**s4rams**

I need a little more info about your situation. Ubuntu should handle audio automatically in most cases. What hardware do you have and what "drivers" are you trying to install exactly? Also what version of the distro are you running?

Thanks
JC

---

### Post by Eric Weir on 2008-04-17
> **siafulinux said:**
> I had a similar situation with the Busy Box terminal while installing 8.04 Beta, but after blowing hard into the CD-Drive the problem seems to be corrected.
Wow! That never occurred to me!
> Check your BIOS again plugging each drive in separately from the other. Make sure BIOS picks each drive up separately and that  one of the drives is not bad.The fact that the HDs are showing up "not installed" and that they won't  autodetect made me think there's a problem in the HD connections somewhere. I've printed out your suggestions to make sure I touch all the bases.

Thanks

---

### Post by Eric Weir on 2008-04-18
> **siafulinux said:**
> **Let** me know if you were able to figure it out.
Well, I don't know if I got it figured out, but I got it running. Seems the installation did go through on my first attempt, but for some reason it would neither boot from the HD nor detect it.

I took the HDs out, put the one I'm most certain about back in, and got the BIOS to autodetect it. When I put the CD back in it booted from the HD! 

I could be satisfied with the situation is as it is, but I'd like to do a reinstall and set up a separate partition from my /home folder.

How do I start the install from the CD when Kubuntu is already installed on the HD?

Also, is there a GUI partition inspector/editor for Kubuntu?

Thanks,

---

### Post by siafulinux on 2008-04-25
> **Eric Weir said:**
> Well, I don't know if I got it figured out, but I got it running. Seems the installation did go through on my first attempt, but for some reason it would neither boot from the HD nor detect it.

I took the HDs out, put the one I'm most certain about back in, and got the BIOS to autodetect it. When I put the CD back in it booted from the HD! 

I could be satisfied with the situation is as it is, but I'd like to do a reinstall and set up a separate partition from my /home folder.

How do I start the install from the CD when Kubuntu is already installed on the HD?

Also, is there a GUI partition inspector/editor for Kubuntu?

Thanks,

Glad to see it's working for you. 

When trying to get the second drive as /home, I would try to re-install with both hard drives installed, making sure that both drives are correctly picked up by BIOS. 

When installation gets to the hard drive formatting and partitioning section, choose to do so manually. Choose the second drive and mount it at /home and I believe that should do it for you.

There are gui partition editors for *ubuntu; I like qtparted. Use Synaptic or do a "sudo apt-get install qtparted" in a console.

If you are going to re-install, put the CD into the drive and see if it picks it up first before loading the hard drive. If so, just choose to install again. Otherwise, make sure BIOS is set to boot from CD before HDD or there may be a boot menu asking you which device you want to boot - would have to select this option from boot, but not all BIOS's have this feature.

---

### Post by siafulinux on 2008-04-26
There are instructions to do so without having to re-install. I would use [qtparted]("http://qtparted.sourceforge.net/") to wipe the new drive and then follow these directions.

[http://ubuntuforums.org/showthread.php?t=318013]("http://ubuntuforums.org/showthread.php?t=318013")

---

### Post by Eric Weir on 2008-04-26
> **siafulinux said:**
> There are instructions to do so without having to re-install. I would use [qtparted]("http://qtparted.sourceforge.net/") to wipe the new drive and then follow these directions.

[http://ubuntuforums.org/showthread.php?t=318013](http://ubuntuforums.org/showthread.php?t=318013)

I'm responding to your previous reply and this one. Thanks for both. My current situation is that I have Kubuntu on my primary 40 GB drive with /home in a second partition and my old 10 GB drive temporarily installed as a second drive. When I've got the kinks worked out in my installation, I'll take the 10 GB out and put the second 40 GB drive back in and use it to backup /home.

Meantime I think I'm gonna give Xubuntu a try in place of Kubuntu. I haven't done much work configuring the Kubuntu installation, and I've been very disappointed in the performance of Thunderbird on both Ubuntu and Kubuntu. 

I have qtparted installed and have used it just to inspect the partitions on the two drives. I'll probably use it to format the second 40 GB drive when I put it in.

While I'm at it, I checked out your website. Kinda surprised that a Linux advocate's making a go of it outside metro Atlanta, but then I see you're at Ft. Stewart. Are you finding people receptive?

A friend, a former Tech engineering prof, who doesn't work in IT, just a committed Linux user, persuaded Atlanta Public Schools to go to Ubuntu and helped them make the transition.

I appreciate your suggestions.

Sincerely,

---

### Post by siafulinux on 2008-04-27
> **Eric Weir said:**
> I'm responding to your previous reply and this one. Thanks for both. My current situation is that I have Kubuntu on my primary 40 GB drive with /home in a second partition and my old 10 GB drive temporarily installed as a second drive. When I've got the kinks worked out in my installation, I'll take the 10 GB out and put the second 40 GB drive back in and use it to backup /home.

Meantime I think I'm gonna give Xubuntu a try in place of Kubuntu. I haven't done much work configuring the Kubuntu installation, and I've been very disappointed in the performance of Thunderbird on both Ubuntu and Kubuntu. 

I have qtparted installed and have used it just to inspect the partitions on the two drives. I'll probably use it to format the second 40 GB drive when I put it in.

While I'm at it, I checked out your website. Kinda surprised that a Linux advocate's making a go of it outside metro Atlanta, but then I see you're at Ft. Stewart. Are you finding people receptive?

A friend, a former Tech engineering prof, who doesn't work in IT, just a committed Linux user, persuaded Atlanta Public Schools to go to Ubuntu and helped them make the transition.

I appreciate your suggestions.

Sincerely,

Hi again

I was going to suggest giving Ubuntu a try as you kept mentioning Kubuntu and then I saw you have already :-).

I used to swear by Kubuntu because I prefer KDE, but honestly, the Kubuntu team seems to be behind when it comes to the same level of integration I find in Ubuntu. I now use it almost exclusively, but I'm waiting to see how KDE 4 and Kubuntu work out after the kinks and dislikes I have with it are worked out.

~
In this area I find people deaf to any ideas other than what their buddies or peers tell them. It's very difficult. I've had a very good friend for years finally switch to Linux after getting a Vista machine. He gave his MAC to his parents and got a PC based laptop instead. He asked me to install Linux since I always brought it up and he is now becoming a Linux geek very quickly! 

Before the switch, he told me all he heard when I brought up Linux was "blah, blah... Linux, blah, blah... Free, blah, blah... great", etc. I fear this is a common situation with people. They hear all the great stuff, but until we can get them to actually "try" it, most will not begin to switch. Sadly so.

Anyway, glad to have you with us and you must spill some beans as to how you got the school system to switch - would love to do that in this area!

---

### Post by Eric Weir on 2008-04-27
> **siafulinux said:**
> I used to swear by Kubuntu because I prefer KDE, but honestly, the Kubuntu team seems to be behind when it comes to the same level of integration I find in Ubuntu.

It's clear that no matter what distribution I end up with, I'm gonna have to learn more about linux. That said, I think I have to be a bit more humble. The configurability of kubuntu -- and the color; I hate ubtuntu's red/orange/brown theme -- appealed to me, but realistically I may need something that's a little closer to a system that "just works." So maybe I should give ubuntu a second chance. Just curious, though, have you had any experience with xubuntu? I like the idea of a quick, streamlined system. 

> Anyway, glad to have you with us and you must spill some beans as to how you got the school system to switch . . . . It wasn't me, it was my friend. It started with him helping the school his daughter attended. It didn't hurt that once the district expressed interest he could actually go ahead and design and install a system for them. I don't know all the details. I'm very interested in what kind of software they're using, both for instruction and administration. 

About all I know about what they've done is that in each school all the terminals operate off one server. So in addition to not having to pay for the operating system and applications, they have also minimized hardware costs.

Curious about who does the writing on your website, i.e., the stuff that's been created locally, not the stuff you provide links to. I thought the thing that went through what ubuntu has to offer the ordinary user -- I forget the actual title -- was very well done.

As I say, curious about your experience with or impressions of xubuntu.

Regards,

---

### Post by siafulinux on 2008-04-27
> **Eric Weir said:**
> It's clear that no matter what distribution I end up with, I'm gonna have to learn more about linux. That said, I think I have to be a bit more humble. The configurability of kubuntu -- and the color; I hate ubtuntu's red/orange/brown theme -- appealed to me, but realistically I may need something that's a little closer to a system that "just works." So maybe I should give ubuntu a second chance. Just curious, though, have you had any experience with xubuntu? I like the idea of a quick, streamlined system. 

It wasn't me, it was my friend. It started with him helping the school his daughter attended. It didn't hurt that once the district expressed interest he could actually go ahead and design and install a system for them. I don't know all the details. I'm very interested in what kind of software they're using, both for instruction and administration. 

About all I know about what they've done is that in each school all the terminals operate off one server. So in addition to not having to pay for the operating system and applications, they have also minimized hardware costs.

Curious about who does the writing on your website, i.e., the stuff that's been created locally, not the stuff you provide links to. I thought the thing that went through what ubuntu has to offer the ordinary user -- I forget the actual title -- was very well done.

As I say, curious about your experience with or impressions of xubuntu.

Regards,

Well, Ubuntu's theme can be changed. The brown doesn't bother me, I kinda like it, but a sleek black and silver theme would be fantastic. Xubuntu is much like Gnome, but "lesser" than. If that's the correct word for it. It's supposed to run smoother on older hardware and originally I felt it did, but at last try, it seemed to be about as slow as Gnome on Ubuntu loading certain apps. I think it's just the apps themselves and not XFCE on Xubuntu. Give Xubuntu a try though, you may be pleasantly surprised with it.

One thing I like about using the Gnome like desktops is that Ubuntu, Edubuntu and Xubuntu are all similar in style, design and feel (Ubuntu and Edubuntu both use Gnome)... so if you're used to KDE as a user and you want Edubuntu, you have to adjust. Though you can install kubuntu-desktop. Still the integration with Gnome and even XFCE is much better in my opinion!

~
The server machine hosting multiple desktops can either be a thin-client setup (no hard drives) or perhaps a thick-client (hard drives that mount a remote /home partition); similar to what you are trying to do. Since you speak of reduced hardware, I believe it would be a thin-client. They are fantastic, but usually require a fairly decent machine to boot the remote terminals and I found there to be some problems with sound. Hence I actually prefer the "thick-client" setup, but perhaps using a CD instead of a HDD. 

Since we spoke of people who are not interested in switching to Linux earlier and thin-clients, at work I have an issue with the "IT guy" as he refuses to put Open Source on the network; but cannot tell me why. 

They have these Roaming Profiles on Windows that sometimes loads your desktop and sometimes does not until reboot. It sucks and is stupid. Switching to a thin-client or thick-client type setup would help; but no interest at all! Ugh!

~
As for the website, I believe the section on the site you are speaking of is "[Linux @ Home]("http://www.hinesvilleonline.net/home/")"? I think I wrote that page myself, but some pages I did adapt from other sources. Need to do some re-writing though! Thanks for the compliment.

---

### Post by Eric Weir on 2008-04-27
> **siafulinux said:**
> Well, Ubuntu's theme can be changed.
I'm aware of that. Even tried it. It's not so simple, though, at least not for me. E.g., changing themes doesn't change the way applications look. E.g. I created a blue theme, but when I started OOo I still got the organge-ish OOo splash screen. 

> Xubuntu is much like Gnome, but "lesser" than. If that's the correct word for it. It's supposed to run smoother on older hardware and originally I felt it did, but at last try, it seemed to be about as slow as Gnome on Ubuntu loading certain apps.I'm in the process of installing xubuntu right now. I will definitely give ubuntu another try, though.

What mail client do you use? I've been using thunderbird for a long time, and I like it. But it's never worked very well on k/ubuntu for me. Very slow. E.g., right clicking to bring up the context menu, there's a distinct pause before the menu shows up. It's that way with everything. Every action is noticeably delayed. Scrolling in mail boxes is very jerky. It can't keep up with either the scroll wheel or the slider. After you stop scrolling on the wheel, it continues to scroll jerkily through the message list. Makes it very difficult to go to a specific place in a list. Not at all my experience with tb on windows.

I thought putting my installation on a 40 gb drive -- it was on -a 10 gb previously, and had gotten VERY slow there -- --, would improve tb's performance, but it hasn't. Again, the rest of the system is a piv 1.6 ghz and 512 mb of ram. 

> The server machine hosting multiple desktops can either be a thin-client setup (no hard drives) or perhaps a thick-client (hard drives that mount a remote /home partition); similar to what you are trying to do. Since you speak of reduced hardware, I believe it would be a thin-client.Yes, that's what it was.

> As for the website, I believe the section on the site you are speaking of is "[Linux @ Home]("http://www.hinesvilleonline.net/home/")"? I think I wrote that page myself . . . .That was it. You did a good job.

A question about the xubuntu installation that's underway now -- 83 % done -- I opted for manual partitioning, just to make sure, as near as that can be done, that the existing partitions would be preserved. I did have to assign mount points. For the main partition on the second drive I wanted to use /dev/sdb1, but that was not an option. I chose one of the options that was offered -- either /tmp or /usr/local -- -assuming I could change it later. 

Did I do the right thing? I want to use the second drive just as a place to back things up, mainly my /home folder. Would /dev/sdb be an appropriate mount point for that purpose. Also, why wasn't that an option?

Regards,

---

### Post by siafulinux on 2008-04-28
> I'm aware of that. Even tried it. It's not so simple, though, at least not for me. E.g., changing themes doesn't change the way applications look. E.g. I created a blue theme, but when I started OOo I still got the organge-ish OOo splash screen.

Going to "System" -> "Preferences" -> "Appearance" changes the windows, icons and popups to the colour theme specified. Not sure why it doesn't work for you. I still get the brown OpenOffice splash screen, but I think that doesn't have anything to do with the system theme itself.

> What mail client do you use?

I currently use Evolution. Don't know why Thunderbird would be slow though? It may just be a Thunderbird issue rather than Ubuntu.

> A question about the xubuntu installation that's underway now -- 83 % done -- I opted for manual partitioning, just to make sure, as near as that can be done, that the existing partitions would be preserved. I did have to assign mount points. For the main partition on the second drive I wanted to use /dev/sdb1, but that was not an option. I chose one of the options that was offered -- either /tmp or /usr/local -- -assuming I could change it later.

Did I do the right thing? I want to use the second drive just as a place to back things up, mainly my /home folder. Would /dev/sdb be an appropriate mount point for that purpose. Also, why wasn't that an option?

I'm not sure about this. About to walk out the door, but will see what I can find when I get back from work, though by know I'm sure you already know what happened...

JC

---

