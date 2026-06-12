---
title: "Best Nettop?"
date: 2010-01-01
forum: Hardware
---

### Post by stillnotcool on 2010-01-01
Hi folks,

Forgive me if this has already been discussed; however, I couldn't find a straightforward thread on nettop devices through forum searches.

What is the most "Ubuntu friendly" nettop box currently on the market?  By this I mean: Which of the currently available nettop devices requires the least post-install configuration after a fresh installation of Karmic (full/standard desktop version).

I'm asking because I'm thinking about purchasing a nettop as a simple desktop machine for daily tasks like Web browsing, email writing, word processing, etc., and am hoping a nettop like the Acer AspireRevo, Eee Box, or Levnovo Q110 would suit my needs.  I may also attach some external devices for CD/DVD ripping and storage.  Of course, I wish to use Karmic as my primary OS but want to avoid as many post-unstallation shenanigans as possible.

Thanks in advance for your help, stories, recommendations, and instructions.

---

### Post by rwigle on 2010-01-06
I am also considering an ubuntu nettop, AND I am puzzled there have been no postings. 

The system76 meerkat [http://system76.com/product_info.php?cPath=27&products_id=91](http://system76.com/product_info.php?cPath=27&products_id=91) looks just right, but I worry about the (apparent) hassle with the way they handle customs/tax. (THis is related to delivery to Canada.)

In Canada, the Dell Optiplex 780 (small form factor one) is both expensive AND, it seems, can't be bought here with Ubuntu.

---

### Post by Kevbert on 2010-01-06
I'm still waiting for my Acer Revo R3610 which comes with Win7 as standard. When I eventually get it I'll be trying out Ubuntu on it. Has anyone got any experience of this nettop ?  I've seen reports that Vista is poor on this nettop (but is very resource hungry on most PCs).
It has the same processor as the Meercat.

---

### Post by stillnotcool on 2010-01-06
Thanks for replying!  I was beginning to think my initial questions were of interest to no one but me.

rwigle: I agree that System76's Meerkat looks like an excellent machine.  The fact that I could outfit one of the ION boxes with an internal CDROM drive makes it even more appealing.

Kevbert: When your Revo arrives, please do give us as many details as possible!  I'd like to know how a basic desktop environment functions on one of those (as the price is certainly right).

---

### Post by Kevbert on 2010-01-07
Just found [this]("http://ubuntuforums.org/showthread.php?t=1202852&highlight=install+pendrive") for the Revo R3600 (the one before mine). Looks like there's going to be a bit of a delay before I get mine...
It also looks like the XMBC frontend is also being use by some Revo users.

---

### Post by Kevbert on 2010-01-11
Finally got my new Revo R3610. I've dual booted Ubuntu 9.04 with Windows 7 and it works like a dream. Atheros Wireless and Nvidia Ion graphics work out of the box with no additional drivers required (I haven't tried compiz though).  
I'll try and write a HowTo when I get a chance as there are one or two things that you may want to consider when installing.
Now if only I could work out why Windows and Ubuntu only see 3Gb and not the 4Gb installed (may be a BIOS thing)...

---

### Post by stillnotcool on 2010-01-11
Thanks for the update, Kevbert.  For what purposes are you using your Revo, and what kind of performance are you experiencing?  I look forward to your guide.  Please do write one!

Also: I don't suppose your trouble with the operating systems not seeing 4GB of RAM would have anything to do with the 32-bit RAM limitation issue, would it?  Are you running 64-bit versions of Jaunty and Win7?

---

### Post by Kevbert on 2010-01-11
Both are 64 bit versions. The two main reasons I got the machine are to record CCTV video and to update a website on local weather data from my weather station.
I've tried running Boxee on it but unfortunately it doesn't seem to work (may be CPU or Nvidia compatibility problem - will try on my main 64 bit desktop if I get a chance). Will try out XBMC later (installed OK, and maybe Miro). Don't intend to install/run Compiz or Conky.

Edit...
Tried out both Miro and XBMC and they were poor using default display driver. Miro was jerky on HD video and XBMC was so ssssllloooowwww. Found out that I needed to install a different driver and everything is now just brilliant.
Regarding the memory problem I'll contact Acer as Win7 says I have 4Gb physical but only 3Gb available and Ubuntu only ever sees 3Gb. There's no BIOS setting to change this (BIOS options are pretty basic).
I'll post all the info in a new thread / HowTo

The Boxee problem is due to a 32 bit library file being the wrong revision. Getlibs does not resolve the problem in 9.04 64 bit.

