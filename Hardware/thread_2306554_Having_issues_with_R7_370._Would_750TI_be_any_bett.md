---
title: "Having issues with R7 370. Would 750TI be any better?"
date: 2015-12-16
forum: Hardware
---

### Post by ithinkibrokeit2 on 2015-12-16
I am experiencing the BSOD and I can't figure out how to install Ubuntu. I have an R7 370 and I have been posting in various places without luck. Could you please explain how one might go about using the open source driver so I might be able to install ubuntu? 

Thanks

My question concerns my inability to get Ubuntu installed at the  moment. I am able to boot to the installation medium, but it seems to be an issue with the graphics card. As the title states, I currently have an ASUS R7-370 and I am just wondering in terms of support/compatibility, would switching to an NVIDIA make any more sense.

---

### Post by deadflowr on 2015-12-16
How far into the install process have you gotten?

(Have you tried the nomodeset method; ie, when you first get the boot menu for Ubuntu you press F6 to open a dropdown menu, then toggle the option for nomodeset, the press esc to return to the main boot menu window and proceed with the installation)

---

### Post by QIII on 2015-12-16
Posts merged and moved to their own thread.

I have an R9 290X that works perfectly fine.  Although I have had no problems installing Ubuntu with AMD video adapters, deadflower has made a good suggestion for a first try with your issue.

---

### Post by ithinkibrokeit2 on 2015-12-16
> **deadflowr said:**
> How far into the install process have you gotten?

I can get to the menu, and I have tried 'nomodeset' and 'nolapic' in the settings before boot with no luck. After the settings menu, the screen flashes a couple of times but then goes blank. I have not been successful in getting further than that.

> **QIII said:**
> Posts merged and moved to their own thread.

I have an R9 290X that works perfectly fine.  Although I have had no problems installing Ubuntu with AMD video adapters, deadflower has made a good suggestion for a first try with your issue.

That's interesting.... I have been reading (for a couple of weeks) every sticky and post I can that addresses the proprietary vs. open AMD driver and how the blank screen could possibly be attributed to digital output, as I don't have any VGA connections. I don't know if there is a way of slipping in a driver for the installation process... or how you would even do that.

---

### Post by QIII on 2015-12-16
Do you get a "No signal" message on your monitor if you leave it be for 30 seconds or so?

---

### Post by ithinkibrokeit2 on 2015-12-16
> **QIII said:**
> Do you get a "No signal" message on your monitor if you leave it be for 30 seconds or so?

I can check in a couple of hours when I get home.

So to answer your question QIII, no it does not. It does however, stay on with a blank screen until the CPU gets hot enough to cook dinner. I was able to actually boot into Mint 17.2 Cinnamon, and I observed the following error messages. 

See attachments.

[ATTACH=CONFIG]266200[/ATTACH][ATTACH=CONFIG]266201[/ATTACH][ATTACH=CONFIG]266202[/ATTACH]


Edit: CPU usage was a little high. I imagine it has to do with the fact that the GPU isn't being utilized and is putting extra demand on the CPU. What's interesting, is that despite the 2nd picture givent options for the fglrx driver, if I click on it- it will just immediately revert back to x-org and changes won't stick.

---

### Post by QIII on 2015-12-16
I take it you are not able to install the driver on Mint, either?

Have you tried doing so via the terminal?

---

### Post by QIII on 2015-12-16
> **ithinkibrokeit2 said:**
> 
Edit: CPU usage was a little high. I imagine it has to do with the fact that the GPU isn't being utilized and is putting extra demand on the CPU. What's interesting, is that despite the 2nd picture givent options for the fglrx driver, if I click on it- it will just immediately revert back to x-org and changes won't stick.

OK.  When you use the GUI installer, do you immediately do 

```
sudo amdconfig --initial
```

afterwards and reboot?

This is not *supposed* to be necessary any more, but as often as I answer these question I am convinced it's a good thing to do.

---

### Post by ithinkibrokeit2 on 2015-12-17
> **QIII said:**
> OK.  When you use the GUI installer, do you immediately do 

```
sudo amdconfig --initial
```

afterwards and reboot?

This is not *supposed* to be necessary any more, but as often as I answer these question I am convinced it's a good thing to do.

