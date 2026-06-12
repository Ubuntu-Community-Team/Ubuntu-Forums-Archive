---
title: "no sound with new 5.10 install, no /dev/dsp, soundcard supported in kernel"
date: 2006-03-20
forum: Hardware &amp; Laptops
---

### Post by set235 on 2006-03-20
hi all, 
 trying to figure out how to get my sound working with new install of ubuntu 5.10 breezy. first i will give you my hardware specifics, then tell you what all i have done so far.
my pc (built it myself of course)
asus k8u-x motherboard with onboard sound (AC'97 6 channel)
amd athlon 64 2800+ oc'd to 2.1ghz
1gb mixed ram
evga geforce fx 5700 ultra graphics
dlink ethernet

its not the ultimate gaming rig, but it gets the job done nicely.

ok, so what i have done so far.......
1. installed ubuntu 5.10 breezy to empty partition, dual booting with  winxp pro
2. everything working except NO SOUND
3. remembered a previous install using 5.04 hoary i installed that, of course            deleting partition and recreating.
4. SOUND WORKS FINE with new hoary install, however blackdown java does not, an application i want to use seems to only work with blackdown java in linux so hoary will not do.
5. upgraded from hoary to breezy using synaptic, upgrade went flawless
6. SOUND NO LONGER WORKING, now starts my trouble shooting...
7. lspci shows:
0000:00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)
8. lsmod shows:
snd_intel8x0           30144  0
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
                               as well a lot more of course....but not dealing with sound that i can see.
9. ran modprobe snd-intel8x0 (as root, returned no errors)
10. ran modprobe snd-ali5451 (as root, returned no errors)
11. ran alsamixer  , returns:
alsamixer: function snd_ctl_open failed for default: No such file or directory
                              (same error as root or user)
12. ran lsmod again to see if showing snd-intel8x0 now (not snd_intel8x0), not there, exact same results as before.
13. ran find / -name "snd-intel8x0*"  (as root)  to see if the file exists, and returns:
/lib/modules/2.6.10-5-386/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.10-5-386/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-intel8x0m.ko


there is no /dev/dsp file either...................
anyone got any ideas?

---

### Post by apviper on 2006-03-22
I'm having the same problem.  I can't get the sound working for the life of me.  No /dev/dsp :neutral:

---

### Post by Stone123 on 2006-04-02
my ali5455 configs are as fallows :
rambo3@ubuntu:~$ cat /etc/modprobe.d/alsa-base
> 

# ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-intel8x0
options snd-intel8x0 index=0
options snd-intel8x0 buggy_semaphore=1
# module options should go here

# OSS/Free portion
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0

# card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

# OSS/Free portion - card #1
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

# OSS/Free portion - card #2 (cmipci)
alias sound-slot-1  snd-card-1
alias sound-service-1-0 snd-mixer-oss
alias sound-service-1-3 snd-pcm-oss
alias sound-service-1-12 snd-pcm-oss


and i dont know if this is needed :
rambo3@ubuntu:~$ cat /etc/modprobe.d/blacklist-oss
> 
blacklist ali5455

needs to be blacklisted as that version i used was buggy in ubuntu.

rambo3@ubuntu:~$ cat /home/rambo3/.asoundrc
> 
  pcm.intel8x0 {
           type hw
           card 0
        }

        ctl.intel8x0 {
           type hw
           card 0
        }


---

### Post by set235 on 2006-04-10
Stone123  I could kiss you!!!!!!
that got it working!!!!!!!
yes, it has been 2 weeks since my post here, in the mean time i went back to gentoo linux and was still having the same issue with my ALI5455 sound. after 2 weeks i was starting to get a little frustrated, i couldnt find a solution on gentoo forums. so last night i was once again googleing my issue and lo adn behold, i found this (my own) post with a solution!!!
all i had to do was to edit my /etc/modprobe.d/alsa-base (/etc/modules.d/alsa in gentoo) and it works like a charm!!!!!

Thank you so much!!!!!!!!!

---

### Post by namtaf on 2006-04-10
Hi,

is this a fix for th intel ich6 sound issue? I have a problem where there is no sound, but thought it was a codec problem. Can you confirm this?

Many thanks

---

### Post by postadelmaga on 2006-07-29
I still have same problem ... also after editing alsa-base ... (i all copy the stuff posted by rambo ... 
All that is very strange : i have dapper 6.06 and at the first install all go well (also sound m5455 ali) but after installing new kernel then no sound so i tried restart everything (all Dapper) but nothing. 

Please help me no more use winzoz and give sound to my xgl
Thanks ...

---

### Post by Stone123 on 2006-08-11
I am still on my semester so  i ll check it in a few days , it might be newer alsa doesnt need bugy semaphor. And try to blacklist ali5455 , i dont know why i uncommented the ali driver.

UPDATED kernel no problems.

Works on etch too.

---

