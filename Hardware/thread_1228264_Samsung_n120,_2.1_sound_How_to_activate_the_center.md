---
title: "Samsung n120, 2.1 sound How to activate the center speaker"
date: 2009-07-31
forum: Hardware
---

### Post by kat_ams on 2009-07-31
I bought a Samsung n120 netbook and was curious about the 2.1 channel sound. Out of the box with Ubuntu Netbook Remix the 3rd speaker (which is the screen itself) does not function. With the addition of an alsa ~/.asoundrc file to my home directory everything works now like a dream and my Samsung n120 sounds great!

So the steps to get your 3rd speaker working are as follows
[LIST=1]
[*]in alsamixer set the front setting to full volume
[*]create an .asoundrc file as follows (I've put in extra comments to make it easy to follow
[*]put the .asoundrc file in your home directory
[/LIST]

1st and explaination of the code piece by piece

# give your setting a name I choose two point one
**pcm.twopointone {**

# tell alsa what we want to do... route the sound
      **type route**

# copy the default surround 4.1 setting
      **slave.pcm surround41**

#tell alsa how many channels to use 2.1 is 3
      **slave.channels 3**

#play the sound for the Front Left .0 to play through the Front Left speaker .0 at full volume 1 
      **ttable.0.0 1**

#play the sound for the Front Right .1 to play through the Front Right Speaker .1 at full volume 1 
      **ttable.1.1 1**

#play the sound for Front Left .0 to play through the center speaker .4 at half volume 0.5
      **ttable.0.4 0.5**

#play the sound for the Front Right speaker .1 through the center speaker .4 at half volume 0.5
      **ttable.1.4 0.5**

# you can choose to comment the above two lines and uncomment the next line which will give you
#play the subwoofer sound LFE .5 through the center speaker .4 at full volume 1
**##     ttable.5.4 1**
**}**

and now for the code to copy and paste into your own ~/.asoundrc file.
Most people will not have an ~/.asoundrc file you will have to create an empty file and insert the following code

```

#alsa config for the Samsung n120 2.1 speakers
pcm.twopointone {
   type route
   slave.pcm surround41
   slave.channels 3
   ttable.0.0 1
   ttable.1.1 1
   ttable.0.4 0.5
   ttable.1.4 0.5
# uncomment next line to route LFE.5 to center.4
##     ttable.5.4 1
}
```

---

### Post by muximus on 2009-12-13
hey.. i just bought the same.. n u r mistaken about the 3rd speaker.. it is on the bottom near the touchpad, to the left... it works in windows, but i have not had any success in making it honk in ubuntu.. think u can help me out?

---

