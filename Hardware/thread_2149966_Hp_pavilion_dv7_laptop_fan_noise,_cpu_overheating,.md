---
title: "Hp pavilion dv7 laptop fan noise, cpu overheating, slow graphics performance."
date: 2013-05-30
forum: Hardware
---

### Post by stelladeli on 2013-05-30
Hello,

I have an Hp Pavilion dv7 (4 years old) laptop with Ubuntu 12.10 (32-bit) and Windows 7 installed.

When I'm running Ubuntu, the fan never stops making noise and the laptop gets too hot even when idle and especially starts to lag when running Firefox and/or VLC player and/or Transmission BitTorrent Client simultaneously. CPU usage sometimes reaches 100% with a single Firefox window open (eg. streaming site).
On the other hand, in Windows 7 there isn't any fan noise and the laptop is cool while idle.

I run "sensors" and "sensors -f" commands on terminal and this is what I got with no processes running (CPU usage about 1-2%):
> 
acpitz-virtual-0
Adapter: Virtual device
temp1:        +93.0°C  
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +88.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +86.0°C  (high = +105.0°C, crit = +105.0°C)

acpitz-virtual-0
Adapter: Virtual device
temp1:       +199.4°F  
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +188.6°F  (high = +221.0°F, crit = +221.0°F)
Core 1:      +185.0°F  (high = +221.0°F, crit = +221.0°F)

