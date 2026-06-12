---
title: "Can't resume after suspend on eee pc 1000HA, Ubuntu 9.04 Netbook Remix"
date: 2009-04-24
forum: Hardware
---

### Post by smartkenny on 2009-04-24
Hi, all

I installed Ubuntu 9.04 Netbook Remix on my eee pc 1000HA, and everything works perfect exception this one: after suspend by collapse the lid, and open the lid to resume it, it hangs there with a black screen and one line of characters. No key responses. Press any key combinition such as Ctrl_Alt_Del, or Ctrl_Alt_F7 doesn't help at all.

Anybody gives any sugguestions?

Thanks,

Kenny

---

### Post by Gagzilla on 2009-04-26
FWIW I'm getting the same problem with 9.04 on Lenovo X61 tablet. Resume after a suspend returns to a blinking cursor on a blank screen.  No key combinations work. The only difference is that this is an intermittent problem. 

Resume after suspend worked fine in 8.10 on this laptop.

---

### Post by jensjk on 2009-04-28
I have the sam problem on a HP Pavilion DV6000 laptop - worked fine with 8.04 and 8.10, but an update in acpi some time i january caused the problem - hoped it solved after installing 9.04,but the problem persists

---

### Post by jensjk on 2009-04-28
Enabling desktop effects, thereby adding Nvidia restricted drivers, solved my problem

---

### Post by bluevalley on 2009-04-28
> **jensjk said:**
> Enabling desktop effects, thereby adding Nvidia restricted drivers, solved my problem
Could you explain in detail? 
I met the same problem with my Samsung R510 laptop. 
Thanks!

---

### Post by gabepez on 2009-05-04
Hello Everyone, I am having the same problem on eee PC 1000HE.

A few notes regarding what I found so far:

[LIST]
[*]Adjusting brightness via the controls does not do anything
[*]I can see (very faintly) that the display is on, and can even see the brightness adjustment notification window.
[*]Resuming from suspend produces this bug, but resuming from hibernate works properly.
[/LIST]

I am going to take a quick look at the scripts executed on resume, to see if there is an obvious difference, but I am somewhat new to troubleshooting Ubuntu.

If anyone has any hints or suggestions but no time to try, let me know and I will see if I can try them out.

---

### Post by Maringouin on 2009-06-13
I put my Eee PC 901 into 'suspend' this afternoon and when I tried to wake it up (by pressing the power button, which was flashing), the external monitor came on and so did the Eee PC monitor, but the Eee monitor then flashed once and went black. Powering off and restarting does not help, the screen stays black.

The external monitor works fine. The webcam and sound system work fine. All my documents are fine. Internet works fine. Printing is fine.

The only other glitch is that the blue display light for wireless stays on whether wireless is enabled or not.

In addition to having an external monitor, I also have an external keyboard and mouse hooked on via a single USB hub. One tip I found when googling this was to disconnect the USB hub and reboot. This didn't help. It also didn't help when I rebooted with the external monitor disconnected.

I am very much a newbie with Linux and Ubuntu so I don't understand a lot of the code flying around. However, I copied all the logs I could find (messages, debug, user, etc., etc.) into text files and could upload them if anyone thinks that would be useful.

This doesn't seem to be an isolated problem (I've seen other threads raising this issue) but for the moment I can't find an answer I understand.

I suppose that since everything apart from the monitor works, if push comes to shove I could just re-install Ubuntu (it's on a separate drive from my data so presumably I could re-install from the original USB key without losing my data--which is totally backed up anyhow). But it would be nice if I didn't have to do that.

I would appreciate any help. Like I said, I'm a newbie, so please have pity on my ignorance and explain things in easy steps. I'm good at following instructions.

Many thanks.

Edit: additional information--
Fn+F5 works fine to enable/disable the external monitor.
I can remember putting the computer on suspend only once before. At that time I had no problem resuming. The external keyboard-and-mouse USB hub was connected but NOT the external monitor. So maybe that's the starting place to look for a solution.
Thanks again.

---

### Post by sirdan on 2009-06-29
I had the same problem. I followed the suggestion posted by [jensjk]("http://ubuntuforums.org/member.php?u=365931") . Went to:
System->Preferences->Appearance and under the Visual Effects tab, chose "Extra". This workaround worked for me, but still indicates an underlying bug with video and suspend.

---

