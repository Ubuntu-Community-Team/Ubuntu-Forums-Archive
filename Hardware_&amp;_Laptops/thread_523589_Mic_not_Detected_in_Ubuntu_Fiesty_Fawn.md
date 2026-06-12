---
title: "Mic not Detected in Ubuntu Fiesty Fawn"
date: 2007-08-12
forum: Hardware &amp; Laptops
---

### Post by designwiz on 2007-08-12
i installed kopete to voice chat on Yahoo.. i never ever bothered to check whether my micro phone worksin linux coz it did or rather does work on vista!

After reading around threads/posts/forums, i finally have arrived to the conclusion that my mic has not be detected
coz

1.Right Click Sound Icon-->Open volume control--> No mic option

2.In Alsamixer i cannot see an optio mic

The o/p of aplay -l file i
> card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



Also AlsaMixer
> 
&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.13 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                              &#9474;
&#9474; Chip: SigmaTel STAC9221 A1                                                   &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=0.00, 0.00] 


Can anyone help me out and get this thing running
Any help would be greatly appreciated thanks!
I hope i can get it working thanks in advance Regards

---

### Post by designwiz on 2007-08-13
can any1 help me out .. im tryin to fix it.. any help would be appreciated

---

### Post by designwiz on 2007-08-22
its been more than week since i posted my problem, havent been able to solve it yet.. help thanks in advance

---

### Post by fredj on 2007-08-23
Open the alsa mixer (double click on the speaker icon in the taskbar). Look under the File->
Change Device menu and make sure that the correct sound device is connected.
I am assuming that your microphone is plugged into the soundcard if it isn't post again.
Then use the Edit->Preferences menu to ensure that all the possible volumes controls and
switches are present for both record and playback.
To use your mike you will need to make sure that the mic recording control is selected and a
suitable volume levels is set. You may also need to select and set the mic boost control.

---

