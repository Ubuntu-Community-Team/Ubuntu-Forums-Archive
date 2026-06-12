---
title: "Acer Aspire One AO532H Ubuntu Support"
date: 2010-05-26
forum: Hardware
---

### Post by LKNT on 2010-05-26
Hi everyone,

I am about to buy an Acer Aspire One AO532H netbook and I wanted to know if there are any incompatibility issues with Ubuntu. I need to buy it rather quickly so I would need to know soon.

Thanks a lot.

---

### Post by cprofitt on 2010-07-11
I am looking for information regarding this as well -- anyone know.

---

### Post by nbaes on 2010-07-11
I have an Acer Aspire One AO532h - as a matter of fact, I'm typing this reply on it right now. It's a great little netbook, and it runs Ubuntu Netbook Remix 10.04 with no problems that I have noted. I'm using a wireless internet connection and have no issues, the display works great, the sound is fine, and for such a small computer, it feels really responsive under Ubuntu (I can't say the same for Windows 7 Starter, which is what the computer was loaded with when I first got it - it was really terrible, so I wiped the whole hard drive and am only using Ubuntu). 

Two caveats, though: first, the media card reader is not recognized by Ubuntu, at least not out of the box. Also, although everything is working fine, I do have an issue where the computer will suddenly sometimes say that there is no battery life remaining, and that it has to suspend. It will do this even with a full, freshly-charged battery. However, I just wait a couple seconds and press a key on the keyboard to wake it up, and then I can continue working as normal without the problem recurring. Search around the forums for more reports of this issue on this particular netbook; I'm not sure what causes it, and I'm not convinced that it is bothersome enough for me to try and dig around in the system to fix it.

Overall, it's a great fit for Ubuntu, so go ahead and get one! :)

---

### Post by ubugrrl on 2010-07-13
Like nbaes, I'm also using an Acer Aspire One 532h. I wiped out win7 starter too .... uggg! I have the same issue with the battery indicator. I'll suddenly get a message that the battery is critically low and the computer is about to hibernate, which it does. I then reboot and all is fine again.

I also notice that the battery indicator seems to go down really fast. I can be fully charged and within a few hours down to nothing. When I still had win7 on it, it would indicate I had 8 hours (or more) of battery life. Not sure if that was wishful thinking on the part of windows or if my battery is now being sucked on more...

But other than this, Ubuntu is working great!! I would recommend it.

---

### Post by ubugrrl on 2010-07-13
found this other thread about the acer aspire one battery issue:[ http://ubuntuforums.org/showthread.php?t=1487918]("http://ubuntuforums.org/showthread.php?t=1487918")

---

### Post by avacado on 2010-10-14
Google "ubuntu netbook compatibility" there is a community contributed wiki

there is no driver for a card reader common to the many aspire one variants.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633852](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633852)

this may be a minor annoyance, you could use a camera as external card drive or buy a card reader. but if an sd memstick card reader is important this may not be the rig for you.
I also had trouble with skype which works fine in windows on the same netbook (Skpes fault not ubuntus).

better still, take a usb with netbook edition loaded to the shop and try it out and put your rport on the wiki

---

### Post by ynaught on 2010-12-01
The battery issue is cleared up with a BIOS upgrade.

The Skype issue is fixable, but it's a bit of work.

I've been using an external adapter when I need to read my SD card.  Better than rebooting to W7!

My wireless does occasionally drop and reconnect, but I have no idea whether that's related to hardware, software, or physics.

---

### Post by crucialhoax on 2010-12-14
The acer ao532h is a wonderful laptop. I have to say that I am very impressed with how much this little guy can do. Linux has supported almost everything ootb except for the card reader and bluetooth. The card reader however is an easy fix because of USB card readers. My wireless has never dropped once, the webcam is decent, and battery life is amazing.

The wireless needs to have a kernel module or something to be installed and that fixes a abnormally low signal when obviously close to the wireless.

