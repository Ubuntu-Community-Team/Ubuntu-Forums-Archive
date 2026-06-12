---
title: "Black screen on LiveCD"
date: 2008-02-15
forum: Hardware &amp; Laptops
---

### Post by sanflores on 2008-02-15
Hi, i have a problem (a BIG one) with Ubuntu 7.10. CD starts ok, I select "Starts or install ...", I see the loading screen, and just when it should show me the desktop, the screen goes black, but, if i go to TTY 1 (for example) i can see everithing, so... i think is the video card that dosen't work... what should i do?

Hardware:

Motherboard: ASRock "ALIVENF6G-VSTA/M/ASR"
Video card: NVIDIA GeForce 6150E (onboard)

Bios configuration:
Video set to Onboard and memory sharead with the video card to "Auto"


What I've tried?:

Xorg.conf output:

Section "Device"

Identifier       "Generic Video Card"

Driver          "Vesa"

BusID           "PCI:0:13:0"

Section "Monitor"

"Generic monitor"

"DPMS"

horizontal 30-70 and the vertical 50-160


---------------------------------------------------

start and stop gdm

---------------------------------------------------

Ctrl + Backspace

---------------------------------------------------

Start the instalation with the parameters (F6) noapic nolapic

---------------------------------------------------

And that's all... if any have a solution... i would be really really happy :P

Greetin's from Argentina, and sry for my English :lolflag:

---

### Post by Yellow Pasque on 2008-02-15
Try the alternate install CD. That's usually a good way to solve video compatibility problems with the LiveCD.

---

### Post by DJ_Peng on 2008-02-15
You can also try forcing safe video mode (I believe that's what it's called). I had the same problem with my Nvidia video card with the LiveCD and was able to fix it by switching to my onboard Intel graphics. Since your Nvidia graphics are onboard that trick won't work for you so if safe video mode doesn't work I'd definitely recommend the alternate installer. I had to use it when I first switched to Ubuntu from WinXP because I didn't have enough RAM in that box. Yes, you'll lose the pretty graphics, but it's a great backup way to uninstall Gutsy.

Is there a known issue with Nvidia drivers on the LiveCD that I haven't heard about?

---

### Post by sanflores on 2008-02-15
I've already tried the safe video, and dosen't work.

Question: "If i install with the alternate cd... is there any chance that later the video work?"

Already download the alternate... now i burn it and tomorrow i'll install Ubuntu from there.

---

### Post by DJ_Peng on 2008-02-15
Sure, although you may need something like [Envy]("http://www.albertomilone.com/nvidia_scripts1.html"). Not everyone likes it but it's never done me wrong.

---

### Post by Yellow Pasque on 2008-02-15
> **DJ_Peng said:**
> Is there a known issue with Nvidia drivers on the LiveCD that I haven't heard about?
I've seen a lot of threads on it, mostly in the 64-bit forum. The LiveCD doesn't seem to like modern GeForce onboard chipsets or GeForce 7 and 8 series cards. You should definitely check out Envy since a lot of nvidia users swear by it. (doesn't work quite so well for ATI).

---

### Post by sir4taye on 2008-02-15
I just used boot: live noapic nolapic and the blank screen problem stopped.

___________________________________
compaq presario f700, nVidia geforce 6100 (onboard mem),
1G ram, amd64 tk-55 1.6 Ghz, broadcom 4311 mini-pci wlan

---

### Post by sanflores on 2008-02-16
It work's!!!

I've used the alternative CD (text mode installation) and work's just perfect

thx's to all ;D

---

### Post by DJ_Peng on 2008-02-16
> **Temüjin said:**
> You should definitely check out Envy since a lot of nvidia users swear by it. (doesn't work quite so well for ATI).
I love Envy. Last night I got new Intel drivers for my onboard video ( which I don't use, but I took teh drivers anyway) and came back from a reboot to a black screen. I logged into Recovery Mode, fired up Envy, and when I rebooted again all was right in the world. :)

I know Envy's added support for ATI, but I didn't realize there were issues with it.

---

