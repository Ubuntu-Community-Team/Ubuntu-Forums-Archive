---
title: "PLS HELP! HP nx6325 Sound is not woriking"
date: 2008-03-13
forum: Hardware &amp; Laptops
---

### Post by kribel on 2008-03-13
Hello!

Since a few days I try to configure my soundcard and nothing helps.
I installed Ubuntu 7.10 on my HP nx6325 laptop.

My Hardware:
Notebook: HP nx6325 (EY350EA)
CPU: AMD Turion 64 X2 TL-52
Screen: 15" 1400x1050
Soundkarte: ATI SB450 HDA Audio (rev 01), ADI1981HD CODEC

Here is my problem description:
1. I installed Ubuntu 7.10
[INDENT]+ sound was working[/INDENT]
[INDENT]+ quick launch buttons were working[/INDENT]
[INDENT]- microphon was not working[/INDENT]

2. I tried to intall ALSA driver after this description [http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0]("http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0"). The problem is, I could not find the "modules.conf" file.
[INDENT]- Nothing worked! The LED on the mute key was illuminated.[/INDENT]

3. I executed "alsaconf" in a shell
4. I installed the linux-backspots-modules.
[INDENT]+ Sound is working[/INDENT]
[INDENT]+/- Microphone is working only a few minutes[/INDENT]
[INDENT]- Quick Launch Buttons are not working[/INDENT]
[INDENT]- the volume control is strong non linear[/INDENT]

What shoud I do to get working the Quick Launch Buttons, the microphone and to linearize the volume control?

Best Regards
Konstantin

---

### Post by earth_consumer on 2008-03-13
try my post.... I hope it helps, it worked for me

[http://ubuntuforums.org/showthread.php?t=723742](http://ubuntuforums.org/showthread.php?t=723742)

---

