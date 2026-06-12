---
title: "HowTo: Compaq Armada 1750 Sound Setup"
date: 2005-09-29
forum: Hardware &amp; Laptops
---

### Post by mhancoc7 on 2005-09-29
This is a fairly staight forward guide to setting up sound on the Compaq Armada 1750 laptop. This has worked for me on my personal laptop running Hoary. I feel confident that it should help get your sound working or at least lead in the right direction. However, you will be using this info AT YOUR OWN RISK!

Step 1: Use the Synaptic Package Manager to install libsdl1.2debian-all. This is only needed for game sounds (ie SuperTux).

Step 2: Open a new Terminal and enter, sudo gedit /etc/modules. This will open your modules file in gedit. Now add the following to the bottom of the file. sb io=0x220 dma=0 mpu_io=0x330 irq=5 Now save the file and close gedit and the Terminal. Reboot and hopefully your sound is now working. If so congratulations. If not go to Step 3.

Step 3: Download the HowTo package below and follow the instructions within it to create your new Compaq Setup Disk that will help to determine and possibly edit your irq settings.

[http://www.whatwouldjesusdownload.com/compaq_armada_1750_sound_setup_ubuntu.tar.gz](http://www.whatwouldjesusdownload.com/compaq_armada_1750_sound_setup_ubuntu.tar.gz)

I hope this HowTo will be helpful. It is my first. I have only been using Linux for about a year. I started with Ubuntu and I love it. I am so excited about getting my sound working. I hope to be able to help others as well. I need to also thank all the people who helped me through their posts.

God Bless, Jereme

---

### Post by mahsoud on 2007-10-08
didnt work for me, still says no device... although sound works in winxp

---

### Post by mhancoc7 on 2007-10-08
> **mahsoud said:**
> didnt work for me, still says no device... although sound works in winxp

Sorry that it is not working for you. I do not have my 1750 anymore so I can't be much help.

Jereme

---

### Post by pordzio on 2007-11-06
HI!

Here's the method, that worked for me:

1. Download custom dsdt.aml from: [http://acpi.sourceforge.net/dsdt/view.php?id=168]("http://acpi.sourceforge.net/dsdt/view.php?id=168")

2. Add DSDT.aml to the initramfs using [this script]("http://gaugusch.at/acpi-dsdt-initrd-patches/initrd-add-dsdt")

3. Add line "option snd-es18xx enable=1 isapnp=1 port=0x220 irq=5 dma1=0 dma2=1 mpu_port=0x388" to /etc/modprobe.d/options values in this line are read from Compaq Setup located on disk. If you can't access setup, you can download and make a diskette from compaq site)

4. add "snd-es18xx" to /etc/modules et voila!.

Sound should be working now.

In my case i had another problem. The sound was jerky. The solution to it is unloading and loading again module snd-es18xx. If after few restarts the sound is still jerky , then add lines "modprobe -r snd-es18xx" and "modprobe snd-es18xx" to /etc/rc.local/ , BUT place them before "exit 0"


Wish you good luck.

---

