---
title: "Nvidia 8800GT (not GTX or GTS but new G92 chip) no X"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by SergeiFranco on 2007-10-30
Hi there, I have just purchased new video card - it is nvidia GeForce 8800GT 512MB PCIE.
I have installed it, turned on computer and expected it to work straight away (like the time I did swap from 6600GT to 7600GT) but no joy.
It will not start X not under "nv" or "nvidia, tried nvidia-xconfig, dpkg-reconfigure etc. also tried to remove nvidia-glx-new completely then reinstall same problem, it complaints something about unable to find device in /dev/nvidia0 or something similar, it also puts out different error message under "nv".


Apparently I am not supposed to use official nvidia driver (NVIDIA*.run), or at least it is what I gather from this forum...

I am running out of options here... although I have not tried official nvidia driver yet or envy.

I am stuck in vesa mode.

Please advice.

```

$ lspci 
.......
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0611 (rev a2) (prog-if 00 [VGA])
        Subsystem: Giga-byte Technology Unknown device 3465
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at f4000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at 8000 [size=128]
        [virtual] Expansion ROM at f7000000 [disabled] [size=128K]
        Capabilities: <access denied>
........

```
xorg.conf
```

...........
Section "Device"
	Identifier	"nVidia Corporation NVIDIA Default Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"VX2235wm"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NVIDIA Default Card"
	Monitor		"VX2235wm"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1680x1050" "1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
..........

```

---

### Post by SergeiFranco on 2007-10-30
update - I have tried nvidia official driver - it complaints something about not supporting my video card.
Same thing with envy.
I just checked and the linux driver does not have my Card in the list, while windows driver for it just has been released couple days ago...

---

### Post by aoanla on 2007-10-30
Well, your card *is* the newest nVidia card available (only out for a day or two!), and linux driver production often lags a little behind Windows drivers.

Out of interest, which official drivers were you using? The stable release 100.14.19 dates from the 18th of September, and therefore almost certainly wouldn't officially support your hardware.
You might (but I'm not guaranteeing anything) have better luck with the more recent beta release 100.14.23, which dates from the 19th of October (that said, the beta doesn't include the 8800GT in its supported list, either).

Otherwise, I would imagine that there will be a suitable release in the next week or so - unlike ATI, nVidia has generally tried to be relatively quick at supporting new chipsets in linux...

---

### Post by aoanla on 2007-10-30
Update: I direct your attention to the following thread on the "official" nVidia linux forums:

[http://www.nvnews.net/vbulletin/showthread.php?t=101223](http://www.nvnews.net/vbulletin/showthread.php?t=101223)

Note especially the reply from the nVidia representative at the bottom. (Basically "Sorry, we didn't get support into a linux driver before the release. We're working on it as fast as we can.")

---

### Post by SergeiFranco on 2007-10-31
interesting, here in New Zealand we had this card for sale for at least a week.
Oh, well I have to wait and see how long it will take them to release linux driver for it.

---

### Post by Necreia on 2007-11-02
Damn!  Looks like I'm stuck in a super low resolution for a while :/

I hope the driver doesn't take months.

---

### Post by SergeiFranco on 2007-11-02
I am running 1680x1050 in vesa mode no problem....

EDIT: BTW new nvidia-glx-new has been released, will test it if it has support after I come back from work.

---

### Post by SergeiFranco on 2007-11-03
new nvidia-glx-new still does not support my card...

---

### Post by ATLANT3AN-UK on 2007-11-04
Yeah I had the exact same problem, only for me I cant even login, it does not accept my password as being correct although I know it is. I put my old card back in, I will wait until Crysis comes out then I will swap it back for the 8800 GT as thats the only real reason I brought the card :)

ATLANT3AN

---

### Post by buzzin on 2007-11-04
Vesa mode works for me too...

/me prays that nvidia live up to their rep and get this driver out soon

---

### Post by Necreia on 2007-11-05
This is terrible indeed.... I'm stuck having to use Windows XP until nVidia releases that driver :(.

I gave my old video card to my Fiancee before I tested the new one (yeah, poor move), and while Vesa works for documents-- I need my gaming.

nVidia is really good about this sort of stuff in the past, and here's to hoping that it'll be a fast fix.

---

### Post by bettlebrox on 2007-11-07
Looks like support will be here soon!

[http://www.phoronix.com/scan.php?page=news_item&px=NjE1OQ](http://www.phoronix.com/scan.php?page=news_item&px=NjE1OQ)

Hopefully the prices of the card will drop to ~$200 here in the US by then! :)

---

### Post by regomodo on 2007-11-08
> **bettlebrox said:**
> Looks like support will be here soon!

