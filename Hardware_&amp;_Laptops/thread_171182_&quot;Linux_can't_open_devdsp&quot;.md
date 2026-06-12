---
title: "&quot;Linux: can't open /dev/dsp&quot;"
date: 2006-05-06
forum: Hardware &amp; Laptops
---

### Post by torx on 2006-05-06
Hi all, i'm getting this error "Linux: can't open /dev/dsp" when i'm trying to use "festival" to synthesize some text. Does anyone know what's wrong?

---

### Post by torx on 2006-05-07
bumper!!

---

### Post by dare2dreamer on 2006-07-31
> **torx said:**
> bumper!!

More than likely, esd is grabbing your soundcard. Try using esddsp to launch festival:

echo "say something, please." | esddsp festival --tts

I believe esddsp is in the esound-clients package.

---

### Post by rdrink on 2006-09-02
I'm having the same problem (under Dapper) so I figured I'd pick this thread up again with what I've figured out so far, in case it helps anyone else:
In response to dare2dreamer: I belive it's just esd. Here's why (for one thing, because esddsp says "no such command")...
In trying to troubleshoot and see if I could get *any* audio (which has been working fine) I opened up Jack control. It spit out an error message saying it couldn't launch jackd (but nicely informed me I was using alsa). So I tried launching jackd from a command line with the -v (verbose) option and found out why alsa wasn't happy: hw:0 already in use.
That seemed odd because I didn't have an audio apps running... so I looked at my processes and noticed two sleeping 'esd's. I did a man on esd and found out it's the 'enlightened sound deamon'... ok well that explained that. So I killed both those and tried jackctl again... viola, jack worked.
I then tried your command again as  echo "hello" | esd festival --tts and got the error ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave. So I took a good guess at that, quit Jack, and issued the pipe to esd again... and that time I got a sequence of three loud beeps... ok so audio works... but also an error 'no option festival'. I also seemed to be sitting at a prompt (or inside a process) and had to cntrl-c to get back to the cmd line.
Which leaves me with: alsa is working, esd is a deamon (which announces when it's launched!), and you can't pipe to it...
None of which solves the problem in festival.

So torx, did you figure anything out? I tinkered with festival's (Parameter.set 'Audio_Method '), with no results. And I looked in init.scm and some other .scm files but have yet to find where on would even set the default audio dev (not that I even know what that is right now).
And I did an ls /dev | grep dsp and I do have a dsp dev (and not a dsp1 or dsp2, as was suggested in another post)... even if festival can't use it.

So I'm thinking, missing library? dunno

BTW I never did figure out where those two zombied esd's came from... But last night I was auditioning some sounds off a website, using whatever file player Firefox launches by default... maybe it never closed them.

And I figure that tidbit was worth posting; because imagine how confused I would have been the next time I launched Jack!

rd

---

### Post by yamhouse on 2006-09-16
I was having a similar problem, and was able to get Festival to synthesize speech simply by killing the two sleeping esd processes. Not sure where those processes came from -- they seem to appear after I boot the machine.

---

### Post by akvik on 2006-10-21
Hi,
I've got the same problem, but with all sound altogether. Both in KDE and Gnome. A loud beep comes when I adjust the volume control to a certain level. Get the same message from Alsa when trying to play something. ```
pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
```
No esd processes lurking about, though :-)

---

### Post by bweil on 2006-10-31
> **yamhouse said:**
> I was having a similar problem, and was able to get Festival to synthesize speech simply by killing the two sleeping esd processes. Not sure where those processes came from -- they seem to appear after I boot the machine.

I had nearly the same problem.

festival was working a few days ago, then suddenly I had this can't open /dev/dsp issue.  Rebooting did not help.

I tried killing the two copies of esd (actually, killing the first one made both go away.)  and that made festival work again.  I haven't tried rebooting again.

---

### Post by aresgunther on 2007-03-24
Hey.  I was experiencing the same problem, but now I have it fixed.  Go to synaptics and check every package that begins with 'alsa'.  You can

```
sudo apt-get install alsa*
```

as well, but this gives you a whole hell of a lot more packages than you really want.  

After you have downloaded and installed all of the alsa packages, reboot and try festival again.  The error should be gone.

I got the solution from : [http://s2.selwerd.nl/~dirk-jan/gpsdrive/archive/msg06405.html](http://s2.selwerd.nl/~dirk-jan/gpsdrive/archive/msg06405.html)


ares

---

### Post by il_ventu on 2007-05-17
I got the same error. Now, installing **alsa-oss** and **oss-compat**, it works.

Ciao
a

---

### Post by serverside6 on 2007-08-25
For me, it was simple:

sudo festival

Hope this works for y'all.

---

### Post by serverside6 on 2007-08-29
For me, it was simple:

sudo festival

Hope this works for y'all.

---

### Post by timothywcrane on 2007-09-20
I had the same problem just a few minutes ago. My problem however, did not seem to be as semi-permanent. I was listening to a text file while I was surfing at the same time. I soon had a firefox freeze at the same time I was having the festival glitch. I closed firefox and the festival problem cleared up mid festival-text-file, and I was able to listen to the remainder of the text file. I just went back to the site I was browsing and realized that there was sound embedded into a flash intro on the site. It seems to me that when there is ever a fight over the use of sound, there is always a loser, and maybe even all. I am not sure of this, but if I remember somewhere in the cobwebs of my mind, that there is a way to prioritize programs for sound resources, but someone with a better memory might have further comment. :-)        <----- by the way today is supposed to be the birthday of the sideways text smileyface. HBday2U, HBday2U, :)

---

### Post by To be confirmed on 2007-10-19
That last post was interesting. Is there any answer to this question??

---

### Post by octesian on 2007-11-27
I closed mplayer and it works again.  I dont know much about sound but I think mplayer was hoggin it.

---

### Post by frank_costanza on 2007-12-07
I closed Banshee and then it worked. I don't know why it can't be used at the same time.

---

### Post by navaburo on 2008-01-02
Why festival uses the outdated /dev/dsp (OSS emulation) is beyond me.

To make it use ALSA, do the following:

```

printf ";use ALSA\n(Parameter.set 'Audio_Method 'Audio_Command)\n(Parameter.set 'Audio_Command \"aplay -q -c 1 -t raw -f s16 -r \$SR \$FILE\")\n" > .festivalrc

```

Then you can listen to music *and* use festival simultaneously.

(credit for this goes to the guys at the Gentoo doc wiki [http://gentoo-wiki.com/HOWTO_speechd]("http://gentoo-wiki.com/HOWTO_speechd"))

---

### Post by rwbrussels on 2008-01-10
Just a free-form reply to this thread about troubles with the audio being locked out and Festival not able to access dev/dsp.

** I tried everything in this forum to fix the same problem, and eventually solved it by reducing the "release time" for dev/dsp in the KDE manager to zero, meaning it releases the dsp access immediately. **

Hope that helps...

---

### Post by kvdbreem on 2008-03-15
navaburo,
Thanks for the help.  Tried that and it works.

---

### Post by TimD123 on 2008-04-27
Thanks navaburonavaburo,

Your solution worked for me as well.  For me it was the Totem Movie Player seemingly grabbing the sound card interface and not letting go.

All is good now.

Cheers.

---

### Post by SimonS on 2008-05-09
> **navaburo said:**
> Why festival uses the outdated /dev/dsp (OSS emulation) is beyond me.

To make it use ALSA, do the following:

```

printf ";use ALSA\n(Parameter.set 'Audio_Method 'Audio_Command)\n(Parameter.set 'Audio_Command \"aplay -q -c 1 -t raw -f s16 -r \$SR \$FILE\")\n" > .festivalrc

```

Then you can listen to music *and* use festival simultaneously.

(credit for this goes to the guys at the Gentoo doc wiki [http://gentoo-wiki.com/HOWTO_speechd]("http://gentoo-wiki.com/HOWTO_speechd"))

Just a quick addendum for any divs like me who blindly copy-paste into the terminal without reading what they're doing: that assumes you're in your home directory. To make this completely foolproof (for I am a "complete fool") that code byte should look like:

```

printf ";use ALSA\n(Parameter.set 'Audio_Method 'Audio_Command)\n(Parameter.set 'Audio_Command \"aplay -q -c 1 -t raw -f s16 -r \$SR \$FILE\")\n" > ~/.festivalrc

```

Thanks though - that solved all of my problems!

---

### Post by drywhenwet on 2008-05-14
Thanks a lot to this post.  It solved my problem.


> **navaburo said:**
> Why festival uses the outdated /dev/dsp (OSS emulation) is beyond me.

To make it use ALSA, do the following:

```

printf ";use ALSA\n(Parameter.set 'Audio_Method 'Audio_Command)\n(Parameter.set 'Audio_Command \"aplay -q -c 1 -t raw -f s16 -r \$SR \$FILE\")\n" > .festivalrc

```

Then you can listen to music *and* use festival simultaneously.

(credit for this goes to the guys at the Gentoo doc wiki [http://gentoo-wiki.com/HOWTO_speechd]("http://gentoo-wiki.com/HOWTO_speechd"))

---

### Post by korvins on 2008-07-08
That worked for me as well... Thanks!

By the way, would it be possible to install a packet and have everything configured? 

Like for instance installing orca, and having festival and everything ready to go? That should be the easy part, once all the voice thing is already done!

---

