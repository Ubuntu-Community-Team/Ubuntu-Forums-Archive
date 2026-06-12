---
title: "AR5822 wireless crashes Belkin F6D6230-4 router"
date: 2012-07-29
forum: Hardware
---

### Post by adpads on 2012-07-29
Hi all!

I've got an Acer Aspire S3-391-53314G52add ultrabook here, booting in 13 seconds to kubuntu from its 20GB onboard SSD. Sweet linux machine for those interested!

Trouble is, the Atheros AR5B22 WLAN (b/g/n) keeps crashing my Belkin  	F6D6230-4 v1000 router (firmware v. 1.00.15). Admittedly, it's a pretty flaky router, but this problem seems to be unique to this combination of computer and router - and indeed to Ubuntu on this computer, as Windows works fine, and some other distros (e.g. OpenSuSE 12.2) don't support the wireless at all. 

The trouble occurs with both radios, in the 2.4 GHz and 5.2 GHz bands. After a slow connecting process (1-2 minutes) the connection works for 5-30 minutes, and then the router crashes and restarts, taking every connected user's internet with it.

All Belkin offers for this router is an unsupported beta firmware v. 1.00.19 that they tell people not to use. There isn't even a download of the original firmware, so if it is bad I won't have a way back. dd-wrt does not support this router.

Anyone familiar with this problem? Should I fix the wireless drivers or the router firmware?

---

### Post by ahallubuntu on 2012-07-29
I've personally had a few bad experiences with Belkin routers, to the point where I would never buy one.  The fact that yours is so poorly supported plus does not support DD-WRT are good reasons to get rid of it and get a router that isn't flaky.  Unfortunately, not all routers are created equal.  Some are just junk.

If you want another dual band router that can run DD-WRT (and Tomato), try the Linksys E3000.  It's an older router but good. (Also has a gigabit ethernet switch if that matters to you.)  Cisco (who makes Linksys) has been unloading refurbished versions of this router for about $50 USD via Newegg.com .  I have bought a couple of them for various projects - only a 90 day warranty but no problems so far.

---

### Post by adpads on 2012-07-30
Thank you! I couldn't agree with you more about the router. That Linksys E3000 looks like a pretty smooth operator, and if I can track one down in this country I think I'll surely take your advice!

Just one question from the linux side: Switching to Google Public DNS seems to have reduced the frequency of the crashes pretty drastically, to once every couple of hours. Why? What's it actually doing?

Thanks again for your quick help!

---

### Post by ahallubuntu on 2012-07-30
Typically, if you set your router's WAN to "obtain automatically," it will get not only its IP address but also its DNS servers from the internet provider.  So when you look up domain names (whenever you visit a web site, the name must be looked up in the DNS servers to obtain its IP address), you are using the internet provider's DNS.

If you use Google's DNS, then you're not using the internet provider's DNS any longer.

Why would that make your router more reliable?  Hard to know.  Google's DNS could be faster than the internet provider's DNS or something.  You're probably changing something that makes the router work less hard or something.

Did you change the DNS in the router or in your wireless configuration in the laptop?  You can also try changing the DNS in your router itself instead of just on your laptop and see if that makes any difference.

---

### Post by adpads on 2012-08-03
Thanks again for your help! I quickly found that the improvements I thought I saw with Google public DNS were illusory, so I took a risk and spent a wad of local currency on a new Linksys E3000 router.

I"m astonished at how much faster the entire home network feels - partly because negotiating the wifi link is a lot quicker, but DNS also feels a lot faster for some reason. The next step will be to actually connect a drive to it, and see if that works - the old Belkin used to routinely crash during read/writes and corrupt the entire file system on the connected drive.

Not a fix on the linux end, but I'll mark this thread solved in a couple of days if things stay this smooth. Thanks again!

---

### Post by adpads on 2012-08-04
I'm sorry to report that this problem is NOT solved. I'm having the same issue with the new router. So the culprit is definitely ubuntu.

