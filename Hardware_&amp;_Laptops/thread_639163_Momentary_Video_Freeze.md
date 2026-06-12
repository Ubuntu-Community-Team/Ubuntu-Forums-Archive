---
title: "Momentary Video Freeze"
date: 2007-12-12
forum: Hardware &amp; Laptops
---

### Post by sowelie on 2007-12-12
I am having an issue that is really hard to figure out because it's seemingly random.  I have an HP laptop with an nvidia go 6150.  I have the latest restricted drivers installed.  I also have compiz fusion with emerald running.  Every now and then, the video will freeze for 5-10 seconds.  I can still hear audio (music playing, messages coming in through pidgin etc) but the video freezes.  I haven't really been able to link the problem to any one thing, it happens while running any app.  My only thought is that maybe my video processor is getting hot because sometimes when it happens I hear the fan kick into high gear.  Has anyone else experienced this problem?

---

### Post by henriquemaia on 2007-12-13
> **sowelie said:**
> I am having an issue that is really hard to figure out because it's seemingly random.  I have an HP laptop with an nvidia go 6150.  I have the latest restricted drivers installed.  I also have compiz fusion with emerald running.  Every now and then, the video will freeze for 5-10 seconds.  I can still hear audio (music playing, messages coming in through pidgin etc) but the video freezes.  I haven't really been able to link the problem to any one thing, it happens while running any app.  My only thought is that maybe my video processor is getting hot because sometimes when it happens I hear the fan kick into high gear.  Has anyone else experienced this problem?

I have this too. It seems to me that it’s related to Nvidia card. It happens to me when I’m putting a lot of stress on the video card, when playing games, for instance. I have a Compal IFL90 with an Nvidia 8600M GT.

---

### Post by sowelie on 2007-12-18
Anybody have any suggestions?

---

### Post by chewearn on 2007-12-20
Your problem might be related to wrong refresh rate reported by nvidia driver; see this bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/104105](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/104105)

If you don't use Twinview, there was a suggested fix in the bug report that you can try.

If you do use Twinview, then I'm trying a setting in CompizConfig Settings Manager right now; not sure if it will work yet.  The setting is under General Options > Display Settings; disable "Detect Refresh Rate", then manually set the refresh rate using the slider bar to the actual rate (as reported by the monitor).

---

### Post by sowelie on 2007-12-22
Thank you for the suggestion!  This seems to have fixed the problem, I haven't used it for long so it's hard to say.  At least the refresh rate is right now.  Thanks!!

---

### Post by sowelie on 2007-12-30
I still am getting a momentary freeze every now and then :(.  The desktop effects are much smoother though.

---

### Post by sowelie on 2008-01-31
For anyone experiencing this problem, I have an HP laptop with what they call a Geforce Go 6150.  As far as I can tell this is a special HP only video adapter.  Anyway, I don't think nVidia really supports it anymore.  I fixed my issues by going back to an older driver, the one I'm using right now is 100.14.19.

---

### Post by Z_o-s-o on 2008-01-31
I've got the same intermittent pause.

Can you give me some info on what you did?

---

### Post by Z_o-s-o on 2008-02-01
I'll add that right now im using the restricted driver and getting the pauses.

---

### Post by sowelie on 2008-02-06
If you go to NVIDIA's site, select your card model under the driver downloads and then go to archive, which is a link on the left, you can pick an older version.  You may have to try a few to figure out what works best.  The install is really easy, just stop GDM:

```
sudo /etc/init.d/gdm stop
```

Then run the driver you downloaded:

```
sudo /path/to/download/the-driver-you-downloaded.run
```

Keep in mind, this version of the driver builds a custom kernel module.  This means, if your kernel is updated (i.e. in the update manager) you'll probably need to re-install the driver.  So, keep the installer handy.  It may sound scary, but it's not bad at all, the kernel isn't updated all that often anyway.

Also, what card do you have?  I found the reason mine has so many issues is because it's an unsupported adapter as far as NVIDIA is concerned.  It's a custom HP adapter with the NVIDIA logo slapped on it.  To tell you the truth the driver selector doesn't even list my model, so I just went with the six series, since it's a GO 6150.

---

### Post by Z_o-s-o on 2008-02-06
I've got the 6150 as well.  Thats really the only fault I have with Ubuntu at the moment.

---

### Post by sowelie on 2008-02-07
Did the older driver help with your issue?

---

### Post by Z_o-s-o on 2008-02-07
No.

When I went to the older version, X wouldnt start.  So I installed Envy and went with the latest one, and that performed even worse.

---

### Post by sowelie on 2008-02-08
Did you check out the xorg log files when the old driver failed?

---

### Post by Z_o-s-o on 2008-02-08
It was totally unworkable.

I could boot into safe mode and use Vesa to get in, but nothing ran.  So I decided to try Vesa when booting normal, but it kept black screening, same with nv driver.

---

### Post by pietiediemuis on 2008-06-12
dammit, i have this problem too. i have the onboard nvidia 6100 nforce 405 video card... anyone know how to fix this yet?

---

### Post by chewearn on 2008-06-12
> **pietiediemuis said:**
> dammit, i have this problem too. i have the onboard nvidia 6100 nforce 405 video card... anyone know how to fix this yet?

I think the nvidia 61xx integrated graphics are rather stressed when running compiz.  If you don't mind doing without compiz, you might see significant video playback improvement.

.

---