[http://www.phoronix.com/scan.php?page=news_item&px=NjE1OQ](http://www.phoronix.com/scan.php?page=news_item&px=NjE1OQ)

Hopefully the prices of the card will drop to ~$200 here in the US by then! :)

$200 ! That is crazy! They are about $400 in the uk

---

### Post by bettlebrox on 2007-11-09
U could kill 2 birds with one stone, get a cheap ticket to the US, have a nice holiday, and with the exchange rate, get a 8800gt for about a hundred quid! ;)

---

### Post by Cresho on 2007-11-11
my card outperformce the evga 8800gtx.  i have a 6400 amd black edition with a bfg 8800gt oc.  then again, he has a 5200 athlon.  futuremark reads 9200 for him and 10200 for myself.  cant wait for my linux drivers.  running 800x600 vesa here.

---

### Post by Rupertronco on 2007-11-13
> **Cresho said:**
> my card outperformce the evga 8800gtx.  i have a 6400 amd black edition with a bfg 8800gt oc.  then again, he has a 5200 athlon.  futuremark reads 9200 for him and 10200 for myself.  cant wait for my linux drivers.  running 800x600 vesa here.

Your system may outperform his, but 2 8800gts in SLi have a hard time matching a gtx, let alone beating it. It's not the gpu that's winning that battle. Roomie and I have the same boards, processors, ram, even identical overclocks. Only difference is he's running the 700mhz 8800gt in sli and I pulled out one of my 2 gtxs and it still crushed his dual 8800gt setup. The GT is an amazing card for the money, but it's not going to out perform a gtx anytime soon. 

What will be really amazing is when the 640mb 8800gts with the new gpu around Christmas. Those cards will fly.

---

### Post by SergeiFranco on 2007-11-13
FYI: I scored 10800 in 3D Mark with E6300 @ 2.8Ghz and video card at stock settings.
BTW The reference board comes with real crappy heat sink, it pays to get aftermarket unit otherwise it will be in 80'C range and having all sort of problems. Although here in NZ summer is just about to start hence the temp.
I just installed Thermalright HR-03 Plus (I had to modify the bracket because GT version is not out yet), and my load temp dropped to 47'C.
Also Windows driver is also rubbish, there is some sort of conflict between PC Wizard 2008 and Nvidia control panel (real rubbish as well) that results in BSOD.
Also since discussing the pricing I have paid for mine 450NZD (google for rates).

---

### Post by josh2112 on 2007-11-15
Ok, back on topic...  Still no information about the release date of a 8800GT-supporting driver?

I've got one in the box sitting on the floor of my living room... every day I see it... it taunts me...

---

### Post by SergeiFranco on 2007-11-16
Nothing so far, I regularly check nvnews forums (or whatever it is called) and so far no progress.

---

### Post by regomodo on 2007-11-16
vesa works well for me. I'm very impressed by this card and my setup in general.

3dmark05 v100 gives me a score of ~17000 which is a major leap from ~5600 from my 1.8ghz sempron + 6800gt. This thing screams through almost everything cranked to 11

---

