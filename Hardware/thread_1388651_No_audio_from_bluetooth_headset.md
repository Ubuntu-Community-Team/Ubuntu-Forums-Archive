---
title: "No audio from bluetooth headset"
date: 2010-01-23
forum: Hardware
---

### Post by zippyties on 2010-01-23
I am trying to use my Jabra BT125 with skype on Ubuntu 9.10.  So far I have been able to pair it with Bluez no problem and the Jabra even makes the little beeping sound it makes when connected.

Next when I try to use skype no audio comes through the jabra or the computer speakers.  Just to test it I called my wife, and she said she could hear me just fine on her phone so the mic works but not the speaker.

Is this just a setting that I missed ie. telling Ubuntu to use the speaker as well as the mic on the Jabra?

any help is appreciated.

Thanks

---

### Post by zippyties on 2010-01-23
bump

---

### Post by gradinaruvasile on 2010-01-23
After pairing, right click on the volume icon and see if the bluetooth handset is added as an audio card. Then see both the input and output is routed through it.

I use blueman - its an alternate bluetooth manager, simple to use, better than the default one. I use it succesfully with a bluetooth handsfree with Skype and Sip Communicator mostly.

---

### Post by zippyties on 2010-01-23
**@gradinaruvasile**
Thanks for your help.  I have attached images of sound configuration menu the way I have it now, let me know if I am doing something wrong.

thanks,

---

### Post by gradinaruvasile on 2010-01-23
Theoretically it should work this way. I have exactly the same setup and it works for me. Check with skype's echo test.

---

### Post by Mothinator on 2010-01-23
I'm having the same problem, except with a plantronics discovery 655 headset. 

Also, Skype comes out my speakers.

---

### Post by Mothinator on 2010-01-23
I also don't think it is a problem with Skype.

Going into the PulseAudio Manager and trying to play a sample through the headset also does not work.

I've tried following the [bluetooth headset document]("https://help.ubuntu.com/community/BluetoothHeadset"), but I think it is only for Jaunty. I get an error at this step:

```
pactl load-module module-alsa-sink device=btheadset
Failure: Module initalization failed

```

---

### Post by zippyties on 2010-01-23
I thought it might just be skype also but I can't get any sound out of it at all.  That's why i thought it might just be a checkbox that i missed.

---

### Post by nab on 2010-01-30
Hi all,

I had a simular problem with my nokia bh-103 and my Ubuntu 9.10:

I tried using BluetoothHeadset for 9.04 at [https://help.ubuntu.com/community/BluetoothHeadset]("https://help.ubuntu.com/community/BluetoothHeadset")

with "$ hcitools scan" it didn't find the device
and "$ pactl load-module module-alsa-sink device=btheadset"
gave also some error.

But I could see that the headset was paired with my PC in the Bluetooth applet, so I just installed the recommended programms:

"$ sudo apt-get install paprefs paman padevchooser"

and then I followed the rest of the guide starting with point 14.
I just had to copy the automatic name within the Manager instead of alsa_output.btheadset (in my case bluez_sink.00_0B_E4_3A_8B_96 for the Default Sink - Other and bluez_source.00_0B_E4_3A_8B_96 for Default Source - Other).

The headset works with Skype :-)

I hope this helps :-)
Niko

Edit:
And when the Adapter doesn't seem to work, try activating it in windows as suggested here [http://ubuntuforums.org/showthread.php?t=1365249]("http://ubuntuforums.org/showthread.php?t=1365249&highlight=bluetooth+headset")

and another guide here:
[http://ubuntuforums.org/showthread.php?t=1340196]("http://ubuntuforums.org/showthread.php?t=1340196")

---

### Post by gradinaruvasile on 2010-01-30
I just installed blueman (an alternate bluetooth manager, way better than the default one), it has options to associate a device directly to headset. It does all the work, it initiates the bt device as pulseudio device. I just had to route the microphone.

---

### Post by Mothinator on 2010-03-02
The advice above did not help for me.

It appears there is a bug report filed for this issue: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/444017]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/444017")

---

### Post by farbird on 2010-03-03
add the blueman ppa.... it worked for me..are u using karmic?

---

### Post by Mothinator on 2010-03-03
Farbird,

Thanks for the advice. Yes, I am using Karmic.

Adding the blueman PPA and installing blueman did not help the problem.

---

### Post by farbird on 2010-03-03
did u use the skype package from the repositories?

or from skype.com itself?

i got mine working from the deb downloaded from skype.com

iirc, the one from 9.10 repo didnt work well with blueman and my bt headset

---

### Post by Mothinator on 2010-03-03
It is 2.1.0.81-1 from Skype.com.


However, I don't believe it is an issue with Skype, and I cannot get sound through the headset from pulseaudio either.

---

### Post by farbird on 2010-03-04
i have had some issues with cheap bt adapters... but i had invested in a US$4 bt dongle which work well... at dealextreme.com.

dont go for the US$2 bt adapter....it didnt work on my 9.10

---