Should I try installing Jupiter(on another thread the OP said that it didn't help) or cpufreq?  Disable discrete graphics? Any ideas how to resolve this?
Thanks in advance!

Specs: Memory 2.0 GiB, Processor Intel® Core™2 Duo CPU P8600 @ 2.40GHz × 2, /dev/sda5 Disk space used for Ubuntu 34%.

---

### Post by Yellow Pasque on 2013-05-30
> Disable discrete graphics?
What graphics do you have?
```
lspci | grep VGA
```

---

### Post by stelladeli on 2013-05-30
Thank you for replying, [[COLOR=#000000]Temüjin[/COLOR]]("http://ubuntuforums.org/member.php?u=327594").
This is what the terminal showed
> 01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI M96 [Mobility Radeon HD 4650]

---

### Post by Yellow Pasque on 2013-05-30
The open-source radeon driver is not good with power management on laptops. Try setting the power profile to low and see if it helps: [http://www.x.org/wiki/RadeonFeature#KMS_Power_Management_Options](http://www.x.org/wiki/RadeonFeature#KMS_Power_Management_Options)

Your other option is to use Ubuntu 12.04.1 and run the Catalyst Legacy driver.

---

### Post by Mark Phelps on 2013-05-30
If you want to reinstall using Ubuntu 12.04.1 (the LAST version that works with AMD restricted drivers and your card), you can download it from the link: [http://old-releases.ubuntu.com/releases/precise/]("http://old-releases.ubuntu.com/releases/precise/")

---

### Post by stelladeli on 2013-05-30
[[COLOR=#000000]Temüjin[/COLOR]]("http://ubuntuforums.org/member.php?u=327594"), your input has been very helpful!!!
I finally understand! I'm on to making the changes right now.

Currently the power method is profile "default". I'll set it first to "auto", because I find it less aggressive.

Mark Phelps, thank you also. A new installation will be the last thing I'll try. It will be extremely uncomfortable.

---

### Post by stelladeli on 2013-05-30
Okay, I have a problem. When I run "cat /sys/kernel/debug/dri/0/radeon_pm_info" or "sudo echo auto > /sys/class/drm/card0/device/graphics/fb0/device/power_profile" it says "Permission denied".
Right now I have no proprietary driver in use. Do I need one in order to apply the pm features?

From what I understand: Ubuntu 12.10 + xorg 1.13 + fglrx + Mobility Radeon HD 4650 = no good. (*Why AMD???*:()
And if I downgrade to xorg 1.12, there is chance to or will I surely break Unity? Should I try that, considering that I'm an absolute beginner?

So...how am I supposed to adjust the setting of power profile? Why is "Permission denied"? Should I do it as root? Any thoughts?

---

### Post by Yellow Pasque on 2013-05-30
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

```
echo "low" | sudo tee /sys/class/drm/card0/device/graphics/fb0/device/power_profile
```

---

### Post by stelladeli on 2013-05-31
Yes! Thank you so much!That did it! :D
After start-up the temperature went as high as 91°C (power_profile "default" and even with "auto"!!! :( ). Then I set it to mid and after awhile these were the changes:

temp1:  +91°C -> 68°C
Core 0: +86.0°C ->Core 0: +62.0°C 
Core 1: +83.0°C ->Core 1: +61.0°C

I feel that if I were to let the laptop stay idle a bit longer, the temp could have decreased a bit more.

Then I tried "low" just to check it out.The temp went as low as 60°C (Core 0: +54.0°C,  Core 1: +54.0°C).
Finally, the laptop was silent and waaaaay cooler than usual!!! :D Things sounded amazing on low!!!! I  was only running terminal and gedit.

I opened Firefox, temp started rising (not above 69°C), still less noisy and cooler than usual. With VLC also open, it went up to 75°C.

But I do think that I need to set it to "mid" profile, because I tend to go hard on the graphics (streaming, VLC etc) and I read on x.org/wiki that "low" could cause display problems on some laptops. Either way "mid" and "low" seem to feel the same, when I have processes running.
What would your opinion be on that matter? Mid or low is a better choice?

---

### Post by stelladeli on 2013-05-31
Okay, to make this setting executable on every boot-up, this is what I did (Solution I found at a thread on [https://forum.ubuntu-gr.org/viewtopic.php?p=247573](https://forum.ubuntu-gr.org/viewtopic.php?p=247573). They also give a solution for Ubuntu 13.04):

Opened up a terminal window, typed
```
gksu gedit /etc/rc.local
```
and in the penultimate line, one line above ***exit 0***, I typed
```
**(sleep 30 ; echo low > /sys/class/drm/card0/device/power_profile) &**
```
saved the file, closed it and restarted Ubuntu.

[FONT=trebuchet ms]Then, after giving the ```
cat /sys/class/drm/card0/device/power_profile
```[/FONT][FONT=trebuchet ms] it returned "low", just as I had set it to be!

My laptop is certainly less noisy , but still quite hot sometimes(78°C, even 88[/FONT][FONT=trebuchet ms][FONT=trebuchet ms]°C[/FONT]). I will experiment with mid and low and see what works best for me. Nevertheless, this seems to be the only solution considering that I still want to run Ubuntu 12.10 and not 12.04.

I have only one last question. [/FONT][FONT=trebuchet ms][FONT=trebuchet ms]In an attempt to solve the problem, [/FONT]I added a ppa to my system and installed some fglrx packages. Afterwards I regretted it, since this wasn't going to help me with my Radeon and wanted to remove whatever I had installed. I think I did that through Software Sources. I opened Synaptic Manager and noticed that I had fglrx and fglrx-amdcccle installed. I couldn't remember if these packages were pre-installed and I removed them. Do I need these packages? I feel that my laptop is a tad slower.... Does fglrx have anything to do with that?

Thanks to all of you![/FONT]:)[FONT=trebuchet ms]
[/FONT]

---

### Post by stelladeli on 2013-07-02
The situation persists, in fact it has been aggravated. Although I have a low power profile set, from the moment I boot the laptop the temperature rises uncontrollably and the fan makes too much noise. 
Flash player runs incredibly slow, firefox pages go often "unresponsive" for some seconds, and the laptop is burning (reaching 103[FONT=trebuchet ms]°C)[/FONT].

Could it be because I have never dust cleaned the fan?

Is downgrading to ubuntu 12.04 the only solution?

Please, any advice would be greatly appreciated!
Thanks.

---

### Post by Yellow Pasque on 2013-07-02
Ubuntu 12.04.1 might be the best solution for the moment. The open-source radeon driver is getting better power management, though: [http://www.phoronix.com/scan.php?page=news_item&px=MTM5NjE](http://www.phoronix.com/scan.php?page=news_item&px=MTM5NjE)

Hopefully, Ubuntu 13.10 will incorporate those changes.

---

### Post by stelladeli on 2013-07-02
Yes, hopefully.
I was so excited to finally install Ubuntu, I never thought it would make my computer experience sometimes worse than it was before on Windows. I wish I knew about this beforehand and installed 12.04 instead.
Thank you for your time.

---

### Post by stelladeli on 2014-06-20
_Final update_:
1. Cleaning up the inside of the fan, dramatically relieved the problem!!!!
2. Now, the clean fan combined with the "forced" low profile graphics performance, my laptop runs in relatively normal temperatures (around 50-60[FONT=trebuchet ms]°C). This behaviour is similar to the one I observe in Windows 7.[/FONT]
3. Yes, the general problem with my Graphics Card performance (AMD Radeon HD Mobiility 4650/5165) is still existent, both in Ubuntu 12.10 and in Ubuntu 14.04 [which I am currently using (I switched from the default "dpm dynamic power management" to the "low profile"]), since AMD isn't supporting my card with a proprietary driver compatible with latest kernels.
4. I will be patiently awaiting a proper resolution by either AMD/ATI or Canonical.

---