### Post by ghostdev85 on 2007-11-16
Hello,
Try this link... It's a beta driver for ia32...
[http://www.nvidia.com/object/linux_display_ia32_169.04.html](http://www.nvidia.com/object/linux_display_ia32_169.04.html)
It worked for my LFS... You'll have to compile the driver yourself tho...

---

### Post by esodin on 2007-11-17
> **ghostdev85 said:**
> Hello,
Try this link... It's a beta driver for ia32...
[http://www.nvidia.com/object/linux_display_ia32_169.04.html](http://www.nvidia.com/object/linux_display_ia32_169.04.html)
It worked for my LFS... You'll have to compile the driver yourself tho...

It seems to be the right driver ... but I can not get i loaded. Anyone had a luck with this driver, 8800GT and Gutsy? If you have could you post instructions?

---

### Post by SergeiFranco on 2007-11-18
yeah same problem (partial Xorg.0.log):
```
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
```

first it complained about not existence of /sbin/lrm-video I touched it. Then it complained about access denied on that file, chmod it. now it complains about not being able to find /dev/nvidiactl (which is there).

169.04 theoretically should support my video card but for some reasons it does not work.

Can some one post work around, please.

---

### Post by Cresho on 2007-11-18
here is a tutorial





setup bios
(monitor vga cable on vga pci-e card)
advanced bios features->boot from cd rom
advanced bios features->init display first->onboard vga
advanced bios features->onboard gpu->always enabled
save and exit

power off
(monitor vga cable on onboard vga)
--------------------------------------------------------------------------------
load ubunu cd and bootup (during install, gpu fan is spinning at its max which is normal).
--------------------------------------------------------------------------------
install ubuntu
reboot
eject cd when prompted
--------------------------------------------------------------------------------
reboot into the operations system, log into it and you should be fine after this point (this is just to verify that your onboard is alright).


open terminal up and type this without the quotes.  you also should have the ubuntu cd in the drive as well.

"sudo apt-get install automake1.9 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx-dev librsvg2-dev checkinstall libglade2-dev"

dont forget to answer the termianl questions like yes and enter.....8(
--------------------------------------------------------------------------------
download the driver from nvidia

[http://www.nvnews.net/vbulletin/showthread.php?t=102509](http://www.nvnews.net/vbulletin/showthread.php?t=102509)

log out of ubuntu after download is finished
hit ctrl+alt+F1
log into your username at the prompt in terminal

then in terminal
cd /home/yourusername/Desktop
ls (just to see if your in the right directory where you downloaded the file in firefox)
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86_64-169.04-pkg2.run
(ignore the question or say no to kernel download during instal, allow 32bit compatibility, and have nvidia xconfig update the x)

"sudo reboot" in the terminal

--------------------------------------------------------------------------------
shut down and reboot into bios

eject cd since its not needed

setup bios

advanced bios features->boot from hardisk
advanced bios features->init display first->peg
advanced bios features->onboard gpu->enabled if no ext peg

save and shut pc down
(monitor vga cable on  onboard vga)
turn on pc and it should boot into ubuntu (gpu fan slows down) at this point, everything is black and should be left alone until something pops up.  be patient.  there is a fix for this problemby editing grub's menu.lst to remove "splash" or add "vga=normal"


troubleshooting!!!!!!
after some updates, I had blackscreens and couldnt get back into the system.  something got overwritten during the update so i fixed my problem by re-doing the steps from the very start.  It has only happened to me once after some updates.  i was able to get back into everything easily .  I keep the nvidia driver easily accessible so i can cd into the directory.
--------------------------------------------------------------------------------



--------------------------------------------------------------------------------

---

### Post by SergeiFranco on 2007-11-18
oh also can some one tell me how to pipe the last error message that startx gives, I tried startx > log.txt but that creates empty file. Or how to copy screen on tty into file. It would help as the error messages there are very different to Xorg.*.log files.

---

### Post by SergeiFranco on 2007-11-18
> **Cresho said:**
> here is a tutorial
setup bios
(monitor vga cable on vga pci-e card)
advanced bios features->boot from cd rom
advanced bios features->init display first->onboard vga
advanced bios features->onboard gpu->always enabled
save and exit

power off
(monitor vga cable on onboard vga)
--------------------------------------------------------------------------------
l
--------------------------------------------------------------------------------
shut down and reboot into bios

eject cd since its not needed

setup bios

advanced bios features->boot from hardisk
advanced bios features->init display first->peg
advanced bios features->onboard gpu->enabled if no ext peg

save and shut pc down
(monitor vga cable on  onboard vga)

--------------------------------------------------------------------------------
That is only relevant to someone with on-board video.
I have tried to install official way (nvidia official that is) and I cannot work around that "cannot find /dev/nvidiactl" problem. I think this due to some bug in the driver itself.

---

### Post by SergeiFranco on 2007-11-18
Hmm found a discrepancy in the [http://us.download.nvidia.com/XFree86/Linux-x86/169.04/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/169.04/README/appendix-a.html)

It seems either list of supported model by 169.04 driver is ether missing 8800GT or the driver does NOT SUPPORT this video card (it seems to me later).

---

### Post by victor_c26 on 2007-11-18
What? It specifically says in the download page that support for the 8800GT was added in this driver.

[http://www.nvidia.com/object/linux_display_ia32_169.04.html](http://www.nvidia.com/object/linux_display_ia32_169.04.html)

---

### Post by Cresho on 2007-11-18
well, my problems was occuring with the 64bit version of ubuntu.  I just did a fresh install in safe graphics mode easily...though I had to shut down the pc 5 minutes in between each boot just to get the safe graphics going.  64bit version would just hang for hours on end.  Now that I have this installed, im going to try the nvidia 32bit version beta drivers.

---

### Post by SergeiFranco on 2007-11-19
I am trying rectify this through nvnews forum as well...
[http://www.nvnews.net/vbulletin/showthread.php?t=102626](http://www.nvnews.net/vbulletin/showthread.php?t=102626)

---

### Post by SergeiFranco on 2007-11-19
Made it work, reinstall nvidia-glx, then purge nvidia-glx, then install nvidia driver.

---

### Post by Cresho on 2007-11-20
my issue was with the 64bit version after all.  32bit works perfect.  I did not even need to use my onboard video gpu.

---

