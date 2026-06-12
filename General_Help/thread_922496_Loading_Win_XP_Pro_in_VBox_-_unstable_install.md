---
title: "Loading Win XP Pro in VBox - unstable install"
date: 2008-09-17
forum: General Help
---

### Post by rhardie on 2008-09-17
I have a rock solid install of Win XP Pro using Virtual Box on my main production system.

I am experiencing a persistant challenge with an install on my laptop in that there is either a corrupted or missing DLL or, upon re-install of Win XP, I get Windows Screen then re-boot request - repeatedly.

I don't seem to be having problems with Guest additions, mounting HD or CD.

I'm on my third install attempt with Windows.

Uninstalled the Windows Guest OS as well as deleted all virtual drives and then did a complete power shut off for 2 minutes before re-boot and reload Windows.

Also, I had a very difficult time getting Ubuntu loaded and repeated attempts were required.

My first thought is:

a) unstable hard drive; however, my Ubuntu is very stable (of course, that is why I'm using Linux instead of Windows whenever possible)

b) I need to manually delete some file somewhere on my hard drive that are related to Windows in virtual environment

I was having challenges with the version of Virtual Box via the Synaptic download manager so I went to Sun's website and downloaded their version 2.0

System Config

Toshiba P15 laptop
P-4 single core 2.8 GHz
1GB RAM
120 GB HD 7200 RPM

Virtual Box 2.0
Windows XP Pro
Virtual HDD 10 GB
Virtual RAM 512 MB

Any thoughts or ideas are welcome.

Regards,

RHardie

---

### Post by EmanresuusernamE on 2008-09-17
It's a virtual machine, copy your virtual hard drive from your desktop to your laptop and use that instead of reinstalling Windows.

Make sure you're using the same versions of Virtualbox too.

---

### Post by rhardie on 2008-09-17
I'll give that a try.  I just completed my Widows install - again and am doing updates.

How would I copy my virtual HD to my Ubuntu Desktop?  Are referring to my going to the "Devices" | Mount CD/DVD-ROM | HOst Drive MATSHITA DVD-RAM UJ-811 (dev/scd0)

Thanks, in advance.

PS:  I should also mention that the Windows Install worked fine up until downloading Service Pac 2.

---

### Post by EmanresuusernamE on 2008-09-17
> **rhardie said:**
> I have a rock solid install of Win XP Pro using Virtual Box on my main production system.
Take the one off of your main production system and put it on your laptop, then load it from VBox.

---

### Post by rhardie on 2008-09-17
OK.

Seems to be working now.

This is a really, really nice virtualization set up after Guest Options are installed for "seamless" operation.  Looks just like an Ubuntu desktop with the exception of the extra work bar and "start" button for Windows sitting just above the Ubuntu menu bar.

Thanks.

RHardie
Austin, TX

---

### Post by EmanresuusernamE on 2008-09-17
Glad to hear you got it to work.  Please mark your thread name as: [Solved].  :)

---

### Post by rhardie on 2008-09-24
Thanks.

---

