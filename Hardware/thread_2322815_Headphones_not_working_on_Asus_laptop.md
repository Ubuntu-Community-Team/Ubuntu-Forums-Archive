---
title: "Headphones not working on Asus laptop"
date: 2016-04-30
forum: Hardware
---

### Post by Jack Harper on 2016-04-30
Sound works fine from speakers, but when I plug in my headphones no sound comes from headphones but it keeps playing from speakers. Laptop is Asus G751JT, I have 16.04 LTS installed and fully updated. Headphones work on the preinstalled Windows 10.

Here are my Alsa details:

[http://www.alsa-project.org/db/?f=6d358e8b683771d1ac039b8b9a09075c2bb61b84](http://www.alsa-project.org/db/?f=6d358e8b683771d1ac039b8b9a09075c2bb61b84) Thanks :)

---

### Post by Jack Harper on 2016-05-01
Bump :(

---

### Post by DuckHook on 2016-05-01
In Ubuntu, headphones may not be switched automatically. Mine won't. I have to switch to them on the sound applet. Instructions [here]("https://help.ubuntu.com/16.04/ubuntu-help/sound-usespeakers.html").

---

### Post by Jack Harper on 2016-05-01
> **DuckHook said:**
> In Ubuntu, headphones may not be switched automatically. Mine won't. I have to switch to them on the sound applet. Instructions [here]("https://help.ubuntu.com/16.04/ubuntu-help/sound-usespeakers.html").

I dont have headphones there, only Analog Stereo Output and Analog Surround 4.0 Output. They should switch automatically, on previous laptops I used it was never a problem, I plug the headphones and sound comes through them, no switching of any kind, but now it looks like Ubuntu doesnt even register they are connected. I hope someone experienced with Alsa can take a look. I also tried booting 14.04.4 in live mode and headphones also didnt work.

---

### Post by Jack Harper on 2016-05-01
I fixed my issue somewhat by adding:

```
options snd_hda_intel model=asus-mode4
``` into ```
/etc/modprobe.d/alsa-base.conf
```

Now I heard sound from both the speakers and headphones.

---

### Post by DuckHook on 2016-05-01
Go back to Sound Settings applet and look for separate headphone entry again. If there, you may be able to set/switch sounds between the one output and the other. If still not present:```
sudo apt update
sudo apt install pavucontrol
```*pavucontrol* a control panel with much finer control features. Open it from the dash (not available in System Settings) and look around for headphone jack to switch outputs, etc.

---

### Post by gnusci on 2016-05-01
Did you check the settings with alsamixer.

---

### Post by Jack Harper on 2016-05-02
> **DuckHook said:**
> Go back to Sound Settings applet and look for separate headphone entry again. If there, you may be able to set/switch sounds between the one output and the other. If still not present:```
sudo apt update
sudo apt install pavucontrol
```*pavucontrol* a control panel with much finer control features. Open it from the dash (not available in System Settings) and look around for headphone jack to switch outputs, etc.

There is no headphone control in pavucontrol at all on my system.

---

### Post by Jack Harper on 2016-05-02
> **gnusci said:**
> Did you check the settings with alsamixer.

Yes, no headphones there just like with pavucontrol.

---

### Post by DuckHook on 2016-05-02
Try the solutions in [this]("http://askubuntu.com/questions/132440/headphone-jack-not-working") askubuntu thread. You may need to try them one after the other, but first remember to back out the changes made previously. There is a logic to trying fixes: it is easier to track what works and what doesn't by starting out from the same state each time.

---

### Post by Yellow Pasque on 2016-05-03
^Some of the various fixes in that thread are model-specific and don't match the OP's laptop model. Would not recommend..

I think the asus-mode4 hack works because it maps pin 0x21 to a headphone out. Your headphone pin appears to be 0x21, but it doesn't appear to be recognized as a HP out in your alsa info:
```
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
...
[    4.844761] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=2 (0x14/0x1a/0x0/0x0/0x0)
[    4.844763] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
```

As for a solution that will get you jack sensing/auto-mute, I'm not sure at the moment and I'm getting ready for work. I may have more thoughts on it later today/this week.

---

### Post by Jack Harper on 2016-05-03
> **Temüjin said:**
> ^Some of the various fixes in that thread are model-specific and don't match the OP's laptop model. Would not recommend..

I think the asus-mode4 hack works because it maps pin 0x21 to a headphone out. Your headphone pin appears to be 0x21, but it doesn't appear to be recognized as a HP out in your alsa info:
```
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
...
[    4.844761] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=2 (0x14/0x1a/0x0/0x0/0x0)
[    4.844763] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
```

As for a solution that will get you jack sensing/auto-mute, I'm not sure at the moment and I'm getting ready for work. I may have more thoughts on it later today/this week.

Thank you, I appreciate the help. I tried other numbers in that asus-modeX and a few achieve the same effect as 4, and some dont give any sound through headphones.

---

### Post by DuckHook on 2016-05-03
Thanks for stepping in, Temüjin.

@ Jack Harper: you are in better hands with Temüjin than you are with me. I will leave the two of your to solve this. ;)

---

### Post by Yellow Pasque on 2016-05-03
Can you grab an ALSA info with the asus-mode4 hack for comparison?

The next thing I would try is removing the asus-mode4 hack, reboot and use hdajackretask. You may have to show unconnected pins and use the advanced override to get jack detection working properly.
```
sudo apt-get install alsa-tools-gui
hdajackretask
```

---

### Post by Jack Harper on 2016-05-03
> **Temüjin said:**
> Can you grab an ALSA info with the asus-mode4 hack for comparison?

The next thing I would try is removing the asus-mode4 hack, reboot and use hdajackretask. You may have to show unconnected pins and use the advanced override to get jack detection working properly.
```
sudo apt-get install alsa-tools-gui
hdajackretask
```

[http://www.alsa-project.org/db/?f=786c5e99cc929e3bef0f3a87bac8ebb07e2c8461](http://www.alsa-project.org/db/?f=786c5e99cc929e3bef0f3a87bac8ebb07e2c8461)

Here it is, I installed hdajackretask, how can I identify correct pin for the override?

---

### Post by Yellow Pasque on 2016-05-04
You'll have to figure it out through experimentation. (Sorry, I know that's not very helpful.)

Perhaps this bug report will help you. It's also an Asus laptop with a headphone and S/PDIF combo jack: [https://bugzilla.kernel.org/show_bug.cgi?id=106771](https://bugzilla.kernel.org/show_bug.cgi?id=106771)

---

### Post by Jack Harper on 2016-05-04
> **Temüjin said:**
> You'll have to figure it out through experimentation. (Sorry, I know that's not very helpful.)

