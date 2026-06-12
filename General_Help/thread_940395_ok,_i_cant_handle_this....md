---
title: "ok, i cant handle this..."
date: 2008-10-07
forum: General Help
---

### Post by timstone on 2008-10-07
i have found no way to record 2 sources from my sound, so now i need to add a new windows partition and install xp on there, or do a vmware install or something...

what is the easiest and most painless way to go about doing this?

---

### Post by cariboo on 2008-10-07
Why not explain your problem, we may be able to help.

You will probably run into the same problem with a vm as it uses virtual hardware instead of the real thing.

Jim

---

### Post by timstone on 2008-10-07
ok well then i dont want VM, ill have to re-partition somewhere

the problem im having is that i cant record from my mic, while playing music...and i cant have that!

---

### Post by tgalati4 on 2008-10-07
I assume that you tried alsamixer and you weren't able to mix properly?  You need to give us some more info on your hardware and what specifically you are recording.

---

### Post by timstone on 2008-10-07
ok...more info....here you go

```

tim@tim-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)
03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 03)

```

as you can see i have onboard sound...i used to have a soundblaster card but i think i threw it out for some reason....

what im trying to record is my voice + background music, but it only allows me to do one or the other....i cant even record voice and just LISTEN to the music at the same time, it always tells me there is no recording device or the sound device is in use.

i have alsa and pulse audio both and neither have seemed to work, possibly because i dont now how to set them up properly i dont know

---

### Post by timstone on 2008-10-07
ok since no one has the answer, how do i go about making a partition big enough for windows so i can dual boot?

---

### Post by timstone on 2008-10-07
this forum sucks for help

---

### Post by Titan8990 on 2008-10-07
> this forum sucks for help


Thank you for posting to get free help from volunteers, not even waiting 24hrs, and then telling us we suck. You are the reason we continue to help people. Also, I have to tell you, you could not have been more persuasive in getting people to assist you.

/sarcasm off

---

### Post by timstone on 2008-10-07
well see the problem is this.....people post asking what your problem is, then they just disappear, its like they had no intention on helping....

---

### Post by Titan8990 on 2008-10-07
Or it could be that:

A) They did not have a solution to your problem

B) Only check the boards a couple times a day and have not yet checked back with this thread

C) Were turned off by your attitude for the entirety of the thread


Don't worry. I am going to point you in the right direction for getting effective help on forums such as these. Here is the [Survival Guide to Technical Forums](http://www.joehobart.com/postingguide.htm)


Edit: I personally give a thread about 1 week (what I have always considered reasonable) to get help, only bumping daily (this is the policy of this forum anyways). Instant gratification just can not be expected unless you are paying someone.

---

### Post by jancelis on 2008-10-07
With that attitude this is the only answer you'll get from me

---

### Post by jerome1232 on 2008-10-07
> **timstone said:**
> this forum sucks for help

Thanks.

I'm going to help a bit anyways despite your attitude.

Pulseaudio is designed with these things in mind, it can send streams to different sound cards on the fly, it can pipe audio across the network and more, what program are you using to record audio? Is it only designed to use OSS or Alsa?

If you just want to repartition to install windows you can boot into a live cd and use gparted for this, System->Administration->Partition Editor.

beware installing Windows will wipe your mbr and make Ubuntu unbootable, it's installer isn't designed with other os's in mind.

---

### Post by tgalati4 on 2008-10-09
This forum is better than most for providing help, but you need some patience.  It's not like we are logged in 24/7.  (Well some are.)

There seems to be a knowledge gap here.  Recording multiple channels is not difficult in linux.  Many folks do it all the time.  It may not be easy to set up depending on your harddware.

You have an intel ICH6 chipset which is well-supported under linux.  You need to tell us what recording setup you are using (hardware and software) and tell us what you have tried so far.

You can use alsa, jack, or pulse audio to mix your channels.  If you are using audacity for recording, then you may need an oss-to-alsa wrapper to get the combined recording.

---

### Post by EmanresuusernamE on 2008-10-09
> **timstone said:**
> this forum sucks for help

Did you pay for support?  Doubt it.
Did you pay for the OS?  Shouldn't have.
Are we talking to you in English or some other language? English.

Hey, guess we're a bit better than other places.  As others have said, we're volunteers.  Oddly enough, some of us have lives that we must attend to, (like a job, spouse, children or pets perhaps).

If you want faster results, either pay up or shut up.

---

### Post by meditatingfrog on 2009-08-03
> **timstone said:**
> well see the problem is this.....people post asking what your problem is, then they just disappear, its like they had no intention on helping....

Do you have critical data on your system?  I mean, if it's urgent that you record your music, then you could just back up any critical data, install Windows XP, create two partitions with the XP installer, then reformat and reinstall Ubuntu on the second partition.  That should work.

I'm not sure how to resize partitions after an installation of an operating system, but there is probably a software package that was written that will allow you to do this while you have Ubuntu installed so your data will stay in tact (I would still recommend backing up any CRITICAL data).  

What kind of searching have you done to try to find the software package that would do this?  Have you tried searching for "partition" in synaptic package manager or add remove programs?

---

