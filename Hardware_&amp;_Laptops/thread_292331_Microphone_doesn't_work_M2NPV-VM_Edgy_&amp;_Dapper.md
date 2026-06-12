---
title: "Microphone doesn't work M2NPV-VM Edgy &amp; Dapper"
date: 2006-11-03
forum: Hardware &amp; Laptops
---

### Post by jvsmith on 2006-11-03
Recently purchased the following system.
Asus M2NPV-VM BIOS 0504
AMD 4200+ Dual-Core 65W
1 GB DDR2 800 mhz ram
250 GB WD WD2500YS
Nice case
DVD +- R/W
Seasonic P12 330W PS
Card reader
Silverstone SST-FP32-B

My problem is that with both Dapper and Edgy the microphone doesn't work. I've verified that I don't have a hardware issue by installing W2k. I've messed some with aumix, along with volume control and the sound recorder but as of yet no luck. Any recommendations are welcomed.

TIA

---

### Post by balak on 2006-12-31
Did you find a solution? If so, please post here.

I bought the same mobo and got the audio to work but the mic is still unusable.

thanks!

---

### Post by rjdriscoll on 2007-02-20
I have an M2NPV-MX Motherboard and also can get nothing with the microphone.

Has anyone had any luck with it yet?

I've looked at the data sheet for the AD1986A SoundMAX codec (on the Analog Devices Website) and see that the microphone gain can be set to 0dB, +10dB, +20dB or +30dB.  However I can find no way to change this gain setting and wonder if there is a clue here.  If the gain is set to 0dB then it will need 1 volt from the microphone which will be impossible!!

I guess I must try to understand how the kernel driver works.

Apart from this the sound is OK and everything else works fine.  Even with the inexpensive Sempron 3400+ (clocking at 1.8 GHz) and two sticks of 533 MHz memory it is impressively quick.

---

### Post by acmarfil31 on 2007-06-03
Hi, has anyone already solved this issue? Would appreciate posting any solution.

Thanks.

---

### Post by crimsun on 2007-06-03
> **acmarfil31 said:**
> Hi, has anyone already solved this issue? Would appreciate posting any solution.

It would help if you provided details regarding which kernel you're running (`uname -r`) and the output from the `amixer` command.

---

### Post by acmarfil31 on 2007-06-05
hi, uname -r returned, **2.6.20-16-generic**.  I suppose this is the kernel version i'm running.

I've attached the amixer output also. I'm able to hear my voice using my mic, but SKYPE doesn't seem to detect so, neither sound recorder.

Thanks.

---

### Post by balak on 2007-07-04
OK, I got this working.

I am not sure if this is applicable to all kernels, but I am using 2.6.20-16-generic 
I recently upgraded my desktop from edgy to feisty.

Open alsa-mixer (double click the sound control in the panel, top right). We just need to configure this to be able to use the microphone.

In File->change device, select the Alsa mixer option
In Edit-> preferences tab, check line-in, line-in capture, microphone, microphone capture and capture.
In the playback tab, mute the line-in and microphone
In the Recording tab, MUTE the speaker and ENABLE the microphone! Thats it!

Fixing the mic on my desktop has been my TODO for the last six months (ever since I assembled this desktop) so I glad I got this done. I am able to record my voice, tested it also with skype's test call.

Thanks to tgalati4 and this thread
[http://ubuntuforums.org/showthread.php?t=488531&highlight=skype+microphone](http://ubuntuforums.org/showthread.php?t=488531&highlight=skype+microphone)

---

### Post by acmarfil31 on 2007-10-19
balak, thanks for your post.  I've encountered same problem in ubuntu-gutsy.  Luckily, your procedure worked as well.

Cheers!

---

### Post by garton on 2008-05-24
Quite interesting. I use this mobo with Windows XP and the microphone doesn't work there either. I'll try to use the suggestion above, and translate it to Windows-ish.

---

