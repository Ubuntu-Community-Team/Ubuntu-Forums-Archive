---
title: "No Active Cooling for CPU"
date: 2020-12-12
forum: Hardware
---

### Post by dragoontufellow on 2020-12-12
Hello,

I'm having trouble with my fans. They're not detected in lm-sensors nor are they detected in any other sensor program. I've noticed that my computer has been very quiet despite it having a semi-aggressive fan curve in BIOS; thinking it was odd I left Psensor running as i did my usual activities and noticed that my temps reached well beyond the threshhold set in BIOS. Normally at 50c my fans would start adjusting and at 70c they would completely cap i reached 68c and didn't notice a audible difference. so after looking at lm-sensors i realized i had almost no information, in Psensor I only see GPU fans.
this is alarming because I've been throwing a lot at the CPU and it hasn't been actively cooling possibly resulting in minor damage to the CPU socket and/or motherboard. any help in fixing this issue would be greatly appreciated.

[Specs]

MB: MSI x570 pro-a
CPU: Ryzen 2700x (W/ Ryzen Wraith Prism Heatsink)
RAM: 16 GB G.Skill Ripjaw V 3200mhz @ 3200mhz
GPU: EVGA RTX 2070 Super
HDD: WD Black 1TB
PSU: EVGA 850W G3
SSD: Intel 1TB(i forget the model) M.2 (Boot Drive)
NC: Asus AC68 802.11ac
2x Phantek stock case fans 140mm (Intake)
1x Noctua F12 IPPC 3000 RPM PWM Fan (Exhaust)
OS: Dual Boot, Primary: Ubuntu-Mate 20.04 64bit, Windows 10 64bit
Proprietary Drivers:  Bcmwl-Kernel-Source (AC68), Nvidia-450-Meta

Also I'm not very experienced with Linux so please bare with me.

---

### Post by CatKiller on 2020-12-12
If you've got the fan curve applied in the UEFI then there's nothing more that needs to be done, unless you've got some application in Windows that's turning off UEFI control of the fans.

To get more sensor readings you might need to use the out-of-tree [it87](https://github.com/a1wong/it87). If your UEFI *isn't* controlling your fans you can feed those sensor readings into fancontrol.

---

### Post by DuckHook on 2020-12-12
Welcome to Ubuntuforums dragoontufellow,

Have you done?: ```
sudo sensors-detect
```If not, please first do so. Then post all of output to this thread between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

Please note that I am referring to the whole sensors-detect process. Post all of that. It will be long, but you can scroll back across the output and select it with a mouse.

Then post output of: ```
sensors
```

---

### Post by dragoontufellow on 2020-12-12
Somehow it fixed itself. so I'll create a summery in case others have this issue.

before i posted i installed lm-sensors and fancontrol via terminal:
     **sudo apt install lm-sensors fancontrol**

then i ran both but nothing seemed to happen
     **sudo sensors-detect** (yes to all)
     **sudo pwmconfig**    (no fans detected)
**sudo sensors** (Tdie temp + Tctl Temp is all it detected)

then after posting this I went into BIOS and cranked my fans to max thinking if they won't adjust I'll just make it so they're always maxed so my CPU won't overheat. So I did that saved and exited logged back into Ubuntu checked Psensor again and voila fans detected
so i ran sensors detect again then ran sensors and all of it showed up. and after resetting my bios settings back to a fan curve it now works perfectly.

so what i think happened was because my BIOS by default is CSM and I forced it into UEFI without touching anything else it bugged out and when I re-adjusted the fan curve and saved my BIOS it updated the config and fixed the issue. I did mess around with my GPU drivers a little bit selecting the original open source driver but I didn't apply the setting, that might have had something to do with it but i doubt it, the other explanation I can think of is maybe when i installed fancontrol and restarted it began working but considering i restarted several times before and after changing bios settings i doubt this too however it's worth a shot if you're having this issue.

like I said I'm not very familiar with Linux and i've never experienced this previously but perhaps this will help someone else. I'm closing the thread I appreciate anyone who tried to help me Happy Holidays.

---

### Post by CelticWarrior on 2020-12-12
> [COLOR=#000000]so what i think happened was because my BIOS by default is CSM and I forced it into UEFI without touching anything else it bugged out [/COLOR]

No, not that.
First of all, BIOS and [UEFI]("https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#CSM_booting") are motherboards' firmware. If you have one you *don't *have the other. UEFI replaced BIOS a long time ago (a decade, give or take). So, you have UEFI, not BIOS (that same vendors still call it "BIOS" or "UEFI BIOS" doesn't make it so, it's simply wrong; "BIOS" is being dragged on due to the familiarity with it and perhaps because it's an easier acronym).

CSM =  Compatibility Support Module = Legacy > [COLOR=#202122][FONT=sans-serif]The [/FONT][/COLOR]*Compatibility Support Module allows legacy operating systems and some legacy [option ROMs]("https://en.wikipedia.org/wiki/Option_ROM") that do not support UEFI to still be used.*
In a nutshell, CSM/Legacy exists to allow older non-UEFI compatible OSes to be installed and soon it'll be a thing of the past, not soon enough though: > [COLOR=#202122][FONT=sans-serif]In November 2017, Intel announced that it planned to phase out support for CSM by 2020.[/FONT][/COLOR]

The Wiki link above has all you need to know about your firmware in an OS agnostic way, as it should be. The [Ubuntu's Community Wiki guide about UEFI]("https://help.ubuntu.com/community/UEFI") is complementary.

---

### Post by dragoontufellow on 2020-12-12
What i was trying to say is CSM was the default setting in order to install Ubuntu i had to change it as a result i think it bugged out, I'm not entirely sure what the difference is between UEFI and CSM, only that it makes a huge difference in how your OS communicates with the BIOS in this case I assume that my Bios was having a communication error with Ubuntu however i could be wrong this is my first computer with a CSM either way I listed everything i did between identifying the problem and fixing it in case someone else has a similar issue.

I don't know a whole lot about BIOS/Motherboard features i tend to specialize OS functionality and stability and a bit about computer hardware but when it comes to base level configurations I can only speculate based on logical assumptions rather than technicality.

---

### Post by CelticWarrior on 2020-12-12
I strongly suggest you read what I wrote and the links. That should be enough to understand the basics.

---

