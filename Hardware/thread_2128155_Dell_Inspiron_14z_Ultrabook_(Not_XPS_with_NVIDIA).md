---
title: "Dell Inspiron 14z Ultrabook (Not XPS with NVIDIA)"
date: 2013-03-22
forum: Hardware
---

### Post by Veoden on 2013-03-22
[COLOR=#333333][FONT=Lucida Grande]Hi,[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]I just receive my new notebook a Dell Inspiron 14z (5423) With AMD Readon video and Hibryd hard disk.[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]This notebook cames with windows 8 that a try just for the first discharged ( 4 hours).[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]I Install Ubuntu 12.10 64bits, after dismount the strange raid with gparted and find a workaround about the wired network everything work perfect.[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]But the battery is dead in only 1:30hs. After some search i found that in the most of the cases the problem is the video card I found a workaround with NIVIDIA card but nothing with Readon.[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]I tried to use open driver and proprietary drivers and still nothing.[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Someone could Help me?[/FONT][/COLOR]

---

### Post by cpsully69 on 2013-04-07
Hello Veoden,
I'm sorry I cannot provide any help...I was searching the forums for EXACTLY this same topic.  If you get any response, it would be great if you could share it.  I've googled a lot and can't find a definitive power management guide.

Some say that laptop-mode-tools is obsolete at this point...I've installed it, tweaked some scripts, and the scipts seem ineffective (ie. turning bluetooth off, cpu scaling, turning off eth0, turing off external video, etc.)

I've make sure that i8k is in the kernel modules (apparently this operates the Dell CPU/GPU fans, etc.)

Running powertop, I've switched the "bad" to "good" under tunables, and still drawing ~27W of power (1:30 battery life)

I'm also not sure if pm-utils is the answer, and there's some scripts there that do things once it detected the AC->battery switch (like CPU scaling, display brightness, and other power save modes).

My lspci shows two video controllers...the Intel (HD4000 according to the specs), and the ATI Radeon 7500M/7600M.  I haven't tried the proprietary drivers yet, as I assumed the Intel was driving my laptop LCD, and I wasn't really using the ATI except if I connected an external screen via HDMI? Or maybe I have that backwards?

I don't mean to hijack your post, but I was hoping I could add some more detail and see if other folks had similar problems and found the answer  (maybe a different distro?)

---

### Post by Veoden on 2013-04-07
Hi cpsully69,

I kind found a workaround.
Follow this [http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450) you will solve half of problem. 
Do not use the video driver that came with Ubuntu and nither in the proprietary drivers configuration.
Use the drivers that is the link i above.
I said that solve half of problem cause the heat and power issue is related to that video driver, but using this link you can use only the Radeon 7500 mode, (2:30 Hs battery) but if you try to but with the Intel mode (4:00Hs battery) the second time you boot the system freezy during the boot.

So the heat problem is solved in both mode, the change for the two modes (Ati vs Intel) still do not, the time of battery is worst that Windows.

I think i can live with this until appropriate driver are made.

---

### Post by cpsully69 on 2013-04-08
Wow! Pretty extensive post/how-to!  Thank you....I would have NEVER found that!  I will give it a try and reply back here.  Thanks for your help!

---

### Post by leizzer on 2013-06-17
[B]EDIT:
[/B]I was on a hurry and didn't test it very well.

Now I think my HDMI cable is broken.
[B]
Old-post:[/B][I]
Hello, Veoden

Have you tried the pc with HDMI? I just tried to use my Dell 14z (Ubuntu 13) with a monitor but It doesn't detect the external display.[/I]

---

