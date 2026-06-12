---
title: "KUBUNTU 7.10 hangs on dv6605"
date: 2007-12-17
forum: Hardware &amp; Laptops
---

### Post by kingpin_uy on 2007-12-17
Hi,

i had installed kubuntu 7.10 on my HP laptop ( dv6605us ) and it hungs up on the splash screen, the progress bar hungs at the begining, just a small blue bar apears and then nothing... the hard drives light turn on but i left it and stays there forever.
i tried the nopic noapic thing but i think i´m not doing it rigth... it just starts on recovery mode but not always, sometimes it hungs too. 
any suggestions?

thanks in advance,
Andres.

---

### Post by crouton on 2007-12-17
If you can boot in recovery mode, edit your /etc/usplash.conf file (nano /etc/usplash.conf) and change the xres to 1024, yres to 768.  Save and reboot, see if that helps any.

---

### Post by kingpin_uy on 2007-12-17
crouton thanks for your help, but this didn't worked.
I change to 1024x768 then 1280x800 (this is the notebook max resolution) and 800x600 but it stills hanging at splash.
When i press alt+ctrl+F1 it shows Trying or using 1280x1024 - Using 1125xNNN - Using 1024x768 and hangs there.... no matter what did i edit in /etc/usplash.conf

installing linux on my laptop brings me a lot of problems!! nvidia grafics (i think theyre solved thanks to Envy!), Broadcom wireless (i did the HOWTO but it didnt worked) and booting normaly :D 

any other suggestion?

thanks!

PS: te safe boot sometimes hangs on 'Uniform CDROM driver versio 3.20' and i have to boot a couple of times, opening the dvd drive.

---

### Post by aipforum on 2007-12-20
I have the same laptop, and I had problems with Ubuntu, Kubuntu and PCLinuxOS.

I was digging through some other distro disks that I had, plus what my roommate had, and I popped in Ubuntu Studio just out of curiosity.  Hadn't seen it, heard of it or tried it before ... figured I had nothing to lose.

Much to my surprise, it installed perfectly.  Then using Envy got the NV card to work fine.  Then Automatix and a few other things using a wired ethernet and I am set.

Works just fine !

I would suggest giving it a try.

I don't know what the difference is (probably the tweaked, low-latency kernel), but for whatever reason, it works for me.

Hollar if you get stuck.

-- Brent
[email]btj@brentcctx.com[/email]

---

### Post by reasoner on 2007-12-29
if I remember right the i386 version of Ubuntu didn't boot, or was that the i386 version of OpenBSD. Anyway when I used the amd64 version on my dv6605us it worked (both OpenBSD and Ubuntu) I haven't tried Kubuntu.

The nvidia binary driver works with the NVIDIA GeForce Go 7150M but I don't like closed source and the nv driver doesn't work, so I'm stuck at 1024x768 with the vesa driver. Aparently the vesa driver only works at resolutions supported by the BIOS and the top resolution in the BIOS is 1024x768. 1024x768 is a little blurry because it doesn't match the native panel resolution of 1280x800. The nv driver is reported to work with the 7150M in other laptops so I have hope it will start working with the dv6605 eventually.

Sound works but when I plug in the headphones the soundcard doesn't detect it and the speakers and headphones both continue to put out sound.

The USB2 ports work. I have nothing to test the firewire port with.

The wired ethernet port works. I haven't tried the broadcom wireless ethernet yet.

Touchpad works. SD card slot works. DVD burner burns CDs. I haven't tried burning a DVD under linux yet. It reads DVDs under linux anyway. The touch sensitive keys above the keyboard like volume and play/pause work. The scroll section of the touchpad works. There is only two mouse buttons with the touchpad. Too bad, I like a third button.

I only tried suspend once and it didn't work. I think it may have just been the display that wouldn't come back up.

The hardware is so new on this machine that HP didn't even create Windows XP drivers for a couple of things. HP says you can't use XP, it's Vista only. I think it's possible to downgrade to XP and round up some drivers though.

Edit: I found out how to enable headphone detection for speaker muting. See [https://wiki.ubuntu.com/HP_Pavillion_dv6000_(dv6604nr](https://wiki.ubuntu.com/HP_Pavillion_dv6000_(dv6604nr))
 It is said that version 2 of the  BCM94311MCG broadcom wireless device included in this machine won't work with the native Linux drivers without the 2.6.24 kernel and the latest driver version. So apparently you can't use a stock Gutsy kernel with the linux drivers. See the link above for the 6604 to eliminate the bcm errors in the console and dmesg. Supposedly Ubuntu Hardy Heron will work. I guess the wireless card will probably work with NDIS Wrapper.

---