[[COLOR="Red"]See this thread.[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1379320")

---

### Post by teh603 on 2010-01-31
My dad's using an Acer AspireRevo 1600 that I installed Jaunty on, and it seems to be working just fine. Sound and 3D accelleration don't work without the nVIDIA driver that I don't know how to install, but I can always wait for Lucid to get that thing working. They're not that important to him. He uses it to check his email, mom uses it to read the lolcats on icanhascheezburger.com, and that's about it.

It seems to share a good chunk of the Acer Aspire One BIOS, in that f12 is the key for calling up the boot device menu.

---

### Post by Kevbert on 2010-01-31
With regards to nVidia effects you may need to install the driver via Synaptic (nvidia-glx-180) and you also will want to install nvidia-settings (manager).
With sound, what is the terminal output of
```
lshw -c multimedia
```
It may be necessary to add the line
```
options snd-hda-intel model=acer
```
to the end of your /etc/modprobe.d/alsa-base file (or something similar depending on the output of the previous command).

---

### Post by teh603 on 2010-02-01
```
(redacted):~$ lshw -c multimedia
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: MCP79 High Definition Audio
       vendor: nVidia Corporation
       physical id: 8
       bus info: pci@0000:00:08.0
       version: b1
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
(redacted):~$ 
```

Edit: If I'm reading this right, why is it using an Intel driver for an nVidia chip?

---

### Post by Kevbert on 2010-02-01
That's correct. Mine (for my Revo R3610) reads exactly the same. So far I've have not encountered any sound problems. I've attached my /etc/modprobe.d/alsa-base.conf file (as that may help if you're still having problems).

---

### Post by Bendemann on 2010-02-01
Does the optical port work, too (DTS, AC3)?

---

### Post by teh603 on 2010-02-01
> **Kevbert said:**
> That's correct. Mine (for my Revo R3610) reads exactly the same. So far I've have not encountered any sound problems. I've attached my /etc/modprobe.d/alsa-base.conf file (as that may help if you're still having problems).

You do realize I can't make heads or tails of that file, right?

I'm one of the few Linux users out there who isn't a programmer.

---

### Post by Kevbert on 2010-02-02
Bendemann. The optical port is an SPDIF. Personally I haven't tried it, but believe that it works under Ubuntu. I have no means of checking it.

