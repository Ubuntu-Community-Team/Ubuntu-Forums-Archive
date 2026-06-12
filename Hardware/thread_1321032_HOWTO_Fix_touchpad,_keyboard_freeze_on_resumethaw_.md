---
title: "HOWTO: Fix touchpad, keyboard freeze on resume/thaw for laptops with i8042 controller"
date: 2009-11-09
forum: Hardware
---

### Post by lightrush on 2009-11-09
[COLOR="Magenta"]**0. UPDATES**[/COLOR]
Added "" around the parameter $1 for compatibility as pointed out by mikkle.

**1. WHO IS THIS FOR**

This HOWTO applies to laptops based on Intel chipset which have their keyboard and/or touchpad connected to i8042 controller. You could find if you have one of those by running:
```
sudo lshal | grep i8042
```
If this spits anything then you do have an i8042 controller.

**USE IF:**
[COLOR="Red"]This HOWTO will most probably help you IF:[/COLOR]
Your laptop resumes/thaws with frozen keyboard and/or touchpad AND a newly connected USB mouse/keyboard works AND your laptop has an i8042 controller.

[COLOR="Red"]This HOWTO MAY help you IF:[/COLOR]
You don't know if you have i8042 controller and your laptop exhibits the aforementioned behaviour. You can try and see if it fixes your problem. Report back if it did.

**DO NOT USE IF:**
[COLOR="Red"]This HOWTO will NOT help you IF:[/COLOR]
Your laptop resumes AND newly connected USB keyboard/mouse DO NOT work.
In this case you probably suffer from a resume failure which causes your whole system to be frozen.

[COLOR="Red"]This HOWTO will NOT help you IF:[/COLOR]
Your touchpad and/or keyboard do not work at all after a fresh boot.
In this case you probably have a problem related to i8042 but NOT this one. There are people around who have ideas on workarounding that. Use the amazing Search button of these forums. You might find a miracle!

**2. WHAT THE PROBLEM CONSISTS OF**

This is a bug somehow related with the i8042 controller found in many Intel based laptops on the market. I do not know why it happens and how exactly the bug works but I know how to workaround it.

This bug appeared in Intrepid Ibex for me and this workaround circulated in the forum at that time in one form or another. Later it disappeared in Jaunty for me so I have completely forgotten about it until now. In Karmic it presents itself in exactly the same way as in Intrepid which is as follows:

   **2.1.** Suspend/Hibernate the laptop
   **2.2.** Resume/Thaw the laptop
   **2.3.** Repeat until the keyboard and/or touchpad is frozen

**3. HOW TO FIX IT**

In order to fix this we need to unbind the controller on suspend/hibernate and later re-bind it on resume/thaw. Pm-utils provides us with a framework which can execute shell scripts on suspend/hibernate/resume/thaw. Our solution is in the form of one such script and all we need to do is - put it in the right place for Pm-utils to execute. We do that following these steps:

   **3.1.** Download the script:
   [>>Download<<]("http://sites.google.com/site/lightrush/files/01i8042?attredirects=0&d=1") Save it to your home folder. The following instructions assume that.
   **3.2.** Open a Terminal (GNOME: Alt+F2 > gnome-terminal) and go to your home directory:
   ```
cd ~
```
   **3.3.** Make the script executable:
   ```
chmod +x 01i8042
```
   **3.4.** Move it to the Pm-utils user hooks folder:
   ```
sudo mv 01i8042 /etc/pm/sleep.d/
```

**DONE**

**4. EXPECTED RESULTS**

Your laptop should no more resume/thaw with frozen keyboard and/or touchpad.

---

### Post by mikkle on 2009-11-18
Works like a charm! :-D

I have experienced the exact behaviour you outline, with the exact same history, even.
I'm running Ubuntu on a Lenovo T61, for the record.
This fix really, really saved my day! Cheers!

Had to change
```
case $1 in
```
to
```
case "$1" in
```
in the script, though. Otherwise it never triggered.

Thanks heaps!

:O) Mikkle

---

### Post by lightrush on 2009-11-18
Hm interesting, these $1 and "$1" have to be equivalent ... and I swear it works w/o "" on mine but for the sake of your experience I will update the script with "" :) .

---

### Post by drs305 on 2009-11-20
Worked on a Lenovo N100 - Thanks!

---

### Post by songmaster on 2009-11-21
Works great on my HP Pavilion dv7 Laptop with Kubuntu 9.10 - thanks!

---

