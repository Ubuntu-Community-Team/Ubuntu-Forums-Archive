---
title: "use the correct driver/GPU"
date: 2018-01-02
forum: Hardware
---

### Post by mkschmidt on 2018-01-02
TL;DR: How do I make my PC use the MESA (or RadeonSI or whatever) drivers instead of i915?

I wanted to play DiRT Rally on my Ubuntu system. According to the recommended system specifications [COLOR=#ACB2B8][FONT=&quot]AMD GPU's require MESA 13.0.3 or better (tested)[/FONT][/COLOR]. I have a Radeon RX 480 4GB and am using the amdgpu-pro driver. And, sure enough, the game doesn't work with that driver. I don't know much about graphics drivers, so I looked around on the forums to see how to install MESA drivers. The forum posts I saw were a bit vague, some saying that MESA isn't a driver but rather a set of libraries, others saying that it comes pre-installed with Ubuntu. I tried uninstalling the amdgpu-pro driver, and the computer switched to MESA. I didn't even have to restart the computer. (That will be important later on.) I could play the game. However, in a few days I had to restart my computer. I found that the screen resolution had gone down, and I couldn't adjust it through the system settings. I found that the driver had switched from MESA to i915. So how do I have Ubuntu use the correct GPU and drivers for the job?
Also, it would be nice if anyone could link a beginner-friendly explanation of how these drivers work, because the ones that I found all required quite a lot of background knowledge. I'm not very familiar with the way Ubuntu/Linux graphics work.

System specifications:
Ubuntu 16.04 LTS
Intel Core i5-6400
XFX Radeon RX 480 4GB
16GB 2133 MHz DDR4

---

### Post by Yellow Pasque on 2018-01-02
Your post doesn't make sense to me (in multiple ways I don't feel like typing).

Post your /var/log/Xorg.0.log file. Use code tags.

---

