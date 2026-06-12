---
title: "Ubuntu 9.10 - resolution problem @1280x1024"
date: 2010-04-05
forum: Hardware
---

### Post by angelovarna on 2010-04-05
Hello, 
I installed Ubuntu 9.10 on my girlfriend's computer, everything is running great, except one - i have problem with the resolution. 
She has 17" LCD monitor (samsung) with 1280x1024@60 Native resolution. But Ubuntu let me to choose only between 640x480, 800x600, 1024x768, and from nvidia setting panel - 1154x1024 and 1360x768.
The video card is integrated (the motherboard is AsRock ALiveNF6G).

Can someone tell me how can I set the right resolution (1280x1024)?

Thanks in advance.

(I'm sorry for my bad English)

---

### Post by angelovarna on 2010-04-07
So, no one can help me? :(

---

### Post by angelovarna on 2010-04-10
Hello?

---

### Post by ubik89 on 2010-04-10
which video card do you have?

---

### Post by tgp1994 on 2010-04-10
> **angelovarna said:**
> Hello?

Ya, I'm having the same silence issue in my thread, too :P

Have you checked for proprietary updates with the Hardware Drivers utility?

---

### Post by angelovarna on 2010-04-10
Yes, i installed the latest nvidia driver. And the video card is integrated.

---

### Post by tgp1994 on 2010-04-10
> **angelovarna said:**
> Yes, i installed the latest nvidia driver. And the video card is integrated.

In my NVIDIA X Server Settings panel, (System>Administration), for the X Server Display Configuration, you can click the Advanced button and enter in a manual resolution. Give that a try.

---

### Post by angelovarna on 2010-04-11
I tried this but nothing happens. And also every time when i restart the computer, it runs in 1024x768 (the max resolution in xorg.conf, i tried to add 1280x1024 - without effect), so i have to start NVIDIA X server panel and set the resolution to 1154x1024.

---

### Post by tgp1994 on 2010-04-11
> **angelovarna said:**
> I tried this but nothing happens. And also every time when i restart the computer, it runs in 1024x768 (the max resolution in xorg.conf, i tried to add 1280x1024 - without effect), so i have to start NVIDIA X server panel and set the resolution to 1154x1024.

Hmm, got me then :S Maybe you can post about this on NVIDIA's forums (if this is proprietary, I think that's were it comes from.)

---

### Post by angelovarna on 2010-04-12
Under KDE (openSuse) everything was fine, but my girlfriend doesn't like it.

---

### Post by mastablasta on 2010-04-12
Perhaps you should try to change your girlfriend not the OS!? :P
 
But seriously, have you checked if monitor is propperly recognised? as i know some monitors also need "drivers" in Windows.
 
EDIT something is probably wrong in driver setting. I have a reversed situation with old ATI rage and widescreen monitor. In WinXP resolution is not propperly shown and screen is stretched. In Ubuntu it works good and has propper display resolutions to chooose from.

---

### Post by angelovarna on 2010-04-12
This is the monitor: [http://www.samsung.com/me/products/monitor/lcdmonitors/720n.asp](http://www.samsung.com/me/products/monitor/lcdmonitors/720n.asp)
Samsung SyncMaster 720n 17" (native resolution: 1280x1024@60)
I haven't problems with my widescreen Samsung 206BW which is 20.1" - 1680x1050, but my video card is GeForce 9600GT.
Thats why i'm thinking that the problem is in the xorg.conf.

---

### Post by _0R10N on 2010-04-12
Did you executed sudo apt-get upgrade?? I've recently installed ubuntu on my 
laptop and I was having screen resolution problem too. Upgrading 
installed packages solved the problem.

If this doesn't work, please post the output of lshw relative to your 
video hardware, so we can look for specific problems.

Kind regards!

_0R10N >>

---

### Post by angelovarna on 2010-04-13
Yes, its updated.
I tried with another distro - Linux Mint, but there is the same problem.

---

### Post by tgp1994 on 2010-04-13
> **angelovarna said:**
> Yes, its updated.
I tried with another distro - Linux Mint, but there is the same problem.

Well, we can for sure limit it down to an issue of the linux kernel (or something common in both distros) interacting with the hard ware. And I think you should still consider posting about this on NVIDIA's forums.

---

### Post by _0R10N on 2010-04-16
I had the same issue and it went away updating Ubuntu. I didn't need to look for a specific driver. So, if you didn't do it so far, try updating the whole system.

Kind regards!

_0R10N >>

---

### Post by tgp1994 on 2010-04-16
> **_0R10N said:**
> I had the same issue and it went away updating Ubuntu. I didn't need to look for a specific driver. So, if you didn't do it so far, try updating the whole system.

Kind regards!

_0R10N >>

Ya, that could have been a kernel update. And did 10.04 just come out?

---

### Post by caymahallesi on 2010-04-16
> **tgp1994 said:**
> Ya, that could have been a kernel update. And did 10.04 just come out?

Did you fix your screen resolution problem?
can you post your xorg.conf here?

---

### Post by tgp1994 on 2010-04-16
> **caymahallesi said:**
> Did you fix your screen resolution problem?
can you post your xorg.conf here?

Who, me? Why did you quote me, but not reference the quote at all :P

---

### Post by bitbandit999 on 2010-04-20
As a matter of interest, I have the same problem (being unable to select 1280x1024) and I am on Ubuntu 9.10 with Intel 4500MHD so it isn't an Nvidia issue. (Unless there happens to be the same issue with the Intel driver that exists with nvidia)

I have installed the latest updates - no change.

Were you able to configure 9.10 to use 1280x1024 eventually or just give up?

Thanks.

---

### Post by tgp1994 on 2010-04-20
> **bitbandit999 said:**
> As a matter of interest, I have the same problem (being unable to select 1280x1024) and I am on Ubuntu 9.10 with Intel 4500MHD so it isn't an Nvidia issue. (Unless there happens to be the same issue with the Intel driver that exists with nvidia)

I have installed the latest updates - no change.

Were you able to configure 9.10 to use 1280x1024 eventually or just give up?

Thanks.

Hmm, then I think it's either a bug in X11 or gnome. Most likely x11, since the OP was (or should have been) using NVIDIA's control panel.

---