### Post by kruzztee on 2009-11-21
I followed your steps, but it didn't work out.
The output of sudo lshal | grep i8042:
```
  info.linux.driver = 'i8042 aux'  (string)
  info.linux.driver = 'i8042 kbd'  (string)
udi = '/org/freedesktop/Hal/devices/platform_i8042'
  info.linux.driver = 'i8042'  (string)
  info.product = 'Platform Device (i8042)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042'  (string)
  platform.id = 'i8042'  (string)
udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 KBD port'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio0'  (string)
  serio.description = 'i8042 KBD port'  (string)
udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio0/input/input4/event4'  (string)

```

but still it didn't work out...

---

### Post by lightrush on 2009-11-21
> **kruzztee said:**
> I followed your steps, but it didn't work out.
The output of sudo lshal | grep i8042:
```
  info.linux.driver = 'i8042 aux'  (string)
  info.linux.driver = 'i8042 kbd'  (string)
udi = '/org/freedesktop/Hal/devices/platform_i8042'
...

```

but still it didn't work out...

Did you try plugging USB mouse/keyboard after resuming? If those do not work then probably your computer is frozen and not just the touchpad/keyboard. Alternatively it is possible that the problem you experience is not related to this issue and just exhibits the same symptoms.

---

### Post by kruzztee on 2009-11-22
The problem is that my touchpad not detected from the start of ubuntu. I already tried to follow nomux solution but it didn't work.. My touchpad detected as Macintosh Emulation.
This bug is kinda depressing considering I used a netbook.

---

### Post by lightrush on 2009-11-22
> **kruzztee said:**
> The problem is that my touchpad not detected from the start of ubuntu. I already tried to follow nomux solution but it didn't work.. My touchpad detected as Macintosh Emulation.
This bug is kinda depressing considering I used a netbook.

Lame... Well then the issue is definitely different. I can recall that someone used i8042.reset as a kernel parameter for something like this. Don't take my words literaly since the right command might not have been exactly that, but do search for "i8042" and "reset" and you might find something interesting. Dismiss what I said if you have already tried that.

Alternatively you could try compiling latest mainline kernel or try compile 2.6.28 (presumably that one worked for you). :)

---

### Post by drbsjtmndl on 2009-11-22
is it going to work with amd turion x2 motherboard? i am using a hp laptop with ubuntu 9.10. please help me.every time i do so i have to restart my laptop.

---

### Post by lightrush on 2009-11-22
> **drbsjtmndl said:**
> is it going to work with amd turion x2 motherboard? i am using a hp laptop with ubuntu 9.10. please help me.every time i do so i have to restart my laptop.

Well if you have the i8042 controller you can give it a try. Did you try plugging in a USB kbd/mouse and see if they work?

Report back if it works - I will update the HOWTO description.

---

### Post by kruzztee on 2009-11-22
> **lightrush said:**
> Lame... Well then the issue is definitely different. I can recall that someone used i8042.reset as a kernel parameter for something like this. Don't take my words literaly since the right command might not have been exactly that, but do search for "i8042" and "reset" and you might find something interesting. Dismiss what I said if you have already tried that.

Alternatively you could try compiling latest mainline kernel or try compile 2.6.28 (presumably that one worked for you). :)

Maybe I should try to recompile mainline kernel like you said...
But can U inform me where can I find the most comprehensive kernel compilation guide on the net?

---

### Post by lightrush on 2009-11-23
> **kruzztee said:**
> Maybe I should try to recompile mainline kernel like you said...
But can U inform me where can I find the most comprehensive kernel compilation guide on the net?

Place one:

