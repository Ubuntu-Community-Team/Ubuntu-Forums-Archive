---
title: "UNR Review - new user"
date: 2010-02-05
forum: Hardware
---

### Post by lparsons21 on 2010-02-05
I recently acquired a Gateway 2104u Netbook with Windows 7 on it.  I 
wanted to play around a bit with it by loading Linux on it.  I hadn't 
actually done anything with Linux since Caldera came out to give you a 
timeframe.

Ubuntu Network Remix (UNR) is a Linux distribution optimized to some 
extent for the netbook environment.  It is designed to be easy and 
simple to install and to look and work well on netbooks.  It is very 
successful based on my narrow experience.

Installation : 
UNR is supposed to be loadable on a flash stick and installable or 
runable from it.  I never could get this netbook to boot from it.  I 
tend to think it is something in this particular netbook because other 
reports are that it works fine.

So I created a DVD from the downloaded iso.  Booted into it and tested 
it running from the DVD.  Everything seemed to work well enough to want 
to do the install.

So I started the install from the DVD.  All went smoothly, and the 
default partitioning scheme is to split the drive nearly in half so that 
you can switch between UNR and some other OS, in this case W7.  Install 
took 10-15 minutes, start to finish and when it booted things were 
mostly good.

It didn't automatically use the wireless NIC in this netbook, so I had 
to do a simple configuration in Network Connections.  Enter the SSID of 
the network, specify security type, and give the passphrase.  Then it 
worked fine.  So I think it saw it, just didn't set it up automatically.

As an aside, I did later fiddle around and reinstall UNR, and the second 
time it did pick up the wireless and made the setup slightly simpler, 
mostly because it prompted for it.

All else worked fine.  Wired NIC, sound, video, touchpad, keyboard.  No 
glitches.

One other thing that was nice, was appearance.  Much easier on the eyes that using W7, no squinting or reading glasses needed for these old eyes on the 10" widescreen.

Performance:

Superb!  I had expected that it would be better than W7 in the uses I 
had for it, and it is, but only slightly.  Snappy and responsive are 
good words to describe the performance under either OS.  I was a bit 
surprised at that as I expected that a 1.6Ghz Atom wouldn't perform well.

Random thoughts:

I use a netbook for ebook reading and watching Hulu at home, in bed.  
With UNR, the Hulu experience is very good, better than under windows.  
But the ebook reading is poorer by far.  I got the FBReader program and 
it works fine with my pdb files, but it is just not a very good ebook 
reader, imo.  Which seems strange as some of the dedicated ebook 
hardware is running Linux, you'd think there were better ebook readers 
available.  But it isn't the case.

Yes, I know, I could read with Adobe or the browser, but neither of 
those are as slick as eReaderPro which is available for OSX, Windows and 
the iPhone/iPod Touch.

When on a trip, the netbook would fill in to do email, web surfing, 
usenet, ebooks and some video.  UNR can fill all those quite well, with 
the exception of the ebook reading.

In all this, I actually attempted to take the netbook back to w7 only.  
But the recovery DVDs don't repartition, so things just didn't work 
well.  To the point that it would start grub then reboot over and over 
again.

So I opted to reinstall UNR.  On the second install, I had to do the 
partitioning manually because the default wanted to split the HD up even 
more which wasn't what I wanted.

Overall:

UNR is a good choice as only or second OS on a Netbook based on my 
limited experience with it.  The only hole for me is the ebook reading 
and that is just a missing good Linux app for it.

Otherwise, everything else works as expected.  Install is very easy for 
someone with some knowledge of installing an OS from scratch.  I 
wouldn't want to give a DVD to my mom (she's 89) to install, but then I 
wouldn't give her a W7 DVD to install either.

Lloyd

---

