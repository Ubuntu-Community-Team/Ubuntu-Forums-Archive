---
title: "High frequency noise using kernel 2.6.10"
date: 2005-03-21
forum: Hardware &amp; Laptops
---

### Post by hcf on 2005-03-21
After I upgraded to Hoary my laptop started to make a high frequency noise (like rapid morse code). The noise starts at boot time immediatly after grub, and continues  until I shut down. If there is some kind of CPU load (moving the mouse pointer etc.) the noise stops during the load.

But, if I pass acpi=off to the kernel, there is no noise.

Anyone else with this problem?
What is causing it? -- I have no idea!

I,m running Hoary with the latest uppgrades, and my laptop is an CL56 with Intel Celeron M 1,4GHz and ATI Mobility 9700 128MB.

---

### Post by rmjokers on 2005-03-21
I have a encountered a similar problem with my laptop.  However, it was making the noise with both Warty and Hoary.  I found a discussion on the kernel mailing list where they mentioned a problem with bad capacitors on the motherboard that would cause the high pitched noise when the machine went in and out of the C3 power saving state.  If you plug in a laptop that has this problem, it isnt trying to conserve power and the noise goes away.  The only proposal I have seen for aleviating this problem is to change the kernel's HZ setting from 1000 Hz to 100 Hz which makes the noise much less audible.  I havent had a chance to try this yet.  You can quickly diagnose whether this is the problem on your laptop by plugging it in to see if the noise goes away.

---

### Post by hcf on 2005-03-21
Mine makes the noise wether it's plugged in or not.

---

### Post by andreas_mauser on 2005-07-23
Hi.
having a DELL D610 and having this problem as well.

Anyway if its plugged or not, the noise is there. BUT if I put some load to the machine like opening openoffice word, the noise goes away as long as the machine is busy with something.

I tried to install laptop-mode and laptop-mode-tools. This stuff works together with hdparm I found out. But since kernel 2.6.x doesnt support hdparm on ata drives anymore (am I right???) this does not solve my problems, using hdparm gives me strange ioctl error messages.

acpi=off does work too in my case, but a laptop without power management features is crap, means the battery lives for about 1 hour and I can not see anything, suspend if off too I assume.

On warthy the issues is the same, so we all hope the next version of ubuntu will come without this annoying sound - in the meantime, does anyone have a hint, an advise or at least an idea how we can get rid of this noise?

I am a linux newbie and have nothing to with setting some kernel frequenties up or down, I dont know how that works.  ](*,) 

But I would like to help solving this, so if there is anyone out who has experience and a little time, I really would appreciate this.

Thanks a lot,
Andreas.

---

### Post by major on 2005-07-23
I had similar problems with my laptop, the problem turned out to be my sound card and built-in microphone. Going to the audio settings and muting the microphone input stopped the noise (was just feedback).

Not sure if this is the same problem you all are experiencing, but disabling ACPI may just be disabling the sound card from initializing.

---

### Post by andreas_mauser on 2005-07-27
Resolution..:

haha, I did it (I think...)
after spending ages for searching, bothering every linux guy around, asking too many questions I passed the following to the kernel (because the high freq comes up, when OS and BIOS cant communicate well with each other):

root=/dev/sda2 ro pci=bios idle=halt acpi_sleep=s3_bios quiet splash

the full thing looks like:

title           Ubuntu, kernel 2.6.10-5-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/sda2 ro pci=bios idle=halt acpi_sleep=s3_bios quiet splash
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

THANK YOU for the hint with "acpi=off", cause this qas the reason why I spent some time with the kernel parameters.

I HOPE there is anyone out who also jumps as high as me, cause using windows isnt a choise. ubuntu rocks :) and you too!

 \\:D/

---

### Post by jonsson on 2005-07-29
My old IBM Thinkpad A22m running Kubuntu 5.04 (2.6.10-7) has suddenly (a few days ago) started making strange noises as well. However, I already have acpi=off (only ever got APM to work properly) and it happens regardless of whether it's pluged in or not.

