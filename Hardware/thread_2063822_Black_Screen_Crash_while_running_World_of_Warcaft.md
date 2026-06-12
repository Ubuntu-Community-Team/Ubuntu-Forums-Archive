---
title: "Black Screen Crash while running World of Warcaft"
date: 2012-09-27
forum: Hardware
---

### Post by locoguano on 2012-09-27
Under Ubuntu with Wine and under Windows World of Warcraft will crash to a black screen at random times. I can still hear sound, the computer doesn't seem to lock up, but the screen just goes black and requires a hard reboot to get it back. I resolved this problem under Windows by following these directions.

"I'm not sure if you've fixed your issue or not..but I too, have a Gateway P7805u and NONE of these suggestions (although great) will not help. It's a known issue with this laptop with the GPU..there IS a fix, however. This worked for me..been over 15 hours since a crash, and I even let wow stay open all day today.

1) Rivatuner
a) Download and Install rivatuner : RivaTuner v2.24c download from Guru3D.com (If installation doesn't work download this file and put it in the same directory as the installer: Download RivaTuner x64 signed Drivers | techPowerUp
b) Run Rivatuner and click the power user tab
c) Then go to RivaTuner \ NVIDIA \ Overclocking and click the plus button
d) Go to "EnablePerfLevelForcing" and double click the grey box next to it and enter the value "1"
e) Then go to RiverTuner \ Overclocking \ Global and under there go to MaxClockLimit and change the value to at least 200 (I have an older p-6860fx so I'm not sure what clock speeds yours is but it should be enough, but if it is not, then raise this)
f) Go back to the main tab and click the arrow button all the way to the right of the words "ForceWare decteded" and click on the icon of a gpu (system settings a.k.a system tweaks menu)
g) Once there set the "Force Constant Performance Level" to performance 3d
h) Expectedly, the clocks should be way lower than it should be (it's because the gpu's have an "extra 3d" profile that rivatuner doesn't support) If you did step e and set up MaxClockLimit correctly, just raise up the values to your default clocks in gpu-z (you may need to raise MaxClockLimit if you can't go all the way)
i) Then just check the "Apply Overclocking at Windows Startup" and the startup settings should matchc the clocks you want
j) Restart computer"

Because RivaTuner is not available for Linux, I am really not sure where to go with this. I do not want to dualboot or go back to Windoze, but... well... I am a WoW junkie!

Any help with accomplishing what is described in these directions under Ubuntu would be greatly appreciated.

---

