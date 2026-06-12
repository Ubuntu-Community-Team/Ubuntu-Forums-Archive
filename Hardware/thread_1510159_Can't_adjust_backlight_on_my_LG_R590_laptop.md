---
title: "Can't adjust backlight on my LG R590 laptop"
date: 2010-06-15
forum: Hardware
---

### Post by weijie90 on 2010-06-15
Dear people from the future:

The problem has been fixed. See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/803051](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/803051)

```

Hélio Nunes (dedalu-dedalu) wrote on 2011-07-04:	 #3
Workaround:
1) install the nvidiabl module from https://github.com/guillaumezin/nvidiabl (Downloads > nvidiabl-dkms_0.69_all.deb);
2) add a line with 'nvidiabl' in /etc/modules;
3) add 'acpi_backlight=vendor' to the GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub;
4) run update-grub.

Reboot.

Hélio Nunes (dedalu-dedalu) wrote on 2011-07-04:	 #4
If you have problems with the workaround after reboot, read this issue: https://github.com/guillaumezin/nvidiabl/issues/14
```
Hi,

I'm using Kubuntu 10.04 on a LG R590 laptop. I can't adjust the backlight. Whenever I use the Fn+Up or Fn+Down keys to try to do so, the brightness indicator on the screen shows up but the brightness level cannot be changed.

I have tried adjusting it via the KDE power management interface, but whenever I use that slider, the backlight shuts off completely (but the screen LED display works) and I have to restart X to make it readable.

The current brightness is 100%.

Any help would be greatly appreciated.

Thanks!

---

### Post by weijie90 on 2010-06-16
bump :)

---

### Post by andfer on 2010-06-25
I have the same problem.
Using the Ubuntu 10.04 64bits updated (as of June-25-2010)
My model is LG R590 P BE54P1
Video: Nvidia GeForce GT 335M - Video RAM: 1GB

The funny thing is that when I updated the nvidia driver for Windows 7 (257.21) I lost the backlight brightness control in Windows too.

---

### Post by saddan on 2010-07-21
Sorry to bother you both on this post, but I cannot send private messages yet.

I'm also thinking about buying  one LG R590 for me and intend to use only linux.
Besides the backlight issue, does everything else work fine on ubuntu  10.04?

Thanks in advance.

---

### Post by weijie90 on 2010-07-27
Everything else works, except for the multi-tap feature of the touchpad.

---

### Post by theskin on 2010-07-27
I had a similar issue with my asus laptop . Solved it by upgrading the kernel to 2.6.34 .

And now i have brightness control i never use it lol :D

---

### Post by weijie90 on 2010-07-27
> **theskin said:**
> I had a similar issue with my asus laptop . Solved it by upgrading the kernel to 2.6.34 .

And now i have brightness control i never use it lol :D

Upgrading didn't solve it :(

---

### Post by theskin on 2010-07-27
sorry that didn't work :(

---

### Post by andfer on 2010-07-27
> **weijie90 said:**
> Upgrading didn't solve it :(

The upgrade don't help here with Ubuntu too.
You can have any tip to cope with the brightness of this monitor at max all the time? I am thinking to start to use sunglasses to use it..

---

### Post by mansourk on 2010-07-28
Hi,
I have seen the same problem on a DELL inspiron 14r machine with ubuntu.

---

### Post by habibbr on 2010-07-30
Same problem here! 
anyone with lucky?
tinking in use sunglasses too... 
betterr than windows 
:)

using ubuntu 10.04 and r590 i5
also I could not use wireless until I done the first aptitude safe-upgrade

best regards

---

### Post by yashaneiman on 2010-10-08
Sorry for replying to a possibly dead thread, but this seems like a widespread problem, and I spent some time battling it.

I have an LG R560 laptop with Ubuntu Lucid, and Ubuntu's brightness controls don't work. Nothing helped.

As I now understand, the brightness controls in Ubuntu are trying to change the screen's backlight intensity. Now, my laptop model has a LED backlight, which means that its intensity can't be controlled in principle. The only way to simulate a change in brightness is to change the parameters of the displayed colors themselves, e.g. gamma correction. This is probably what Windows does in response to the brightness keys. Of course, this action only affects the visual experience, and not the power consumption.

Anyway, the Ubuntu brightness controls are not clever enough for this one. Instead, you can adjust the gamma correction using the xgamma command, e.g.:
```
xgamma -gamma 0.8
```

---

### Post by romulow22 on 2011-03-02
Hi, since the last post, the lg r590 had an update BIOS and the brightness in windows worked.

I installed the Ubuntu 10.10 and the brightness control don't work.

So I think the problem now is on Ubuntu kernel, not in laptop, because the brightness in windows is working now!


sry my bad english!

---

### Post by suid0 on 2011-04-12
Hello all.. 

I was googling about this problem and after I gave up I found a solution while resting.. lol

BTW I did that in a Slackware box but I'm pretty sure Ubuntu will work the same.

Install the NVIDIA driver.. the orginal one I mean.. After that, go to NVIDIA X Server Settings that should be available on your WM menu.

After it's open, navigate to X Server Color Correction and there you go!! brightness control.. and it works!!!! :D

Suggestion.. reduce both brightness and gamma to have a better result.

I posted on my blog with the same thing so google can have more results so more people can learn that thing
[http://suid0.unitednerds.org/wpress/2011/04/12/how-to-configure-brightness-on-linux-with-lg-r590-5700-notebook/](http://suid0.unitednerds.org/wpress/2011/04/12/how-to-configure-brightness-on-linux-with-lg-r590-5700-notebook/)


[ ]'s

suid0 a.k.a Sergio
[email]suid0@unitednerds.org[/email]

---

### Post by weijie90 on 2011-11-19
Fixed. See the comments at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/803051](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/803051)


```
Hélio Nunes (dedalu-dedalu) wrote on 2011-07-04:	 #3
Workaround:
1) install the nvidiabl module from https://github.com/guillaumezin/nvidiabl (Downloads > nvidiabl-dkms_0.69_all.deb);
2) add a line with 'nvidiabl' in /etc/modules;
3) add 'acpi_backlight=vendor' to the GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub;
4) run update-grub.

Reboot.

Hélio Nunes (dedalu-dedalu) wrote on 2011-07-04:	 #4
If you have problems with the workaround after reboot, read this issue: https://github.com/guillaumezin/nvidiabl/issues/14
```

---

