---
title: "Ubuntu not installing on new build"
date: 2011-01-19
forum: Hardware
---

### Post by DukeBoxer on 2011-01-19
I just built a new desktop, planning on using it as an HTPC/Web Server/In house file server and I can't for the life of me get ubuntu installed/to work on it. There is either a kernel panic when trying to start up the live CD of 10.04 and if I try to install 10.10 with the alternate installer it works fine but after I restart it locks up after about 10 minutes, this continues until it locks up right at the login screen. Here are my specs

Asus P7P55D-E Pro Motherboard, 1156 chipset
Intel Core i5 760 Quad Core
2 x 4 Gigs GSkill Ripjaw 1333 Ram
MSI Twin Frozer GTX 460 Video Card
16 gb Kingston SSD
1 TB Seagate HDD

(I know this is overkill for what I want to use it for, but I do want it to last for and be relevant for many years)

This seems to be a problem with Linux itself because I can install *cough* Windows 7 and everything works just fine. I can get logs and stuff if someone can tell me what they need for me to copy down. Sometimes it seems like it says something about the CPU when the kernel panic happens. I've even tried to install 11.04 (upgraded from 10.10) but still nothing. Unfortunately I can't accept it and install Windows on it, thats not why I built the computer, so any help would be appreciated.

One more thing, I don't think it's a problem with the video card because I borrowed a GeForce 8800 from a friend and the same thing happens. I also removed one of the RAM sticks, unplugged a card reader and the Blu-Ray/DVD drive and only left the hard drives plugged in and there was still a problem.

Thanks for any help!

---

### Post by MiKOTRON on 2011-01-19
Can you tell us what it says about the CPU when when it crashes?
Try to install again and use ```
**BOOT_DEBUG=2**
```That should give you lots of information and let you know what it did when it crashes.
It seems like the kernel just isn't jivin' with your hardware right out of the box.  When we find out where it went wrong, we'll be able to change the boot parameters to fit your hardware. 

Let us know. ;)

---

### Post by DukeBoxer on 2011-01-19
Where would I get the log from after it debugs? Sorry but I've never had to do something like this before. Also when I start the installer where do I go to enter that code, to the more options part (like F something right?)

---