teh603. I'm not a programmer either, but still like to dabble and try things out. I assume that you're sound is still not working. You could take a look at this [COLOR="Red"][thread]("http://ubuntuforums.org/showthread.php?t=843012")[/COLOR] (which is a bit long) and [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1395189") thread (especially the last post).

---

### Post by Bendemann on 2010-02-02
Thanks Kevbert,

and is the audiochip from Nvidia, too, or is it stuff like Realtek? Can you post lspci please?

---

### Post by Kevbert on 2010-02-02
> **Bendemann said:**
> Thanks Kevbert,

and is the audiochip from Nvidia, too, or is it stuff like Realtek? Can you post lspci please?

Terminal commands for R3610:
```
$ lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
03:00.0 VGA compatible controller: nVidia Corporation Device 087d (rev b1)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
$ lsusb
Bus 002 Device 002: ID 04f2:0963 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
The audio (along with most other devices) is nVidia based. See also my [[COLOR="Red"]thread on the R3610.[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1379320") This details additional information on the R3610 along with links to details on the Intel chipset and nVidia motherboard.

---

### Post by teh603 on 2010-02-02
Aparrently the 180 driver doesn't support the ION chipset, but the 190 driver does. So it looks like its just a matter of waiting until Lucid for proper integration?

---

### Post by Kevbert on 2010-02-02
> **teh603 said:**
> Aparrently the 180 driver doesn't support the ION chipset, but the 190 driver does. So it looks like its just a matter of waiting until Lucid for proper integration?

I'm using the 180.44 driver (see attached screenshot) and have just tried running Compiz (the cube) with no problems. Also HDTV via web works fine.

---

### Post by teh603 on 2010-02-02
Odd. Didn't seem to work on mine at all. It killed the basic gnome screensavers as well.

---

### Post by Kevbert on 2010-02-03
Jaunty works for me. The driver was not installed by default, but had to be installed via Synaptic. 
The problem was that the graphics seemed to work immediately out of the box, but once I tried doing anything there was some screen corruption/display lag. The system said no proprietary drivers were being used and none were required for the graphics, hence the reason I had to install via Synaptic.
Karmic must work as there's an article on Boxee on the Revo in the latest Full Circle magazine (see my thread for link). Boxee on Jaunty doesn't work for me.

---

### Post by teh603 on 2010-02-03
> **Kevbert said:**
> Jaunty works for me. The driver was not installed by default, but had to be installed via Synaptic. 
The problem was that the graphics seemed to work immediately out of the box, but once I tried doing anything there was some screen corruption/display lag. The system said no proprietary drivers were being used and none were required for the graphics, hence the reason I had to install via Synaptic.
Karmic must work as there's an article on Boxee on the Revo in the latest Full Circle magazine (see my thread for link). Boxee on Jaunty doesn't work for me.No idea, then. I installed the 180 driver thru Synaptic and it flat out doesn't work. The nVidia website says the 190 driver will support the Ion chipset, and its not like dad's using it for anything that requires 3d accelleration anyway. So we can afford to wait for Lucid.

---

### Post by Kixtosh on 2010-07-02
Any new ideas on this topic since February? I'm in the market for a small form factor desktop or nettop. I've been considering:
 
- Dell Vostro slim form factor.
- Dell Zino HD.
- HP Slimline.
- Zotac Mag.
- Foxconn nettop.
- Asus EeePC.
- Acer AspireRevo.
- Building from separate components (case, motherboard etc.).
 
I would like to have the option to use a digital audio connection, such as optical or coaxial, and wireless internet, but it seems to be quite a challenge to check out all the possible compatability issues (video, audio, wireless ...). Budget anywhere from $200-400 or so.
 
Comments, suggestions, testimonials and website links all welcome!

---

### Post by Kevbert on 2010-07-03
Have you seen [[COLOR="Red"]my thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1379320") on the Revo R3610 ? 
However it's reported that the Ion chipset may not be updated due to Intel producing a new CPU (N450) which is currently incompatible with nVidia graphics (uses Intel integrated graphics instead).

---

### Post by Kixtosh on 2010-07-03
@Kevbert: Yes, (thanks for the link,) I did find that thread already. I think it might be the only one I found dedicated to the Revo. I need to read it again, but I seem to remember that there were some issues that you and others had to iron out or circumvent.

---

### Post by Kixtosh on 2010-07-04
Well, after reading the Revo thread again, I got the impression:
 
- There are some problems with wireless connectivity (whether internal, or external).
- There are some issues with video.
 
The video issues include using a proprietary driver (no biggie, right?), shared RAM memory, and some other user reported limitations/issues. So, I'm wondering if the new Zotac ZBOX might solve some of these issues:
 
- Improved (claimed) "Next-Gen" DDR3 Nvidia ION graphics.
- So, it seems to have dedicated video memory. Does this help a lot?
 
Heres the newegg page, and the manufacturer page:
 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16856173005](http://www.newegg.com/Product/Product.aspx?Item=N82E16856173005)
[http://www.zotacusa.com/zotac-zboxhd-id11-u-intel-atom-d510-1-66-ghz-dual-core-all-in-one-mini-pc.html](http://www.zotacusa.com/zotac-zboxhd-id11-u-intel-atom-d510-1-66-ghz-dual-core-all-in-one-mini-pc.html)
 
It's currently $260 before tax, with shipping, but no RAM, no HDD, and no OS ... so not exactly one of the cheaper options for the category when you add all that up.

---

### Post by llinuxn00b99 on 2010-07-22
I think the best nettop is the Zotac Mag.  It comes without an OS, so you don't have to pay the Microsoft tax just to later remove Windows.  Also, the nVidia ION processor is great and can drive 1080p video.

This website compares a few nettops nicely: [http://nettop-comparison.info](http://nettop-comparison.info)

---

### Post by Kixtosh on 2010-07-29
The link in the post above ^^^^ is a bit outdated, but I'm currently leaning toward a Lenovo Q150. They were on sale recently from Newegg for just under $350 and included the nVidia ION2, with 512MB dedicated graphics memory as well as the Atom D510 CPU (dual core 1.6GHz, 800MHz FSB). The Lenovo handheld multimedia keyboard was also included in the price (before tax).

You have to pay attention to the model version when looking, since different model versions may not have the D510 CPU or the newer ION2 GPU. Hard drive sizes vary too, but I'm not interested in a large HDD for this type of usage. The ones I have looked at come with Win7. 

I would expect Lenovo to do a good job of avoiding obvious issues such as wireless cards that don't work properly, and Lenovo seems to have been fairly Linux friendly lately.

[http://shop.lenovo.com/SEUILibrary/controller/e/web/LenovoPortal/en_US/catalog.workflow:category.details?current-catalog-id=12F0696583E04D86B9B79B0FEC01C087&current-category-id=7989AA4D07004515BEDB0E93AED8B49D](http://shop.lenovo.com/SEUILibrary/controller/e/web/LenovoPortal/en_US/catalog.workflow:category.details?current-catalog-id=12F0696583E04D86B9B79B0FEC01C087&current-category-id=7989AA4D07004515BEDB0E93AED8B49D)

Apparently, from what I've been reading, even the newer ION may not be enough for decent 1080p playback, so I may eventually just give up and buy a smallish laptop with better specifications instead ... for about $100-200 extra.

---

