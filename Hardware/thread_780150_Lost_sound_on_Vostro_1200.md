---
title: "Lost sound on Vostro 1200"
date: 2008-05-03
forum: Hardware
---

### Post by Jfrench on 2008-05-03
Hello there, upgraded to Hardy when it was released, decided to install 64bit version, everything worked flawlessly on my Vostro 1200 laptop. When I installed the sound worked along with everything else, but the sound has seemed to have stopped working completely,  I can't figure out why.

It is a HDA Intel Chip. Please post if you have any ideas.

---

### Post by locky28 on 2008-05-04
Same here on my Inspiron 1420, just stopped working. 

It was kind of after I let totem install a codec to play an mp4 file so I'll try and get rid of that codec and see how i go.

---

### Post by Jfrench on 2008-05-04
Let me know how that goes, I don't recall if the sound stopped working after I installed a codec. I might have not noticed until some time after.

---

### Post by locky28 on 2008-05-05
Couldn't find the codec I installed :(

---

### Post by Jfrench on 2008-05-05
I have fixed my audio.
All I did was 

Into the terminal type, the following to see if your sound card is detected.

```
find /lib/modules/`uname -r` | grep snd
```

If you didn't see your sound card displayed try the following.

```
sudo aptitude install linux-ubuntu-modules-`uname -r`
```

You may need to restart, I didn't tho :P.

I didn't try this to being with because I thought it was a different issue since it was working to begin with

[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

This was very helpful.

---

### Post by locky28 on 2008-05-06
Well I ended up reinstalling as it was a fresh build of 8.04 anyway and no luck. I tried your suggestion jfrench and still no result.

The thing I just noticed though, is when I dual boot into XP theres no sound in that either.

Now on the weekend I went to a LAN and was gaming all day from my XP partition with some Zalman 5.1ch headphones set up for surround sound plugged into the 3 ports on the front of my lappy. Now whenever I set the XP settings back to laptop speakers then restart it's always set on 5.1ch when I check the settings again in XP :S

Any ideas? I've had a look on google but I'm not really sure what to search for.

I'm running 32 bit 8.04 btw.

---

### Post by locky28 on 2008-05-08
Ended up being a shorted out headphone port. Fixed it by just plugging in and unplugging my headphones real quick in each port.

---

