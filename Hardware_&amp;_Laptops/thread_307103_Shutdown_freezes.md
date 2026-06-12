---
title: "Shutdown freezes"
date: 2006-11-26
forum: Hardware &amp; Laptops
---

### Post by Xtyn on 2006-11-26
I've got a problem with the shutdown on my LG LW 60 Express laptop.  I have Ubuntu 6.10. When I press shutdown, Ubuntu shuts down but the laptop does not, it freezes at a black screen. I tried from the console: sudo shutdown -h now but it was worse, it was a red screen that froze this time. I found out that if i press hibernate, the laptop actually shuts down, so I do have an alternative. I have dual boot and shutdown works from windows. When shutdown freezes I have no other alternative but to keep the power off button pressed for 5 seconds and it shuts down but I don't really like this alternative, I don't think it's safe. Another alternative would be to restart the computer, boot windows and shutdown from windows, but I'd prefer it to work from Ubuntu. The problem actually started since I tried to play Nexuiz on PCLinuxOS, so this shutdown problem persists in all distributions. I thought that a fresh install will solve the problem. Nexuiz froze when the game should have started and no combination of keys could exit the game, so I had to force it to shutdown by keeping the power off button pressed. Hope you can help me on this one guys...

---

### Post by JA2 on 2006-11-30
Do you have any graphical enhancements enabled, such as OpenGL/Xgl, 3D desktops, etc.?

Could be an ATI video driver issue, where the display transition from graphics to text mode on shutdown is failing and causing your X session to freeze.  

I used to see those errors on older revisions of nVidia drivers on my Toshiba laptop, but no longer with today's newer drivers and OS updates.

What Ubuntu version are you running?

---

### Post by Xtyn on 2006-12-01
I'm using Ubuntu Edgy Eft. I have an Intel 915 card and that's not the problem. No, I'm not having any graphical enhancements. Strangely, the broblem seems to have solved itself. One day, it just shutdown normally. :) Thanks for your post.

---

### Post by IcarusR on 2006-12-03
Got a similar problem here.... I select shutdown button, Ubuntu goes through normal shutdown, 
gets as far as the Ubuntu logo & the orange progress bar dissapears but it  does not power off.
Is there any way I can temporarily disable the graphics so I can see where it hangs ??

Compaq M700 with ATI Rage Mobility P/M AGP 2x (rev 64) card running Ubuntu 6.10 Edgy EFT 
with standard 2.6.17-10-generic kernel.

---

### Post by uBo on 2006-12-06
@IcarusR: do you have a pentium m too? i really plan to file a bug on that, i have this problem ever since i installed dapper. edgy is the same. hangs just before turning the power down.

---

### Post by Kross on 2006-12-07
> **uBo said:**
> @IcarusR: do you have a pentium m too? i really plan to file a bug on that, i have this problem ever since i install
ed dapper. edgy is the same. hangs just before turning the power down.


Try This=
[http://ubuntuforums.org/tags/index.php/shutdownpower-hang-ezfix/]("http://ubuntuforums.org/tags/index.php/shutdownpower-hang-ezfix/")

Let Me Know..

<=Kross=>

---

### Post by uBo on 2006-12-14
thanks Kross, but this fix disables all ACPI functionality, which is not feasible for laptop users like me.

am i right in assuming that?


just for your information:
[THE BUG in launchpad]("https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43961") has been filed a long time ago and seems quite active.

---

### Post by uBo on 2006-12-19
[See this post]("http://www.ubuntuforums.org/showthread.php?p=1907415") for an idea how to solve the problem.

It seems the kernel module **snd-hda-intel** is the root of the problem.

---

