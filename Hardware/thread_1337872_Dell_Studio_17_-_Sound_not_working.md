---
title: "Dell Studio 17 - Sound not working"
date: 2009-11-25
forum: Hardware
---

### Post by ndefontenay on 2009-11-25
Hi.

I just bought a dell studio 17 and I got no sound at all.

I do get a default sound device (with no name) in sound preferences but that's about it.

Can someone help me at least find out if my card is detected properly and eventually find a solution for that?

This laptop features a JBL sound system. I guess it's a bit exotic.

regards,

nico

---

### Post by ndefontenay on 2009-11-26
Gentle bump. Anybody can help me identify the problem?

---

### Post by ndefontenay on 2009-11-30
Hi anyone.

I don't know what I do wrong on this thread but I would really love to get my sound working on this laptop.

Everything else is doing wonder. I would really appreciate a little help. If the amount of information is not enough for your liking please let me know what will do you good.

I'm so desperate with this.

thanks

Nico

---

### Post by davidryderuk on 2009-12-01
Hi,
In order to fix your problem it is important to know what sound card you have. This can be done by running the following command from terminal:

```
sudo lshw -short
```

In this particular case I carried out a quick google search for your laptops specifications and I think your probably using an "Intel 82801H HD Audio" card.

Looking up information on this card I then found a bug report describing a similar problem to your current one. 

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/411574?comments=all](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/411574?comments=all)

There don't seem to be any solutions that work for everyone, however based on comment #14 in the bug report I would suggest trying the following to start with:

1. Open terminal, which can be found in Applications > Accessories > Terminal.

2. Open up the /etc/modprobe.d/alsa-base.conf file by running the following command from terminal.

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

3. Find and replace the following line

> options snd-hda-intel power_save=10 power_save_controller=N

with this one

> options snd-hda-intel model=dell-m6

4. Reboot your machine.

5. Open System > Preferances > Sound.

6. Go to the Hardware tab and ensure that the Profile is set to "Analog Stereo Duplex"

7. Check to see if the sound is now working properly.

---

### Post by ndefontenay on 2009-12-01
Hi david.

I'm floored.

I've been toying around with different options in the alsa base conf file from other threads without much success.

I currently have no internet at home so I will print these instructions and try it tonight. I'm so grateful.

As the saying goes, instead of giving a fish to someone, learn him how to fish, so can you tell me how you found that bug?

thanks

Nico

---

### Post by davidryderuk on 2009-12-02
> so can you tell me how you found that bug?

When I found out that your sound card was probably an "Intel 82801H HD Audio" card, I did a google search for "Intel 82801H HD Audio karmic". The first link listed in google is the bug report. 

The harder part is knowing what soundcard your laptop is using, which is why it would be a good idea to check when you get home by using the command:

```
sudo lshw -short
```

Additionally if using the option

> options snd-hda-intel model=dell-m6 

doesn't get your sound working then you might want to check what possible model options are likely to work on your laptop. You can do this by following the instructions in the link below (although don't try reinstalling alsa).

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by ndefontenay on 2009-12-02
dell-m6 was the one. I'm now enjoying sound at home.

I will try to include the option power_save=10 which I think is kind of important. If it doesn't work too bad but worth a try.

Thanks a ton David. You are right the sound card is the important one. I thought intel sound card was kind of generic.

Now I have a really nice laptop with a really nice OS which works flawlessly and within fraction of seconds... Literally!

---

### Post by davidryderuk on 2009-12-03
I'm glad you got the sound working. Hopefully the bug will be fixed at some point to work with the default options.

---

### Post by ndefontenay on 2010-03-25
Update: With Lucid Lynx, sound worked with speakers but not with headphone. Apply same fix as above to fix it.

---

