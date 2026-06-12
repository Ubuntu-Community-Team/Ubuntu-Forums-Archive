---
title: "Stereo ouput through single speaker"
date: 2011-12-05
forum: Hardware
---

### Post by Sylos on 2011-12-05
Hello. 

I have a laptop with a rather poor little single speaker output. After installing ubunut it appears that only one channel of a standard stereo track (youtube etc) is being output.

I had a little google around and saw mention of using an asoundrc file to tell alsa to mix the two but it hasnt worked.

Pulse doesnt offer any option for switching to mono output.

Does anyone know of a way to set pulse to output both sides through the mono?

Thanks

---

### Post by Sylos on 2011-12-05
UPDATE:

Fiddling has broken sound completely. When I try to bring up the sound prefs I get "Waiting for sound system to respond".

Reinstallation of all the pulse components and force-reload alsa has no effect. Annoying.

---

### Post by Sylos on 2011-12-06
Thinking about this problem I wonder if it may be possible to limit the number of channels that alsa can have be putting a line in the asoundrc file.

I saw this on a website for limiting it to 2 channels:

```
pcm.plug1s {
  type plug
  slave {
    pcm "hw:1,0"
    channels 2
  }
}

```

I wonder if I cahnge it to:

```
pcm.plug1s {
  type plug
  slave {
    pcm "hw:1,0"
    channels 1
  }
}

```

That would force the left and right output to be pumped through the same channel adn thus give me the full sound from my single speaker.

Not quite sure how to do this and get all of the device names right. I also wonder how I successfully add this as a preset option in the sound prefs menu.

Any insights gratefully recieved.

---

### Post by Sylos on 2011-12-07
Well trying the above didnt work (I probabbly havent written it correctly).

I have had some success with following this post:

[http://ubuntuforums.org/showthread.php?p=11519793#post11519793](http://ubuntuforums.org/showthread.php?p=11519793#post11519793)

but whilst both channels are now played it is accompanied by AWFUL crackling and popping. I tried fiddling with the alsamixer settings to see if that helped but no effect.

Any ideas..... please?

---

### Post by LinuxFan999 on 2011-12-07
Did you try using external speakers?

---

### Post by Sylos on 2011-12-07
Cheers for the reply

External speakers arent really an option here. The laptop is a present for my girlfriend and she wants the mobility of the laptop. Anything that impairs that (such as having to carry and set up external speakers) will somewhat ruin it for her.

Headphone output also works fine but Im trying to make it so she can use the laptop and all of the features.

Any other suggestions?

---