Any suggestions?

---

### Post by adpads on 2012-08-13
Bump

---

### Post by ahallubuntu on 2012-08-13
Open a terminal and type

```
watch tail /var/log/daemon.log
```

and leave that open as you work...and try to see what happens just when you have crashed the router.

Also, what firmware are you running on your E3000?  I have two of them (I use them for various projects).  I recommend replacing the stock Cisco firmware.  One of my E3000's has DD-WRT, the other has Tomato.  Both are good, but I am more familiar with DD-WRT myself.  You can login with ssh and even look at what's happening there.  It is Linux, after all...

---

### Post by adpads on 2012-08-25
That command works fine on a debian machine that has no problems, but on the ubuntu machine in question, I get

```
tail: cannot open `/var/log/daemon.log' for reading: No such file or directory

```

---

### Post by adpads on 2012-09-17
Jut as an update on this case (maybe more of a soliloquy):

This computer became known as the "assassin," for its tendency to crash routers and kill people's work, once I started trying to use it out in the world in cafes and libraries. It was a danger to society. I tried a lot of different distros to find one that could drive all the hardware correctly. 

I suspect the problem may affect all of the debian-based distros. (Debian didn't boot at all in my only, cursory attempt, while I experienced problems similar to what I faced under Ubuntu with Linux Mint Debian Edition). Of the RPM distros, OpenSUSE did not drive the wifi card out of the box, and without an ethernet port on this computer I had no way to download the drivers.

I eventually settled on Mageia 2 out of necessity rather than choice. I have never liked the way wifi works in Mandriva/Mageia, but in this case it turned out to be my saviour. I can't say it was a pleasure getting Mageia to run properly on this computer - for example, KDM and GDM were both buggy, but in the end, with with autologin and policykit, it boots about 5 secondsa faster than ubuntu did; to make things not look ugly, I had to install gnome-shell and gnome-tweak-tool to configure decorations and themes, and then remove them, since they required networkmanager, which conflicts with the drakx-net-applet; a million other annoyances - but the end result is at least a machine that runs smoothly, even if I had to sacrifice my fast-booting mate and cinnamon desktops.

I still have ubuntu on a partition of the hard drive on this machine, and if a future update to the hardware drivers should fix the problem, I'll be glad to switch back.

For the record, this problem affected about two thirds of all the routers in the world this computer came in contact with, including, to my recollection, all household routers, and most public ones at cafes, airports, etc.

---

### Post by adpads on 2012-09-28
Update: I found a solution [here]("http://www.linlap.com/wiki/acer+aspire+s3"):

```
#echo "options ath9k nohwcrypt=1" > /etc/modprobe.d/ath9k.conf
```

So far it seems to be working. We'll see, but I'm hopeful...

---

### Post by adpads on 2012-09-29
Nope... I was happy for about an hour, but, though it stopped killing the router, the wifi connection still flatlines every 2-5 minutes. Even with the compat-wireless backports package installed from the repos, it's no better.

I guess this machine really wants to be a Mageia computer. Sometimes they are like children: we just have to respect what they were born to be.

Mageia sees the wireless card as: 

```
02:00.0 Network controller: Atheros Communications Inc. Device 0034 (rev 01)
```

and for some reason it screams along. The thing that surprises me is that it works at all, since it looks like everyone else seems to be having a hell of a time with this wireless card.

---

### Post by adpads on 2013-01-04
Hooray! Cautious joy for the assassin!

Discovered today that the wireless works apparently well with kernel 3.2.0-35-generic and the compat-wireless backports from the 3.6 kernel.
With a little tweaking under ubuntu, got power consumption at idle down from 10-11 watts under Mageia 2 (with my own frequency scaling since there was no support for sandy bridge) to 5-6 watts - sometimes below 5!

If true, this is wonderful news - at last the assassin is king of ultrabooks! Let all S3 owners rejoice!

---