### Post by MiKOTRON on 2011-01-20
All of your logs will be in /var/log  The BOOT_DEBUG=2 option will make the installation verbose so that you see what's happening.  
Check this out.[ https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions") See the F6 part and appending part.

---

### Post by DukeBoxer on 2011-01-23
ok so here is what it said with ubuntu 10.10 desktop

Kernel Panic: Not Suncing, attemted to kill idle task
PID: 0, comm Swapper Taitned: G  D

I also saw that my MoBo is compatible with installing Mac OS X so I put an installer disk in to see what would happen with the verbose mode

Panic CPU 3 caller kernel trap at 0x00226790, type 14 page fault

I also had a similar kernel panic talking about cpu 3 trying to start the live mode of PC-BSD 8.2

Could there be a problem with the CPU itself. I find it hard to believe becasue Windows installed fine on this machine.  I've swapped out video cards, took out one of the sticks of RAM, unplugged everything except for the essentials and I still get problems. This is killing me.

---

### Post by DukeBoxer on 2011-01-23
UPDATE- I unhooked everything except for the SSD, the video card and one  stick of RAM (so only 4gb) and I started it up in LiveCD mode and it  didn't freeze after about 3 hours of being on, which is way more time  than it ever lasted before. Now my problem is the Ethernet port isn't  working. I'll look into that then try putting things back in 1 by 1 and  see where the problem is taking place...

---

### Post by DukeBoxer on 2011-01-25
Update 2 - I restarted to see if I could replicate the "no freeze" and it froze again in about 2 minutes so that was just luck that it didn't freeze. I did notice that if I hit the power button, the "shut down the computer" prompt came up, so it seems it's just the keyboard and mouse that are frozen. At the end of the day though I ended up sending the MoBo back because the ethernet port stopped working. We'll see what happens with the new one...

---

### Post by MiKOTRON on 2011-01-25
I'm wondering if it's your video card driver...  Are you using the proprietary Nvidia drivers from the Ubuntu "additional drivers" tool? Try installing the driver binary provided at nvidia.com [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) The latest version is 260.19.36[U]

[/U]It looks like the old driver has a bug that that caused X servers version 1.9 and higher to crash when color index overlays  were enabled.

I just guessing but when you said that your mouse and keyboard stopped working it's probably because X crashed.  The X server controls those functions.

BTW that GeForce GTX 460 looks awesome from what I read!
__

---

### Post by MiKOTRON on 2011-01-25
The fact that you used your friend's video card, I don't think matters because it's the same driver for both cards.

---

### Post by DukeBoxer on 2011-01-26
This was happening both the restricted drivers and the nouveau drivers. The 260.19.29 driver didn't even let me log in.  We'll see what happens when I get the new board but I appreciate all the help!

---

### Post by DukeBoxer on 2011-02-15
Ok, so I got my new board, same as before, and still having problems. Last night I tried the new Debian 6 Live CD and I got it to boot (which is a miracle because most everything else wasn't) because I wanted to see if all the memory and CPU's showed up in the system monitor and they did but it soon crashed. Then I rebooted in failsafe and check the system monitor again and it only showed 1 CPU. It also didn't crash, but I didn't give it too much time because it was late. The other night I ran a memory test for almost 11 hours with all 8 gigs plugged in, it went through 8 times and there were no errors. I'm thinking one of 3 things...

1 - That there is a small problem with the CPU but windows isn't bothered by it (which installs flawlessly on the rig, blah!)

2 - The board and nVidia cards aren't jiving ( I have tried a GTX 460 and a GeForce 8800 and both times there have been problems)

3 - I have an SSD hooked up and that might be giving some sort of problem (although I highly doubt it)

I have tried to boot the computer with a live CD with basically bare bones, only 1 stick of RAM, no HDD at all, and both video cards (1 at a time) and there have still been problems. I have also read that you can install OS X on this board no problem and I have only been able to get it to boot to the installer 1 time (Always some sort of kernel panic) I just ordered a Gigabyte P55 UD3 board so we'll see if it might just be the board...I hope so

---

### Post by MiKOTRON on 2011-02-16
Is the RAM that you're using, on the qualified vendors list in the MB manual?  Do you have the BIOS set up properly?  Just checking.

---

### Post by DukeBoxer on 2011-02-17
I've tried a million different things in the BIOS. Can you give me some clues as to what I need to set some of the BIOS options to? I was going to send the CPU back but I can't imagine it's the problem. The memory is in the qualified vendors list, but not the 4gb sticks, which is actually weird because no 4gb sticks are even though it says it can support up to 16gbs. What kills me is the fact that I can get winblows on it no problem.

---

### Post by DukeBoxer on 2011-02-18
SOmething just dawned on me as I was thinking about all this, when I looked at the system profiler or whatever it's called under Winblows I saw that it said "Total installed memory = 8gb" "Total usable Memory = 4gb"...Could that be a sign that there is just too much memory installed? I'm going to see if I can get my hands on 2 x 2gb sticks and test that...

---

### Post by Stephann on 2011-02-18
According to specs, it looks like your memory is fine.  There've been mixed reviews on the motheboard itself, in terms of quality control (one reason I don't really use Asus anymore.)  I actually considered that exact board for my own media server.  For a media/file server, 4 gigs of RAM would even be overkill.

That said, if you can get OSX to install, that's the route I'd go for as a media server.  Flash just doesn't work that well on *nix yet, and it's impossible to get Netflix to stream on *nix machines.  That said, you might want to take a look at your AHCI settings (related to how your disk drives are accessed.)  Is it in IDE mode?  SATA?  Native?  This could be the reason your OSX kernel's panicking when trying to install, and could be throwing off your Ubuntu live systems.  If you have an IDE drive lying around, you could try installing Ubuntu to that first, and see how that goes.

Just a couple of thoughts; I feel your pain.  New system builds can leave one pulling their hair out.

---

### Post by DukeBoxer on 2011-02-18
Thanks for replying! Maybe thats why I'm losing my hair, ha! I did all the changes to the BIOS to get Mac OS X installed, changed IDE to AHCI, changed the resume to S3 only. The Kernel Panics are happening while the installer (Mac)/ Live CD (Linux) are booting up, not even on the installer/desktop yet. I'm taking the computer somewhere tonight to test 2 x 2gb sticks.

I just ordered and tried out a Gigabyte P55 UD3 board and I am getting the same problems, kernel panics, and with that board I can't even get to the Mac DVD after iBoot starts up so...What if I take my hard drives and install Ubuntu on them on a different computer and then put them back in there? There would still probably be lockups though. Oh well

---

### Post by Stephann on 2011-02-18
So, yes, that's another route to go; installing Ubuntu to the disk from another computer, then swapping it over.  I'd strongly suggest using the alternate installer, and 1) install just a minimal system, 2) swap the hard drive into the new build, then 3) running apt-get install ubuntu-desktop from the command line (which will give you your graphical environment, assuming that's what you want.)

I run my Ubuntu system on AHCI just fine, for what it's worth; just that I know there's no shortage of complications with the different setups.  Also, make sure you have your RAM speed set correctly at 1333 (it should be by default) and disable any overclock options you might have set.

You could also try a different live system, just to see if there's any fortune there.  Maverick's a little buggy for me; you could give Jaunty or Karmic a whirl and see if you have more luck, or even Knoppix or the live Gparted disk.  Something definitely sounds fishy here....

---

### Post by DukeBoxer on 2011-02-18
Ah good idea about the minimal install!! I'll write that down. I had everything set to IDE when I first started but after reading some more and trying Mac OS I saw that setting everything to AHCI was the way to go, funny thing is about that, Windows 7 wont even boot if thats activated. I don't overclock at all so that should be fine, although looking back I thought I had seen the RAM actually running at 800mhz.  Here's the list of LiveCD's I've tried...Ubuntu 10.04, 10.10, 11.04, Linux Mint 9, 10, Linux Mint Debian, Debian 6, Fedora 14, OpenSuSE...I think that's it. The only one's I have had luck with getting to a desktop was anything pure Debian, meaning Debian 6 and Mint Debian but then I got back to the freezing problems so...

The only 2 things left that could be causing the problems are that RAM in any order (like 1 4gb stick, the other 4gb stick or both together) or the CPU, I've either disconnected or switched out everything else.

---

### Post by Stephann on 2011-02-18
Quick thought comes to mind; is there a chance your DVD rom drive is bad?  Are you burning the discs and verifying they burned clean?

---

### Post by DukeBoxer on 2011-02-19
OK, I think I have it now, we'll see though. So what I did was install a  base system (great idea that never even crossed my mind by the way!!)  and then installed everything else. I did the install with only one  stick of memory in and luckily it was the good stick. Even though  memtest checked everything out to be ok one of the sticks was definitely  bad because now it wont even show up in the system monitor as there  being 8gb installed. Now i need to return this memory...

A few more things, I did the install, just in case, with the GeForce  8800 in the box instead of the GTX 460 but I just put that back in and  installed the restricted driver. We'll see if that will give me any  problems now. I want to upgrade it to 11.04 or at least the same kernel  as 11.04 because it has nouveau support for the GTX 460 which would be  nice (I think anyway)  I'll update if there are any more problems!

Thank you everyone for all your help!!

---

### Post by DukeBoxer on 2011-02-20
OK, one more thing because I was having problems with file systems not mounting and crashes and whatnot. My SSD was causing the problems. I'm not sure if it keeps loosing power or the connection or what but that was causing the crashes. It also might have been because I had / on the SSD but then /var /opt /tmp and /home on a regular HDD.  Who knows. Also the GeForce 8500 (it's not 8800) that uses nouveu works fine but if I put the 460 in and install the nVidia driver it freezes.

