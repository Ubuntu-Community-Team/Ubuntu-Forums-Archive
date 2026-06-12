---
title: "HP Mini keyboard issues"
date: 2011-02-03
forum: Hardware
---

### Post by ghost25 on 2011-02-03
Hey guys, I've got yet another bugger of a question for y'all.

My brother bought himself an HP Mini (not sure if it's a 110 or 210 model, no readily visible way to check, and having issues with it) about 18 months ago, that originally came with Windows Vista on it. He can't stand Windows, so he asked me to install Linux on it. I installed SUSE on it and walked away, no problem.

Well, as is sometimes the case with computers, especially mobile ones, one day his hard drive just up and died. No real cause to it, it just crapped the bed and refused to boot. This happened while it was in my possession, as he wanted to use Ubuntu. He had seen me previously using Ubuntu on my own laptop, and he liked the layout. So, while backing up his data, the keyboard suddenly decided to stop working.

I thought at that point it might be a symptom of the hard drive dying, which while irritating wasn't that big of a deal; I had another laptop drive laying around in my parts bin. This one I remembered had Ubuntu already installed on it, so I swapped it in.

Problem. The keyboard still doesn't work, and external USB keyboards aren't recognized. I can't type anything in at all, and both user accounts on the drive (the one that needs to be wiped) have passwords, so no luck there. His touchpad is extremely skitchy as well, you're lucky if you can keep it moving in a straight line.

I burned an .ISO image of Ubuntu 10.04 Netbook Remix on my Windows 7 laptop, and put it on a CD-RW since he doesn't have an external DVD drive, just the standard Plextor external CD drive. Windows burned it no problem, but when I went to turn the optical drive on and plug it into the netbook, no luck again. No power even though it's plugged in, and no response. BIOS won't recognize it as being there.

So, I'm stuck. I'll re-summarize my issues and what I've done.

*Keyboard won't work at all, nor will external USB devices.
*Hard drive was replaced, this evidently did not solve the problem.
*Optical drive isn't recognized by the BIOS and won't power on.
*I've tried using a bootable USB flash drive, with the same results.

Anybody else got any ideas? Or do you think his machine is borked completely? I'm thinking the latter, due to the keyboard and USB issues, but maybe you can give me a ray of hope.

P.S. he's been bugging me about doing it, and now that I have time to, it won't work. We're both gonna be pissed if it went to hell.

Thanks for any help y'all can offer us.

EDIT: Okay, update time.

I didn't realize that the keyboard actually DOES work, as I am able to access the startup BIOS using the keyboard. It's a matter of the keyboard not being recognized once the computer gets to the login screen. This I was able to bypass by using the "Universal Preferences" option and selecting the Onscreen Keyboard. Kludgey, but it worked. So far, anyway. Is it possible the kernel got corrupted or something? I'll update if I find anything else out.

---

