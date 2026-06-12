---
title: "Sigmatel HD Audio Disappearance"
date: 2009-11-29
forum: Hardware
---

### Post by TrevT93 on 2009-11-29
This morning I booted up my laptop to find that the Sigmatel HD Audio device has completely dropped off the radar.  The computer is making like it never even existed...much to my dismay.  (The stupid thing worked for me last night...)

It doesn't just seem to be Kubuntu, either.  It's disappeared from Fedora, Windows Vista, and Windows 7 RC 1, too.  Obviously, this is trouble with the device itself, not just the OS(es) trying to utilize it.

I get the feeling that there is nothing to do short of buying a USB or ExpressCard sound card...but if anyone else has any ideas, I'm up for trying them out, because I'd rather not spend the money.

---

### Post by TrevT93 on 2009-12-24
Bump.  (Well, it *has* been three weeks!)

Still no sound.  Any help/more info would be appreciated.

---

### Post by RedSingularity on 2009-12-24
See if your volume is all the way up.  Type the following into a terminal 

alsamixer

Make sure your volume is all the way up in there.

---

### Post by TrevT93 on 2009-12-24
```

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.20 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                              &#9474;
&#9474; Chip: Motorola Si3054                                                        &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Caller ID [Off]                                                        &#9474;
&#9474; 
&#9474; 
&#9474; 
&#9474;                       &#9484;&#9472;&#9472;&#9488;                        &#9484;&#9472;&#9472;&#9488;
&#9474;                       &#9474;MM&#9474;                        &#9474;MM&#9474;
&#9474;                       &#9492;&#9472;&#9472;&#9496;                        &#9492;&#9472;&#9472;&#9496;
&#9474; 
&#9474;                    <Caller I>                   Off-hook                     &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;

```Is this what I'm supposed to be seeing?

(PS, using the volume buttons on my laptop (Fn+PageUp or PageDown) no longer provoke a response by my computer.)

---

### Post by RedSingularity on 2009-12-24
That is showing the sound as muted.  Increase the level with the up and down arrow keys.

---

### Post by TrevT93 on 2009-12-24
I just said that my computer won't react to using the volume keys.  On my computer, they are Fn+PageUp (Volume +), Fn+PageDown (Volume -), and Fn+End (toggles mute).

And it's not like the card is just muted, it appears as though it's gone.  When I go into Windows, I get a notification that the sound card no longer exists, and the volume manager won't react to anything.  It just shows an X in the taskbar.

---

### Post by RedSingularity on 2009-12-24
If it is not working in windows either it sounds like a hardware problem.....not a software one.  We can try a few things though.....first post the output of 

aplay -l

---

### Post by TrevT93 on 2009-12-24
I figured it would be a hardware problem.

```

card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

---

### Post by RedSingularity on 2009-12-24
In a terminal do the folowing

sudo modprobe snd-hda-intel

See if you have sound.

---

### Post by TrevT93 on 2009-12-24
Nope, no sound, no terminal output.

Possibly this has something to do with how hot my computer can get at times?  Is it possible that a wire or something was melted?  The machine can get really hot when I try to play games, for instance (it only has an Intel GMA 945)...

---

### Post by RedSingularity on 2009-12-24
Ah it would seem that it is your speakers then.  One more thing, post the output of 

lspci | grep Audio

---

### Post by TrevT93 on 2009-12-24
```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

```

The speakers, but also the audio ins and outs at the front of the computer, I think.  I can't get anything there either.

---

### Post by RedSingularity on 2009-12-24
Its all attached to the same sound card so if one is bad it would be that all are bad.  It may be time for a new sound card buddy.  How old is that one?

---

### Post by TrevT93 on 2009-12-24
> **RedSingularity said:**
> Its all attached to the same sound card so if one is bad it would be that all are bad.  It may be time for a new sound card buddy.  How old is that one?

Well, this is a laptop that'll be two years old tomorrow.  Kinda sucks that a laptop will only last a few years before it starts to go bad, but I guess that's how the computer companies make their money, huh?  The common user can't replace their own stuff and won't pay through the nose to let the GeekSquad do it for them (when a new PC is cheap enough that the replacement through GeekSquad only costs slightly less).

I'm looking to get a new laptop before college anyway.  Something with better graphics.  I've already picked one out, in hopes that Newegg won't run out of it before a few months from now...although I could pick out another easily.

Last thing: do you know anything about graphics?  Because I have an outstanding issue w/ a Radeon graphics card, the open source driver, and Kubuntu 8.10.

Thanks for the help!

---

### Post by RedSingularity on 2009-12-24
I can look into it for you......start a new thread and link me to it.  :)

---

### Post by TrevT93 on 2009-12-24
The thread's already there...[or right here]("http://ubuntuforums.org/showthread.php?t=1358785"), for that matter.

---

