---
title: "Headless Install help, please"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by rorschach on 2009-07-20
I'm wanting to do a headless install (re-install, really) on my system.

A little background:
The system in question used to be my main system - my desktop. I had it set up as a dual boot environment, with windows XP for occasional gaming. Over the last year, I have stopped using my desktop as a desktop entirely, using it as a media server for my living room.

Now, recently, I've been struggling to get .mkv files to be streamed successfully to any of my systems in the living room. I've tried many solutions, including fuppes, tversity (windows partition), mediatomb, and twonky media server. Most recently, I tried going through a few tutorials on doing a custom build of ffmpeg and mediatomb to allow for transcoding of the h.264 encoded mkv files. Since doing this, neither of the current media servers I can have running on the system work properly.


So now:
I'm at a point where I want to blow away the windows partition (I never boot into it anymore anyway), and would kind of like to do a cleaner install of Ubuntu, removing some of the mucking about I did in all of my multimedia endeavors. However, I'd ideally like to do this entirely remotely. Anyone know how I can accomplish that? Also - is there a particular flavor of Ubuntu that I should use rather than the main distro?

---

### Post by dstew on 2009-07-20
I don't have any ideas for you as far as a good distro, but I have some experience in installing Ubuntu over the net instead of using a CD.

To install over the internet, you need to have another computer on your home network that can serve a boot image to your media computer, and your media computer must have a PXE (Pre-eXecution Environment) BIOS. If you have this type of BIOS, you should have a boot choice in your BIOS settings menu to "Re-install over the network" or "boot from ethernet port" or something like that. I have done this using a Linux computer to act as the boot image server. See this [How-To]("https://help.ubuntu.com/community/Installation/LocalNet"). [Here]("http://ubuntuforums.org/showthread.php?t=690483") is the thread about my experience.

You can also install over the network by booting a USB stick configured to start the image that will give you a network installation menu. The boot image for Jaunty is [here]("http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/boot.img.gz"). The instructions are [here]("http://wiki.geteasypeasy.com/Install:_over_the_Internet_using_a_bootable_USB_stick"). This looks pretty easy, but I have not tried it.

If you can install files onto your media computer, you can make the computer boot a network-install kernel directly using grub. [Here]("https://help.ubuntu.com/community/Installation/NetbootInstallFromInternet") is the How-To. You put the same network install initrd.gz and linux (kernel file) into the /boot directory where the other Linux kernel(s) are. Then, at your grub menu, hit 'c' to get a command line. Then, boot the network-install kernel using```
root (hd0,0)
initrd initrd.gz
kernel linux
boot
```Of course, replace the root argument with the grub name of your Linux system partition. This way seems pretty easy. Again, I haven't tried it.

---

