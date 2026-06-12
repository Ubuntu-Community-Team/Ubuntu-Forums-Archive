---
title: "Microphone HDA Intel... so many issues i cannot tell the woods from the tress anymore"
date: 2008-04-29
forum: Hardware
---

### Post by ferdinando_villa on 2008-04-29
Please, if anyone can help me... i'm starting to spend way too much time on this, reading lots of articles about my problem, and nothing seems to work...

If you just google anything related to Hda Intel card and Ubuntu, there are lots of people with serious problems with this type of card, and I am no different. I am on Ubuntu 8.04 64 (fresh install, but i had exactly the same problems on 8.04 i386), and my card is

card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


However, by looking at the usual problems, I cannot help but feeling that the solutions proposed (recompiling ALSA, mess with /etc/modprobe.d/alsa-base file, etc) might not be what I needed, since my problem seems to be (but only seems!) slightly less complicated...

In general, sound works fine for me; speakers fine, volume control responsive, headphones fine, and i can even hear myself when using the microphone (with a headset plugged in)...

However, i cannot, no matter how I try, configure the microphone capture, so it seems like it is going directly through the card, and not being captured at all. It doesn't work in Skype, Ekiga, or Audacity either.

I guess I am just at a loss on how to configure the capture settings, since all the rest of the sound configuration seems to be fine...

please, if anyone knows anything about it, or has had any luck with this specific card, let's talk... here are some of my configurations,including a screenshot of my mixer settings, for maybe I am doing something wrong with this capture settings in the first place

user@user-laptop:~$ cat /proc/asound/pcm
00-04: ALC883 Analog : ALC883 Analog : capture 1
00-00: ALC883 Analog : ALC883 Analog : playback 1 : capture 1

user@user-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on Apr 21 2008 for kernel 2.6.24-16-generic (SMP).

user@user-laptop:~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xb0000000 irq 16

user@user-laptop:~$ lspci | grep -i audio
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)


Any help, will be greatly, greatly appreciated!

---

### Post by ferdinando_villa on 2008-04-29
Forgot the screenshot... here it is

---

### Post by ikevie on 2008-04-29
I want to know the answer to this question too but I haven't been successful with any tutorial.

---

### Post by aaaantoine on 2008-04-30
I'd like to find out how to get it to work, as well.  I'm not a fan of having hardware on my computer that doesn't do anything.

On a similar topic, ferdinando, I see in that screenshot that you don't have the Surround channel visible.  What channel does your audio output come from?  Does your hardware detect when the headphone jack is in use?

---

### Post by Moonlit Knight on 2008-06-29
Hi I have the same problem here I plugged my guitar to the line in or the microphone and I can hear myself playing but it seems that it goes through the plug to the speakers directly. 

It doesn't capture anything.

I'm using Hardy Heron and I had to compile alsa because alsamixer didn't work.
I used this commands to reinstall alsa

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

Thank you in advance.

---

### Post by StriderK on 2008-09-09
I am also having the same issues as the first poster. Sound works, headphones work, but the mic doesn't seem to capture. It does seem to capture "something," but that's only a high pitched squealing noise.

---

