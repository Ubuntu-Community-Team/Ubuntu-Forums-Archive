---
title: "No Sound Thru Laptop Speakers (Headphones Work) - 82801CA"
date: 2008-03-20
forum: Hardware &amp; Laptops
---

### Post by markovian72 on 2008-03-20
**This post could be related to an Ubuntu bug filed at**: [https://answers.edge.launchpad.net/ubuntu/+question/19793](https://answers.edge.launchpad.net/ubuntu/+question/19793) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				No sound comes from my laptop speakers no matter how I change the alsamixer settings, but sound does come through the headphones when I plug them in. I'm using Ubuntu 7.10 on a Compaq Presario 2700 and my soundcard is:

Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01), Analog Devices AD1886

Interestingly the LiveCD for Ubuntu 7.04 does play sound thru the laptop speakers. However, the Ubuntu 7.10 LiveCD and many other LiveCD's with a more current linux kernel don't play and sound thru the laptop speakers (Fedora 8.0, SimplyMepis 7.0, PCLinuxOS2007, Xubuntu 7.10). This makes me think something went wrong in the latest versions of the alsa drivers for my hardware.

I've been trying to get this to work for a couple months and have had no success getting the sound to work after recompiling the alsa driver to the latest version and various other ideas I've seen in other forums. It seems like this should be simple to fix since headphone sound already works. Any help greatly appreciated.

Here's a link to the Launchpad question I posted that was never resolved:

[https://answers.edge.launchpad.net/ubuntu/+question/19793]("https://answers.edge.launchpad.net/ubuntu/+question/19793")

---

### Post by David.S on 2008-03-20
Copy an paste this in the terminal and restart you computer It helped with me
sudo apt-get install linux-backports-modules-generic

---

### Post by markovian72 on 2008-03-26
Thanks for the suggestion.  Installing the backports didn't get sound working.  Any other suggestions?

---

### Post by xhalarin on 2008-05-15
I have this exact same issue with Ubuntu 8.04 with a fresh install on a Presario 2700.  I have tried playing with the gui mixer settings and also the alsamixer command line mixer to no avail.  Would love to hear any other suggestions.  Thanks.

---

### Post by neutralstorm on 2008-05-16
I am very curious about this as well.
With me it is a little different though.
I have very faint sound. All volume levels
are on max. 
This has been an ongoing issue for me going back
to Edgy. 
That said it is not that big a deal, it just would be 
nice to have it working.

ps. I've searched all over for solutions; but had no luck.

---

### Post by Led-Zeppelin on 2008-06-15
i have the same problem on my presario 2700  but headphones don't work :mad::mad::mad::mad::mad::mad:

vary frustratig

---

### Post by Magnum010 on 2008-07-10
Me too, I have checked half a dozen distros, and specifically versions of Ubuntu/Kubuntu.  I think it has something to do with ALSA 1.0.13????  Maybe.  But Linux is new to me, eerily enough I am trying to switch and my main system worked so good, no problems installing so nothing to educate me on how to overcome.  Not so with my POS Presario.  Kudos UBUNTU SHame on Compaq

---

