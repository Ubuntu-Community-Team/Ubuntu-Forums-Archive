---
title: "Help installing Warty on laptop, please!"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by neilthemonster on 2005-04-09
Hi all

I've got Warty working on my desktop PC, dual-booting happily with W2K.

Now I've got a laptop from work, and permission to install Linux :-)

It's an AJP laptop - a rebadge of a Clevo 2200C. PIII 800MHz, 512MB RAM (64MB shared video) and 20GB.

The integrated chipset for LAN, video and sound is all SiS.

On attempting to install, Warty won't display. I went through the options and used 
*boot: linux vga=771* , and managed to get through the installation process. However, when I rebooted I just got a lockup and no display at all.

Has anyone else experienced this, please, and can anyone help?

Thanks in advance

Neilthemonster.

---

### Post by neilthemonster on 2005-04-09
Hi all

Sorry - forgot to mention a bit of potentially useful info.

I've tried the Warty LiveCD, and it doesn't boot - it drops to a *grub>* prompt and won't load the kernel or boot.

I have been able to boot and use a Knoppix 3.6 LiveCD I picked up at LinuxWorld last year, but I have to downgrade the screen settings on boot to 1024x768. Other than that it booted fine.

I really hope someone can help - I love using Ubuntu on my home machine, and it would be fantastic to work on it on my laptop too.

Cheers

Neil

---

### Post by lorap on 2005-04-13
it's being a strange thing...
my notebook was declared as linux most unfriendly but everything work fine.
did you change in the bios settings to load from cd?
haven't you forgotten that?
pavel

---

### Post by neilthemonster on 2005-04-13
Hi Pavel

Yes, I did ensure that the BIOS was booting from CD.

As I said, it will actually start the install process of Warty (as long as you use the boot: linux vga=771 option.

It's once the install is (apparently) complete that I can't then boot into Linux.

As as aside, I also can't boot the Ubuntu LiveCD, but can boot Knoppix.

I've ordered some Hoary CDs and I'm going to give that a try.

Thanks for the response.

Regards

Neil

---

### Post by neilthemonster on 2005-04-19
Hi all.

Just to put an end to this thread - I'm writing this using Mozilla on Warty on my laptop.

Don't ask me how, as I don't know - after three failed attempts to install Ubuntu, I tried to install Xandros and that failed - then tried a 4th time to install Ubuntu and sat there, open-mouthed, as it happily installed, connected to the apt repositories, updated and booted into a desktop.

So thanks for the suggestions, I am a happy Linux lappy user now!

---

