---
title: "Why does my laptop work with Kubuntu 12.04, but not Ubuntu 12.04 and other OSs?"
date: 2014-07-03
forum: Hardware
---

### Post by Al1000 on 2014-07-03
Hi,

I had been looking for something to replace XP on my 10 year old Packard Bell EasyNote E6307 laptop, which has 768MB of RAM and this CPU:

> al@al-Packard-Bell-EasyNote:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 28
model name      : Mobile AMD Sempron(tm) Processor 3000+
stepping        : 0
microcode       : 0x41
cpu MHz         : 800.000
cache size      : 128 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt 3dnowext 3dnow up lahf_lm
bogomips        : 1603.51
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 32 bits virtual
power management: ts fid vid ttp

I assume that PAE being listed under ''flags,'' means that PAE is supported.

After trying to boot with a few distros I eventually found that Kubuntu 12.04 booted up just fine - which I subsequently installed after deleting XP and partitioning the hard drive to include a 1GB swap partition. I have now been using it for a couple of weeks without any problems. The only thing is that it's not very fast on this old laptop and VLC media player doesn't play videos on full screen smoothly, but I also use Linux Puppy which I installed (frugally) on another partition, so use VLC on it. I had previously been using various versions of Puppy in ''live mode'' for a couple of months when XP was still on the HD, and have also briefly used Ubuntu 12.04 and Mint 16 as dual boot systems on my desktop pc with XP, so have some limited experience with Linux.

Most versions of Puppy that I've tried work fine on this laptop, whereas most ''large'' Linux OS's do not, and I'm trying to establish why that is. While I'm absolutely  delighted with Kubuntu and am planning on installing the latest version on my desktop pc, it would be nice to have a slightly lighter long-term supported OS for this laptop.

As far as I can tell, the issue is related to the graphics. An ''under development'' version of Puppy I tried on this laptop hung during booting up, then made it slightly further (but still didn't boot up completely) after I remastered the ISO on my desktop pc, after installing a VIA graphics package to it that the developer kindly supplied.

Lubuntu 14.04 and Linux Lite 2.0 also both hung during booting up, after displaying an error message which mentioned ''via-ircc'' and ''device not available,'' then ''can't reserve'' and a long number.

Ubuntu 12.04 displayed the same error message but booted into ''low graphics mode,'' but I didn't know how to do anything from there apart from reboot the computer.

This is what ''lspci -v'' says about the graphics:

> VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A  [S3 UniChrome Pro] (rev 01) (prog-if 00 [VGA controller]) 
    Subsystem: Packard Bell B.V. Device c008 
    Flags: bus master, 66MHz, medium devsel, latency 128, IRQ 16 
    Memory at a4000000 (32-bit, prefetchable) [size=64M] 
    Memory at e1000000 (32-bit, non-prefetchable) [size=16M] 
    [virtual] Expansion ROM at a0000000 [disabled] [size=64K] 
    Capabilities: [60] Power Management version 2 
    Capabilities: [70] AGP version 3.0

Having used Windows since the '98 version I am well used to having to install hardware drivers when installing the OS, and have noted that Linux OS's include such drivers in the distro. Could it be that whatever graphics driver is needed for this laptop is included in Kubuntu, but not in the other OSs that didn't work, or is there another reason why Kubuntu works and the other OSs do not?

If they would work with an additional graphics driver, is there any way I can find out what it is, and install it? I suppose I would have to somehow install the graphics driver first, in order to be able to boot up, unless there is a remastering ISO application avaliable for larger Linux OSs like there is for Puppy?

Any advice much appreciated.

---

### Post by sudodus on 2014-07-03
Your computer is old and not powerful enough for standard Ubuntu. Several hardware devices are limiting the performance. I'm glad Kubuntu 12.04 LTS works for you. Probably you would also be successful with Xubuntu 12.04 LTS (but it is only supported until April 2015, while Kubuntu is supported until April 2017).

There are also other alternatives with lighter desktop environments that might play video better, that you find in the following links (and links from the links)

For old computers with lower specifications, you may :

[LIST]
[*]Read this link [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640") 
[*][COLOR=#696969]Try Lubuntu or Xubuntu 14.04 LTS (supported until April 2017) -- may be problems with your VIA graphics[/COLOR] 
[*]Try Xubuntu 12.04 LTS (supported until April 2015) 
[*]Alternative to Unity on 12.04 LTS : [Gnome Classic]("https://help.ubuntu.com/community/PreciseGnomeClassicTweaks") 
[*]Community re-spins based on Ubuntu 12.04 LTS: ***Bento, Bodhi*** and ***LXLE*** 
[/LIST]

Try them live before installing according to this link
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

---

### Post by Al1000 on 2014-07-03
Many thanks for the info and links, which I'll have a read through. 

Now I know it's a matter of getting the software to work with the hardware, rather than the other way around.

---

### Post by SeijiSensei on 2014-07-03
Your computer probably has one 512 MB and one 256 MB memory stick.  If so, you could replace the latter with another 512.  I did a quick search for your machine at crucial.com and saw only 256 and 512 MB parts.  

Adding memory is the quickest way to improve performance, but it looks like your computer's design doesn't support upgrading to, say, 2 x 1GB sticks.  Still the 512 MB part costs just $20 at Crucial, so it's a small investment that might pay off.

---

### Post by Al1000 on 2014-07-03
Thanks for the response. I believe you're correct about the RAM and I recently considered swapping the 256 MB stick for another 512MB stick, but I'm not sure how much of a difference that would make in this particular case. According to Conky system monitor, after a reboot, with VLC playing a low-ish resolution video in full screen, not altogether smoothly - with Conky displayed on top - the computer is using 46% RAM, 0% swap, but 100% CPU.

I have seen Kubuntu use up to around 20% of the 1GB swap partition after running applications for a while, and I've seen Puppy using over 40%, so I do get that more RAM would make it run faster under other circumstances, and might just upgrade it anyway.

---

### Post by SeijiSensei on 2014-07-03
There's really very little you can do about the video issue. Modern video compression formats like H.264 are very processor-intensive.  You could stick to watching material encoded in less-demanding formats like DivX/XviD.  Usually videos like these are distributed in the AVI container while H.264 encodes are most often stored in MP4 or Matroska (MKV).  Unfortunately most encodes use H.264 these days because of its higher quality.

Modern graphics adapters often include special hardware to decode H.264 so that the CPU isn't handling the load.  I doubt your machine could support upgrading to an adapter like that though. 

You could use something like ffmpeg or mencoder to convert an H.264 video to XviD, but that's rather a lot of work.  I did that when H.264 videos first appeared on the scene and my then desktop computer could not play them smoothly.  Eventually I solved the problem by buying a new NVIDIA card with [support]("http://en.wikipedia.org/wiki/VDPAU") for hardware decoding.

---

### Post by Al1000 on 2014-07-03
Thanks again for the info. I hadn't considered that different formats would have different loads on the CPU. Most of the videos I have downloaded recently have been in .flv format.

I recall downloading codecs and converting videos from one format to another back in the days of Windows '98, just to get them to display, but reckon the easiest thing for me to do with this laptop is to stick to Puppy for watching videos, as I have yet to come across one that doesn't play smoothly on VLC with it. While CPU usage sits at 100% using Kubuntu playing a video, it typically varies between around 60 - 70% using Puppy.

(Although after sudosus' advice and reading up on Xubuntu, I might give that a try instead of Kubuntu)

Interestingly enough though, when the computer is at ''idle'' with Conky the only application running, CPU usage with Puppy varies between around 3 - 7%, while with Kubuntu it sits steadily at 1%!

---