What I neglected to mention previously is that I did not in fact *install* Mint. I was only able to get into LiveCD in compatibility mode trying your method would have been lost at reboot, so this morning I went ahead with an install. Your suggestion worked, so thank you! 

The question remains though, is a NVIDIA card like the 750 better supported? I mean I still don't know what to do for Ubuntu, so I'm wondering if I might be better off going to something else that won't cause as much hassle..? 

Thanks again QIII!

---

### Post by QIII on 2015-12-18
You will find fan boys on both sides.  I say use what works for you.  I have used AMD/ATI products for a long time, although I have used NVIDIA products along the way.  I'm not sure that one is better than the other.  You'll find roughly as many threads on the Forums asking for help with each.

What I can recommend, however, is reading some impartial reviews.  You can start with phoronics.com, although they have a bit of a chip on their shoulder because AMD sometimes seems to be in bed with Canonical.

If you are a gamer using Linux:  NVIDIA.  If you are a gamer on Windows:  AMD.  If you do GPGPU computing (like some distributed computing projects that have GPU clients): AMD.  If you don't care, pick one with the features you want at the best price, whichever OEM.

---

### Post by kurt18947 on 2015-12-18
My recent experience with Nvidia/AMD graphics. I'd run a low end Nvidia card (GT210?) with an AMD motherboard for some years because I thought Nvidia worked better. I had problems with suspend/resume while using the open source Nvidia driver but the proprietary Nvidia driver worked okay. I was watching RAM usage and there appeared to be a leak. For example a freshly booted ubuntu-gnome session might use around 400-500 MB. Use it for a while and RAM usage might rise to close to 800-900 GB running the same programs. Log out, log back in and RAM usage would be back to around 500 MB then begin to rise again. I uninstalled the Nvidia driver and card and used the onboard AMD graphics (HD4200 I think) No more memory leaks. I am not a gamer and don't run graphics heavy programs but so far so good. I've never tried to  install AMD proprietary drivers because I don't see the need.

---

### Post by Yellow Pasque on 2015-12-18
It could be a bad card. The aforementioned phoronix site had an R7 370 running with Ubuntu 14.04.3 and using the latest two releases of Catalyst:
[http://www.phoronix.com/scan.php?page=article&item=amd-crimson-linux&num=1](http://www.phoronix.com/scan.php?page=article&item=amd-crimson-linux&num=1)

Any chance you could test this GPU in Windows? Maybe also try a LiveUSB of Xubuntu 16.04:
[http://cdimage.ubuntu.com/xubuntu/daily-live/current/](http://cdimage.ubuntu.com/xubuntu/daily-live/current/)

As for the question of whether a GTX 750Ti would be a good choice, I've read a lot of satisfied reviews from folks running under Linux with the binary Nvidia driver, though with older versions of Ubuntu, folks had to use the 'nomodeset' hack to get Ubuntu to install.
I just got a GTX950 and it works well on Debian sid.

---

### Post by ithinkibrokeit2 on 2015-12-18
> **QIII said:**
> If you are a gamer using Linux:  NVIDIA.  If you are a gamer on Windows:  AMD.  If you do GPGPU computing (like some distributed computing projects that have GPU clients): AMD.

Interesting... 

[Edit: my interests are more in password cracking, and that sort of thing. Floating point precision is more important so I thought having an AMD card would provide greater compatibility with open-source drivers. Without being able to easily boot into Ubuntu though, I am starting to have concerns.]

> **kurt18947 said:**
> RAM usage might rise to close to 800-900 GB running the same programs. Log out, log back in and RAM usage would be back to around 500 MB then begin to rise again. 

Wow! :wink:

> **Temüjin said:**
> Any chance you could test this GPU in Windows? Maybe also try a LiveUSB of Xubuntu 16.04:
[http://cdimage.ubuntu.com/xubuntu/daily-live/current/](http://cdimage.ubuntu.com/xubuntu/daily-live/current/)

Sure, I'm willing to give it a shot. You want me to run the benchmark? Regarding Xubuntu, I can try..... but I haven't yet resolved the issue of getting past GRUB/blank screen on Ubuntu yet, just Mint.

---

### Post by QIII on 2015-12-20
If your interests are in password cracking, we won't help you further with this.

Please refer to the [Ubuntu Forums Rules]("http://ubuntuforums.org/misc.php?do=showrules"), in particular this section.

> Cracking: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed.

Closed.

---

