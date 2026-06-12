---
title: "Ubuntu 10.04 + ATI Radeon 5730 - eyes hurt"
date: 2011-10-15
forum: Hardware
---

### Post by mpeshev on 2011-10-15
Hello everyone,

Few months ago I had to change my laptop and unfortunately I got stuck with an ATI driven one. I have another notebook + desktop running Nvidia (and all of my previous machines were using Nvidia) and now I have troubles running my Ubuntu in a smooth manner.

Now, my Nvidia HP system runs Ubuntu and Fedora with no driver problems at all. My Lenovo Y560 now, the new system, has Radeon 5730 and I couldn't make it work for a long time. I run Ubuntu 10.04 and Win 7 here - the Win 7 system works great, but I prefer using it for a secondary OS and just setup my Ubuntu.

I have been unable to run Linux drivers for several weeks due to the dual video boot with integrated Intel but figured this one out. After installing Fedora and Ubuntu with the proprietary ATI drivers technically it works - drivers 'seem' installed and the control panel is working, but I can't use the system for more than 15-20min without ending with a headache and eyes hurting.

The problem seems complex to me as I don't see any specific waving on the monitor and the ATI settings are the same as the settings on my Win 7 cpanel setup. I did some testing for fonts and contrast plugs, but it keeps hurting and I get tired after less than half an hour work.

I'm pretty desperate right now cause even if I ask any of my geek friends to help me, it takes like 20-25mins to feel the pain and it is not obvious during the first 5-10mins. There is no shaking nor any obvious emission of the screen. To be honest my Windows setup seems even more shaky than the Ubuntu one but I could work for 8-10h in Win and only 20-30min on Ubuntu.

Is there any way to check if there is something wrong with the setup or is there any special feature/option that could be helpful for that scenario?

Summary:

Lenovo Y560
ATI Radeon 5730
Ubuntu 10.04 + Win 7 (tried Fedora 15 too, same problem with the video)

---

### Post by RileyLynx on 2011-10-16
If you're using the proprietary ATI Radeon drivers on a laptop it's probably doing some horrendous power saving by lowering the screen brightness, and raising the contrast. For my laptop it defaults to this in both Linux and windows. I originally thought my laptop just had a really awful screen, till I noticed plugging in the power vastly improved things. 

If this is the issue it's easy to disable, load up the ATI/AMD Catylist Control Center and turn the PowerPlay>Vari-Bright option to maximum quality, or just disable it completely.

---

### Post by mpeshev on 2011-10-16
I've been playing with all possible settings in the control center for several weeks - brightness, contrast, saturation etc, no luck, also changing all settings for the quality of the picture and trying different DPIs and font settings. Also I have Win 7 with the same control center and tried to replicate the exact set of settings but no luck.

Any idea how can I check if there are any issues with that on a low level config?

---

