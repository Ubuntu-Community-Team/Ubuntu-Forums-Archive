---
title: "Cyborg R.A.T. 7 Mouse Issues (even after applying xorg.conf fix)"
date: 2011-09-10
forum: Hardware
---

### Post by mpmistr on 2011-09-10
I am running Ubuntu 11.04, Unity 3D, ect

I recently purchased a RAT 7 and I knew it wouldn't work out of the box with Ubuntu but I did add the extra config settings to my xorg.conf to fix the inability to click or drag windows issues after a short period of time.

Section "InputClass"
        Identifier "Mouse Remap"
        MatchProduct "Saitek Cyborg R.A.T.7 Mouse"
        MatchDevicePath "/dev/input/event*"
        Option "ButtonMapping" "1 2 3 4 5 6 7 2 9 10 11 12 0 0 0"
EndSection

However I notice that when dragging windows, icons, ect it is very very  jerky. Moving a window causes the entire window to just 'fly' across the screen, where I once had fluid motion of my windows (wobbly windows enabled) it is very erratic now. I tried my old mouse, a Logitech MX518 and I do not see the issue. With the MX518 everything is very fluid and work's great.

I know this is a very high DPI mouse (and I did hear that high DPI mice + xorg = bad), and I've tried a few configuration changes to lower the DPI but none of these have worked.

I found some information about being able to lower the sensitivity by creating a file called 10-x11-input.fdi

sudo gedit /etc/hal/fdi/policy/10-x11-input.fdi
<match key="info.capabilities" contains="input.mouse">
<merge key="input.x11_options.AdaptiveDeceleration" type="string">7</merge>
</match>

I've increased the number very high (as higher makes the mouse sensitivity slower, in theory) but this has not worked. I've also tried setting Option "Resolution" "XXXX" going as low as 300dpi (assuming this affects DPI?) with no results.

Anyways like I said I didn't really figure this mouse would work 100% under Ubuntu but if there is a fix out there for this, that would be awesome.

If system specs matter. I am running the following:
i5 2500k 3.3ghz quad core
16gb ddr3 memory
128gb M4 Crucial SSD
NVidia GeForce 460 GTX 768MB with the 270.41.06 propriety driver

Thank you for reading.

---

### Post by jonerich on 2011-12-26
Did you ever figure this out? Ive got the same problem.

---

