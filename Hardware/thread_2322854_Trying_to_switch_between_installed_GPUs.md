---
title: "Trying to switch between installed GPUs"
date: 2016-04-30
forum: Hardware
---

### Post by drewhamm7292 on 2016-04-30
[FONT=Verdana]Alright guys here's the deal. I have a MSI 390 that I'm currently using on my Windows install. The problem is I would much rather use Linux instead for all the games that I can and only switch to Windows for games I can't play under Linux. I have a feeling the majority of you know that AMD's Linux drivers are absolute garbage though so I'm not currently able to do that.[/FONT]
[FONT=Verdana]I have my old 2 GB 960 sitting on my shelf so I was wondering if I could install it in my second PCI slot and use it while I was in Linux and then use the 390 under Windows. Is there any way to do this without having to constantly either switch the cards or power connectors? I would like to have both installed but have my install only recognize the Nvidia card in the second PCI slot. Any help would be greatly appreciated.[/FONT]

---

### Post by T.J. on 2016-05-01
[FONT=tahoma]Hi, Drew! [/FONT]:D[FONT=tahoma]

The short answer to your question or questions is: yes.  We will have to take this a step at a time. [/FONT][FONT=tahoma]How you do this depends greatly on your equipment, your setup, and your willingness to try different things until you succeed.  

The first thing you need to be aware of is that if you have a AMD card and a Nvidia card in the same machine, your computer's firmware might shutdown one or more the cards because it can't decide if you are trying to use SLI/CrossFire.  It may not even boot up.  You should update your BIOS/UEFI firmware to the latest version before you even try.  You may have to try switching the cards' slots in order to get it to boot up.

[/FONT][FONT=tahoma]What you do after that depends on your setup.  You didn't say if you are using a KVM, dual booting or something else.  One thing you may need to do [/FONT][FONT=tahoma]blacklist the driver for the card that you don't want Linux to use, so that Linux doesn't try to use it on auto-detect.

[/FONT]
If you can tell me if you plan to dual-boot or something different, I can be more specific.

For example, I use an AMD 6870 and am Nvidia 960 in the same machine.  I have one card dedicated to Windows and one to Linux.  I do not dual boot. I use a KVM with video passthrough to run Windows.

---

### Post by QIII on 2016-05-01
> I have a feeling the majority of you know that AMD's Linux drivers are absolute garbage though so I'm not currently able to do that.

News to me.  Particularly since AMD is working very hard with the open source community (in particular Canonical) to bring together a genuinely useful open source driver (AMDGPU) that the proprietary Linux driver (AMDGPU Pro with Vulkan) will use as a base later this year.

I've been using AMD graphics cards for years without any problems at all.  Admittedly, before AMD bought ATI, the support was terrible.  But that was 8 or 9 years ago.  Still, the old ATI reputation has gotten stuck to AMD.

Have you asked anyone about any difficulties you have had with AMD cards in the past?

---

### Post by T.J. on 2016-05-02
I think Drewhamm is referring to the fact that Radeon cards regardless of generation, have been "hit or miss" compared to Nvidia's level of user support, which supports generations of cards, with better features, and far longer than AMD does with theirs. 

Most Linux users just use the open driver, but the open driver doesn't have support for OpenGL 4.  Gamers or CAD  now they are totally left out in the cold when their OS is upgraded. As salt to the wound, the FGLRX driver has had longstanding bugs for years, such as cursor corruption, which AMD never fixed. AMD has depreciated the FGLRX driver before Mesa gets the OpenGL 4.2 support quite right in the open Radeon driver, so their suggested replacement is less functional. 

Eventually depreciating cards is fine, but depreciating cards that are  older than 2011 en-mass is a bad policy when a significant number of users still need that OpenGL 4 support.  They should have staggered the  cut-offs.  Most people use their video cards for at least 3-6 years,  which means a significant number of people are still using older cards  that are suddenly no longer supported.  Combine  that with the fact that the only cards guaranteed to work with the  replacement AMDGPU driver are the R9 series - 2013 or newer, since certain R7s are  disabled by default - and I'd be angry too. That means the only non-Windows users with guaranteed support from AMD own cards that are less than 3 years old. 

 This is a problem AMD has really bungled.

---

### Post by drewhamm7292 on 2016-05-03
T.J. I honestly until this build only ever had one HD in a machine. My plan was to install Mint on a 500gb mechanical drive and keep Windows installed on my SSD. I was just going to use GRUB to switch between them. 

On the other subject I don't mind working out issues, I honestly enjoy the challenge. How would I go about blacklisting the AMD card?

---

### Post by drewhamm7292 on 2016-05-03
> **QIII said:**
> News to me.  Particularly since AMD is working very hard with the open source community (in particular Canonical) to bring together a genuinely useful open source driver (AMDGPU) that the proprietary Linux driver (AMDGPU Pro with Vulkan) will use as a base later this year.

I've been using AMD graphics cards for years without any problems at all.  Admittedly, before AMD bought ATI, the support was terrible.  But that was 8 or 9 years ago.  Still, the old ATI reputation has gotten stuck to AMD.

Have you asked anyone about any difficulties you have had with AMD cards in the past?


AMD has absolutely abysmal drivers for gaming. I am getting 15 to 20 less FPS in my games with the 390 than with the 960. Considering in Windows the 390 consistently beats the 970 and destroys the 960 I see that as driver issues. Everyone else I've spoken to has said the exact same.

---

### Post by T.J. on 2016-05-03
> **drewhamm7292 said:**
> T.J. I honestly until this build only ever had one HD in a machine. My plan was to install Mint on a 500gb mechanical drive and keep Windows installed on my SSD. I was just going to use GRUB to switch between them. 

On the other subject I don't mind working out issues, I honestly enjoy the challenge. How would I go about blacklisting the AMD card?

You need to: 

1. Create file in /etc/modprobe.d/.

[I]sudo nano /etc/modprobe.d/radeon.conf

[/I]2. Add a line to block the radeon driver from being loaded[I]

blacklist radeon
[/I]
3. Save it, and reboot.

You may have to add an additional file to block HDMI sound for the card if it has HDMI, and you do not want the driver to load.

After reboot, you can verify the results using the *lsmod *command to see what drivers are being loaded.  After that works, we can get to whatever next steps you need to get things right. =)

---

### Post by T.J. on 2016-05-03
> **drewhamm7292 said:**
> AMD has absolutely abysmal drivers for gaming. I am getting 15 to 20 less FPS in my games with the 390 than with the 960. Considering in Windows the 390 consistently beats the 970 and destroys the 960 I see that as driver issues. Everyone else I've spoken to has said the exact same.

Most of the Linux games are ported around Nvidia's implementation of  OpenGL, so if you are going to game on Linux, it's your best bet.

FPS in games is not a good judge of a video card's performance as the games are generally optimized for one card or another.  When Valve optimized their games for Linux, they were able to achieve much higher frame rates. You are right though,  AMD's drivers for Linux are pathetic.  They are trying to fix that with a totally new driver, but as I mentioned above, they needed to plan it better.

That is not to say that Nvidia's are perfect.  The 900 series uses signed firmware, which makes it harder for developers to create an open driver.  Where Nvidia excels is that their Windows driver and Linux driver share the same codebase.  That means that the performance is fairly equal regardless of the OS as far as the driver is concerned.  (That does not factor in the fact that X11 requires indirection to use the card as it can't handle hardware acceleration directly.)

---

