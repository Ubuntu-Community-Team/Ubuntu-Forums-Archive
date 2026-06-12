---
title: "NVIDIA Driver installed and now Ubuntu won't load"
date: 2010-09-30
forum: Hardware
---

### Post by SEOMike on 2010-09-30
Hello.  This is my first post, so please forgive me if this is the wrong place for this thread.

I installed an update for my video driver from the "restricted driver" in Ubuntu and upon reboot the screen just goes black and the computer never starts.  I found some advice online and pretty much every command starts with "sudo" and my grub command line says it's an unrecognized command.  Then I thought I'd just try reinstalling Ubuntu and start over, but I can't figure out how to remove the "broken" installation and I don't want it to just sit and eat up my drive, so I'm hoping someone can help me remove this offending driver.

I am BRAND NEW to Linux and a lifelong Windows guy so you'll have to be patient and explain to me exactly how to remove this driver using the grub command line because that's all I can get.  I was really starting to enjoy Ubuntu.  If this were Windows, I'd have no problem fixing it, but I don't speak Unix yet.

I've got 10.4.1 64bit on a Vaio VGN-Z820G.  Thanks in advance for your help!

---

### Post by SeijiSensei on 2010-09-30
Just reinstall the same way you did the first time, and everything should come out the same.  

If you're comfortable managing disk partitions, and you want more control over the installation, choose manual installation when the installer asks you about the drive.  You should see an ext4 partition, and maybe one marked for swap as well.  Select and edit the ext4 partition.  In the dialog box that follows, choose Ext4, check the format box, and assign the partition to the mountpoint called simply /.  The installer will delete the contents of the partition, format it afresh as ext4, then write the installation there.

I always use the built-in installer for the NVIDIA driver.  Look for the "Hardware Drivers" or "Additional Drivers" application and run it.  It will search the hardware, identify the NVIDIA card, and download and compile the necessary driver automatically.  It should be available when you reboot.

---

### Post by SEOMike on 2010-09-30
Thanks.  Is reinstalling the only way to get rid of the driver?  The computer won't boot to Ubuntu' GUI at all and the only thing I have available is grub command prompt so there's no going into the system and using any wizards.  Is that available outside the GUI?

If I can get my current installation back to working without reinstalling that would be preferable.

---

### Post by SeijiSensei on 2010-09-30
> **SEOMike said:**
> Thanks.  Is reinstalling the only way to get rid of the driver?  The computer won't boot to Ubuntu' GUI at all and the only thing I have available is grub command prompt so there's no going into the system and using any wizards.  Is that available outside the GUI?

If I can get my current installation back to working without reinstalling that would be preferable.

It's actually not the driver that's the problem.  Whatever installation process you used borked the boot loader; that's why you see the grub prompt.

Technically the answer to your question is yes, as you could boot a rescue distribution like Knoppix and tell it to fix the master boot record on the hard drive.  But to be honest, you're much better off just reinstalling if you have nothing worth saving on this disk.  If you do, then you might want to boot the [Knoppix]("http://www.knoppix.net/") CD first.  When it's up, you'll see the partitions on your hard drive arrayed as icons on the desktop.  You can open them and copy what you need to another location like a thumbdrive, then reinstall Ubuntu.

---

