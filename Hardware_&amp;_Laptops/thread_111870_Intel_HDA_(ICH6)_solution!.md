---
title: "Intel HDA (ICH6) solution!"
date: 2006-01-03
forum: Hardware &amp; Laptops
---

### Post by basje on 2006-01-03
Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

A lot of people have problems with this and much of those point a finger to ubuntu when in fact this is an Alsa problem and should have been solved before the alsa support for this card went into the kernel.

First of all there loads of people that have problems during boot when hotplug loads this module, the sollution is to boot in recovery mode and run
$> chmod -x /etc/init.d/hotplug
$> reboot

Now you will boot into ubuntu but without sound and a probably without some of other stuff, but at least you will boot.

The problem with the intel-hda module is solved in alsa-1.0.9, which you can find in kernel 2.6.14 or on the alsa website. So, if you compile the 2.6.14 kernel or the >= alsa 1.0.9a your problem will be solved.

Since the 2.6.14 kernel solves loads of laptop trouble (especially on new ones), I took this solution, but if everything else works alright, I advise to take the easy road and compile the new alsa drivers.

A lot of people that get this card to work also complain about the headphones output that is not working, this should be solved in alsa 1.0.10, so if you recompile your alsa drivers, keep in mind of taking really the last version.

after compiling the kernel and the drivers, you should not forget to run
$>sudo chmod ug+x /etc/init.d/hotplug
to reactivate hotplug during boot.

I solved my trouble with this solution on my Asus A3W00E

greetings,
Basje

---

### Post by jezjones on 2006-01-23
Hi there,

Thanks for suggesting this solution however i cannot get it to work.

I have been trying to get sound working with ubuntu on my laptop since Hoary and i have come to the conclusion that ALSA is the problem. It is very difficult to install correctly, requiring loads of packages that are non-standard.

I have just recompile a 2.6.15 vanilla kernel from kernel.org to get the latest.
I also used alsa 1.0.11rc2 which again is the latest.

I installed the alsa-lib package and the alsa-utils.
Now i get a popping sound when i change volume controls but nothing comes out of XMMS, but unlike before with the alsa version bundled in breezy, XMMS does not complain of a misconfigured sound card.

In total i think it have spent about 30 man hours on this over the last three months. If that was contract work (which i do for a living) i would have paid for the laptop again!!!

So my situation is that i have an up to date sound card. 
I have the very latest kernel.
I have the very latest alsa.
Things are installed correctly (according to the system).....

Still no sound. I am about ready to throw this machine out the window!!
I have done an alsaconf and it saw the right card etc.
I have gone into alsamixer and there are no channels that are muted.

Just what is the big issue with linux and sound???
I think that part of the problem is that there are about a million competing programs to do it... so that within Gnome i can set the sound to contradict itself with setting one thing to ESD, another to OSS and a third to ALSA.

Now before anyone tells me how good sound is when it is detected out of the box, that is not a good way to judge something. 
How good something is can be best judged by how easy it is to troubleshoot.
Having just recompiled a kernel, without issue, I spent more time trying to figure out and install the drivers, even now i only think it all went ok.

Given that i am not a newbie, i feel this is a key area where linux and in this case Ubuntu needs work.... lots of it!!!


Jezjones

---

### Post by jezjones on 2006-01-23
Ok, now i am just about to throw my machine away and head back to redmond.

I have rebooted from the above it seems that my sound card is no longer configured... when i open xmms i get told that things are not right.

Is this because the modprobe i did after the alsa drivers install was not run at start up so the new drivers are not being inserted into the kernel?

Also i am getting the following at the start of my dmesg

```

Cannot allocate resource for EISA slot 1

```
and then the boot up is in the dark until i get to the gdm screen.

So my thoughts are now that sound is simply too difficult to make work in linux... especialy with the poor documentation on the alsa site.... or use old hardware.
Without getting into a big rant, is this really the future of linux? Either use old hardware to ensure that it is supported or use a commercially supported OS.
From a practical point of view, the driver situation with linux has not changed in the last 3 years i have been using it so why should it change in the future - there is no cost benefit to developing for linux.... nvidia might be making drivers for linux but they are about the only ones!!!!!

