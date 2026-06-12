---
title: "xrandr and matrox dualhead2go"
date: 2010-03-03
forum: Hardware
---

### Post by laramichaels1978 on 2010-03-03
Hi everyone, 

I have read [https://wiki.ubuntu.com/X/Config/Multihead](https://wiki.ubuntu.com/X/Config/Multihead), but am still unsure if I can use xrandr to do what I need.

I am using a [Matrox Dualhead2go]("http://ubuntuforums.org/www.matrox.com/graphics/en/products/gxm"), which connects into my laptop's HDMI port and presents itself to the video card as a very wide 2560x1024 screen.

Can I use xrandr to tell Xorg that (what Xorg thinks is) a 2560x1024 screen is in reality two separate monitors? 

I need to do this so that, eg, maximizing a window to "full screen" maximizes to be 1280x1024, rather than spanning it over the entire two screens. :p

Thank you for any help!

~lara

---

### Post by djscribe on 2010-07-09
I 2nd Lara's report. I'm running Lucid 10.4 and detects both monitors using the Matrox DH2Go signal as one big monitor, but only in Failsafe. At least this is what Administration/Multiple Screens option shows. Only difference in my case vs Lara's is I don't have a problem with maximizing to both screens, but the only way my system displays properly is in FailSafe.

I've ruled out hardware, since I have XP on a its primary partition and dual screens work fine there full 2560x1024. I refuse to rely on Microsoft for dual screens. So...what's the skinny on that Xorg or Conf file that needs editing to fix this?


System: Dell Optiplex GX620
RAM: 1GB
80GB FreeSpace on SATA II drive
CoreDue 3.2
Video: Onboard Intel Integrated Media Accelerator 950 [GMA950] 512MB

Thanks in advanced guys.
- Scribe

---