[http://ubuntuforums.org/showthread.php?t=311158]("http://ubuntuforums.org/showthread.php?t=311158")

Place two:

[https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile")

Make sure you read both thoroughly before you do anything. Make sure you at least somewhat understand the differences between the several mechanisms to compile a kernel on Debian/Ubuntu. :)

---

### Post by kruzztee on 2009-11-25
Already compiled new kernel, but still my touchpad is not detected.
Although I surprised to know how easy compiling kernel nowaday.

When I try to google the problem there are many result show that there are so many patch for ALPS Touchpad for some particular brands and types...

---

### Post by lightrush on 2009-11-26
> **kruzztee said:**
> Already compiled new kernel, but still my touchpad is not detected.
Although I surprised to know how easy compiling kernel nowaday.

When I try to google the problem there are many result show that there are so many patch for ALPS Touchpad for some particular brands and types...

Change the laptop. :D

---

### Post by YesSir on 2009-12-09
Thanks lightrush, works perfectly on my Eeepc 901 =D>

---

### Post by dpv140 on 2009-12-28
I am having the same symptoms as the original post. Every time the laptop (SONY Vaio) comes back from suspend/hibernate, the keyboard fails to work, albeit the touchpad is always fine, and an external USB keyboard works fine as well.

I followed the instructions for setting up the bind/unbinding, and a review of the "pm-suspend.log" messages reveals that it is called in the right order and apparently successfully (below is the tail):

```
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
/etc/pm/sleep.d/10_grub-common resume suspend: success.
/etc/pm/sleep.d/01i8042 resume suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk resume suspend: success.
/usr/lib/pm-utils/sleep.d/000record resume suspend: success.
```

[line number 5 is the script of the original post]

However, the keyboard is still unresponsive when returning from suspend/hibernate, and I'm at my wits' end attempting to further debug this problem. This all happened when I upgraded to Karmic, and if necessary I can downgrade. Any help is appreciated.

---

### Post by lightrush on 2009-12-30
Well, I am currently at Debian Squeeze, Kernel 2.6.30 and while it is a bitch to make the simple things work it is overall a lot more stable than Karmic. It is about a mix between Jaunty and Karmic, having older kernel and system components and newer GNOME 2.28. Most GNOME components get updated with new upstream versions since Squeeze is not released yet. Most components are at 2.28.4. The only real problems I have met so far are the same GVFS problems that exist on Jaunty - segfaults when using gvfsd-sftp, gvfsd-smb over many and large files on a remote share. That said I haven't experienced the bug of this thread in Squeeze yet.

I haven't really answered on-topic but this is my overall fix for Karmic for now. Quite a few things remained unpatched and broken and the main work goes into Lucid now I think.

---

### Post by pillu on 2010-01-19
I tried this fix but didn't work on my laptop (lenovo 3000 N100). Upon checking pm-suspend.log I found that the script had not run at all. Can anyone suggest a way to make it run on resume? The contents of pm-suspend.log are> Tue Jan 19 20:46:17 CST 2010: performing suspend
Tue Jan 19 20:46:30 CST 2010: Awake.
Tue Jan 19 20:46:30 CST 2010: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend: success.
/usr/lib/pm-utils/sleep.d/99video resume suspend: Returned exit code 1.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video resume suspend: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode resume suspend: success.
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
/etc/pm/sleep.d/10_grub-common resume suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk resume suspend: success.
/usr/lib/pm-utils/sleep.d/000record resume suspend: success.


---

### Post by pillu on 2010-01-19
Fixed the problem by changing the ownership of the scipt to root. It was set to my default user before and that was why it wasn't executing on resume. Now everything works well. Thanks for the fix :D

---

### Post by whirl on 2010-01-24
I have a FS amilo Si1520 with ubuntu 9.10 and this very same problem, it resumes from suspend with a frozen trackpad, working keyboard. Hibernate works perfectly. I tried this and made sure the script is owned by the root but now when try to suspend or hibernate it just locks the screen. Any ideas?

Cheers!

---

### Post by bangateng on 2010-02-11
it works like a charm... thanks lightrush...

---

### Post by artroy5 on 2010-02-23
Hey this worked great for me on my Lenovo 3000 n100.  I had to restart, I don't know if that was implied or I just missed it.

Anyway, thanks for the great fix!
:KS

---

### Post by bford16 on 2010-03-03
This did not work for me until I changed ```
case $1 in
``` to ```
case "${1}" in
```This is the syntax used in the other scripts in /etc/pm/sleep.d on my HP dv7 1232NR laptop with Ubuntu 9.10.

---

### Post by supermarchino on 2010-03-26
from /var/log/pm-suspend.log

```

/etc/pm/sleep.d/01i8042 suspend suspend: /etc/pm/sleep.d/01i8042: 29: cannot create /sys/bus/platform/drivers/i8042/unbind: Directory nonexistent
Returned exit code 2.

```

Why?

Vaio CS series.

(No need to say it does not work, built in keyboard still not responsive at all...)

---

### Post by lightrush on 2010-03-26
> **supermarchino said:**
> from /var/log/pm-suspend.log

```

/etc/pm/sleep.d/01i8042 suspend suspend: /etc/pm/sleep.d/01i8042: 29: cannot create /sys/bus/platform/drivers/i8042/unbind: Directory nonexistent
Returned exit code 2.

```

Why?

Vaio CS series.

(No need to say it does not work, built in keyboard still not responsive at all...)

Are you running Linux 2.6.31 or 2.6.32?

---

### Post by supermarchino on 2010-03-26
2.6.31.

2.6.32 out of the box (Lucid live cd) suffers from the same issue. Still not tested with the script.

---

### Post by lightrush on 2010-03-26
> **supermarchino said:**
> 2.6.31.

2.6.32 out of the box (Lucid live cd) suffers from the same issue. Still not tested with the script.

Well Linux 2.6.32 has changed that interface for reason not known to me. My last observation on 2.6.31 was that it worked. I switched to 2.6.32 on Debian long time ago and it stopped working for me. The remaining mechanism to change the behaviour of the i8042 driver is by using kernel boot parameters. For more info on those look [here]("http://lightrush.homelinux.org"). Try experimenting with those.

As far as Linux 2.6.32 is concerned, I had the bug since my upgrade to 2.6.32.something_less_than_10. Recently I upgraded it to 2.6.32.10 (that was few days ago) and I haven't encountered the problem but the testing is ongoing. I will report back with results for the latter.

---

### Post by luwandah on 2010-03-27
Awesome fix. Works for my ASUS 1005PE running UNR 9.10.

Output of uname -a:
Linux little-one 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

---

### Post by lightrush on 2010-03-27
> **luwandah said:**
> Awesome fix. Works for my ASUS 1005PE running UNR 9.10.

Output of uname -a:
Linux little-one 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

Glad to hear but you probably want to also read my previous post prior to upgrading to 10.04. Look above or click [here]("http://ubuntuforums.org/showpost.php?p=9033545&postcount=28").

---

### Post by lightrush on 2010-03-29
A week using Linux 2.6.32.10, no touchpad/kbd freezes so far. Maybe we may finally not need this for Lucid Lynx/Debian Squeeze. :popcorn:

---

### Post by whirl on 2010-03-30
> **lightrush said:**
> A week using Linux 2.6.32.10, no touchpad/kbd freezes so far. Maybe we may finally not need this for Lucid Lynx/Debian Squeeze. :popcorn:


Ive been using lucid too for few days and everytime I try to resume from suspend it freezes my touchpad. I tried this trick too but didnt help. I have fs amilo si1520.

---

### Post by lightrush on 2010-03-30
> **whirl said:**
> Ive been using lucid too for few days and everytime I try to resume from suspend it freezes my touchpad. I tried this trick too but didnt help. I have fs amilo si1520.

That is rather lame to say the least. Here is what you can try.
    Get the latest Debian Unstable CD (just the first one). Install it on your laptop, selecting Laptop in the installer where it asks. Run it for a few days and see how it behaves. If you don't observe freezes then it is the kernel of Ubuntu. I think the current Lucid kernel is 2.6.32.9. Debian Unstable comes with 2.6.32.10. I am running Squeeze with the same kernel and I have seen no problem until this moment.
    If you find it easier you can get a 2.6.32.10 kernel from [here]("http://www.kernel.org/pub/linux/kernel/v2.6/") and compiling it on your Lucid install. Ubuntu does not seem to have a compiled package with 2.6.32.10. For compilation procedures you can look around or in Ubuntu's wiki.
    Let us know if you have any progress testing and results.

---

### Post by whirl on 2010-03-30
> **lightrush said:**
> That is rather lame to say the least. Here is what you can try.
    Get the latest Debian Unstable CD (just the first one). Install it on your laptop, selecting Laptop in the installer where it asks. Run it for a few days and see how it behaves. If you don't observe freezes then it is the kernel of Ubuntu. I think the current Lucid kernel is 2.6.32.9. Debian Unstable comes with 2.6.32.10. I am running Squeeze with the same kernel and I have seen no problem until this moment.
    If you find it easier you can get a 2.6.32.10 kernel from [here]("http://www.kernel.org/pub/linux/kernel/v2.6/") and compiling it on your Lucid install. Ubuntu does not seem to have a compiled package with 2.6.32.10. For compilation procedures you can look around or in Ubuntu's wiki.
    Let us know if you have any progress testing and results.
Yeah, Ive been reading from various places that it could actually be because of the latest BIOS that FS has to offer (1.20). The sad thing is that I cannot flash to the older one because of my processor. Dont know if thats true but Ill post it here when I have time. Gotta run! Thanks for the reply o/

---

### Post by lightrush on 2010-03-30
Hmmmm, try the other kernel.

---

### Post by Tingvan on 2010-05-22
i take the process, but it doesn't work. Compute doesn't get into sleep.
then i check the file pm-suspend.log and find:

```
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/01i8042 suspend suspend:/etc/pm/sleep.d/01i8042: 29: [COLOR="Red"]cannot create /sys/bus/platform/drivers/i8042/unbind: Directory nonexistent[/COLOR]
Returned exit code 2.
Sun May 23 00:42:52 CST 2010: Inhibit found, will not perform suspend
Sun May 23 00:42:52 CST 2010: Running hooks for resume
```

i am a rookie. my os is ubuntu netbook remix 10.04.
please help me.

---

### Post by lightrush on 2010-05-22
This fix is not relevant to Lucid. Sorry. You can try kernel options for i8042 instead.

---

### Post by Tingvan on 2010-05-23
oh,Maybe it's not the same problem. 'cause my laptop remains dim after awake from suspend. 
I have to brighten the LCD manually. 

I am not good at kernel. i'd like to quit.

yesterday i happened to find a bug report page about similar problem.
There was a patch on that page. 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/551234](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/551234)