I do appreciate all the help i have got from this forum, but it is a concern that despite so many people having this problem there is not a fix for it.... or the fix is so complex that it is easier to reboot to the other (XP) partition when i want to watch a movie of something!!

---

### Post by iNerdSure on 2006-01-23
For a moment when I saw the title, I was excited that the SILENT NO SOUND barrier is finally broken. Alas, this isn't to be. For all the M$Win bashing, and all the praises heaped on Linux, my experience with the conversion hasn't been at all satisfactory. 

For someone who depends on a laptop (whatever the OS) to make a living, I find it most frustrating to be unable to have sound in order to run Skype, or do product video clips, or even use my modem when I need to send a fax.

I'm a Linux newbie, but have used PCs since M$DO$ days from 1980s. For all the hype of stability and resistance to virus, spware and adware, my view is that why does one need a stable and robust PC when it can't deliver all the functionality?

This has been my main disappointment. For the thousands of downloads/hits per day, plus s-nail mail copies, and the 6-monthly distro new release, why swarm and overwhelm users, especially newbies, when a few key functionalities of the OS is not performing, when, perhaps, efforts should be focussed on bugging these issues out first. 

Well, I hope some expert guru or developer in the community is reading this forum to have a good feel of what the users are experiencing.

---

### Post by incubus on 2006-01-23
Same problem here.
However, I installed Dapper in another partition and the issue is solved there (newer kernel and alsa). 

My question: is there is a way of apt-getting only what is necessary from dapper to make the sound work on breezy? This seems to me a more debian (elegant) kind of solution.

I tried to install only alsa-base and alsa-utils, but it didn't work. 

Thanks,
incubus

---

### Post by jezjones on 2006-01-27
dont suppose you could tell me how to get dapper?

I had a look but there doesnt seem to be a download for it... is it only bit torrent?

Jez

---

### Post by Jason_25 on 2006-01-27
[http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/)

releases > dapper > flight 3

---

### Post by incubus on 2006-01-29
Well. It seems that using Dapper packages in Breezy is not a very good strategy. I couldn't make it work and worse, other things broke.

I don't recommend others to follow that path. The sound in Dapper is working almost 100% for me. But we still have to find a solution for Breezy, which is the current stable version of Ubuntu.

In case you haven't seen this, take a look at:
[https://wiki.ubuntu.com/HdaIntelSoundHowto](https://wiki.ubuntu.com/HdaIntelSoundHowto)

Best,
incubus

---

### Post by incubus on 2006-01-29
Ok, I put laziness away and decided to try the solution in the Wiki I just posted (i.e. download and install Realtek's own ALSA drivers).

It worked perfectly and I'm listening to music in Breezy. So far it seems to be very robust. The one in Dapper is not perfect in my case.

Not my favorite approach, but better than using an unstable distribution, Dapper, just to have sound.

Hope that helps other people,
incubus

PS: Although the Tarball file has an automated script to install everything for you, you'll need the packages for compiling.

---

### Post by iNerdSure on 2006-02-03
Anyone experimented with the latest ALSA drivers in 1.0.11rc3 releases? If yes, hope you would share the experience, good or bad. Thanks in advance.

---

### Post by iNerdSure on 2006-02-12
Experimented with ALSA 1.10.11rc3 drivers today. Still NO SOUND! :Absolute SILENCE :( 

The dmidecode output still shows "Disable" status:
[PHP]
Handle 0x000D
        DMI type 10, 6 bytes.
        On Board Device Information
                Type: Sound
                Status: Disabled
                Description: ADI

[/PHP]
So, perhaps, the cause isn't with the ALSA drivers, but rather that of the BIOS? Anyway, I'm just not technically competent enough to figure out.

---

### Post by jundalabee on 2006-05-01
Hi Pplz,

I found a solution that worked for me. Probably a fluke. I have an Asus p5ld2.

I downloaded the new Alsa drivers, (no luck). Then I downloaded the latest realtek drivers (Reltek_linux34). I just extracted them, went to the decrompressed directory, ran a ./install as su. After this I changed the setting in Volume Control (Applications, Sound and Video, Volume Control), in the File, change device from HDA to Realtek. 


Might I say the new Tool album sounds sweet.

---