The computer issues a sound about once per second. Usually it's a high pitched beep but sometimes it just clicks or beeps with a lower frequency.   :???:

---

### Post by andreas_mauser on 2005-08-03
Have you >noflushd< installed?
try this and also the laptop-mode and laptop-mode-tools
and then use my kernel settings above.

did it work..?

---

### Post by LokiCoki on 2005-08-26
andreas_mauser you are my hero!

I have an IMB Thinkpad T22 and I had the same problem.  I tried installing Gentoo on my T22 and I got that awful high pitch noise when the computer was idle (which doesn't happen when I boot in Windows).  On the Gentoo forums, nobody seemed to have any solutions...

So I decided I would try another distro.  After some search, I found that Ubuntu was working very well with Thinkpads.  I installed it and got the same annoying noise.

But now!  My Thinkpad is whisper quiet!  I added the options to /boot/grub/menu.lst and everything is perfect!

Thanks a lot!

---

### Post by lx73 on 2005-10-17
andreas_mauser: Thank you from me, too!

This is the _very_ last thing that made my Linux experience short of absolutely stellar. I have a Dell Inspiron 8200, and I've known about the acpi workaround since I got it in 2001. Having AC or battery power didn't make a difference. Every once in a while I would dig deep in the linux kernel mailing archives to figure out how I could use ACPI while not having the annoying noise. So far I have come empty, but your 

pci=bios idle=halt acpi_sleep=s3_bios

solution worked! That is soooo splendid. Thanks again for sharing it with us.

---

### Post by fyassine on 2005-10-31
I also have a inspirion 8200 and although this did fix the high pitched whine, it appears it also killed the sound card.  

If pci is set to anything but noacpi, the sound card will not be recognized on boot.

---

### Post by grinias on 2005-11-10
Great job andreas!!!!

It works on Breezy too!!! I have an ACER TM 4101WLMi and that noise was a problem for me in Hoary and of course it followed me in Breezy. So now we know it works for kernel 2.6.12 of Breezy without having installed laptop-mode-tools and noflushd. 

Thanx again

Elias

---

### Post by andreas_mauser on 2005-12-11
Hi all,

well, so the high frequency is gone from all of you - I experienced another funny detail, you too? Pls let me know!!

When my Laptop is idle, doing nothing, waiting for the screensaver lets say, from time to time I have a strange disk access, making a *krrks* sound - but only when dile - I still have same settings as described before.

Could anyone tell what this is and how to solve this? Or have anyone played with other settings then mine?

I get panic my disk will fail if I stop working...:o) :???: 

Kind regards,
Andreas.

°°give gates no chance, protect yourself with linux°°

---

### Post by LBadvance on 2006-04-18
Can u step me through this? I'm new to ubuntu and my Acer Aspire 3623WXCi is giving me the whine/buzzing issue  people already stated here.

Thanks would really appreciate this.

---

### Post by uersel on 2006-09-04
**andreas_mauser**, you made my day!! 
I got dapper drake running on my T60p and the constant high-pitched noise was driving me crazy. But now thanks to your kernel settings it's gone!!

Thank you.

**LBadvance**: 
1. open /boot/grub/menu.lst as root with your favorite text-editor.
for example: ```
sudo vim /boot/grub/menu.lst
```
2. scroll down till you find the first boot entry for Ubuntu. should look something like this:
```
title          Ubuntu, kernel 2.6.15-26-686
root           (hd0,2)
kernel         /boot/vmlinuz-2.6.15-26-686 root=/dev/sda3 ro quiet splash
initrd         /boot/initrd.img-2.6.15-26-686
savedefault
boot
```
3. now in the kernel line just add the options that andreas_mauser has provided. don't change anything in the line, just add the options! should then look something like this:
```
kernel          /boot/vmlinuz-2.6.15-26-686 root=/dev/sda3 ro pci=bios idle=halt acpi_sleep=s3_bios quiet splash
```
4. reboot and choose the entry you just changed. noise should be gone.

hope this helps...

---