but i don't know how to handle it.

faint.....

anyway thank [COLOR="Teal"]lightrush[/COLOR] a lot.

---

### Post by drs305 on 2010-05-23
Just a note for Lucid users. 

My Lenovo N100 touchpad would not work after coming out of "suspend" mode. On my 32-bit laptop, adding "i8042.reset" to the *GRUB_CMDLINE_LINUX_DEFAULT=* line in /etc/default/grub solved it for me (don't forget to run "sudo update-grub" after making the change). 

It's worked for some but not for others. Good luck.

---

### Post by Lip123 on 2010-12-28
Hi,
I've got an Samsung NC 10 Plus netbook and had the same bug. ( Intel N10 Family DMI Bridge).

Your script helped me, thank you very much!

---

### Post by Rythh on 2011-03-05
Thanks a lot, worked wonders. :)

---

### Post by lobstar on 2011-03-14
Hi

Got a lenovo y310 3000

Just installed Linux Mint 10 Julia (had the same problem with 9)

I copied the script, tried changing it to "$1"but it does not work. The suspend log says

```

Running hook /etc/pm/sleep.d/01i8042 suspend suspend:
/etc/pm/sleep.d/01i8042: 29: cannot create /sys/bus/platform/drivers/i8042/unbind: Directory nonexistent

Running hook /etc/pm/sleep.d/01i8042 resume suspend:
/etc/pm/sleep.d/01i8042: 29: cannot create /sys/bus/platform/drivers/i8042/bind: Directory nonexistent
```