### Post by bama7474 on 2010-02-05
I started out the same way you did...I purchased my Toshiba NB305 four days ago and started out partitioning my HD in half with UNR to try out the new Linux OS...Thank god I really loved UNR because I attempted to start up win7 after rebooting and the partition had somehow messed up the bootconf for win7...So I went back and completely installed UNR to the HD...I was pleased to find out that almost everything worked, per se out of the box.  Display is crisp and easy to read with the larger icons (which are reported to be in the future compatible with touch screen mini's in the future)  I did find out that the suspend and hib modes are not supported which is a bummer, I purchased this mini because it was designed for portability, now I have to either leave everything running or shut down when I go from point A to point B.  Hopefully in future updates this function will be compatible.  Wireless connection is a little weak, other laptops in my house read excellent signal strength through out the house, while my Toshiba displays half the strength.  So far I've not dropped my connection.  Overall, UNR is very well built and easy to use.:P

---

### Post by NB305 on 2010-02-05
I have to agree that UNR is very nice to use compared to Win 7 starter. Even with the problems I am having with it (sleep/hibernate/brightness/external monitor), I find myself keep on going back to UNR.

---

### Post by lparsons21 on 2010-02-05
On mine, the sleep seems to be working fine.  And yes, the wireless is weak under UNR and that is a PITA.  But I'm primarily an Apple user and this gives me an excuse to get another Airport Extreme to put in the room I do most of my updates and such in.  Strangely, when surfing the web and other internet things, the wireless strength is weak, but it isn't an issue.

Only under software update do I get a real problem.

---

### Post by lparsons21 on 2010-02-05
> **bama7474 said:**
> I started out the same way you did...I purchased my Toshiba NB305 four days ago and started out partitioning my HD in half with UNR to try out the new Linux OS...Thank god I really loved UNR because I attempted to start up win7 after rebooting and the partition had somehow messed up the bootconf for win7...So I went back and completely installed UNR to the HD...I was pleased to find out that almost everything worked, per se out of the box.  Display is crisp and easy to read with the larger icons (which are reported to be in the future compatible with touch screen mini's in the future)  I did find out that the suspend and hib modes are not supported which is a bummer, I purchased this mini because it was designed for portability, now I have to either leave everything running or shut down when I go from point A to point B.  Hopefully in future updates this function will be compatible.  Wireless connection is a little weak, other laptops in my house read excellent signal strength through out the house, while my Toshiba displays half the strength.  So far I've not dropped my connection.  Overall, UNR is very well built and easy to use.:P

Dual booting worked fine on mine, grub replaced the mbr that windows uses for boot.  I later decided to do it all over again (hey, I'm retired time is all I have!) and found that getting an MBR back in place so it would only boot windows was not for the faint of heart with this machine, the way Gateway did the recovery thing.

---

### Post by Merlinson on 2010-02-08
I had the same symptoms of weak wireless signal while a dual boot in windows7 showed a strong signal.  I was also getting periodic disconnects that required reboots to reconnect.  I have an aspire one, but googling suggests this works for a variety of netbooks.  

```

sudo apt-get install linux-backports-modules-karmic
sudo apt-get install linux-backports-modules-wireless-karmic-generic

```

---

### Post by lparsons21 on 2010-02-10
Thanks for the suggestion.  Worked out fine.  I went from a best signal strength of 25-30% to a best of around 60% in the same location.  Really appreciated.

Now if I could just get Netflix working under Linux, I could shift completely over...

---

### Post by secondtenorblade on 2010-02-10
I bought an acer netbook to amuse myself while on my occasional travels, ebooks, facebook, music player, webmails and the like. I already had a an earlier version of UBUNTU on a CD and loaded this on susequently ubdating to the latest version.
 
I find the full version does everything I need sofar - have yet to try ebooks - so I left wondering why have a netbook version when the full blown version seems to work fine. Am I missing something.

---

### Post by lparsons21 on 2010-02-10
> **secondtenorblade said:**
> 
I find the full version does everything I need sofar - have yet to try ebooks - so I left wondering why have a netbook version when the full blown version seems to work fine. Am I missing something.

I looked at the full version and it was fine, but the UNR has a very different desktop that is very readable and useable on the smallish 10" screens on these netbooks.  Download the iso and make a boot stick or DVD and take a look at it live.

BTW, for ebooks, I never found what I considered a good ebook reader.  So I installed wine and got eReaderPro for Windows.  Works very good and looks good too.

---

### Post by dot dot on 2010-02-12
.

---

### Post by dot dot on 2010-02-12
I have an LT21 also. I've burned my iso copy of remix to a disc however I haven't installed it yet because I want to make recovery discs for factory specs. Any tricks I should know about before I install? Where would I go about pasting the following code for the wireless?

 ```

sudo apt-get install linux-backports-modules-karmic
sudo apt-get install linux-backports-modules-wireless-karmic-generic

```

---

### Post by lparsons21 on 2010-02-13
> **dot dot said:**
> I have an LT21 also. I've burned my iso copy of remix to a disc however I haven't installed it yet because I want to make recovery discs for factory specs. Any tricks I should know about before I install? Where would I go about pasting the following code for the wireless?

 ```

sudo apt-get install linux-backports-modules-karmic
sudo apt-get install linux-backports-modules-wireless-karmic-generic

```

You want to do the Gateway recovery disk creation AND the MS recovery also.  As well as the Windows system repair disk.  That way you are fully covered and can recreate the whole thing as W7 if needed.

As to the code.  Just open a terminal window and paste them in one at a time.

---

### Post by dot dot on 2010-02-13
Dual booting is working fine on mine, however when I'm on Ubuntu I keep getting crash notifications. It seems like they occur when my internet goes down

When I enter the code in the terminal it asks for my sudo password.. Whats that?

---

### Post by lparsons21 on 2010-02-13
It is the same as your user password usually for a new UNR install.

The recovery stuff is really only needed IF you crash the whole darn thing for the most part.  But if you later want to go back to the factory config, the Gateway restore crap won't set the boot record right, IOW, grub will still be there and it won't boot up in an OS if the Linux partition is gone.

---

