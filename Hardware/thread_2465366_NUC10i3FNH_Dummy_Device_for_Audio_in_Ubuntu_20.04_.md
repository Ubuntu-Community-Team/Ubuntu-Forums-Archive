---
title: "NUC10i3FNH Dummy Device for Audio in Ubuntu 20.04 and 21.4"
date: 2021-07-30
forum: Hardware
---

### Post by lostphil on 2021-07-30
The FNH has no analog audio ports, but it does support digital HD audio out of the HDMI, USB and thunderbolt ports. I have the BIOS set with the HD audio enabled and the HDMI port as the primary. 

I have tried Ubuntu 20.04 LTS, 21.4, and Kubuntu 20.04.2 LTS, 21.4 with no avail. Also, I have tried several HDMI cables with my Vizio and Hitachi TV's. I tried searching the forums and asked questions and really did not come across anything that seems to fit my issue. 

Now I do have a USB audio dongle that does get found and setup that gives me audio out with no issue. So it does tell me it is an issue with the Intel digital HD audio hardware.

So at this point I do not know what to try next to get the HDMI audio working.

---

### Post by tea for one on 2021-07-31
It is difficult to offer pertinent advice because I doubt if any user has the exact same hardware to try and troubleshoot the problem.

Anyway, some general suggestions:-

Have you updated the Intel UEFI firmware to the most recent?
In your UEFI settings - Advanced > Boot > Boot Configuration > Windows 10 or Linux?
Have you installed [COLOR="#0000FF"]pavucontrol[/COLOR] - more sound settings to explore?
Possibly a setting in either of the TVs which obstructs the sound?
Do you have access to a PC monitor with speakers and HDMI input? 

The last question would add weight to your comment [highlight]it is an issue with the Intel digital HD audio hardware[/highlight]