---

### Post by DukeBoxer on 2011-03-19
OK, so I had to send my board back again because the ethernet port died, so while I was waiting for the new one I did some reading and saw a lot of things being said about the nouveau drivers causing problems, so when I got my new board I installed a minimal of 10.10, then only after I left it on over night and then all next day to make sure nothing would freeze just in text mode I installed ubuntu-desktop but before restarting I made sure I purged the xserver-xorg-video-nouveau package, installed the nvidia-current package and also added the word "text" to /etc/default/grub where it says "splash quiet" so that if there was ever another problem freezing when it started up I could at least do some work in text mode to try to fix it. So I'll mark this solved and here is the solution...

GET RID OF NOUVEAU DRIVERS if you are having freezing/lockups, even if you aren't using them they are still causing the problems!!!! Sorry to the nouveau developers, you are doing a great job, but with a newer card and so many problems I have to point out that this is what was causing the problems.

---

### Post by DukeBoxer on 2011-04-04
Ok, so anyone looking through this, I did solve my problems, but not with 10.04 or 10.10. I tried both of them, plus Debian 6 and all of them gave me problems, freezes and lock ups. 10.10 worked for a while but whenever I tried to "push" the processor (ripping a Blu-Ray say) It would always freeze.

I installed 11.04 alpha 2 from the alternate cd with ACPI=off and everything has een up and running ZERO problems!! I still would like to take out ACPI=off from the grub menu, but for now life is beautiful. I was wishing for this because I didn't want to have to install windows so I'm happy!!!

---

