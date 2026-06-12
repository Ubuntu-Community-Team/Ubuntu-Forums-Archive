---
title: "Suspend/resume problem and temporary fix for Ubuntu 12.04"
date: 2013-09-01
forum: Hardware
---

### Post by thanuntu on 2013-09-01
I have already posted this [here]("http://ubuntuforums.org/showthread.php?t=1978290&p=12774948#post12774948") already, but I think that it would be more appropriate for me to create a new thread for this problem and its workaround. I have also asked a question [here]("https://answers.launchpad.net/ubuntu/+question/234952").

I have often had intermittent problems with suspend and resume functions on my laptop (Toshiba L505-141), a quite common problem as I understand. The worst part is that these seem to come and go with no apparent reason.
Recently, after a clean install of Ubuntu 12.04 (AMD64), I was happy to see that suspend/resume was working just fine. After some installations (kubuntu-desktop, gnome-shell etc) suspend was no longer working. After I closed the lid the laptop went tp suspend, but when I opened it it would go to a black screen, with the backlight blinking. The only solution was a reboot (either hard reboot, or Alt-Prtsc-REISUB).

Then I reinstalled and suspend was again working fine and I avoided installing "heavy artillery" like the packages above. Happily, I spent a whole week suspending/resuming my laptop by closing/opening its lid and I didn't have to reboot once. But _suddenly_ (I don't know how) the same problem occurred again! :mad:

I tried removing the packages I had installed after the latest stable state. The only one was catfish which is a very small and light package (I was using kernel 3.5.0-37): NOTHING
I tried dist-upgrading the kernel (to 3.5.0-39): NOTHING
I even tried with a kernel I had self-compiled for my CPU (from kernel 3.5.7-16): NOTHING

Taking inspiration from [this solution]("http://askubuntu.com/questions/9518/ubuntu-wont-suspend-anymore-but-it-did-upon-install/10579#10579"), I checked to see if I have acpi-support installed on my system. I did. But I also observed on the Software Center description page that:
> This program is run from [FONT=Courier New]acpi_fakekey[/FONT]

So, I opened a terminal, issued ```
acpi_fakekey
``` and closed my lid. Then I opened it again and... SUCCESS! My session resumed!
Then I closed my lid again and... NO RESUME.

Then I made several tests with three different kernel versions. The results: each time I issued a [FONT=Courier New]acpi_fakekey[/FONT] command BEFORE closing the lid I could suspend/resume.

So, I suspect that the [FONT=Courier New]acpi_fakekey[/FONT] command needs to be inserted at the beginning of the suspend sequence, and/or at the end of the resume sequence.

I am now using this temporary fix, but I am not marking this as SOLVED because it would be better to automate this process. I also have not filed a bug report because I am not using the latest BIOS and am very reluctant to update because this is a work computer and I cannot afford to have it bricked.

If anyone can propose an improvement based on this, it would be most useful.

---