I have an Intel NUC8i3BEH connected to a PC monitor with HDMI input and have not experienced any sound or video problem (although I've never connected it to a TV).

---

### Post by mIk3_08 on 2021-07-31
I don't think this device supports Linux Operating System because to tell you frankly Linux Operating Systems is more different from MS Windows.
We don't have any Plug n Play in here. Mostly, some hardware specially new one won't work completely on Linux it needs hardware code script/drivers so that it will 
run smoothly on Linux Operating System. Let me ask you something,
Thus the manual of your NUC10i3FNH says that it supports Linux Operating System? Because if it thus, 
you won't be able to encounter some difficulties running this device on Linux Operating System.
I don't think this device will work completely on Linux Operating System. As I said Linux is not Microsoft.

---

### Post by mIk3_08 on 2021-07-31
According to my research some like,
NUC7CJYH
NUC7PJYH
NUC7i3DNHE
NUC7i5DNHE
NUC7i7DNHE
supports Linux Ubuntu 16.04 but sad to say Linux Ubuntu Operating System 16.04 now just ended up support just this April 2021
But If you continue to use this device and run it using Linux Operating System, I advise you to change your Operating System
at your own risk and you might try to downgrade your Linux Ubuntu Operating System from 20.04 to 16.04.
Again, I remind you Linux Ubuntu Operating System 16.04 just ended up of support just this April 2021.
So, run it at your own risk.

---

### Post by lostphil on 2021-07-31
> **tea for one said:**
> It is difficult to offer pertinent advice because I doubt if any user has the exact same hardware to try and troubleshoot the problem.

Anyway, some general suggestions:-

Have you updated the Intel UEFI firmware to the most recent?
In your UEFI settings - Advanced > Boot > Boot Configuration > Windows 10 or Linux?
Have you installed [COLOR=#0000FF]pavucontrol[/COLOR] - more sound settings to explore?
Possibly a setting in either of the TVs which obstructs the sound?
Do you have access to a PC monitor with speakers and HDMI input?

The last question would add weight to your comment [highlight]it is an issue with the Intel digital HD audio hardware[/highlight]

I have an Intel NUC8i3BEH connected to a PC monitor with HDMI input and have not experienced any sound or video problem (although I've never connected it to a TV).

Yes, it has the latest UEFI firmware and it only has Linux on it. This NUC will only be a Linux PC if I can help it. ;)

I will try the pavucontrol and see if it works, but I think it will take a bit more to get the digital audio to work (Kernel and/or Driver Update), this model was released Q2 2021. The true part number is NUC10i3FNHN1 and a link to its specifications [https://ark.intel.com/content/www/us/en/ark/products/214604/intel-nuc-10-performance-kit-nuc10i3fnhn.html](https://ark.intel.com/content/www/us/en/ark/products/214604/intel-nuc-10-performance-kit-nuc10i3fnhn.html)

I have tried two different TV's with the same out come. Nether one had any settings for the HDMI audio, so I doubt that is the issue. A HDMI PC monitor with built in speakers or headphone jack was the next thing I want to try and see if that possibly works. The goal of this NUC is to be a TV PC that will be used to play music, videos and surf the web. the one thing I have found, at 4K every thing is tiny, so I will have to do some configuring with the icon and font sizes.

---

### Post by tea for one on 2021-07-31
> **lostphil said:**
>  this model was released Q2 2021. 

That is a very recent release date.
New hardware may need a later kernel.

There are many guides on the internet to install later kernels - may be worth investigating?

---

### Post by lostphil on 2021-07-31
> **mIk3_08 said:**
> I don't think this device supports Linux Operating System because to tell you frankly Linux Operating Systems is more different from MS Windows.
We don't have any Plug n Play in here. Mostly, some hardware specially new one won't work completely on Linux it needs hardware code script/drivers so that it will
run smoothly on Linux Operating System. Let me ask you something,
Thus the manual of your NUC10i3FNH says that it supports Linux Operating System? Because if it thus,
you won't be able to encounter some difficulties running this device on Linux Operating System.
I don't think this device will work completely on Linux Operating System. As I said Linux is not Microsoft.

Any PC will support Linux, you just have to be willing to write drivers and scrips that will fix the issues you encounter. That's what we did 25 years ago to make things work, and from how it was to how it is now, you don't know how easy you have it now. :P As for plug n Play, Ubuntu loaded the correct drivers for the USB audio dongle as soon as I plugged it in, which surprised me. It also seems that this model NUC does run Linux just fine other then the HDMI audio issue. 

Who reads the manuals for these things nowadays? I could not tell you if it says that it supports Linux or not since I did not read it. I went by what I found in the forums.

> **mIk3_08 said:**
> [COLOR=#000000]According to my research some like,[/COLOR]
[COLOR=#000000]NUC7CJYH[/COLOR]
[COLOR=#000000]NUC7PJYH[/COLOR]
[COLOR=#000000]NUC7i3DNHE[/COLOR]
[COLOR=#000000]NUC7i5DNHE[/COLOR]
[COLOR=#000000]NUC7i7DNHE[/COLOR]
[COLOR=#000000]supports Linux Ubuntu 16.04 but sad to say Linux Ubuntu Operating System 16.04 now just ended up support just this April 2021[/COLOR]
[COLOR=#000000]But If you continue to use this device and run it using Linux Operating System, I advise you to change your Operating System[/COLOR]
[COLOR=#000000]at your own risk and you might try to downgrade your Linux Ubuntu Operating System from 20.04 to 16.04.[/COLOR]
[COLOR=#000000]Again, I remind you Linux Ubuntu Operating System 16.04 just ended up of support just this April 2021.[/COLOR]
[COLOR=#000000]So, run it at your own risk.[/COLOR]

If you search the forums, you will see there are people running Ubuntu on older NUC10iXFNH units. Note: These are NUC's that analog audio outputs that I do not have on my model.
[https://ubuntuforums.org/showthread.php?t=2458952&highlight=NUC](https://ubuntuforums.org/showthread.php?t=2458952&highlight=NUC)
[https://ubuntuforums.org/showthread.php?t=2455766&highlight=NUC](https://ubuntuforums.org/showthread.php?t=2455766&highlight=NUC)
[https://ubuntuforums.org/showthread.php?t=2454330&highlight=NUC](https://ubuntuforums.org/showthread.php?t=2454330&highlight=NUC)

When I bought the one I have, I thought it was the older one by the description on Newegg. Which by searching the forums, thought it fully supported Linux. It just needed some minor tweaks.

---

### Post by lostphil on 2021-07-31
Yea, that is one of the things I am looking into, and there might also be a 3rd party driver out there as well.

---

### Post by mIk3_08 on 2021-08-01
> **lostphil said:**
> Any PC will support Linux, you just have to be willing to write drivers and scrips that will fix the issues you encounter. That's what we did 25 years ago to make things work, and from how it was to how it is now, you don't know how easy you have it now.

Yes I agree, that Linux can support any PC but then it is not that easy to other ordinary users to use not like us that is very fanatic to the world of computing. As what I have said that Linux is not Microsoft. Its the kernel that can easily handles the hardware to operate. It needs scripts/codes before it works. Linux kernel is design for hardware / software security reasons that's why Linux is best for server operations. That's why we have to conquer Internet because I believe that the masterpiece of Linux is to handle clouds, data center and etc. We are the number one in that field. When you say desktop just leave it to them, Microsoft. Though we have Linux as desktop due to some internet development job reasons, for us to easily accomplished the designated jobs we had. If only I have same hardware as you do, I'm sure I can run that device smoothly using the latest version of any Linux Distro. :-)

---

