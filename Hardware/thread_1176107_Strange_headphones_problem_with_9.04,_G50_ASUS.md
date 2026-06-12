---
title: "Strange headphones problem with 9.04, G50 ASUS"
date: 2009-06-02
forum: Hardware
---

### Post by Xorlium on 2009-06-02
Hi,

I recently upgraded from 8.10 to 9.04 in my G50 laptop, 2.4 Ghz, Nvidia 9800M, and now when I connect headphones, if I plug them in completely, I can't hear anything (either on the headphones or on the computer itself). If I plug them in but stop at the middle, I can hear sound on the headphones (and also on the speaker). There's a hard to find sweet spot for this.

It worked on 8.10.

I thought it was a hardware problem, unrelated to my installation of 9.04, but I tested it on windows vista and it works fine.

I wouldn't even know what keywords to search for...

Well, if anybody has any idea, thanks!
Xorlium

---

### Post by Xorlium on 2009-06-06
bump

---

### Post by Xorlium on 2009-06-11
bump... anybody? Isn't it an interesting problem? Headphones work on Vista, but not Ubuntu... what could be going on?

I'm kind of a newb (maybe intermediate) and I wouldn't even know what to test now (I tried different headphones, and it's always the same)...

In Vista, when I connect the headphones, a message pops up: "You have connected a device into the headphone slot" or something like that... Is there some way to see if ubuntu has detected it? I mean, other than sound turning off?

Thanks.
Xorlium

---

### Post by weremichael on 2009-06-14
I'm having the same problem on my G50vt. I've tried the directions on this [site]("http://www.linlap.com/wiki/asus+g50v#sound") without any luck. I look forward to this solution.

---

### Post by nyroshan on 2009-07-29
anyone figure out anything yet?

---

### Post by jkl12345 on 2009-08-06
Just wanted to add my voice to the chorus.  Identical problem as the rest, but none of the advice out there seems to work...

---

### Post by des.matthewman on 2009-08-07
This is happening to me too, Dell Precision 690 running 9.04 

:(

Can anyone help us?

---

### Post by linkxs on 2009-08-23
yup, me too. i use ubuntu though. i did try that solution, didn't work. posted a thread about this too, noone responded. yet. ehh.

---

### Post by linkxs on 2009-08-23
hey guys, i found this:

[http://vip.asus.com/forum/view.aspx?board_id=3&model=G50V&id=20090605033929721&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?board_id=3&model=G50V&id=20090605033929721&page=1&SLanguage=en-us)

which links to this:

[http://monalisa.cern.ch/blog/2008/09/16/ubuntu-on-asus-g50v/](http://monalisa.cern.ch/blog/2008/09/16/ubuntu-on-asus-g50v/)

i read through the whole thing yesterday trying to find the sound part, but didn't. I'm gonna go ahead and try again right now..

---

### Post by Xorlium on 2009-09-06
I finally made it work!!

I just found this:
[http://forum.notebookreview.com/showthread.php?t=394692&page=2](http://forum.notebookreview.com/showthread.php?t=394692&page=2)

thanks!

---

### Post by linkxs on 2010-05-04
I seemed to have fixed it in 9.04 and 9.10, now did a clean 10.04 install and have this problem again. Anyone got a solution? 

Also the I can't get the internal mic to work.

---

### Post by AndrewGarib on 2010-06-09
Similar problem with the Asus K52JR. Headphones plug in and sound comes out of them, but unlike in Win7, the laptop speakers don't get muted. Running Kubuntu 10.04 with 2.6.32-22.36 kernel. 

Suggestions?

---

### Post by lidex on 2010-06-09
Try updating your alsa install to 1.0.23 via the upgrade link in my sig. Make sure to uninstall alsa-backports, if installed, first and reboot.

---

### Post by AndrewGarib on 2010-06-10
> **lidex said:**
> Try updating your alsa install to 1.0.23 via the upgrade link in my sig. Make sure to uninstall alsa-backports, if installed, first and reboot.

No offense, but I really don't trust that. I'd be going from 1.0.22 to 1.0.23, so it sounds like it's worth waiting for the upgrade that will come with Kubuntu.

Maybe 1.0.23 comes with openSUSE 11.3? If so, I'll just wait a few weeks for that. That would be even better.

Lidex, how do you know that the upgrade will solve my problem? Does the ALSA project specifically mention my hardware?

---

