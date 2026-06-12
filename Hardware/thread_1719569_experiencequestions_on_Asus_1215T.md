---
title: "experience/questions on Asus 1215T"
date: 2011-04-02
forum: Hardware
---

### Post by VogonZarniwoop on 2011-04-02
I just bought an Asus 1215T - wanted the 1215N, but it seemed like the T  had better linux compatibility so I got that instead.  I just installed  the latest KDE 11.04 64 bit alpha, although I think my questions here  are more or less unrelated to using the alpha version, probably more to  do with HW support for this machine.

Overall my experience has been better than I feared :).  Sleep works,  and i reckon this is the first system I've ever installed Linux on where  the dang thing would come out of sleep mode.  The open source ATI  drivers are working with KWin.  The screen brightness keys work.  I had  to install the proprietary broadcom wireless drivers, but they also  work.  Small trouble with the installer getting stuck, but searching these forums turned up the answer.

A few issues though:

(1) Can I get OpenGL 2.x support with these open source ATI 4250 drivers?  The HW can do it, I'm pretty sure.  glxinfo just reports GL 1.4 right now.

(2) While the backlight brightness keys work, the on/off key does not do anything.  Is there a way to get it to work?  I searched the forum, but to no avail.

(3) Even though I've installed laptop-mode-tools, I get the dreaded  Load_Cycle_Count increase every 5 seconds on battery.  I can work around  it of course with hdparm -B 254, but all that does is make the drive  never spin down, which sucks battery.  I have verified that on battery  the ext4 commit interval is set to 600 seconds, but the disk still spins  up about every 6 seconds.  lm-profiler says ext4lazyinit is causing a  ton of writes.  Anyone know what I can do about this?  I've scoured many  forum threads, but nothing I've tried has helped.  Others report that  they can get a spin-up only a few times an hour, but I can't seem to do  that, even with commit=600.

(4) youtube videos anywhere above 360p  stutter horribly, which they  don't do on my ancient 2003-vintage laptop with a far slower CPU.  It seems like there's no  HW decoding at work.  I might understand that given the 64 bit flash situation with  nidswrapper, but even the HTML5 mode seems to have the same problem.   Even at 360p, the CPU is maxed out.  720 is totally unusable.  Any  ideas for how to improve this?  mplayer has no trouble with 720p videos even full screened, although this also maxes the CPU, so I'm not sure if it's using HW decoding or not.

(5) I get really annoying keybounce - like I'll type "dog" and end up with "dogggg".  Happens every few words. Does anyone else with this or a similar netbook see this issue?

Thanks for any help about these things.

---

### Post by kio_http on 2011-04-02
Personally I do not chose ATI because of this reason and cannot be of much help.

However for the screen On/Off, you can assign a kde keyboard shortcut to this command
```
xset dpms force off
```

---

### Post by VogonZarniwoop on 2011-04-02
> **kio_http said:**
> Personally I do not chose ATI because of this reason and cannot be of much help.

However for the screen On/Off, you can assign a kde keyboard shortcut to this command

Ah!  Works perfectly, thank you.  That's exactly what I wanted.

I was leery of the ATI machine too, but it seemed like the lesser evil here.  Best I could tell by a lot of forum searching was that support for the nVidia Optimus switching is nonexistent in Linux.  NV doesn't want to support it, and there is some hacked up support but I didn't want to mess with that - I wanted to install and go.  And the Intel based models have really poor graphics and don't work well with OpenGL 2.0.  So this seemed like the model most likely to have good Linux support.  I'm not sure if the disk issue can explain all this, but I only get about 3.5 hrs battery life out of it (brand new), rather than the 6 they claim, even under the lightest imaginable usage (just staring at a fixed web page with the backlight on minimum brightness).  Maybe they have some power saving things implemented in Windows that i'm not getting under Ubuntu, but I'm not sure what they might be.  I can't seem to get the disk to spin down for long no matter what I do :-(. The CPU fan never shuts off for some reason, even though the load goes to almost 0.0 and the PowerNow thing has lowered the clock speed from 1.7 to 0.8.

 Anyway thanks for the backlight tip. Very handy!

---

### Post by VogonZarniwoop on 2011-04-02
More data: it seems that a big chunk of power consumption was coming from the open source ATI drivers.  Moving to the proprietary drivers made a big difference.  With screen at min brightness, the total system power consumption is about like this:

Open source drivers: 14 watts (about 3.5 hrs)
Proprietary drivers: 9 watts (about 5.75 hrs)

If I switch off the 802.11, it drops to about 8.6 watts at idle with the screen on, which is good for just over 6 hours of runtime.

Unfortunately, non-Linux people who install on netbooks aren't likely to investigate this quite as much and may end up with far shorter battery life without even knowing about it...

---

### Post by kio_http on 2011-04-02
If the problems are solved, you can use the "mark thread as solved" tool in the "thread tools" menu.

Do youtube videos work properly?

I have an ASUS 1005ha with the Intel GMA 945 series graphic chipset and desktop effects, youtube and even HD playback work flawlessly.

The screen off hotkey however does not work.

---

### Post by VogonZarniwoop on 2011-04-02
It's really only partially solved.  1 and 2 are OK now.  3, 4, and 5 are still being stubborn :)

The youtube videos are still a problem.  720p ones play at around 1 frame every 2 seconds for some reason.  Strange thing is, my ancient laptop has ATI graphics too, but a slower card, and it plays them just fine.

---

### Post by kio_http on 2011-04-03
> **VogonZarniwoop said:**
> It's really only partially solved.  1 and 2 are OK now.  3, 4, and 5 are still being stubborn :)

The youtube videos are still a problem.  720p ones play at around 1 frame every 2 seconds for some reason.  Strange thing is, my ancient laptop has ATI graphics too, but a slower card, and it plays them just fine.

Hmm, perhaps the final release will be better. Maybe temporarily you could use the system without desktop effects(disable in system-settings).

---

### Post by onepsychoboy on 2011-04-13
VogonZarniwoop,

I have the same machine with the latest 64bit version of Ubuntu (1104 beta) installed and am seeing some of the same problems.

I did the wdidle3 fix that was recommended somewhere else, it seemed to work at first but I just noticed last night that my load cycle count started creeping up again.  After I did the fix my LCC seemed to stay withing 16 of the Start Stop Count, now my SSC is at about 550 and my LCC is at 1300.

I have also noticed a keyboard and mouse stutter/stammer, but usually only when starting the machine back up from standby.  And, a reboot will fix this. 

Also, when I come out of standby there is always a big red box in the upper left corner with a white "1" in it.  Obviously, it is the "identify monitor" feature in ATIs admin program.  I have to open the config program and click the button to get rid of it.

Video is stuttering and not as smooth as it should be. I too was never really a fan of ATI but for 225 I could not resist this purchase.

Was going to tinker with it more this weekend to see if I can resolve some of this.  But, at least I have until the end of month to return for a full refund.  Let me know if you make any progress and I will do the same.

---

### Post by z3frog on 2011-10-15
I had the same problem with Youtube on my 1215T, until I started using Unity 2D instead of Unity 3D. Youtube videos are now fine. Also, I've moved onto 11.10 now.

---

### Post by mpw on 2012-01-01
Does anyone has an idea to (3)? ext4lazyinit runs me crazy here.

---

