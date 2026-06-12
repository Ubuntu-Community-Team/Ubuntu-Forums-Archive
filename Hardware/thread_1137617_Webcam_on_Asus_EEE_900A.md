---
title: "Webcam on Asus EEE 900A"
date: 2009-04-25
forum: Hardware
---

### Post by beastrace91 on 2009-04-25
I recently brought into my possession an Asus EEE 900A model. Ubuntu runs well on it, but it does not see the webcam. I tried Cheese Webcam booth and a couple other webcam apps and none of them can see it. Anyone have any idea how I can go about getting Ubuntu to detect the webcam?

Thanks,
~Jeff

---

### Post by blackened on 2009-04-25
Your best bet is eee-control. If it's in the Easy Peasy repos, then

```
sudo apt-get install eee-control
```

else debs are available from here: [http://greg.geekmind.org/eee-control/deb/]("http://greg.geekmind.org/eee-control/deb/").

It appears a newer deb for Jaunty is also available there. I'll have to give it a spin.

---

### Post by beastrace91 on 2009-04-25
I have eee-control installed :/ Any other ideas? EasyPeasy is basically 8.10 with a few tweaks/an over lay for an application launcher. Do you see better support/performance on ur EEE with Jaunty?

~Jeeff

---

### Post by blackened on 2009-04-25
> **beastrace91 said:**
> ...Do you see better support/performance on ur EEE with Jaunty?...

Well, most of the acpi functions that Easy Peasy and EEEbuntu were created for are now part of the generic kernel modules, so, ideally, you could have all of what you have now if you used Jaunty's Netbook Remix.

I used EEEbuntu 2.0 for quite a while before switching to Jaunty, and the latter seems to be the faster of the two by a significant margin, though I don't use the netbook interface on Jaunty but did on EEEbuntu. Ext4 vs ext3 could also account for the speed increase.

As per the webcam, eee-control is the only application that has been able to properly control all the built-in peripherals on my 900, but since you're on a 1000 series this may not hold true. Unfortunately, I'm fresh out of suggestions.

---

### Post by Ripp_Steakface on 2009-04-26
Is it just me or is eee-control not available right now? It won't download/install for me when using apt-get.

---

### Post by blackened on 2009-04-26
> **Ripp_Steakface said:**
> Is it just me or is eee-control not available right now? It won't download/install for me when using apt-get.

If you're using Hardy or Intrepid, then it should be available in the repos, but, because of the update to Python 2.6, there is no compatible version available in Jaunty.

All that said, the guy who apparently develops eee-control has a version on his site that is supposed to be compatible. [http://greg.geekmind.org/eee-control/deb/]("http://greg.geekmind.org/eee-control/deb/")

I'm using version 0.8.3 with modifications made to /usr/bin/eee-control-tray and /usr/bin/eee-control-daemon (as described in post #177 from [http://forum.eeeuser.com/viewtopic.php?id=60919&p=8]("http://forum.eeeuser.com/viewtopic.php?id=60919&p=8")) so that it can properly see and use the earlier version of Python.

---

### Post by emilluca on 2009-05-15
Rather then start a new thread I will tag along with this one. I also can  not get the webcam to work on my 900a.  I have eee-control for jaunty installed.  eee-control shows a checkmark for camera.  I also did the latest bios upgrade and there is no camera control in bios.
I do not use the camera but would like it available if possible.
I switched to the ubuntu 9.x remix for the wireless security I need to connect to work access points.  The default Linux did not allow this.

Emil

---

### Post by beastrace91 on 2009-05-15
Lmao, well your going to feel as dumb as I did. Look @ the booklet for the 900A there isn't a webcam in this model ;)

~Jeff

---

### Post by kamaji792 on 2009-05-16
> **beastrace91 said:**
> Lmao, well your going to feel as dumb as I did. Look @ the booklet for the 900A there isn't a webcam in this model ;)

Interesting...  My 900A has got a web-cam on it.  Look above the screen there is a silver rectangle with one big black circle in the middle (the camera) and a small one to the right (LED to tell you when the camera is being used).

With the netbook remix on it it don't work but it did with the original distro.  Not tried to get it work though.

ATB

---

### Post by beastrace91 on 2009-05-16
@kamaji are you sure its a 900A you have? Mine has the rectangle for the webcam but there is just a plastic piece over it - no actual web cam.

~Jeff

---

### Post by ayrfan on 2009-05-21
Iv'e got a eepc 900a and webcam works ok, did you check BIOS as I think it's disabled by default look under advanced=>onboard devices config

---

### Post by beastrace91 on 2009-05-21
Strange I guess my little guy is the odd one out then. I poked through most of my Bios and did not find a webcam setting anywhere.

~Jeff

---

### Post by jim.hatley.tech on 2009-05-28
Hi all,

I've just installed my 900a, and am having the same webcam issue. it was working with the lame version of Xandros that was on here before.Any suggestions?

---

### Post by beastrace91 on 2009-05-28
Are you using NBR or just 9.04 32bit? At anyrate I would try installing [EEE Control](http://greg.geekmind.org/eee-control/deb/) and see if it helps.

~Jeff

---

### Post by todoleo on 2009-05-30
I'm in the same boat. My EEE PC 900a was delivered this morning. The webcam worked fine with Xandros but is not recognised in UNR 9.04. Everything else is just fine.

Will have a lok on Launchpad and do some googling now.

I'll let you know if and what I find.

---

### Post by todoleo on 2009-05-30
Ok! Webcam up and running well on EEE PC 900A with UNR 9.04 both in Cheese and Skype. 

I installed EEE Control from a .deb I downloaded from [here]("http://greg.geekmind.org/eee-control/deb/"). I then turned the programme on from [System Tools] and left clicked on the icon on the status tray. From there I ticked the box with webcam and all was magically working.

I extend my thanks to the team that run EEE Control. Top work lads!

---

### Post by beastrace91 on 2009-05-30
Yea eee-control is a wonderful gadget, I am unsure as to why it was removed from the Jaunty repositories...

~Jeff

---

### Post by 00parrys on 2009-06-18
Hi Guys,

I have the same problem on the ubuntu 9.04 netbook remix. I have done all of the above steps (ie downloaded eee-control and made sure the camera was on in the bios) and have not been able to get the webcam to work on cheese. I cannot get the mic to work either. Any other advice on how to get them to work?

Thanks,

00parrys

---