Perhaps this bug report will help you. It's also an Asus laptop with a headphone and S/PDIF combo jack: [https://bugzilla.kernel.org/show_bug.cgi?id=106771](https://bugzilla.kernel.org/show_bug.cgi?id=106771)

I will check it out thanks. Will see what I can do with that program and hopefully fix this. Do you think an Alsa upgrade might help?

---

### Post by Yellow Pasque on 2016-05-04
> **Jack Harper said:**
> Do you think an Alsa upgrade might help?

I doubt it. You're running a recent kernel. I didn't see anything in the 4.5.x ALSA changes that would be applicable to this issue: [https://github.com/torvalds/linux/commits/master/sound/pci/hda/patch_realtek.c](https://github.com/torvalds/linux/commits/master/sound/pci/hda/patch_realtek.c)

---

### Post by Jack Harper on 2016-05-04
> **Temüjin said:**
> I doubt it. You're running a recent kernel. I didn't see anything in the 4.5.x ALSA changes that would be applicable to this issue: [https://github.com/torvalds/linux/commits/master/sound/pci/hda/patch_realtek.c](https://github.com/torvalds/linux/commits/master/sound/pci/hda/patch_realtek.c)

I already tried the latest kernel and it didnt change anything, 16.04 LTS does have a slightly older ALSA than the latest version available, 1.0.25 and 1.1.1 is latest.

---

### Post by Yellow Pasque on 2016-05-04
^Yes, but ALSA stopped using their own version number for the kernel space drivers/modules years ago and now they just follow along with the Linux kernel version.
Only the user space tools and libraries still use the ALSA versioning scheme. Since your issue is with the driver not setting up the pins correctly, upgrading ALSA libs/tools will not help.

---

### Post by Jack Harper on 2016-05-04
> **Temüjin said:**
> ^Yes, but ALSA stopped using their own version number for the kernel space drivers/modules years ago and now they just follow along with the Linux kernel version.
Only the user space tools and libraries still use the ALSA versioning scheme. Since your issue is with the driver not setting up the pins correctly, upgrading ALSA libs/tools will not help.

I see, then I will try fixing it with those pins, if not I can hope it will work in 4.6 kernel.

---

### Post by ragnarok4 on 2016-06-17
This may sound crazy but it worked for me plug your headphones into the 3rd audio jack, and select the line-out in the pulse audio volume control. Cheers.

---

### Post by Jack Harper on 2016-07-17
> **ragnarok4 said:**
> This may sound crazy but it worked for me plug your headphones into the 3rd audio jack, and select the line-out in the pulse audio volume control. Cheers.

This "solved" my issue and now headphones work through line out, I guess this is a temporary workaround, thank you for this solution.

---

