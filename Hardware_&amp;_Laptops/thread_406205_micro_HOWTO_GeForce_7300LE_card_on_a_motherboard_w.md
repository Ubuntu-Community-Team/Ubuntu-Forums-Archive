---
title: "micro HOWTO: GeForce 7300LE card on a motherboard with Intel graphics hardware"
date: 2007-04-10
forum: Hardware &amp; Laptops
---

### Post by agrimstad on 2007-04-10
This is a tiny HOWTO on getting a current nvidia graphics card, the GeForce 7300LE (ASUS EN7300LE/HTD/128M) working in Ubuntu Dapper in the case where the motherboard also has an Intel graphics device (ASUS P5GZ-MX).

I initially installed Dapper before I purchased the GeForce card. The video of the onboard chip set (Intel GMA 950) was disappointing, so I decided to shell out for a proper card. Without a small bit of magic, Dapper isn't at all happy with this card. Booting from the Dapper installation CD with the card in its PCIe slot fails.

For those starting from scratch, the simplest thing to do is to avoid installing the card, that is, use the on-board video, and install Dapper. Once that task is done, these simple steps should get the GeForce card working.

**Preparation before installation of the card**.

1. You need the restricted modules and the nvidia-glx packages. Since I use two ubuntu kernels, 2.6.15-28-386 and 2.6.15-28-686, I needed two module packages. Here's how I performed this step

[FONT="Courier New"]  sudo apt-get install  linux-restricted-modules-2.6.15-28-386
  sudo apt-get install linux-restricted-modules-2.6.15-28-686
  sudo apt-get install nvidia-glx[/FONT]

2. Next, and this is the key step to avoid kernel panics, edit the file /etc/modprobe.d/blacklist. Add these two lines to the end of the file:

[FONT="Courier New"]     blacklist agpart
     blacklist intel_agp[/FONT]

3. Now shut down your system.

**Installation and Configuration**

1. Now install the nvidia card and plug your monitor into it.

2. Boot your computer and hit the ESC key when grub comes up to get into its menu (assuming you have left the menu hidden). Select a recovery mode kernel (i.e., single user).

3. Once you are logged, in verify that your nvidia hardware is recognized:

[FONT="Courier New"]   # lspci | grep -i nvidia[/FONT]

   This is my result:
[FONT="Courier New"]0000:04:00.0 VGA compatible controller: nVidia Corporation: Unknown device 01d1 (rev a1)[/FONT]

   If you don't see something similar, you are probably in deep trouble.

   Also check that the nvidia module is loaded. If not, do

[FONT="Courier New"]   # modprobe nvidia[/FONT]

  Here's this check:

 [FONT="Courier New"]  # lsmod | grep nvidia[/FONT]

  This is my result:
[FONT="Courier New"]nvidia               4552916  12
agpgart                36784  1 nvidia
i2c_core               22848  5 i2c_acpi_ec,w83627ehf,i2c_isa,i2c_i801,nvidia[/FONT]

4. OK, almost there. Now configure X11. (You might want to save a copy of your current configuration /etc/X11/xorg.conf to some other name.)

[FONT="Courier New"]  # nvidia-xconfig[/FONT]

That should be it. Now either reboot or go multiuser, i.e.,

[FONT="Courier New"]  # reboot[/FONT]

  or

[FONT="Courier New"]  # telinit 2[/FONT]

I hope you find this helpful. In addition to the GeForce 7300LE this recipe will probably work for the cards in this list: [http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html).

**Backing Out**

If it didn't work, here's how to back out. Remove the graphics card; plug the monitor back into the motherboard graphics connector, and boot from the Ubuntu CD. From the applications menu, select Terminal. Now mount your root file system so you can make a couple of repairs. Suppose your root file system is in the partition /dev/hda1, then do this in the terminal window:

 sudo mount -t ext3 /dev/hda1 /mnt

Now remove the lines you added to the blacklist. The file will be /mnt/etc/modprobe.d/blacklist. And restore your xorg.conf to the directory /mnt/etc/X11.

---

### Post by mike16889 on 2008-07-11
thanx man am about to buy this mobo and an 8600GT but decided to check out other ppl's problems with the board and found this... ill still buy the board but this how to will come in real handy.

o and there is aparantly a typo [QUOTE=enchesss]The important part is blacklisting "agpgart" (note the typo in the howto) and "intel_apg".
[/QUOTE] [HERE](http://ubuntuforums.org/showthread.php?t=766219&highlight=p5GC-mx%2F1333&page=2)

---

### Post by agrimstad on 2008-07-12
Since folks appear still to be finding this item, I'll provide a very brief update.

My micro howto was based on Ubuntu Dapper Drake. A while ago, I decided to upgrade to Hearty Heron. It was much cleaner. Basically you don't need to blacklist the modules used by the (Intel) motherboard video now. I did the basic install--using the alternate CD to get raid and logical volumes--with the motherboard video, then installed the restricted nvida modules. After shutting down to install the video card I tweaked the bios to use the card for video and then booted into Ubuntu. It worked.

These are the nvidia modules I'm using now:

nvidia-kernel-common
nvidia-glx-new
nvidia-settings

---

