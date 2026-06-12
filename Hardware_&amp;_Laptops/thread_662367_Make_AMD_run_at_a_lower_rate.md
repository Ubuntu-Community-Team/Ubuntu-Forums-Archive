---
title: "Make AMD run at a lower rate"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by TorchlightJay on 2008-01-08
Hey,

 So I was wondering if anyone knew of any tips or tricks on how to make AMD run at a lower rate. By that i mean make it run cooler or quieter or at a lower voltage. I know it's essentially going to run the way it's going to run but I've heard about Cool N Quiet for Windows and I was wondering if there was anything like that to make it run at a lower voltage. If you don't, that's fine, I just wanted to know.

---

### Post by jespdj on 2008-01-09
Maybe your computer is already automatically using Cool 'n Quiet. Or is there some reason to think that it doesn't?

First, try this: Right-click on the top panel of the screen. In the popup menu, choose "Add to Panel...". In the window that appears, scroll down to the category "System & Hardware". Select "CPU Frequency Scaling Monitor" and add it to the panel. You'll now have an indicator in the top panel that shows at which frequency the CPU is running. On my laptop, it runs at 800 MHz when it's idle, and jumps up to 2 GHz when busy.

If it really doesn't work, then install the package **cpufrequtils** using Synaptic, or from the command line:
```
sudo apt-get install cpufrequtils
```
Then use the command **cpufreq-info** to get information about CPU frequency scaling on your computer. Copy and paste the output here.

You can also search for "cpu frequency scaling" in the forums here and you'll find more info.

---

