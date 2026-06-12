---
title: "Toshiba Satellite-A215 microphone not working"
date: 2016-05-08
forum: Hardware
---

### Post by richard7893 on 2016-05-08
I have Ubuntu 14.04 LTS installed on my Toshiba Satellite-A215 laptop. I don't think Ubuntu can detect the built-in internal microphone. 

When I go to *System Settings > Hardware > Sound **> Input *There is a box that says *Record Sound From *and within the box it says Internal Microphone Built-in Audio (I attached a screenshot of this in the post). 

When I talk the meter does not move though. So I'm not sure if Ubuntu can detect my built-in microphone. Would anyone be able to provide a way to fix this?

---

### Post by Yellow Pasque on 2016-05-09
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by richard7893 on 2016-06-01
Hey [COLOR=#000000]Temüjin,

I finally got around to reading your post and checking out the link you provided. I followed the instructions and at the end of the terminal commands, a link was provided that has info of my Alsa "stuff". Below is the link that was provided after I ran the command you gave in your reply. Would you please take a look at it? Thanks!

[/COLOR]http://www.alsa-project.org/db/?f=83b1f969c0913c4cf6f72eb7c6692d16caed6b96

---

### Post by Yellow Pasque on 2016-06-02
I'm wondering why you have used this line?:
```
snd_hda_intel: model=thinkpad
```

---

### Post by richard7893 on 2016-06-02
I think it is from an earlier attempt to debug. I checked out some youtube videos that had instructions to add stuff using a type of "notepad" on Alsamixer. What do you think I should do next?

---

### Post by X-RED_Tech on 2016-06-04
First of all, are you sure the mic still works? How have you determined that?
It's a 8-9 years old machine so, yeah, anything can break at any moment...

There's no point in troubleshooting software/OS when faulty hardware is the culprit.

---

### Post by Yellow Pasque on 2016-06-04
I don't see any red flags from your info, but I certainly won't claim to be an expert on the more technical details. My suggestion to you would be to eliminate the model=thinkpad line in /etc/modprobe.d/alsa-base.conf and try the latest kernel module/driver code:
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

Unfortunately, it looks like the PPA is having a bit of trouble at the moment, but the owner is a Canonical employee and is usually good about fixing it from what I've seen.

Alternatively, you may want to try out a LiveUSB of 16.04 if it's not too much trouble.

---

### Post by richard7893 on 2016-06-06
The mic worked when I had Windows Vista installed, but yeah that was a while back. When I erased Vista and put Ubuntu, everything is working except mic though.

Ugh, not working still. You think the only option is installing 16.04? I don't see any reason the mic wouldn't be functional

---

### Post by Yellow Pasque on 2016-06-06
> **richard7893 said:**
> Ugh, not working still.

So you tried the ALSA dkms update I suggested?

> You think the only option is installing 16.04?

No. I just mentioned the Live media as an alternative way to try out the latest kernel sound code.

---

### Post by X-RED_Tech on 2016-06-06
> **Temüjin said:**
> I just mentioned the Live media as an alternative way to try out the latest kernel sound code.

... and as a nice way of troubleshooting:
If the mic works in the live session then you need to go to the bottom of the problem in your installed Ubuntu. Perhaps a fresh install of what works is quicker ;)
If not then it's probably defective. Unfortunately there's no live version of Windows just to be sure. However, if you have done all your backups and you have some Windows installation media I would give it a try anyway, just to be sure. At the end of the day if you find out it still works in Windows then yours is a very rare sound chip or non-standard implementation that only works 100% with Windows drivers. Very unlikely considering the age of the hardware but I'm not the expert, Temüjin is and he already commented he couldn't find anything unusual in your outputs so...

---

### Post by hey2 on 2016-06-06
> **richard7893 said:**
> I have Ubuntu 14.04 LTS installed on my Toshiba Satellite-A215 laptop. I don't think Ubuntu can detect the built-in internal microphone. 

When I go to *System Settings > Hardware > Sound **> Input *There is a box that says *Record Sound From *and within the box it says Internal Microphone Built-in Audio (I attached a screenshot of this in the post). 

When I talk the meter does not move though. So I'm not sure if Ubuntu can detect my built-in microphone. Would anyone be able to provide a way to fix this?

Hi.

Sorry to ask you this, but could you tell me if your shortcut key to decrease the brightness (fn+f6) works?

Thanks.

---

### Post by richard7893 on 2016-06-06
hey2, 

yea my shortcut key works for decreasing/increasing brightness

[COLOR=#000000]Temüjin & [/COLOR][COLOR=#000000]X-RED_Tech[/COLOR][COLOR=#000000],

I have tried the update and followed the instructions carefully for the dkms update. Pretty sure I did it right but the mic still didn't work.

I think I know what you mean with the LiveUSB. I did use a USB to install this version of Ubuntu onto my labtop. I guess I need to run the 16.04 on my USB, see if the mic works, and potentially install 16.04 if the mic indeed does work with 16.04 USB version.[/COLOR]

---

### Post by Yellow Pasque on 2016-06-07
> If not then it's probably defective.

Or it could be a bug that never got solved. Here's an old report from an A215 with the same ALC268 codec: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1081353](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1081353)

richard, if you've tried the dkms code, I would file a bug at this point. Make sure you mention that you've tried the ALSA dkms update and maybe copy/paste the link to the old bug report to show another system with the same PCI ID exhibiting the same symptom.
```
sudo apt-get install apport-gtk apport-symptoms      #these are probably installed already, just making sure
ubuntu-bug audio
```

If you don't get a good response on Launchpad, then you can try the Linux kernel's bugzilla.

---

### Post by richard7893 on 2016-06-11
OK. I reported the bug, hopefully I did it correctly. Here's the link to the report:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1591535](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1591535)

---

