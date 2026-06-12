---
title: "amd drivers"
date: 2013-10-02
forum: Hardware
---

### Post by DominikCZE on 2013-10-02
Hi,
I've been experiencing some random computer freezes in ubuntu which force me to hard reset my laptop. Most often it happens when I click on Dash Home, so I think that it might have something to do with Unity messing up due to the lack of proprietary drivers for my graphics card. Another (minor) issue is the inability to launch Steam. 

Well, I tried to install CCC 13.x for Linux and the installer wouldn't let me install anything except ccc, the driver itself was greyed out. After some trial and error, I ended up following the advice given here: [http://askubuntu.com/questions/98827/ati-driver-re-install-fail](http://askubuntu.com/questions/98827/ati-driver-re-install-fail). Apparently, I already had something installed, even though it didn't show on the additional drivers list, but it didn't help anyway, I still wasn't able to install the driver. 

I ended up doing some more searching and came across this site: [http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware)
From the looks of it, my card isn't even supported (7970M on a Clevo laptop), is there anything I can do to get the drivers properly installed?

I'm on 12.04 LTS.

Thanks for any help.

P.S. I'm not sure I put this in the correct section, as it's more of a software issue, but I didn't find a more appropriate place for this.

---

### Post by x10n2 on 2013-10-02
AMD's Catalyst drivers are pretty dodgy on Ubuntu. They have serious input latency issues with Source engine games (CS:S. Half Life 2, L4D2 etc). It would probably be better to stick to a windows partition for gaming.

---

### Post by Yellow Pasque on 2013-10-02
> 7970M on a Clevo laptop

Hybrid graphics? (Show output of lspci if not sure):
```
sudo update-pciids
lspci | grep VGA
```

---

### Post by DominikCZE on 2013-10-03
@x10n2: Yeah, I game on Windows, that's not much of an issue. It's just that I had a theory that ubuntu might be freezing from time to time due to the absence of amd drivers.

@Temutin: I have an integrated Intel HD 4000 and Catalyst should be taking care of switching between GPUs, I think.

Here is the output:

00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 6800

---

### Post by DominikCZE on 2013-10-05
bump from 3rd page

---

### Post by Yellow Pasque on 2013-10-05
Check the Intel/ATI hybrid graphics thread: [http://ubuntuforums.org/showthread.php?t=1930450&p=12755069#post12755069](http://ubuntuforums.org/showthread.php?t=1930450&p=12755069#post12755069)

---

