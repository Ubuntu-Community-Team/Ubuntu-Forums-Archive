---
title: "VERY SLOW system with Lenovo G550"
date: 2010-10-29
forum: Hardware
---

### Post by Bouazza on 2010-10-29
Hello !

I installed Ubuntu 10.10 one week ago on my brand new Lenovo G550 . Everything went fine, the wifi and the graphics chip were recognized .

But there is one problem : my system becomes awfully slow after some inactivity => The mouse moves very slowly, when I type with the keyboard, it takes nearly 10~15 seconds to see what I wrote, the sound gets distorted etc... When I move the mouse or type something for 3~4 secondes, those symptoms disappear, and as soon as I take my hands of my mouse or keyboard, they reappear .

I went to Gnome System Monitor to see which process caused that : nothing anormal, no excessive CPU and/or memory usage !! Same observation with other tools like "top" .

I tested Maverick Meerkat with other laptops ( an Acer Aspire and a Toshiba ), and I didn't notice these symptoms .

So it has something to do with incompatibility issues with my Lenovo .

Can someone help me to identify the source of theses issues ?

Thanks !

---

### Post by Bouazza on 2010-10-29
I just tried Ubuntu 10.04 and there were no slow downs . So the problem is definitely with Ubuntu 10.10 .

---

### Post by Bouazza on 2010-10-29
Sorry for bumping, but my laptop has been unusable for nearly a week ... Am I the only one with this problem ?

I can't downgrade to the 10.04 because Lucid's Intel drivers don't support the X4500 very well ( artefacts at random moments ), but Maverick's ones do .

---

### Post by innerd on 2010-10-30
You are not the only one, man. Same pc and same problem.

---

### Post by Bouazza on 2010-10-30
Glad to see that I'm not the only one ! :-)

Can someone help me/us please to see which program is responsible for this so that I/we can fill a bug report at Launchpad ?

No Ubuntu developers interested in this bug ?

---

### Post by nklnsk on 2010-11-04
Same problem. Today my wireless crashed. Have this problems for weeks with hope that everything is going to be Ok like on 10.4. Im seriously thinking about reinstall 10.4. till better times come.
Few days ware fine, but in last few days have issues with compiz, it gets really slow and kinda choppy.
Typing in writer takes few sec to do word.
But, sometimes after restart it gets fine. 
On start up have note like: FATAL: Could not load/lib/modules 2.6.35-32-generic/

Hope some help will come soon 

In meanwhile Im goin to take a look around for any solutions.

---

### Post by Bouazza on 2010-11-04
Hello !

I gave up the 10.10, and because no one helped me to identify the source of the issues ( so that I can fill targeted bug reports and help things getting better, but hey, if no one is interested, it's ok ! ), I reinstalled the LTS 10.04 . It works fine provided that you install the packages from xorg-edgers ( otherwise, you'll see some screen flickering because of the official Lucid xorg packages ) .

---

### Post by Decatf on 2010-11-04
I'm pretty sure there was another thread about the stalling issues. I can't find it right now though.

---

### Post by mr-pink on 2010-11-11
Just same problem (and same PC) here. I have tried with 64bit Ubuntu 10.10, has anyone tried with a 32 bit version?

---

### Post by cucu007 on 2010-11-12
> **innerd said:**
> You are not the only one, man. Same pc and same problem.

I have the same machine, the boradcom adapter sucks big time, I switch it for a intel A/B/G miniPCI and it rocks now. Just tow cents.

---

### Post by cucu007 on 2010-11-12
> **nklnsk said:**
> Same problem. Today my wireless crashed. Have this problems for weeks with hope that everything is going to be Ok like on 10.4. Im seriously thinking about reinstall 10.4. till better times come.
Few days ware fine, but in last few days have issues with compiz, it gets really slow and kinda choppy.
Typing in writer takes few sec to do word.
But, sometimes after restart it gets fine. 
On start up have note like: FATAL: Could not load/lib/modules 2.6.35-32-generic/

Hope some help will come soon 

In meanwhile Im goin to take a look around for any solutions.

Well, I know that the G550 has some type of protection in the bios but I found my way around it. Try using a different miniPCI adapter, I swap mine for an intel and this thing is rock solid now. Broadcom support is not there yet at least in this BCM4312. Let me know if you need help, I will subscribe to the thread to help those of you with G550 and the wireless.

---

### Post by cucu007 on 2010-11-12
> **mr-pink said:**
> Just same problem (and same PC) here. I have tried with 64bit Ubuntu 10.10, has anyone tried with a 32 bit version?


