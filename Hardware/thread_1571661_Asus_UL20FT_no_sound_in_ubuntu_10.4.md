---
title: "Asus UL20FT no sound in ubuntu 10.4"
date: 2010-09-09
forum: Hardware
---

### Post by gohkm on 2010-09-09
I'm new to Ubuntu environment, Just try to use Ubuntu and realised there is no sound coming out from laptop.Tried playing mp3 files and do sound testing also no sounds. Any solution??

---

### Post by R4kk00n on 2010-09-10
I'm getting sound out of the speakers, but no sound from headphone jack. Didn't look at whether it's muted.

Well, it's on 100%.

---

### Post by gohkm on 2010-09-10
even I put the volume to 100%, no sound at all coming out from the speaker and the headphone jack.

---

### Post by jimsturdevant on 2010-09-11
I had the same issue on my Asus UL20FT.
First I upgraded alsa to 1.0.23 which did not fix the problem, then I found the following:

From:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/580338](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/580338)


["David Henningsson]("https://launchpad.net/%7Ediwic")             wrote             on 2010-08-02:                                                                        
                       I believe this issue is about to be fixed. Can you please try installing [http://people.canonical.com/~diwic/temp/alsa-intel-hda-optiplex-dkms_1.0.23_all.deb]("http://people.canonical.com/%7Ediwic/temp/alsa-intel-hda-optiplex-dkms_1.0.23_all.deb") , reboot and report back whether it fixes your problem?"

Installed the deb and the headphones work perfectly now.
Good luck!

---

### Post by R4kk00n on 2010-10-22
OK, still got no sound coming out of the headphones even on maverick.
Though now I've got three possible analogue outputs: "speakers", "headphones" and something called "output". Only "speakers" work.

I guess I'll have to file a bug then

---

### Post by jackharvest on 2011-05-16
Yeah, yeah, the topic is 6 months old now, but I have the exact same problem, and the problem was NOT solved in Ubuntu Natty 11.04

Is there anyone who can help solve this mystery? The sound comes out of the speakers just fine. It's just the headphones that don't produce any sound. :\

---

### Post by sk8brding on 2012-02-27
Everything was working on my UL20FT "out of the box" with 10.04.3 LTS. Sound and Mic thru the built in and thru the jacks.
I am using persistent USB. In fact I gave up on all later versions and still use Lucid. Best by far for me.
HDMI has no sound out tho. Need to feed with a cable from the headphones to the TV (Win7 works as it should).
11.04 & 11.10 required some tinkering to get the Mic working.
[http://ubuntuforums.org/showthread.php?t=1849814&highlight=UL20FT](http://ubuntuforums.org/showthread.php?t=1849814&highlight=UL20FT)

---

