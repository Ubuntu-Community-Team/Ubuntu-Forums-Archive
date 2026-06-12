---
title: "Laptop won't wake up"
date: 2012-07-08
forum: Hardware
---

### Post by andrewcole50 on 2012-07-08
Hello, I'm running 12.04 on my Alienware M14x R1 and whenever I close the screen and open it again all that greets me is a black screen with my mouse. I don't even know where to start to try and fix this.

---

### Post by Redblade20XX on 2012-07-08
Most likely its a graphics driver problem. Do you know what graphics card you have?

Post the result of :
```
lspci | grep VGA
```

- Red

---

### Post by andrewcole50 on 2012-07-09
Yes, it's a Nvidia GT 555M with *shudder* Optimus technology.

```
cole@cole:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF106 [GeForce GT 555M] (rev ff)

```

The thing is that it's worked just fine for the three weeks I've been using Ubuntu.

---

### Post by typhoon_tip on 2012-07-09
Did you install bumblebee ?

[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by andrewcole50 on 2012-07-09
Yes I do. I've actually been having graphics problems and I tried to get it fixed but I've kind of given up on it. Here's my other thread regarding my graphics problems
[http://ubuntuforums.org/showthread.php?t=2012264]("http://ubuntuforums.org/showthread.php?t=2012264")

---

### Post by Redblade20XX on 2012-07-09
> **andrewcole50 said:**
> Yes I do. I've actually been having graphics problems and I tried to get it fixed but I've kind of given up on it. Here's my other thread regarding my graphics problems
[http://ubuntuforums.org/showthread.php?t=2012264](http://ubuntuforums.org/showthread.php?t=2012264)

Did you file a report with the Bumblebee project?

Seems like some coding needs to be done.

As an alternative, does your BIOS give you the option to shut off the discrete card until the Bumblebee project fixes your graphics problem?

You should be able know whether or not the suspend problem is truly a Bumblebee problem or something else.

- Red

---

### Post by andrewcole50 on 2012-07-09
I think I'm going to remove bumblebee when I get home from work and see if it's a bumblebee issue. Without bb I can use the discrete card no problem but I can't access the Nvidia one. Do I post my issue here?
[https://github.com/Bumblebee-Project/Bumblebee/issues]("https://github.com/Bumblebee-Project/Bumblebee/issues")

---

### Post by Redblade20XX on 2012-07-09
> **andrewcole50 said:**
> I think I'm going to remove bumblebee when I get home from work and see if it's a bumblebee issue. Without bb I can use the discrete card no problem but I can't access the Nvidia one. Do I post my issue here?
[https://github.com/Bumblebee-Project/Bumblebee/issues](https://github.com/Bumblebee-Project/Bumblebee/issues)

Yes but first read this.
[https://github.com/Bumblebee-Project/Bumblebee/wiki/Reporting-Issues](https://github.com/Bumblebee-Project/Bumblebee/wiki/Reporting-Issues)

- Red

---

### Post by andrewcole50 on 2012-07-10
Bumblebee was the problem. I'm going to report the bug on their site later tonight. Thanks!

---

