---
title: "Can't get sount via HDMI"
date: 2010-01-30
forum: Hardware
---

### Post by boromb on 2010-01-30
Hello,

I hope you can help me with my annoying problem.
I can't get sound out through HDMI.

My Computer is an HP Laptop. HP Compaq 8710W with quite good configuration.
4GB ram, DualCore 9500T, Nvidia Quadro FX3600M

Runing 
aplay -l

> aplay -l
**** Lista över PLAYBACK hårdvaruenheter ****
kort 0: Intel [HDA Intel], enhet 0: AD198x Analog [AD198x Analog]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
For some reason I don't have digital out.
Can it be true?

Thanks,

---

### Post by boromb on 2010-01-30
I have no other digital output from my laptop. Shouldn't I be able to use HDMI to pass through the sound?

I want to use this laptop as htpc when needed.

I love Ubuntu and I don't want to install Windows just to get sound out via HDMI.

Hope someone can help.

---

### Post by boromb on 2010-03-01
I'm still trying to get sound over HDMI.

I have red many different sites and threads without results.

Is there anyone who can guide me?

Please.

Best regards!

---

### Post by Yellow Pasque on 2010-03-01
A lot of nvidia HDMI bugs are fixed in the latest ALSA. Try: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by boromb on 2010-03-05
> **Temüjin said:**
> A lot of nvidia HDMI bugs are fixed in the latest ALSA. Try: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

Thank you!

I have now installed that but I still cant get sound to work.
I'm not getting any digital outputs.

I could connect my NuForce Udac via usb and that worked but connecting HDMI cable doesn't give my any choices. 

I don't know is it so hard to get it to work.

I have another laptop with Vista and everytinh works greatly.
Picture is perfect scaled and I get sound through HDMI but this laptop fan is very loud unfortunately.
Picture from my Ubuntu  out to TV is for some reason to big for the TV but really nice. Resolutions is right. Bad bad bad....

I love my beautiful ubuntu but it's cheaper for me to change OS then buying new HTPC.

Is it even possible to get this working? Why so hard? Why can't it be as easy as Windows? Many other things are easier but Video and Sound settings on Ubuntu are really bad. At least in my case.

Best regards!

---

### Post by Manyette on 2010-03-05
I hope I haven't missed anything in these posts, but I had the same problem with a HP G71 laptop.  You need to load the Ghome-Alsa mixer, and then go to  Preferences->Sound->Hardware, and then enable Digital Sterio HSMI Output.  That worked for me.  Hope this is of some help.

---

### Post by boromb on 2010-03-05
> **Manyette said:**
> I hope I haven't missed anything in these posts, but I had the same problem with a HP G71 laptop.  You need to load the Ghome-Alsa mixer, and then go to  Preferences->Sound->Hardware, and then enable Digital Sterio HSMI Output.  That worked for me.  Hope this is of some help.

My problem is that I don't have any HDMI or other digital line to activate.
Hate it :)

Thanks!

---

### Post by Yellow Pasque on 2010-03-05
You can try to load the module manually:
```
sudo modprobe -v snd-hda-codec-nvhdmi
aplay -l
```
If your device doesn't show up then, I don't know what else to tell you.

---

### Post by boromb on 2010-03-10
Thank you all for help!
I haven't get it to work but I found a solution.
I have bought following
[http://www.nuforce.com/hp/products/iconudac/index.php](http://www.nuforce.com/hp/products/iconudac/index.php)
and now I can get sound out of my ubuntu.

I have no digital out besides HDMI and this thing can forward sound from XBMC to my receiver and
I get surround.

It's not the best solution but it works!

Best regards!

---

### Post by Manyette on 2010-03-10
Hi boromb, well I'm glad it worked for you, but I have a hard time understanding how a machine with an HDMI output doesn't have a digital audio output.  It might just be worth filing a bug on lauinchpad to see if there is a hardware problem that isn't recognized.  Just a thought.

---

