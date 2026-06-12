---
title: "Should LPIA version be used for Atom-based netbooks?"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by bbzzdd on 2009-02-06
I have noticed that there is a LPIA Alternate install CD available.  Many people are using the standard Ubuntu Desktop CD for their netbooks which is optimized for x86 processors.  Should the LPIA version be used instead as it should be optimized for the Atom processor?   Nobody has given me a definitive answer on this on other forums.

---

### Post by bbzzdd on 2009-02-06
I am surprised.  Nobody has an idea?

---

### Post by entropic_existence on 2009-02-07
There are a few threads on the forums about installing 8.10 lpia. Apparently there are some issues and it takes a lot of tweaking during the install process. One thing I'm noticing right now is that the ports repositories (where the lpia architecture is) is REALLY slow. Everything is downloading for me right now at an average of about 13 kbps. Estimating 7 hours to download and install the ubuntu-desktop package.

---

### Post by andrewsimpson on 2009-02-08
The LPIA 8.10 version is good, but the installer is currently broken.

Workarounds are shown [http://ubuntuforums.org/showthread.php?t=1002878]("http://ubuntuforums.org/showthread.php?t=1002878") here.

Advantages of the LPIA version for me have been slightly faster bootup and perhaps longer battery life.  It does feel a bit experimental, but I think that will improve with Jaunty.

Others have good experiences with Ubuntu Netbook Remix (which is LPIA), though this installs with a ext3 filesystem which is very slow with slow-ish SSD units.  It is best converted back to ext2 for SSD drives.

---

### Post by lesbaker on 2009-03-16
I notice for the jaunty downloads that there is the UNR file and then there is the MID file. The UBN is not LPIA but the regular i386 or what not but the MID file is LPIA but for MID devices not netbooks. So what do we people with atom chips use? Or is there one that UNR LPIA?

---

### Post by andrewsimpson on 2009-03-17
> **lesbaker said:**
> I notice for the jaunty downloads that there is the UNR file and then there is the MID file. The UNR is not LPIA but the regular i386 or what not but the MID file is LPIA but for MID devices not netbooks. 

Yes, I tried the UNR (Intrepid) on Acer Aspire One, though I can't actually remember whether it was lpia or i386 based.  The MID version is not so suitable.

A lot of people have been very happy with the UNR (see the aspireoneuser.com forums particularly under Linux / Ubuntu).

I've carried on using the Xubuntu lpia (Intrepid) version and have been very happy with it.  I'll upgrade to Jaunty when the time is right.

Be warned the Intrepid installer has a nasty bug with lpia. See my post above.

---

### Post by spoulsen on 2009-03-19
When you use Intrepid-LPIA, how do you get a working video driver.  The VESA driver it defaults to seems quite slow.

We have spent much time getting the video driver from Gutsy converted to Intrepid.  It is painful since both libdrm and xorg have undergone substantial changes.

---

### Post by andrewsimpson on 2009-03-20
> **spoulsen said:**
> When you use Intrepid-LPIA, how do you get a working video driver.  The VESA driver it defaults to seems quite slow.

We have spent much time getting the video driver from Gutsy converted to Intrepid.  It is painful since both libdrm and xorg have undergone substantial changes.

Oh, I don't know. It just worked for me. :o

Just checked:  Xorg reports that it's using the Intel video driver.  I also have an empty Xorg.conf file.  I understand that Xorg now probes the hardware on startup and creates it's own configuration automagically.

I am using an Acer Aspire One.

---

### Post by jdmpike on 2009-04-15
Has anyone revisited this idea since the Jaunty beta has been released? I am very interested in the lpia optimizations for Atom based processors. I dual boot my Acer Aspire One with Windows XP and notice 6.5 or so hours of battery life there vs. 4.5 or so in Ubuntu 9.04 Netbook Remix.

I have thought about trying to switch architectures post installation, but I am not sure how to do this. Any ideas how to do this? Does it really matter?

---

### Post by andrewsimpson on 2009-04-17
> **jdmpike said:**
> Has anyone revisited this idea since the Jaunty beta has been released? I am very interested in the lpia optimizations for Atom based processors. I dual boot my Acer Aspire One with Windows XP and notice 6.5 or so hours of battery life there vs. 4.5 or so in Ubuntu 9.04 Netbook Remix.

I have thought about trying to switch architectures post installation, but I am not sure how to do this. Any ideas how to do this? Does it really matter?

Yes, I upgraded last night from 8.10 lpia to the current 9.04 lpia with Network Manager.  No problems, apart from a slow download.

Wifi wouldn't work, but reading the workaround in Bug Report #350352 fixed that.

I am using the 3-cell / 8Gb SSD version of the Aspire One.  I guess you are using the 5-cell battery?  Powertop tells me that I am getting just over 3 hour battery life and running at about 8.0 - 8.2 Watts.  Your 4.5 hours does not sound so good.

To improve battery life you need to read all the advice and apply the tweaks in the help.ubuntu Aspire One pages.  Plus you need to install 'powertop' and let it run for a while.  It will tell you where the power is going.  One of my main culprits was the webcam not being in powersave mode (i.e. it was on all the time).

---

### Post by snowpine on 2009-04-17
I am experimenting with the 9.04 lpia alternate install on my Dell Mini 9. It feels a teensy bit glitchy (perhaps because it is still beta) but it does seem to get about 5-10 minutes extra battery life compared to 9.04 i386. Startup is not any faster. Wireless did not work out of the box like it does with i386, but I solved that by installing linux-restricted-modules.

I plan to play with it for another day or so before I make a final decision whether or not to keep it or switch back. So far I do not see any big advantage over i386.

---

### Post by AK Dave on 2009-04-23
Does the 9.04 lpia include aircraft-manager?

---

### Post by snowpine on 2009-04-23
> **AK Dave said:**
> Does the 9.04 lpia include aircraft-manager?

I just checked for you, and aircraft-manager is not in the 9.04 lpia repository.

---

### Post by snowpine on 2009-04-23
Here is another question for y'all. I installed 9.04 lpia onto a usb stick so I could test it on both of my netbooks without doing a full install. I accidentally booted it on my pentium 4 desktop. If lpia is specially designed for the Atom, why does it run okay on non-Atom computers? I am starting to think the i386 vs lpia debate is irrelevant...

---

### Post by adaemox on 2009-09-19
> **snowpine said:**
> Here is another question for y'all. I installed 9.04 lpia onto a usb stick so I could test it on both of my netbooks without doing a full install. I accidentally booted it on my pentium 4 desktop. If lpia is specially designed for the Atom, why does it run okay on non-Atom computers? I am starting to think the i386 vs lpia debate is irrelevant...

I'm also curious about this. I'm getting a laptop with an AMD 64bit Turion processor. I ran an Ubuntu LPIA within a 64bit virtual environment in virtual box to see if it was even feasible and it worked.

I really only care about this for battery life, would this increase battery life compared to x64 or x86?

---

