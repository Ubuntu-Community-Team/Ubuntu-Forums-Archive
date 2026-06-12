---
title: "Sound starts to stutter after some time. Edit: How to test a new Sound card?"
date: 2015-10-07
forum: Hardware
---

### Post by hey2 on 2015-10-07
Hi.

I'm having  a problem on my computer.

After some time using the computer, the sound starts to stutter whenever i watch a video on the browser or in VLC.

It just happen without any reason. I could be browsing the internet and everything is fine, then i leave the computer and when i come back the sound is jerky.

I've tried to check if there was something abnormal on system monitor, but everything seems fine. No high processor or memory usage. No process using to much memory. Nothing.

I've tried to install an old sound card, but unfortunately Ubuntu doesn’t seem to install the drivers.

What do you guys think i could to to diagnose this problem?

P.S: Sorry for my English.

---

### Post by hey2 on 2015-10-13
Hi.

Sorry to bump this but i need some help.

T check if the problem is something related to the motherboard sound, i would like to try a pci sound card that i have.

After i installed it in the computer, Ubuntu doesn't recognize it. It says Dummy sound and the sound doesn't seem to work.

I found this page [http://manpages.ubuntu.com/manpages/trusty/man4/snd_emu10kx.4freebsd.html](http://manpages.ubuntu.com/manpages/trusty/man4/snd_emu10kx.4freebsd.html)

It has a file to download, but where do i put it? What is better way to get the driver to work?

Thanks.

---

### Post by QDR06VV9 on 2015-10-13
Do this for me if you would.
```
sudo apt-get install inxi
```
Then again in terminal
```
inxi -A
```
Post the output back here. Lets see what we got.

---

### Post by Yellow Pasque on 2015-10-13
I think alsa info would give more relevant information than inxi.
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by hey2 on 2015-10-13
> **runrickus said:**
> Do this for me if you would.
```
sudo apt-get install inxi
```
Then again in terminal
```
inxi -A
```
Post the output back here. Lets see what we got.

Hi.

Thank you for your response.

Just to be sure, your post is regarding the new pci card? Not the original post?

---

### Post by hey2 on 2015-10-13
> **Temüjin said:**
> I think alsa info would give more relevant information than inxi.
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

Hi.

Thank you for your answer.

I would like to ask you the same as the post before.

I think someone suggested this before, but it was regarding the problem i have on the original post.

[http://www.alsa-project.org/db/?f=63ef101f0735baee083eb2200475509a359b63bb](http://www.alsa-project.org/db/?f=63ef101f0735baee083eb2200475509a359b63bb)

Is this it?

---

### Post by QDR06VV9 on 2015-10-13
It shows all sound cards. Below is mine.
```
Audio:     Card-1: NVIDIA GF119 HDMI Audio Controller driver: snd_hda_intel Sound: ALSA ver: k4.1.10-040110-lowlatency    
 Card-2: Creative Labs SB Audigy driver: snd_emu10k1 

```

---

### Post by hey2 on 2015-10-13
> **runrickus said:**
> It shows all sound cards. Below is mine.
```
Audio:     Card-1: NVIDIA GF119 HDMI Audio Controller driver: snd_hda_intel Sound: ALSA ver: k4.1.10-040110-lowlatency    
 Card-2: Creative Labs SB Audigy driver: snd_emu10k1 

```

Hi.

Thankks for your fast response.

I was asking because i don't have the card installed right now.

I think the card have the same chip as yours, but is a live 1024.

The link that i posted on the second post is about that driver.

Did yours got recognized?

---

### Post by QDR06VV9 on 2015-10-13
Yes it did get recognized.
I am glad to hear that you do not have it installed, By what i had seen in your alsa text report it was absent.
One more thing to note, Make sure your card is enabled in the BIOS via Auto mode or PCI enabled.
Just getting rid of any chance of that being a possibility.
Regards

---

### Post by hey2 on 2015-10-13
> **runrickus said:**
> Yes it did get recognized.
I am glad to hear that you do not have it installed, By what i had seen in your alsa text report it was absent.
One more thing to note, Make sure your card is enabled in the BIOS via Auto mode or PCI enabled.
Just getting rid of any chance of that being a possibility.
Regards

Hi.

I don't think it's needed on my motherboard.

The only thing i did when i had it in Windows was to disable the onboard sound.

Is this all right?

Wich test should i run? The alsa one?

---

### Post by QDR06VV9 on 2015-10-13
> **hey2 said:**
> Hi.

The only thing i did when i had it in Windows was to disable the onboard sound.

Is this all right?

Yes that is correct. When you have it installed show me the output of the"inxi -A" command.
I have an appointment here that will take me a couple of hours, I will check back to see how you are getting on.

---

### Post by hey2 on 2015-10-13
> **runrickus said:**
> Yes that is correct. When you have it installed show me the output of the"inxi -A" command.
I have an appointment here that will take me a couple of hours, I will check back to see how you are getting on.

Hi.

It's working! I'm really sorry.

I don't know what happened, but the last time, i tried in two PCI Slots and it didn't work.

It gives me three option on the output:

Digital s/pdif

Analog no amplification 

Analog amplification.

What is the difference between the last two?

Is there any test that i could do to check if everything is alright?

---

### Post by hey2 on 2015-10-13
inxi -A

Audio:     Card: Creative Labs SB Live! EMU10k1 driver: snd_emu10k1 Sound: ALSA ver: k3.19.0-30-generic

---

### Post by QDR06VV9 on 2015-10-13
Hey thats great, No need to be sorry here, After all it was success we were after.:D 
Pulseaudio volume control will add some enjoyment to your  usage switching to other cards as well.
I'll check back in a bit.
Good Job..

---

### Post by hey2 on 2015-10-13
> **runrickus said:**
> Hey thats great, No need to be sorry here, After all it was success we were after.:D 
Pulseaudio volume control will add some enjoyment to your  usage switching to other cards as well.
I'll check back in a bit.
Good Job..

Thank you and sorry again for wasting your time.

The no amplification and amplification was also present with the onboard, but i never understood the difference. It seem to make no diference choosing either one. 

I disable the onboard and i'm just using the PCI card.

Now i will test if the issue in the original post is gone.

Thank you.

---

### Post by QDR06VV9 on 2015-10-13
> **hey2 said:**
> Thank you and sorry again for wasting your time.

The no amplification and amplification was also present with the onboard, but i never understood the difference. It seem to make no diference choosing either one. 

I disable the onboard and i'm just using the PCI card.

Now i will test if the issue in the original post is gone.

Thank you.
Again no worries never a waste of time with successful outcomes.;)
If your original problem is solved and you have a decent set of speakers you may be interested in
[PulseAudio equalizer]("http://www.webupd8.org/2013/10/system-wide-pulseaudio-equalizer.html")
Totally up to you!
Regards

---

### Post by hey2 on 2015-10-21
> **runrickus said:**
> Again no worries never a waste of time with successful outcomes.;)
If your original problem is solved and you have a decent set of speakers you may be interested in
[PulseAudio equalizer]("http://www.webupd8.org/2013/10/system-wide-pulseaudio-equalizer.html")
Totally up to you!
Regards

Hi.

Just to give an update.

It's been a few days since i installed the dedicated sound card and the issue is gone. No sound stutter, nothing. 

Unfortunately the sound seems a little worse than the on board chip.

Do you hear some noise when you move the volume slider near the top? I have the same sound chip on mine and i hear some noise. Also, when i mute the sound effects, i hear a pop every time i press the volume button ( especially near the top). What is your card model?

Also i would like to ask everyone, since the original problem seems to be caused by just the onboard sound, do you guys think that it could be something software related? Maybe changing some option.

This is the Alsa information:

[http://www.alsa-project.org/db/?f=63ef101f0735baee083eb2200475509a359b63bb](http://www.alsa-project.org/db/?f=63ef101f0735baee083eb2200475509a359b63bb)

---