I am using the 32-bit ubuntu without issues, i think all the issues we are all having are link to that horrible broadcom BCM4312, dump the damm thing with another minipci adapter, I am confident it will out better. If you have a G550 i can help you switch the adapter.

---

### Post by mr-pink on 2010-11-12
> **cucu007 said:**
> I am using the 32-bit ubuntu without issues, i think all the issues we are all having are link to that horrible broadcom BCM4312, dump the damm thing with another minipci adapter, I am confident it will out better. If you have a G550 i can help you switch the adapter.

Hi! Are u using 32 bit **10.10**? Are u using any special boot option (noapic etc.)?

Actually I was thinking (after looking at the dmesg output) that the problem was related to the trackpad instead of the WLAN adapter. At the moment I'll keep the broadcom adapter, but thank you very much for being so helpful - if I'll decide to switch it I'll ask you how to do it.

---

### Post by cucu007 on 2010-11-12
> **mr-pink said:**
> Hi! Are u using 32 bit **10.10**? Are u using any special boot option (noapic etc.)?

Actually I was thinking (after looking at the dmesg output) that the problem was related to the trackpad instead of the WLAN adapter. At the moment I'll keep the broadcom adapter, but thank you very much for being so helpful - if I'll decide to switch it I'll ask you how to do it.

No special boot options, just download the latest kernel last night compile it and loaded the intel module. Working like a charm. Broadcom support appears nasty at this point. BTW, I had to doa few modification in my boot loader (GRUB) since the compilation process didn't pick it up. I just did a grub-mkconfig -o /boot/grub/grub.cfg 


This wireless is working very well now. Good luck and let me know if u need help.

---

### Post by carl4926 on 2010-11-13
There seems to be a lack of specifics here.

First off the Broadcom wireless is working just fine
```
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
        Subsystem: Broadcom Corporation Device [14e4:04b5]
        Kernel driver in use: wl
```



However not all G550 are the same. My graphics are:
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 09)
        Subsystem: Lenovo Device [17aa:3a00]
        Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 09)
        Subsystem: Lenovo Device [17aa:3a02]
        Kernel driver in use: i915

```
Which incidentally works fine

---

### Post by mr-pink on 2010-11-13
> **cucu007 said:**
> No special boot options, just download the latest kernel last night compile it and loaded the intel module. Working like a charm. Broadcom support appears nasty at this point. BTW, I had to doa few modification in my boot loader (GRUB) since the compilation process didn't pick it up. I just did a grub-mkconfig -o /boot/grub/grub.cfg 


This wireless is working very well now. Good luck and let me know if u need help.

Do u remember if it was working fine with default ubuntu kernel? If so (when I'll have time) I have to try also the 32 bit version of 10.10.

As for wireless, I also think it was working fine after installing proprietary driver.

---

### Post by cucu007 on 2010-11-13
> **mr-pink said:**
> Do u remember if it was working fine with default ubuntu kernel? If so (when I'll have time) I have to try also the 32 bit version of 10.10.

As for wireless, I also think it was working fine after installing proprietary driver.

It wasn't working fine with the default install nor did it worked find with the custom kernel. The solution for me was to switch the minipPCI adapter for an intel one. Now the machine is rock solid in my case. I have heard about the nightmare stories from other using this particular BCM4312 device so I opted to swap it out and reduce the frustration of finding and hacking a custom driver of some sort. I am not saying that there isn't a solution out there that may work, but since I know this particular adapter as it seem to cause is trouble why not do a swap early for an intel and be a happy camper.:)

---

### Post by grimfa on 2011-01-15
Hi cucu07,

I have a lot of problems with my bcm4312 on my lenovo g550 and I am very interested in replacing it with another card.

can you please help me telling me which card to chose and how to get it work with ubuntu 10.10 ?

Thanks and regards,

Grimfa

---

### Post by MountainX on 2011-01-20
The Lenovo G550 is working fine for me with Linux Mint 9. It's plenty fast. It also worked fine with openSUSE 11.3. Those are the only distros I have tried on it.

My only problem is the trackpad edge scrolling doesn't work.

---

### Post by freechelmi on 2011-02-07
> **grimfa said:**
> Hi cucu07,

I have a lot of problems with my bcm4312 on my lenovo g550 and I am very interested in replacing it with another card.

can you please help me telling me which card to chose and how to get it work with ubuntu 10.10 ?

Thanks and regards,

Grimfa

Did you installed the restricted Driver using the assistant ?

---