There was a bug where the bios needed to be updated otherwise as stated previously the laptop would think the battery was dead and suspend. BIOS update to 1.25 and never look back. If you already wiped W7 then just download the `Upgrade` and when installing it choose `Custom` not `Upgrade` uncheck the Validate my windows install once I am online box and dont type in a key. This will allow you to install your BIOS update without having to purchase W7 again. Took me about an hour to do it. I used quite a few tools.

^^^ Read my thread here: [http://ubuntuforums.org/showthread.php?t=1633142&page=2](http://ubuntuforums.org/showthread.php?t=1633142&page=2)

If you have questions lmk.


Overall, this thing is a beast!

---

### Post by kregester on 2011-01-07
532h is a very nice netbook at a very nice price. 
I am running 10.10 desktop not the netbook version with Avant Window Manager, dual boot with Win7 and have Win7 in VirtualBox if needed. I need dual boot for work but Win7 in VirtualBox runs as almost fast as it does native (not great) but the 532h flies with Meercat.  I changed RAM to 2 Gig and swapped HD for 64 Gig SSD.  The RAM and SSD make it very fast and usable and the SSD helps battery life. Updated BIOS and now battery warnings are gone. SD card reader missing problem will be fixed in 11.04 or if I decide to update the kernal. Skype works well once you set audio to use microphone left channel only. 
I liked mine so much, I picked up a second re-manufactured for my niece for under $200 US.. Now we can run Video Skype hooking the 532h up to our big screen TV.
The cooling fan seldom turns on and the SSD draws so little power it never gets very warm.

2 suggestions
Swap RAM out for 2 Gig
Install an SSD harddrive (they are getting cheap) and get a USB case to use the one that came with the 532h as a backup drive.

---

### Post by islandBilly on 2011-01-07
I too am dual booting mine with its original Win7, but I never go there any more - might have to wipe it and get the space back.:) Anyway, I started with 10.04 live on usb, which worked great right out of the box, except for the SD reader and the battery life thing. Rather than the other fixes, I upgraded to 10.10, and that seems to have fixed the power managment. I never had a prob with Skype, but still cannot get the sd reader recognized at all. Oh well. My fiancee has had wireless connectivity probs using the 10.04 live usb on her Toshiba laptop, so there may be something there. It even happened when we were 3 feet from the router, and not when she booted into (shudder!) Vista.

Under 10.10, I recommend using the "user-defined session" rather than netbook remix (I hated that Unity thing) or netbook-2D, which didn't have its min/max/close buttons working. It's really clean and fast.

---

### Post by hansolo4949 on 2011-01-07
I'm using Ubuntu under a Acer 5738z, and it does work well with it. No problems right out of the box, and it dual boots with windows 7 perfectly, and if I need a file from windows, I can just browse throught the c drive. I think Acer does a very good job manufacturing and designing (hardware wise, and aesthetically wise) their computers.


hansolo4949

---

### Post by gokhart on 2011-02-08
Hi,

I recently wiped my AO532h and installed 10.10 netbook edition.  I used "UNetbootin" to create the USB stick and I have bios version 1.25 which does away with some of the other problems I have read about.

With this there are reported issues with the microphone and SD card reader.  The most common solutions are:
1) [http://ubuntuforums.org/showthread.php?p=10379006](http://ubuntuforums.org/showthread.php?p=10379006) to get the microphone working with skype etc.
2) [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530277](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530277) see post #86 for updating the kernel which resolves the SD card issue.

So far everything seems fine for me.

---

### Post by funfrank on 2011-03-10
Mic works out of the box for me.  Just needed to un-mute it.

The Fn + F2 hotkey for shutting of the wifi does not work.  

I am able to turn it off with

echo 0 > /sys/class/rfkill/rfkill0/state

when logged in as root.

I would like to write a script that runs when I press Fn + F2.  

Question 1:  how do I find out the event code for Fn +F2?

Question 2: how do I write a script that can run as root w/o password?

Thanks,


Frank

---

