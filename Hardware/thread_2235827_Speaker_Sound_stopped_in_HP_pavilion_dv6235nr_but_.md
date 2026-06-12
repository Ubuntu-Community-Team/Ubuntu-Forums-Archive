---
title: "Speaker Sound stopped in HP pavilion dv6235nr but headphone works"
date: 2014-07-23
forum: Hardware
---

### Post by Dragoncool on 2014-07-23
Hello!

I hope that someone can help me here, because this problem is making me crazy. :(
So, the sound in my laptop was working fine, but one day I just closed the lid and when I opened it again, there were no sound on the speaker anymore. 
But, If i plug a earphone, then works.

I tried a lot of options that I found in the internet, but nothing worked.
The last attempt was to install the new alsa version (1.0.25), but after ran the .deb file without any error, I'm still running the 1.0.24 version even after rebooting.
This is the link for the info from alsainfo.
**[http://www.alsa-project.org/db/?f=ef7e29aa54b2977a0870a6818a7e8357397ae677](http://www.alsa-project.org/db/?f=ef7e29aa54b2977a0870a6818a7e8357397ae677)**

Any help will be much appreciated!

Cheers,
Joao

---

### Post by Dragoncool on 2014-07-23
Hi.

Just a quick update.
I was able to update the ALSA driver to 1.0.25, but now, there are no sound at all... :(

This is the new info:
[http://www.alsa-project.org/db/?f=37c2caed598a348784b54ef6cd4c0928e957be26](http://www.alsa-project.org/db/?f=37c2caed598a348784b54ef6cd4c0928e957be26)


Cheers,
Joao

---

### Post by Dragoncool on 2014-07-23
Ok, 

I was able to update the kernel and now the sound is recognized, but still there is no sound via speakers, only via earphones...
Here is the new alsa info:
[http://www.alsa-project.org/db/?f=f482038b0e699356aef1f3d2806ca3f7904a4f86](http://www.alsa-project.org/db/?f=f482038b0e699356aef1f3d2806ca3f7904a4f86)

Any suggestions?

Cheers,
joao

---

### Post by Yellow Pasque on 2014-07-23
Try latest driver. First:
```
sudo apt-get install dkms
```
Next, install this .deb [https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201407221524%7Eubuntu12.04.1_all.deb](https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201407221524%7Eubuntu12.04.1_all.deb)

---

### Post by Dragoncool on 2014-07-23
Hi,

Thanks a lot for the reply.
So, the dkms is already up-to-date
Then, I tried to install the deb file, but in the end is showing this:
> ------------------------------
Deleting module version: 0.201407221524~ubuntu12.04.1
completely from the DKMS tree.
------------------------------
Done.
Unpacking replacement oem-audio-hda-daily-dkms ...
Setting up oem-audio-hda-daily-dkms (0.201407221524~ubuntu12.04.1) ...
Loading new oem-audio-hda-daily-0.201407221524~ubuntu12.04.1 DKMS files...
First Installation: checking all kernels...
Building only for 3.8.0-35-generic
Building for architecture i686
Building initial module for 3.8.0-35-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
Done.


Probably because I updated my kernel to 3.8?

Cheers,
Joao

---

### Post by Yellow Pasque on 2014-07-23
Yes, you need the lts-raring version for kernel 3.8.x
[https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily](https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily)

---

### Post by Dragoncool on 2014-07-23
Hi,

Thanks a lot for the reply.
So, the dkms is already up-to-date
Then, I tried to install the deb file, but in the end is showing this:
> ------------------------------
Deleting module version: 0.201407221524~ubuntu12.04.1
completely from the DKMS tree.
------------------------------
Done.
Unpacking replacement oem-audio-hda-daily-dkms ...
Setting up oem-audio-hda-daily-dkms (0.201407221524~ubuntu12.04.1) ...
Loading new oem-audio-hda-daily-0.201407221524~ubuntu12.04.1 DKMS files...
First Installation: checking all kernels...
Building only for 3.8.0-35-generic
Building for architecture i686
Building initial module for 3.8.0-35-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
Done.


Probably because I updated my kernel to 3.8?


Cheers,
Joao

---

### Post by Dragoncool on 2014-07-23
hello,

So, I got another file this time: oem-audio-hda-daily-lts-raring-dkms_0.201407221523~ubuntu12.04.1_all 

And now I was able to install it, but still no sound.
Here is the new info:
[http://www.alsa-project.org/db/?f=b29ed7a9695da8e7bfcf4a59b4038a608d47d51a](http://www.alsa-project.org/db/?f=b29ed7a9695da8e7bfcf4a59b4038a608d47d51a)

I also checked alsamixer and everything is in MAX and nothing is in mute. And the auto-mute is OFF.
I also tried all the options in the pulseaudio and so far nothing is doing noise. Neither a single beep. :)

Cheers,
Joao

---

### Post by Yellow Pasque on 2014-07-23
You should remove this line from /etc/modprobe.d/alsa-base.conf:
```
options snd-hda-intel model=generic
```

Then, reboot or reload alsa
```
sudo alsa force-reload
```

---

### Post by Dragoncool on 2014-07-24
Hi temüjin,

Ok, I remove it and restarted alsa.
Unfortunately there is no sound.
Here is the new info:
[http://www.alsa-project.org/db/?f=905ef5d0f0c8accb439407f0054aaf68889f0039](http://www.alsa-project.org/db/?f=905ef5d0f0c8accb439407f0054aaf68889f0039)

Under this section
!!Loaded sound module options
!!---------------------------

Its appears to me that is something is wrong, because everything is -1 or null. Is this normal?

Looking in the internet, maybe the problem is the Hardware, but I'm not sure yet. Is there any info in the logs that shows that something is still wrong? 

Cheers,
Joao

---

### Post by Yellow Pasque on 2014-07-24
I would try a LiveUSB of Ubuntu 14.04 to verify this occurs with clean, updated install. If it still does not work, file a bug (with the LiveUSB).

> because everything is -1 or null. Is this normal?
Yes.

---

