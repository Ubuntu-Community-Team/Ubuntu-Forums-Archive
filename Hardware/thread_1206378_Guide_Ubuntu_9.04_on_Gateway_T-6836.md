---
title: "Guide: Ubuntu 9.04 on Gateway T-6836"
date: 2009-07-07
forum: Hardware
---

### Post by kaoskorruption on 2009-07-07
If you are reading this, you likely reading my guide for Ubuntu 8.10 on the Gateway T-6836. I am finally getting around to making a guide for 9.10! Overall, 9.10 does work a lot more smoothly, though I would suggest doing a full reinstall rather than an upgrade. I took the upgrade path, which worked okay, but I later found that reinstalling just works more smoothly.

[IMG]http://content.gateway.com/www.gateway.com/media/products/large/t6836.jpg[/IMG]

As I said in my previous guide, the Gateway T-6836 is a great laptop for the price and I would recommend it. It is a sibling of the T-3828 too, so what works for one might work for the other (though not always). Anyways, on with the guide...
[SIZE="5"]
Headphone Issue[/SIZE]
The headphone jack does not work properly upon installation. To fix it, you basically have to upgrade your sound drivers:
1. Download this script: [http://ubuntuforums.org/attachment.php?attachmentid=113163&d=1241945700](http://ubuntuforums.org/attachment.php?attachmentid=113163&d=1241945700) (if that does not work, find the Alsa Upgrade script in this post: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)) - Best to save to desktop rather than opening.
2. Extract the contents to your desktop.
3. Open the terminal (Applications->Accessories->Terminal) and enter ```
sudo ./AlsaUpgrade-1.0.x-rev-1.17.sh -di
```
4. This should take 10-15 minutes. If you think it is frozen, just keep waiting, you wouldn't want to stop the script while it is running.
5. In the terminal again, enter ```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
6. At the very end of the file, add these lines:
```
# This line fixes the headphone jack on the T-6836
options snd-hda-intel enable_msi=0 model=eapd
```
7. Save, exit, and reboot.
8. Play "Time Of The Season" by the Zombies, relax, and enjoy your working headphone jack.

The only other issues with the T-6836 are that Compiz does not work and that the brightness buttons don't work. I will add information on how to get these working as soon as I figure it out. Hope you enjoy your new, working operating system!

---

### Post by odwyerda on 2009-07-17
Hi

Thanks for your guide for 8.04 helped me loads with issues I was having.

I currently still use 8.04 mainly due to my college network. The network in 8.10 did not connect to the wireless network for more than 30 seconds after I upgraded. This issue as far as I could tell was due to the fact that the network manager did not have WPA enterprise only WPA enterprise 2 and for some messed up reason no stable connection could be made. This problem only occured for this laptop and not any others that had 8.04 installed.

Before I upgrade is there a possibility of using the 8.04 network manager? because with out the internet it is pointless.

Many thanks

David

---

### Post by Genecks on 2009-07-17
First off, I wouldn't say the old thread was irrelevant. It was useful. It still may be of use to many users.
[SIZE="5"]
Headphone issue:[/SIZE]
Has anyone experienced a problem with headphones after putting a computer to sleep or hibernating it? I have used the ALSA update script provided on the Ubuntu forums for Debian Lenny. It worked. However, when I put the computer to sleep/hibernation and woke it up, the headphones no longer worked. I had to restart the computer for things to work again.

[SIZE="6"]Screen brightness idea:[/SIZE]
If anyone could get a command for the brightness to change on the screen, then I suspect the brightness keys could be hotkeyed using xkeys or something.

I know xbrightness and xbacklight are two command-line based things for controlling light output. I'm not sure if xbrightness would help reduce battery usage.

I took a look at this from the old thread:

> #!/bin/bash
if on_ac_power; then
setpci -s 00:02.0 F4.B=FF
else
setpci -s 00:02.0 F4.B=B2
fi

I got into a root terminal and tried this:
setpci -s 00:02.0 F4.B=B2

I noticed that it dimmed the screen. This is a good thing.
So, what I have in mind is creating a script that keeps track of what percentage the computer is on.
For instance, at startup, the script will have 100%.

Let's say the file is $HOME/.lcdbrightness/percent

When you use a brightness key (hotkey'd, of course), it checks the percent in that file, cats it to terminal, and either brings down or up the percentage (mathematically), logs it, and then it applies that percentage.

That looks like a good way to tackle this remaining issue.


It looks like it's based on hexadecimal to decimal.
So, the FF = 255.
And the B2 = 191

So, B2 is 191/255 = 0.749019608
~ 75% brightness


[http://www.easycalculation.com/hex-converter.php](http://www.easycalculation.com/hex-converter.php)


There should be a way to give a non-root user the ability to use the setpci command. I suspect this would be creating a secondary script with setpci already in it, and giving regular users permission over it:

all users read/execute access:
> 
setpci -s 00:02.0 F4.B=

And then a third script does the math above, appends it to that secondard script, and eventually changes the brightness.

> **odwyerda said:**
> Hi

Thanks for your guide for 8.04 helped me loads with issues I was having.

I currently still use 8.04 mainly due to my college network. The network in 8.10 did not connect to the wireless network for more than 30 seconds after I upgraded. This issue as far as I could tell was due to the fact that the network manager did not have WPA enterprise only WPA enterprise 2 and for some messed up reason no stable connection could be made. This problem only occured for this laptop and not any others that had 8.04 installed.

Before I upgrade is there a possibility of using the 8.04 network manager? because with out the internet it is pointless.

Many thanks

David

No, I wouldn't screw with an Ubuntu update. Whenever you need a specific OS, keep in mind to always keep it on the HDD. Debian users who play with Sid (unstable) and stable know this. 

Ubuntu 8.04
> Released April 2008 and maintained until April 2011 – ideal for large deployments

I suggest you partition the drive -- backup first -- and then install the newer ubuntu onto a different partition. Otherwise, you could play with a Live-CD and see if you can get things working. But don't delete something that works.

---

### Post by odwyerda on 2009-07-18
> **Genecks said:**
> 
I suggest you partition the drive -- backup first -- and then install the newer ubuntu onto a different partition. Otherwise, you could play with a Live-CD and see if you can get things working. But don't delete something that works.

Don't I know it. Thanks

Dave

---

### Post by enriqg9 on 2009-07-18
Manually install Kernel 2.6.30 and you will have the Gateway T-6836 running perfectly!, the headphone jack will natively work perfectly, including the brightness keys, and all know issues will be correct now!!

---

### Post by Salvar Fawkes on 2009-07-23
> **enriqg9 said:**
> Manually install Kernel 2.6.30 and you will have the Gateway T-6836 running perfectly!, the headphone jack will natively work perfectly, including the brightness keys, and all know issues will be correct now!!

Hmm. Is that going to be the kernel used in Karmic?

---

### Post by c_wilson on 2009-08-05
> **enriqg9 said:**
> Manually install Kernel 2.6.30 and you will have the Gateway T-6836 running perfectly!, the headphone jack will natively work perfectly, including the brightness keys, and all know issues will be correct now!!

Kernel 2.6.30 does fix the screen brightness and brings compiz back, but i still have to upgrade alsa to get the headphones working. Are you getting headphones without the upgrade?

I am experiencing the sound breaking in flash both when the upgrade script is invoked with -di and when invoked with -snap. Sound in flash works fine unless you open a music player before you open your browser in which case flash has no sound. The opposite is true as well (if you play flash, and then open rhythmbox or audacious, you won't be able to play music) My current work around is just closing and opening applications in the necessary order, but perhaps someone has a better option?

EDIT: Solved through Preferences --> Sound. Changed everything to ALSA instead of Autodetect. Rapidly running out of things to fix!!1

---

### Post by kaoskorruption on 2009-08-12
My sound suddenly stopped working completely. I suspect a recent update. Has this happened to anyone?

---

### Post by lilyselden on 2009-08-13
> **kaoskorruption said:**
> My sound suddenly stopped working completely. I suspect a recent update. Has this happened to anyone?

Hi to all. This is my first post after weeks of lurking/learning.

Same problem here (on a T-6836 running 64-bit Jaunty.) This was after I updated with a lot of medibuntu stuff to try to get my DVD and Mp3 players working, and restarted. 

Question: While I absolutely LOVE the fact that there is an Ubuntu 9.04 guide specifically for my laptop (Yay!) I have to wonder if this is a guide only for the **32-bit version** on a T-6836? 

The reason I ask is actually not because of my current issue; I'm sure I broke the sound all by myself. :)
 It's just that earlier (as in,** today**), the speaker sound was fine, but not the headphone sound, and I did the nifty headphone jack trick detailed in the first post and it didn't work. And I'd previously been running 32-bit Jaunty, and had the same issue, and it DID work perfectly in 32-bit. 
(In fact, I had the 32 bit working perfectly until I broke it earlier this week trying to disable Nautilus wallpaper --don't ask) and after failing miserably at trying to repair Gnome and Nautilus from the rescue mode command line, I decided to do a complete reinstall with the 64-bit version. And this time I created separate partitions of /boot, /home, /usr, /var, etc.  

I'm dual-booting with 64-bit Vista (which I'd love to leave altogether one day), and all of my files are backed up already, so...long story short...I **can** afford to scrap this version (again) and go back to 32-bit, where I, at least---through a whole lot of reading this forum--I *did* have all of my sound and multimedia working. Even Compiz was perfect. I've had many more issues since I went to 64-bit. Not looking forward to another reinstall, but like I said, I can do it; it won't kill me. 

Should I just go back to 32-bit? Anybody running 64-bit got it running okay? Believe me, I don't mind at all trying to FIX the current problems, because it's the only way you learn, but if another 64-bit related issue will just pop up, and 64-bit is just more trouble than it's worth.....

Thanks in advance for any suggestions or insight.   :)

(And yes, I did read the sticky post about the pros and cons of 64-bit vs. 32-bit. The cons didn't seem so bad. And I felt stupid not taking full advantage of my 4G RAM, 64-bit machine.)

---

### Post by c_wilson on 2009-08-13
I've been using the 64-bit version of Jaunty and gotten pretty much everthing up and running by upgrading Alsa and manually upgrading to kernel 2.6.30. Others can speak for themselves, but i'm pretty sure i'm not the only one on 64-bit

---

### Post by lilyselden on 2009-08-14
> **c_wilson said:**
> I've been using the 64-bit version of Jaunty and gotten pretty much everthing up and running by upgrading Alsa and manually upgrading to kernel 2.6.30. Others can speak for themselves, but i'm pretty sure i'm not the only one on 64-bit

Thanks for that, c.wilson.

I did wonder about the kernel upgrade; it's about the only thing I haven't done yet. I'll try that and report back.

:)

---

### Post by kaoskorruption on 2009-08-19
The headphone issue came back for me. It won't work. Anybody else running into this problem?

---

### Post by kaoskorruption on 2009-08-20
> Question: While I absolutely LOVE the fact that there is an Ubuntu 9.04 guide specifically for my laptop (Yay!) I have to wonder if this is a guide only for the 32-bit version on a T-6836? 

I based this guide on what I've tested to work on my 64bit version, so if anything, it should work on the 64bit. Still trying to work on fixing this sound thing :\

---

### Post by c_wilson on 2009-08-21
> **kaoskorruption said:**
> The headphone issue came back for me. It won't work. Anybody else running into this problem?

Kernel 2.6.28 has been in the update queue for the last few days as a security update. Did you run updater in the last few days? Maybe that did it?

My headphones are still working.

---

### Post by Genecks on 2009-09-26
*note 
I use debian, but my info is valuable.

BTW, I believe I'm using the 32-bit version of Debian Lenny.
2.6.26-1-686-bigmem

[SIZE="5"]Sound issue re-occurrence:[/SIZE]
Seems to occur with an upgrade to 2.6.26-2-686 kernel.

Plan of action:
1. Remove 2.6.26-2* kernel; remove headers
2. Reinstall 2.6.26-1 kernel; add in headers for that kernel
3. redo the alsa upgrade script
4. in addition (related but off topic), please install r8101 driver instead of r8169 driver
- main website: [http://www.realtek.com.tw/](http://www.realtek.com.tw/)
5. keep reading...

I often find that simply staying one place in time can often keep a system working, which means you don't update anything unless it's a security update. I can't remember if the kernel upgrade was a security update. If so, then it's an issue. I don't think it'll be too serious.

blacklist that old eth0 driver -->

nano /etc/modprobe.d/blacklist

add: blacklist r8169

5. REBOOT

* There is still that issue if you pull out the headphones and then try to replug them in, it won't work unless you reboot. That kind of sucks. I'm sure some kernel or alsa update will eventually get to this.

It'd be nice if someone created a script based on the mathematics that relate to the light control for this laptop. Review some of my old posts for info. Remember, folks, we wouldn't get this far without teamwork.

Other than that...

:guitar: on!

---

### Post by Genecks on 2009-09-27
I'm on an ubuntu live-cd at the moment.
I am able to get the sound right off the bat.
I am also able to plug the headphone jack in and out multiple times without things becoming disabled. I have not tried a microphone feature.

Here is what I am using:

> 
Our first release (Warty Warthog) was in October 2004 so its version was 4.10. **This version (Hardy Heron) was released in April 2008 so its version number is 8.04.**
							
kernel version:
 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

I haven't played with the video settings, but the ethernet seems to be working just fine. However, if this were a HDD install, i'd probably put in the newer driver.

:guitar:

alsa-base
vers: 1.0.16-0ubuntu4

[IMG]http://img87.imageshack.us/img87/2835/alsabase.png[/IMG]

alsa-utils
vers: 1.0.15-3ubuntu2
[IMG]http://img87.imageshack.us/img87/7827/alsautils.png[/IMG]

linux-sound-base
vers: 1.0.16-0ubuntu4
[IMG]http://img87.imageshack.us/img87/8187/linuxsoundbase.png[/IMG]

---

### Post by greencupbay on 2009-10-29
So, it has been about a month since anyone has written on my favorite thread for Ubuntu help. I am a total noobie to this Ununtu stuff. I am running Linux Mint (based off of Ubuntu, just a little nicer) and I still don't have headphone sound. I tried a few things mentioned above, but what ACTUALLY works? I really don't want to have to 'roll back' (windows? What's that?) my kernel for sound support. If anyone has a way to fix this, please reply with steps YOU took to help everyone out with a T-6836 that doesn't know what they are doing. Thanks for the support, friends!

---

### Post by kaoskorruption on 2009-10-30
9.10 came out today with an implementation of a newer kernal. I'm upgrading right now. Anybody want to report on whether or not this is fixed for them?

Update:

I just upgraded to 9.10 and everything is working flawless for the first time in a release with the exception of the brightness controls as they have never worked. This seems to be a spectacular release with lots of new, hopefully useful features. I would say that with this version of Ubuntu, I finally feel comfortable recommending Ubuntu to even my less tech-minded friends.

Minor Complaints:
Boot/Hibernate are still not that fast.
Brightness controls still don't work.

---

### Post by odwyerda on 2009-10-31
Does the network manager have WPA enterprise?

My college network doesn't seems to like WPA 2 enterprise. Hence me being on Ubuntu LTS. Want to upgrade but dont want to loose the internet.


Any other install issues ?

Cheers?

---

### Post by kaoskorruption on 2009-11-01
I know it supports WPA/WPA2 Personal. Not sure about enterprise - you'll probably have to do some looking around.

---

### Post by odwyerda on 2009-11-02
Cheers, 

it seems that no is still the answer. I presume WiCd would work but the last time it didnt like connecting to wireless too much !


Ill see this weekend.

---

### Post by c_wilson on 2009-11-04
> **kaoskorruption said:**
> 
I just upgraded to 9.10 and everything is working flawless for the first time in a release with the exception of the brightness controls as they have never worked. This seems to be a spectacular release with lots of new, hopefully useful features. I would say that with this version of Ubuntu, I finally feel comfortable recommending Ubuntu to even my less tech-minded friends.

Minor Complaints:
Boot/Hibernate are still not that fast.
Brightness controls still don't work.

Yep. Everything seems to working with the exception of the brightness controls. This is on a clean install *not* an upgrade.

---

### Post by kaoskorruption on 2009-11-26
Just wanted to let you know that I see there IS WPA/WPA2 Enterprise.

---

### Post by Salvar Fawkes on 2009-11-26
Something odd is going on with 9.10. The sound works fine (after adding ignore_DB=1), which is a huge relief, but the backlight doesn't dim on its own, and even the workaround isn't working. setpci is still capable of dimming it, but putting those scripts in those locations doesn't seem to have any effect. Any thoughts?

---

### Post by odwyerda on 2009-12-07
> **kaoskorruption said:**
> Just wanted to let you know that I see there IS WPA/WPA2 Enterprise.

Is that in the default network manager install?

Under the last one WPA/WPA2 enterprise were the same option and my network just didnt like it at all.

(i still have to get around to doing the install just the thought of it is stopping me but from what i hear its worth it)


Thanks for letting me know :)

---

### Post by odwyerda on 2010-03-31
Has anyone tried 10.04 yet?
Is there any known issues, I may try it this Easter weekend if there are any known problems it would be nice to know.

Dabhi

---

### Post by c_wilson on 2010-04-03
> **odwyerda said:**
> Has anyone tried 10.04 yet?
Is there any known issues, I may try it this Easter weekend if there are any known problems it would be nice to know.

Dabhi

I've been using 10.04 pretty much daily since alpha 2 and everything seems to be working great except, unfortunately, the brightness controls which are still a no go.

---

### Post by odwyerda on 2010-04-11
Cool thanks, Ill give it a shot over the next week or so.

Does the gapa.exe under wine not work????

---

### Post by odwyerda on 2010-05-13
Hi,

I upgraded to 10.04 and almost everything works great except one or two things so I thought I'd ask here to see if they are specific to me.

1) when on battery power the fan and disk dont stop, reducing battery lifetime alot. Indexing is turned off also. Quite annoying

2) All my web browsers are very very unstable. Before upgrade they were perfect now they freeze and crash for no reason very frequently

---

### Post by Ecologger2 on 2010-11-10
Has anyone upgraded to 10.10 to see how it works with the hardware? I'm still using 9.10 out of fear of losing control.

---

### Post by c_wilson on 2011-03-16
I stuck with 10.04 because i didn't see any compelling reasons to upgrade to 10.10. 

BUT, i just installed 11.04, and despite the fact that i definitely have yet to be sold on the unity interface, i am totally PUMPED to report that somehow two finger scroll now works. Brightness still requires gapa.exe but everything else seems to be working, sound, wireless, etc.

---

