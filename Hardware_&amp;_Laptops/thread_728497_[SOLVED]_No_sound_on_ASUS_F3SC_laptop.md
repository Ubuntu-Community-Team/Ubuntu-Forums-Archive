---
title: "[SOLVED] No sound on ASUS F3SC laptop"
date: 2008-03-18
forum: Hardware &amp; Laptops
---

### Post by jospan on 2008-03-18
Hi, thought I should share my problem - and the solution :) with the forum.

I assume, that you have checked that the speakers are not muted?:) - OK - read on:


WARNING:
I'm a low-tech no-good son-of-a-newbie (have been for 7 years - the learning curve is steeeeeep) ... so please don't ask me a lot of hard questions: I got sound -> I'm happy!


PROBLEM:
No sound after installing Ubuntu 7.10 (Gutsy Gibbon) on new ASUS F3SC laptop.

HARDWARE AND SOFTWARE DETAILS:

Kernel version:
```
jospan@discworld:~$ uname -r
2.6.22-14-generic

```

ALSA version:
```
jospan@discworld:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14 (Thu May 31 09:03:25 2007 UTC).
```

The sound card:
```
jospan@discworld:~$ lspci -v | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

```

The chipset on the sound card:
```
jospan@discworld:~$ cat /proc/asound/card0/codec#0 | grep Codec
Codec: Realtek ALC660-VD

```

Loaded sound driver:
```
jospan@discworld:~$ cat /proc/asound/modules
 0 snd_hda_intel

```


[B]SOLUTION:

Add the following line:
```
options snd-hda-intel model=lenovo
```
to the file /etc/modprobe.d/alsa-base (create the file if it does not exist)
..and yes: I know it says 'lenovo' and yes: I know my laptop is an ASUS! :confused:

Reboot and rejoice to the sound of the Ubuntu opening fanfare::-({|=

Still no sound? - have you checked again that the speakers aren't muted? - Yes? - sorry, can't help you then...I'm the low-tech no-good son-of-newbie, remember?

By the way: I have also confirmed this solution when using Ubuntu 8.04 LTS (Hardy Heron) (ALSA driver 1.0.16) on the ASUS F3SC.[/B]

Stunningly simple, yes? - but not obvious!

If your problem is solved you can skip the rest - its only notes about what I learned during my attempts to get sound working:

I saw the above solution in different variants several places in this forum and elsewhere on the Net. However, somewhere I was led to believe that I could test the solution simply by issuing the command:

sudo modprobe snd_hda_intel model=lenovo

apparently this should make the kernel reload the driver with the model-option - but it didn't - so for many days I unsuccesfully found and tried other suggestions.](*,) I might add that my laptop in those days met quite a few Linux distributions ;-) but I'm glad that I was able to stay with Ubuntu on my journey further into Linux.

Also note that several suggested solutions involved enabling the Backports-repository in the software sources - this was not necessary in my case.

If you have already messed around with all sorts of manual re-configuration of config-files or even downloaded, compiled and installed new ALSA-drivers you might want to revert to the standard ALSA-drivers for your distribution version before you try my solution. You can do this without re-installing the whole operating system. Use this script:

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
#VERY IMPORTANT NOTE:
#Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop'
#are removed after removing the linux-sound-base packages.
# If this happens, then do the following
sudo apt-get install gdm ubuntu-desktop
```

I hope some will find this helpful!

---

### Post by Toshas on 2008-05-10
tks mate! this worked great for me :) u r my hero!!

---

### Post by jospan on 2008-05-12
> **Toshas said:**
> tks mate! this worked great for me :) u r my hero!!

Great! - glad my post was helpfull :)

---

### Post by tmdp76 on 2008-05-14
Just wanted to thank you for this post, which really helped me out after a half day of failed attempts.

So for other people's reference, this solved the problem for me with this configuration:

Ubuntu 8.04
Alsa 1.0.16
Laptop Asus PRO60ESeries - F6E (I think the former model code is that used by italian resellers of "Media World").

Once again, thanks a lot!

---

### Post by Skorzen on 2008-05-29
Thanks! This worked for me, too.

---

### Post by Nexusx6 on 2008-06-05
Hello! I wanted to say thanks for your very useful post! I can confirm that this works on Kubuntu 8.04 on the Asus F9E series laptop.

---

