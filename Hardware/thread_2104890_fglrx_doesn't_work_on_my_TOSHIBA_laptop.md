---
title: "fglrx doesn't work on my TOSHIBA laptop"
date: 2013-01-14
forum: Hardware
---

### Post by HackerWolf on 2013-01-14
):PHi to everyone!! This is my first post on this forum but I'm not a total noob. I use Ubuntu for 5 years but never I've found myself in a similar situation. On 23 Dec. I bought a new laptop, a TOSHIBA L850-1PD ([http://it.computers.toshiba-europe.com/innovation/product/Satellite-L850-1PD/1142961/](http://it.computers.toshiba-europe.com/innovation/product/Satellite-L850-1PD/1142961/) - I'm forced to post italian site), good price (600€) and good specs for me (Intel i7 3630QM+AMD Radeon HD7670M w/ 2GB VRAM - up to 16 GB RAM). I was very happy! I was. I realized wrong purchase when I read that TOSHIBA laptops are out from official AMD support (look at the bottom on [http://support.amd.com/us/gpudownload/windows/Pages/radeonmob_win7-64.aspx](http://support.amd.com/us/gpudownload/windows/Pages/radeonmob_win7-64.aspx)) and when I tried to install Ubuntu 12.10. It installs without any issue but after the reboot... First, there's no way to change brightness (poor battery) but, more important, fglrx simply doesn't work. I've tried to install from software sources, from terminal, to build manually debs but nothing to do. I install fglrx, run amdconfig --initial -f, but after reboot I get only black screen, no LDM. So I try to run startx but I've got always this warning:

(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found

but for lspci this is HDMI output :shock:!!!

Looking into Xorg's log (first&second images) there are some errors regarding VBIOS reading. CCC on Win8 shows me a VBIOS correctly (third image), but GPU-Z can't (fourth image), likewise Ubuntu. Searching on the web, I see a lot of people that are running fglrx on toshiba laptops without issues.

Thank you in advance!!!

---

### Post by HackerWolf on 2013-01-17
No one can help me?:cry:

---

### Post by Mark Phelps on 2013-01-20
Basically -- NO.  You bought what is known as a Hybrid Graphics machine -- two graphics chipsets, one of which automatically kicks in when it is needed.

These work in MS Windows because the OEMS have special drivers developed for them.

Such drivers are not available in Linux.

Folks have had very limited success (if you want to call it that) by installing software (such as Jupiter) that allows disabling one of the video chipsets.  If you want to try that, suggest you search the forums for such posts.

---

### Post by HackerWolf on 2013-01-21
Sorry, but I missed to write that in-CPU Intel HD 4000 is disabled via BIOS or via hardware, so the machine is not an hybrid one and works only with AMD dedicated GPU. Damned Toshiba!!!

Good news, on Win8 I succesfully installed official AMD drivers, 13.1.

---

### Post by Mark Phelps on 2013-01-21
> **HackerWolf said:**
> Sorry, but I missed to write that in-CPU Intel HD 4000 is disabled via BIOS or via hardware, so the machine is not an hybrid one and works only with AMD dedicated GPU. Damned Toshiba!!!

Good news, on Win8 I succesfully installed official AMD drivers, 13.1.

OK ... but they are different drivers -- and I've had experiences in my desktop where the AMD drivers work great in Win7 but the supposedly SAME version AMD drivers in Linux do not.

---

### Post by HackerWolf on 2013-01-28
[http://www.thinkwiki.org/wiki/Problems_with_fglrx#X_server_gives_an_error_.22Invalid_video_BIOS_signature.22_after_installing_fglrx](http://www.thinkwiki.org/wiki/Problems_with_fglrx#X_server_gives_an_error_.22Invalid_video_BIOS_signature.22_after_installing_fglrx)

Is that issue my issue? But my BIOS has no way to switch that option...

---

### Post by Yellow Pasque on 2013-01-28
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1093788](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1093788)

---

### Post by HackerWolf on 2013-02-25
Solved!!! I installed Catalyst 13.2 beta6 and now  works. Only I still can't change brightness. Any idea?

---

### Post by SimonDPRZ on 2013-02-25
check power options ? 
or try this to make hybernating graphics work [http://ubuntuforums.org/showthread.php?t=1930450&page=66](http://ubuntuforums.org/showthread.php?t=1930450&page=66)

---

### Post by HackerWolf on 2013-02-26
> **SimonDPRZ said:**
> check power options ? 
or try this to make hybernating graphics work [http://ubuntuforums.org/showthread.php?t=1930450&page=66](http://ubuntuforums.org/showthread.php?t=1930450&page=66)

no way to change using brightness options and no related files under /sys/devices...

What to do?

---

