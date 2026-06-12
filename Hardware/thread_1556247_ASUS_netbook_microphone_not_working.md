---
title: "ASUS netbook microphone not working"
date: 2010-08-19
forum: Hardware
---

### Post by HonzaPokorny on 2010-08-19
Netbook: ASUS Eee PC 1001PX. 
Ubuntu Netbook Edition 10.04.

The built-in microphone doesn't seem to be working. When I try to record something with the gnome sound recorder, I only get hissing sounds. 

Any ideas? 

Thanks

---

### Post by HonzaPokorny on 2010-08-20
Bump.

---

### Post by NikoNZ on 2010-08-20
Bump

---

### Post by simosx on 2010-08-20
Start off at [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

There is a process to collect hw info of your sound card; these are essential to provide help to you.

A shortcut would be to google for your exact netbook model name, let's say 'asus eee xyz ubuntu', in order to find testimonials of others who installed linux on the same machine.

---

### Post by HonzaPokorny on 2010-08-20
> **simosx said:**
> A shortcut would be to google for your exact netbook model name, let's say 'asus eee xyz ubuntu', in order to find testimonials of others who installed linux on the same machine.

I have now done that. There is a bug report in Launchpad, and one of the commenters said that you need to change the /etc/modprobe.d/alsa-base.conf. After doing that, alsa doesn't get loaded and is nowhere to be found. The 'alsamixer' commmand doesn't work either. Deleting the added line of code doesn't restore the original state.

When I run:

```
$ sudo modprobe snd-hda-intel
```

(which is supposed to reload the driver for my sound card, I get this:

```

WARNING: Could not open '/lib/modules/2.6.32-21-generic/kernel/sound/core/snd-page-alloc.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.32-21-generic/kernel/sound/core/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.32-21-generic/kernel/sound/core/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.32-21-generic/kernel/sound/core/snd-pcm.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.32-21-generic/kernel/sound/core/snd-hwdep.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.32-21-generic/kernel/sound/pci/hda/snd-hda-codec.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.32-21-generic/kernel/sound/pci/hda/snd-hda-intel.ko': No such file or directory



```

I'm lost again. 

Do I have to do something to the kernel?

---

### Post by simosx on 2010-08-20
> **HonzaPokorny said:**
> I have now done that. There is a bug report in Launchpad, and one of the commenters said that you need to change the /etc/modprobe.d/alsa-base.conf. After doing that, alsa doesn't get loaded and is nowhere to be found. The 'alsamixer' commmand doesn't work either. Deleting the added line of code doesn't restore the original state.
....
I'm lost again. 

Do I have to do something to the kernel?

You forgot to add the URL to the launchpad report here. ):P

---

### Post by HonzaPokorny on 2010-08-21
> **simosx said:**
> You forgot to add the URL to the launchpad report here. ):P

Oops!

[Bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580183")

Also, I managed to restore ALSA by installing the linux-backports module for alsa. The jack still doesn't work though.

Thanks

---

### Post by HonzaPokorny on 2010-08-24
Bump.

---

### Post by lidex on 2010-08-26
> **HonzaPokorny said:**
> Bump.

Are you following that bug report?
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by irpsit on 2011-12-31
This is one big problem in ASUS laptops with no solution in sight. I have been waiting for a solution for more than 2 years; and I have tried everything.

---

