---
title: "Festival"
date: 2008-08-14
forum: General Help
---

### Post by jasex on 2008-08-14
Hi, wondering if there was a way to pipe festival output into an encoder, to get it into a recorded sound, like mp3, wav or something else... 

i.e. echo "Hello World" | festival -tts | (encoder here?)

---

### Post by Rhubarb on 2008-08-14
You may want to look at using espeak, it supports dumping a text file / text piped to it straight into a wav file, then from there you should be able to use a different app to convert that into an mp3.

You'll need espeak and lame to do this, so install them in synaptic if you haven't already done so.

```
espeak "hello" -w this.wav
lame this.wav
rm this.wav
```

This creates a wav file with the speech "hello".
It then converts it into an mp3.
Then it deletes the original wav file.

If you need more help doing this, let me know, and I'll investigate further for you.  (I like doing fun things with espeak).

---

### Post by jasex on 2008-08-14
Well... That just might work :D are the voices, crummy computer voices like in Festival, and do they speek letters phonetically?

I am trying to actually make sample sounds, so the wavs would probably work best, being uncompressed and all... I am going to try and make an entire song out of synthesized speech.

---

### Post by Rhubarb on 2008-08-15
espeak has a better voice engine than festival, as you can specify pitch, speed, accent, amplitude, and word gap with it.  -You're best off listening yourself if you think espeak is better / worse than festival.

The pitch of espeak's voice changes depending on the flow of the sentence it's reading, so it's a little easier to understand than festival.


For more information about espeak, type in:
```
man espeak
```
or
```
espeak -h
```


For a list of supported accents:
```
espeak --voices
```


Some examples of different accents:
```
espeak "hello this is a test"
espeak -v english-us "hello this is a test"
espeak -v en-scottish "hello this is a test"
espeak -v en-westindies "hello this is a test"
```


There's lots of things you can tweak for the voice, so experiment with it to find what's best.
Most songs use a vocoder to give that robotic voice effect, it's actually just a singer's voice modulated and mixed up with a tuned sine wave / guitar / instrument.

If you need some help with it, post back here ;)

---

