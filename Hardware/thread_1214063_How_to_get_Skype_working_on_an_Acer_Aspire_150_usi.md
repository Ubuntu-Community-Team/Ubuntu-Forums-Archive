---
title: "How to get Skype working on an Acer Aspire 150 using 9.04"
date: 2009-07-15
forum: Hardware
---

### Post by tomreid on 2009-07-15
Hi

I've been using Ubuntu fairly heavily for around two months now. 

The only thing I have never resolved is getting Skype to work on my Acer.

Sound output works fine, but input does not work. 

When I try the Gnome "sound recorder" app, I get no audio input too. 

The ACER is a dual boot with Win XP, Skype works fine on that, both input, output and video. 

I have done all the obvious, like ensuring the microphone is not muted in the volume control. 

I've also done extensive googling and found no real solutions. 

I have found that the sound settings and various apps that control the sound in 9.04 seem very complex, it seems a bit of a mess to be frank. 

The closest I have ever got to an answer is here: [http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)* "If you are using skype or wine then installing the lib32asound2-plugins will remove them and installing wine or skype will remove the lib32asound2-plugins. I don't use either skype or wine so I was unaware of this issue, sorry. You can still install lib32asound2 but not the lib32asound2-plugins. Other applications that depend on the lib32asound2-plugins may not work after you do this so be aware of that. Hopefully this will be fixed soon."*

I am now considering the option of taking the Ubuntu installation back a version and installing 8.10, but this is a big job and I don't want do do this if there is a fix, so before I do, I wanted to see if there are other people out there that had this issue in 9.04 and what their solitions were. 

I also want to check that if people know that the audio input will work in 8.10.

Thanks

Tom.

---

### Post by tomreid on 2009-07-16
Hi

I didn't get any replies to this, but in case anyone else has the same issue, here is (mostly) the answer:

[http://ubuntuforums.org/showthread.php?p=7628196#post7628196](http://ubuntuforums.org/showthread.php?p=7628196#post7628196)

There is a problem with the ACER in that Ubuntu is not recognizing it's internal mic. 

The work around is to use an external mic in it's line in and it works fine.

I'm going to keep looking for an answer. I'm sure, as the acer is a reasonably new piece of hardware, that a solution will come soon.

cheers

---

