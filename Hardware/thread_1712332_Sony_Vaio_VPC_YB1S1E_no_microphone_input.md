---
title: "Sony Vaio VPC YB1S1E no microphone input"
date: 2011-03-22
forum: Hardware
---

### Post by jandac2011 on 2011-03-22
This Sony model in Y series has an AMD Processor, not an Intel i3 as in YA models. The laptop almost works. I had to fix:
[LIST=1]
[*]screen resolution -- by downloading a driver from [www.amd.com](www.amd.com).
[*]touchpad -- by setting:```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.reset i8042.nomux i8042.nopnp i8042.noloop"
```
in /etc/default/grub. This solution is only partial, as scrolling works only downwards, and the touchpad is not recognized by KDE in the Control Panel.
[*]sound from speakers -- using HDA-Analyzer, I can set VREF in Node[0x19] PIN to either HIZ or GRD (both work). I can probably use  hda-verb to set the parameter during boot.
[/LIST]

I still cannot make the microphone work, either the built-in, or an external one. Unlocking channels and setting one of them to zero does not work. HDA-Analyzer may help, but so far I could not find the right parameter to change to the right value. I think it would be useful to have a script that either systematically, or if the search space is too big - randomly, changes the parameters visible in HDA-Analyzer, records a few seconds of sound (in case of debugging speakers asks the user whether s/he heard anything), checks whether the recorded sound is silence (small size of the file) or not.

Just for the record, all sliders are at max, nothing is muted, recording box checked. The output from alsa-info script is at:
[http://www.alsa-project.org/db/?f=6e8f629e0b5fffac8434e7b452e726775b515f19]("http://www.alsa-project.org/db/?f=6e8f629e0b5fffac8434e7b452e726775b515f19")

What should I do next?

---

### Post by jandac2011 on 2011-03-22
> **jandac2011 said:**
> This Sony model in Y series has an AMD Processor, not an Intel i3 as in YA models. The laptop almost works. I had to fix:
[LIST=1]
[*]screen resolution -- by downloading a driver from [www.amd.com](www.amd.com).
[*]touchpad -- by setting:```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.reset i8042.nomux i8042.nopnp i8042.noloop"
```
in /etc/default/grub. This solution is only partial, as scrolling works only downwards, and the touchpad is not recognized by KDE in the Control Panel.
[*]sound from speakers -- using HDA-Analyzer, I can set VREF in Node[0x19] PIN to either HIZ or GRD (both work). I can probably use  hda-verb to set the parameter during boot.
[/LIST]

I still cannot make the microphone work, either the built-in, or an external one. Unlocking channels and setting one of them to zero does not work. HDA-Analyzer may help, but so far I could not find the right parameter to change to the right value. I think it would be useful to have a script that either systematically, or if the search space is too big - randomly, changes the parameters visible in HDA-Analyzer, records a few seconds of sound (in case of debugging speakers asks the user whether s/he heard anything), checks whether the recorded sound is silence (small size of the file) or not.

Just for the record, all sliders are at max, nothing is muted, recording box checked. The output from alsa-info script is at:
[http://www.alsa-project.org/db/?f=6e8f629e0b5fffac8434e7b452e726775b515f19]("http://www.alsa-project.org/db/?f=6e8f629e0b5fffac8434e7b452e726775b515f19")

What should I do next?
The internal (front) microphone still doesn't work, but the external one can be enabled by unmuting Val0 in Node[0x23] AUD_MIX in HDA-Analyzer.

---

### Post by jandac2011 on 2011-03-30
> **jandac2011 said:**
> The internal (front) microphone still doesn't work, but the external one can be enabled by unmuting Val0 in Node[0x23] AUD_MIX in HDA-Analyzer.
I tried every single parameter in HDA-Analyzer. No change to any single parameter enables the built-in microphone, at least those settable by HDA-Analyzer. Perhaps they should be set in groups.

---

### Post by puller on 2011-04-01
I have a VAIO VPCSB (new S series) with 11.04 and I am not able to make the mic working too.
This seems a regression for ALC275 which was known to work with 2.6.36 (I have 2.6.38.7).

---

### Post by lidex on 2011-04-03
@jandac2011
It appears your hdmi device is default despite your /etc/asound.conf. Go ahead and remove that. Now try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**

---

### Post by jandac2011 on 2011-04-10
> **lidex said:**
> @jandac2011
It appears your hdmi device is default despite your /etc/asound.conf. Go ahead and remove that. Now try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Sorry for such a late answer. I thought nobody will ever add anything here.
I did what you wanted, but I get:
```
jandac@javaio:~$ sudo apt-get install linux-alsa-driver-modules-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-alsa-driver-modules-2.6.32-30-generic
```
This is for the last command. The first two executed without any error messages.

---

### Post by lidex on 2011-04-11
> **jandac2011 said:**
> Sorry for such a late answer. I thought nobody will ever add anything here.
I did what you wanted, but I get:
```
jandac@javaio:~$ sudo apt-get install linux-alsa-driver-modules-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-alsa-driver-modules-2.6.32-30-generic
```
This is for the last command. The first two executed without any error messages.

There's no package in there yet for that kernel. 2.6.32-29 is available. If you still have that one installed, boot into it from grub and run that command again then reboot back into same and check mic. If it works just continue using that kernel or upgrade your alsa install via the link in my sig.

---

### Post by jandac2011 on 2011-04-11
> **lidex said:**
> There's no package in there yet for that kernel. 2.6.32-29 is available. If you still have that one installed, boot into it from grub and run that command again then reboot back into same and check mic. If it works just continue using that kernel or upgrade your alsa install via the link in my sig.
It works. Not only does it enable my built-in microphone, but it unmutes the speakers without the necessity of running HDA-Analyzer each time I boot. The only possible problem is that KDE/phonon complains about some missing output devices, and indeed the HD-Audio Generic, ATI HDMI (HDMI Audio Output) line is grayed out.

---

