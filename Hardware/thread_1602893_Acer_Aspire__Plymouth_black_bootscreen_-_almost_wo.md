---
title: "Acer Aspire / Plymouth black bootscreen - almost working..."
date: 2010-10-22
forum: Hardware
---

### Post by tristan on 2010-10-22
Hi all

Pretty much the only thing that is annoying me about 10.10 is the problems with Plymouth, basically not giving the pretty graphical boot screen as advertised. On the Acer Aspire D250, a very common and standard specced netbook, upon booting I got 15 seconds of black screen with a flashing cursor, followed by about 1sec of bootsplash and then the GDM login. Shutdown gave me the nice graphical (X) plymouth shutdown screen.

On my desktop with an Nvidia GTX460 I largely got it working after following [this guide]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/"). Basically this involves installing a different framebuffer driver and adjusting initramfs and grub2 accordingly to use it.

When I tried these exact steps on the Acer Aspire D250, I got a mixed bag of results: I got a full framebuffer graphic plymouth bootup, but then got dumped to a text login, no GDM, no X.

After reversing these steps and trying a few parameters, the closest I have managed to get to a full graphic boot on the Acer is:

1 - Turn on the frame buffer
```
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
```

2 - Install Startup Manager
```
sudo apt-get install startupmanager
```

3 - Run Startup Manager and change the resolution to 800x600, 24 bit. For the actual grub screen, also use 800x600. Important: set it to show bootsplash **AND** show text during boot. Startup Manager will update initramfs and grub accordingly for you.

4 - Reboot.

If you're like me, what you now get is about 1 second of rapidly scrolling text, followed by a proper X plymouth bootup screen. If you don't like the text, well, tough. If you untick the "Show text during boot" in startupmanager, you'll get the plymouth screen for about 0.5 seconds, followed by 15 seconds of black screen, no cursor.

Maybe some of you Ubuntu rocket scientists can figure out the way to get a full plymouth bootup. If so, let me know :)

---