Any suggestion what to do?

---

### Post by lightrush on 2011-03-14
Most probably means you have a newer kernel that has this functionality removed. At this point you could try some/any of these: [http://lightrush.ndoytchev.com/random-1/i8042quirkoptions](http://lightrush.ndoytchev.com/random-1/i8042quirkoptions) . If none of that works - I really don't know. :|

---

### Post by lobstar on 2011-03-14
Thanks for your reply.

But I'm not sure how I need to try them? I did add the .reset one to the grub file as suggested earlier.

Is that where these lines should be tried out?

---

### Post by lightrush on 2011-03-14
Yes. Try each and test. Luckily this issue has disappeared for me since 10.04. You might want to ask someone on the kernel mailing list. Upstream that is.

---

### Post by lobstar on 2011-03-14
Sweet! i8042.nomux did it. I removed i8042.reset

Here is more about it [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86820](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86820)

Thanks a lot! Believe I have a fully working Linux now.

---

### Post by oldarney on 2011-05-20
worked miracles on ASUS UL30A-X4

---

### Post by dzchimp on 2012-06-28
Yes I know that this thread is a year old. However this helped me with Precise, so I'm going to go ahead and thank the OP.

Only one thing though... With the code for case standby, system wouldnt go into sleep. I commented it out. But on resume, the issue was solved with the code in case resume.

Yes I'm on a i8042 controller-Fujitsu Lifebook LH531. Thanks a lot. This was the only thing that worked for me. I was starting to think I couldnt ever let my laptop go into standby.:KS

---

### Post by 80hd on 2013-02-05
@lightrush


THANK YOU!
THANK YOU!
THANK YOU!
THANK YOU!
THANK YOU!
   
Mint 13 did not exhibit this behavior, and then Mint 14 started it.  
USB and bluetooth input both stopped working after a suspend/resume and it was very frustrating.  
  
Tested on: HP NW8440

---

