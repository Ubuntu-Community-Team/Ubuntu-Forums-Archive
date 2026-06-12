---
title: "Headphone &quot;Jack Sense&quot; Issues On HP dv9000"
date: 2007-07-27
forum: Hardware &amp; Laptops
---

### Post by Walkboss on 2007-07-27
Hi. After weeks of Googling, compiling alsa from source, giving up, trying again, giving up, trying again, I've finally decided to make a new thread hoping and praying for a solution.

Basically my problem is that any sound that comes from plugged in headphones still comes out the onboard speakers. I have no headphone slider in Volume Control or alsamixer.

My chip, according to alsamixer, is a CONEXANT CX20549 (Venice), which I realize have been giving people trouble as Conexant refuses to release specifications.

I understand that there is some sort of patch or something released by Tobin Davis (evidenced here: [http://ubuntuforums.org/showthread.php?t=382645](http://ubuntuforums.org/showthread.php?t=382645)). I've tried applying this patch with no reward but a completely broken sound system. I've fixed my broken sound by installing alsa 1.0.14 from source with no patch, but the jack sense problem persists.

Sorry for the jumbled mess. I hope someone can make sense of all this and help me solve this once and for all.

Thank you for your time!

---

### Post by Walkboss on 2007-07-28
Good morning bump.

Please help! :(

---

### Post by EXCiD3 on 2007-07-28
You are using Feisty right, my dv9000t has perfect headphone detection.

---

### Post by Walkboss on 2007-07-28
Feisty, yes.

I'm seeing no one else has these troubles and I'm losing hope.

I am trying to think of a way to somehow just disable the onboard speakers without ripping the laptop open.

I almost think it's an issue with my jacks themselves as they don't work at all in Vista. Is there any possible way to just disable the onboard speakers altogether?

---

### Post by EXCiD3 on 2007-07-28
I don't know, but you should try contacting HP Support if it isnt working in Vista either.

---

### Post by Walkboss on 2007-07-28
Tried that. They gave me the old "reinstall driver" then when that didn't work "reinstall OS."

Tried both. No dice. 

I'm thinking of bringing it into CC for a looksie while my warranty is still valid. Thanks for your help nonetheless.

---

### Post by EXCiD3 on 2007-07-28
Yeah, sorry, but it appears that your headphones jacks are broken. Hopefully you can get 'em fixed.

---

### Post by Crenfinkle on 2007-08-13
I am having the same issue with the headphone jack on my compaq c501, and doing the same thing: Recompiling, reinstalling, applying patches, giving up, over and over again. I have the same chip, but I don't think there's anything wrong with the jack, because I'm getting sound through the headphones. I can't say that the jack worked fine under Vista because I trashed Vista when I bought the laptop :)

---

### Post by flightless bird on 2007-10-23
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+source/gnome-media/+question/15345](https://answers.launchpad.net/ubuntu/+source/gnome-media/+question/15345) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm having exactly the same issues with gutsy on a new HP G5056EA.

---

