---
title: "Thinkpad T23: How well does Hoary work?"
date: 2005-08-14
forum: Hardware &amp; Laptops
---

### Post by elempoimen on 2005-08-14
I did a search on the forums, but came up with mixed results, so I'm looking for something conclusive.

I'm running the Hoary Live CD right now, and I'm very impressed.  Unfortunately, I had to turn off ACPI support to make it boot, which didn't impress me one bit (this being a laptop and all...).

Sooo....

How is ACPI support for the T23 in Hoary?  What will I need to do to turn it on post-install?

Hibernation?  Does Ubuntu use swsusp2 or some other method to enable hibernation?

Is there any other supported power management?

I notice that I have no sound...is it difficult to enable?

The thing is, I'm looking for something that basically "just works" out of the box.  I don't have much time for noodling around anymore.  But I *really* want a GNOME-based distro, and Ubuntu is one of the best.  But if I need to noodle around quite a bit, I'm open to suggestions of a better distro for this particular laptop (I just need it to be GNOME-based).  Thanks for any help you can offer.

---

### Post by elempoimen on 2005-08-15
Addendum: I've learned that if I want sound, I should turn up the volume. :)

So, that's fixed...any ideas on the rest of this?

---

### Post by heltreko on 2005-08-15
I have an IBM t23 with Slackware 10.1.

Hibernation sound etc. is working great.

You should use APM instead of ACPI. I think ACPI is too new for the t23 and APM is more of the same date.

Slackware 10.1 is working flawlessly on the t23 with the exception of 3D graphics acceleration which the standard xorg savage driver doesn't include. There's a special usergroup suppling an alternative driver which is giving the needed 3D support.

Good luck!

---

### Post by buellman on 2005-08-15
hi heltreko!

does speedstep work on a t23?

greets. buellman

---

### Post by elempoimen on 2005-08-15
[QUOTE=heltreko]I have an IBM t23 with Slackware 10.1.

Hibernation sound etc. is working great.

You should use APM instead of ACPI. I think ACPI is too new for the t23 and APM is more of the same date.[/QUOTE]I've gotten ACPI working OK, for the most part, on this laptop before.  Ubuntu is really the first time I've had trouble.

As far as Hibernation goes, do the hotkeys work?  And do you use a hibernation partition, or some form of Software Suspend?

---

### Post by heltreko on 2005-08-16
*> does speedstep work on a t23?*

I thought the BIOS handled this and I've never investigated further. 

*> As far as Hibernation goes, do the hotkeys work? And do you use a hibernation partition, or some form of Software Suspend?*

I only use suspend by auto timeout (leave it standing and it powers down...) and by closing the laptop (lowering the screen). In both cases I think it goes into "suspend to RAM" and the small moon symbol is lit (close to the battery symbol) and all fans harddrives etc powers down. Activating APM also enables total power down at "poweroff".

---

### Post by heltreko on 2005-08-16
I tested the suspend button (Fn+F4) when I got home. It worked like a charm. No special suspend partition so I'm guessing it's supsend to RAM only.

I forgot earlier to say that the battery meter etc is working nice with APM also.

Anyone with suggestions on how to check if speed step is working?

---

### Post by buellman on 2005-08-17
[QUOTE=heltreko]*> does speedstep work on a t23?*

I thought the BIOS handled this and I've never investigated further. [/QUOTE]

hmmm... i think you have to enable a module to get speedstep working (if speedstep with the t23 is supported)

thanks anyway.
buellman

---

### Post by heltreko on 2006-05-13
[QUOTE=buellman]hi heltreko!

does speedstep work on a t23?

greets. buellman[/QUOTE]

I've currently left Ubuntu and now use Zenwalk but I've mananged to get frequency scaling working on the t23 laptop using cpuspeed and acpi_freq. The methods *should be mostly distribution independant* and you are free to try it.

This was done following these steps.
1. Uncommented /sbin/modprobe/acpi_cpufreq in /etc/rc.d/rc.modules to enable cpu frequency scaling in the kernel. Either reboot or  modprobe acpi_cpufreq .

2. Run  "echo "userspace" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor "

3. Install cpuspeed from [http://carlthompson.net/Software/CPUSpeed](http://carlthompson.net/Software/CPUSpeed) to have the cpu_freq automatically adjusted with respect to workload.
3a. Download package
3b. Untar the package in  /usr/src/
3c.  cd /usr/src/package
3d.  make
3e.  cp cpuspeed /sbin/

4. Run  cpuspeed -d

5. Add  /sbin/cpuspeed -d in  /etc/rc.d/rc.local

To see what frequency your cpu is running you can check it with  cat /proc/cpuinfo

---

### Post by betamax on 2006-05-24
Hi,

My T23 worked well with hoary and dapper ( a few issues with power-management)
.....

So far working Grrrreat with Dapper, very impressed.
Cuttently Ubuntu-Conversion on friends and family members, all XP users ](*,) 

Taa

---

### Post by betamax on 2006-05-24
..oops.....my spelling...sorry......:-?

---

### Post by e_liming on 2006-05-31
[QUOTE=heltreko]I have an IBM t23 with Slackware 10.1.

Hibernation sound etc. is working great.

You should use APM instead of ACPI. I think ACPI is too new for the t23 and APM is more of the same date.

Slackware 10.1 is working flawlessly on the t23 with the exception of 3D graphics acceleration which the standard xorg savage driver doesn't include. There's a special usergroup suppling an alternative driver which is giving the needed 3D support.

Good luck![/QUOTE]

Where can I find this alternative driver? The driver supplied by dapper is dated on 2005... :( and enabling the Composite extension is very slow..

---

### Post by mips on 2006-06-02
I dunno what driver he is using but it might be the DRI one.

Have a look at these links:
[http://dri.freedesktop.org/wiki/S3Savage?action=highlight&value=CategoryHardware](http://dri.freedesktop.org/wiki/S3Savage?action=highlight&value=CategoryHardware)
[http://utah-glx.sourceforge.net/](http://utah-glx.sourceforge.net/)
[http://www.probo.com/timr/savage40.html](http://www.probo.com/timr/savage40.html)
[http://www.botchco.com/alex/new-savage/html/](http://www.botchco.com/alex/new-savage/html/)

---

