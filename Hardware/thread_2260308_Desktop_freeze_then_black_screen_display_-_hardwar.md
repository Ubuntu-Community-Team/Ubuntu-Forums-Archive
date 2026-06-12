---
title: "Desktop freeze then black screen display - hardware failure?"
date: 2015-01-10
forum: Hardware
---

### Post by altosch on 2015-01-10
Hi, 

I have this 4 years old laptop HP ProBook 4525s with Kubuntu 14.10 (detailed specs below) .
Now my laptop display (LVDS) is just black while the computer seems to work fine with an external monitor.

What  happened:

One day my desktop suddenly got frozen. I could move the mouse cursor but nothing responded. So I connected via SSH, checked running processes and I saw nothing suspicious. Then I tried to take down whole KDE with “[FONT=courier new]service lightdm stop[/FONT]”. Nothing happened so I did “[FONT=courier new]shutdown -r now[/FONT]”. The laptop restarted but with black screen: no logo, no bios messages, no backlight, nothing. I connected an external monitor and it worked. I restarted again and preformed memtest86 – no errors. I thought the display is dead.

But in about two days I forgot to connect the power adapter, drained the battery, the laptop turned off. When I turned it back on, the display suddenly lit up and worked as normal. 

In a few days it froze again, ssh connection worked and after that the screen was black too. In that time I already knew about a hard reset: disconnect everything, disconnect the AC power adapter, remove the battery, press and hold the power button for at least 15 seconds, reconnect the AC power adapter (but do not connect the battery), press the power button. It helped – my display worked again. This happened about 4 times in about 2 weeks.

However after the last occurrence I can't get the display to work no matter what I do. The laptop works with the external monitor connected via HDMI just fine. No freezes. The computer doesn't see its display at all. In “System Settings / Display and Monitor” I can see the external one only. **[FONT=courier new]xrandr[/FONT]** says “[FONT=courier new]HDMI-0 connected primary[/FONT]” but no trace of LVDS. **[FONT=courier new]xvinfo[/FONT]** says “[FONT=courier new]screen #0 no adaptors present[/FONT]“. SMPlayer and VLC don't work. Mplayer says „[FONT=courier new][VO_XV] It seems there is no Xvideo support for your video card available.[/FONT]“ and it uses x11. It seems weird to me. Why it doesn't work with the external monitor?

**Please help me:** is this a hardware failure? Should I replace my LCD? What can I do to make sure?

Thanks.



Details about my computer:

HP ProBook 4525s
[http://h20565.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c02176972&DocLang=en&docLocale=en_US&spf.passkey=on&jumpid=reg_r1002_usen_c-001_title_r0004#N102B9](http://h20565.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c02176972&DocLang=en&docLocale=en_US&spf.passkey=on&jumpid=reg_r1002_usen_c-001_title_r0004#N102B9)

**[FONT=courier new]lspci -nn | grep VGA[/FONT]**
[FONT=courier new]01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Park [Mobility Radeon HD 5430/5450/5470] [1002:68e0][/FONT]

Kubuntu 14.10: [FONT=courier new]Linux 3.16.0-28-generic #38-Ubuntu SMP Fri Dec 12 17:38:37 UTC 2014 i686 athlon i686 GNU/Linux[/FONT]

---

