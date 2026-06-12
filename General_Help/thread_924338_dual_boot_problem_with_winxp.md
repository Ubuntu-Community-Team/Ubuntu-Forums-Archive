---
title: "dual boot problem with winxp"
date: 2008-09-19
forum: General Help
---

### Post by Braaimanook on 2008-09-19
Hi all

first I must stress that I am a complete novice with regard to Linux of any flavour. I know a bit about Windows but do not regard myself as anywhere near an expert.

The problem is this and I apologise beforehand if I am in the wrong place.

I have installed Ubuntu Studio onto a USB drive(a Freeagent 500G)

Under windows this was drive letter F.

All went well with the installation upto the point where it found the Win installation and asked whether to install the boot up program into the MBR to which I chose yes, as it said this would give me the option of using XP or Linux.

Now everytime it boots it goes straight into XP and the F drive is not seen under "my computer". If I go into Disk Manager the drive is there along with other drives/ CD roms but does not have a drive letter allocated to it. XP reports that it is healthy but the only selectable option is to delete the partition


Do any of you more knowledgeable folk know what the problem is and how I can fix it?

Thank You

braaimanook

---

### Post by caljohnsmith on 2008-09-19
Welcome to the forums. :)

First off, when you installed Ubuntu Studio to your USB drive, I assume you used a Linux file system like ext2 or ext3, correct? If that is true, then Windows will no longer be able to read from that USB drive, because Windows can only deal with NTFS and FAT/FAT32 file systems. You can use special software to make your Linux partitions available in Windows; one program that I use and like is ["ext2fsd"]("http://sourceforge.net/projects/ext2fsd"), a free program hosted at sourceforge.net. So don't let it bother you that Windows doesn't seem to recognize your USB drive right now. 

Since you have a USB drive, I assume you also have an internal drive? And is that the drive with Windows? If you have your Live CD, it would be helpful if you could boot it, open a terminal (Applications > Accessories > Terminal), and post the output of:
```
sudo fdisk -lu
```
Then I can get a clearer picture of your setup.

---

### Post by Braaimanook on 2008-09-19
Hello caljohnsmith

yes when it installed it formatted the drive using the ext3 file system, again you are correct, there is an internal drive or rather 2. One hard drive holds the XP op system and the second
is a partitioned drive one partition with programs and the second partition holding data. There is also an external drive which is used for backups.

I will d/l the prog. you mentioned, but the version of Ubuntu Studio I have is not a Live version.

I hope that the above may assist you to assist me.

Thank You

---

### Post by caljohnsmith on 2008-09-19
Just out of curiosity, how did you install the Ubuntu Studio since you said you don't have a Live CD version? Is it the alternate install CD maybe?

---

### Post by Braaimanook on 2008-09-19
Hello caljohnsmith

in reply to your query, this is the link I used, should I have d/l a different version?. I have d/l the prog. you suggested and installed it, and I can now see within that prog all the drives and it shows that Linux is there. There seems to be an option to give the drive a drive letter but that doesn't seem to do anything as far as windows seeing it is concerned.


I appreciate you taking the time to help me.


regards
Braaimanook



[http://cdimage.ubuntu.com/ubuntustudio/releases/8.04.1/release/ubuntustudio-8.04.1-alternate-amd64.iso](http://cdimage.ubuntu.com/ubuntustudio/releases/8.04.1/release/ubuntustudio-8.04.1-alternate-amd64.iso)

---

### Post by stickmangumby on 2008-09-19
Hi Braaimanook,

I've never installed Ubuntu on a USB drive before, but I don't think that installing GRUB (the boot up program on the MBR) would allow you to boot to a USB drive. This is because GRUB needs to know exactly where the device it wants to boot off is. As you can easily change the USB port your drive is plugged into, this kind of certainty doesn't exist.

When I boot from operating systems installed on USB sticks, I have to change a setting in my computer's BIOS. You need to change the boot order to boot from USB first, then harddrives or CD-ROM.

If you're unfamiliar with your computer's BIOS, let me know and I'll try and give you some more specific information.

---

### Post by caljohnsmith on 2008-09-19
> **stickmangumby said:**
> Hi Braaimanook,

I've never installed Ubuntu on a USB drive before, but I don't think that installing GRUB (the boot up program on the MBR) would allow you to boot to a USB drive. This is because GRUB needs to know exactly where the device it wants to boot off is. As you can easily change the USB port your drive is plugged into, this kind of certainty doesn't exist.

When I boot from operating systems installed on USB sticks, I have to change a setting in my computer's BIOS. You need to change the boot order to boot from USB first, then harddrives or CD-ROM.

If you're unfamiliar with your computer's BIOS, let me know and I'll try and give you some more specific information.
You raise a good point that we should first confirm with Braaimanook, namely, does your BIOS support booting from your USB drive, Braaimanook? If it doesn't, then I don't think there is any way to boot your USB drive without BIOS support. 

But if your BIOS does supporting booting from USB, then we stand a good chance of getting it to work, because changing its USB port will not change the BIOS boot order, and that's how Grub sees your USB drive. So changing USB ports will not affect how Grub boots it. 

The most ideal situation I think is if you can change your BIOS to boot the USB drive first, like stickmangumby suggests above, and then we can install Grub to the master boot record of your USB drive and get it booting just fine most likely. But to do that, you'll need a Live CD that you can boot, because we can't do all this in Windows. Can you download the Live CD version of your Ubuntu Studio? Or just download a plain Hardy Ubuntu Live CD? I mean, is there any special reason you downloaded the alternate Ubuntu Studio CD and used that?

---

### Post by Braaimanook on 2008-09-19
Hello caljohnsmith

I have yet to reply to stickmangumby but yes he was absolutely correct in his suggestion ref the BIOS, for which I will thank him.

The machine now boots into Linux but not as I expected or hoped for. In booting up it appears to go straight in root mode. By that I mean after inputting user and password it then takes me to what I would call in windows, the c prompt. not as I expected a grapic interface.

As orginally mentioned I am completely new to Linux and have yet to learn at the text input level how to use it.


Regarding you query why this version, well my interests lie in music having been a muso years ago, and the Studio version seemed to fit the bill with a lot of music type programs already bolted on to it.

I could d/l a Live Basic version, the reason I didnt was I was a little put off as I didn't think I had sufficient knowledge to know how to add the various programs that Studio has


Regards


Braaimanook

---

### Post by Bucky Ball on 2008-09-19
If you can type at that cursor, try typing **sudo startx**.

---

### Post by Braaimanook on 2008-09-19
Hello Stickmangumby

Tks for your reply. The advice you gave was spot on, and I can now get to the Linux drive and boot from it, although as reported to caljohnsmith not as I expected. Still with effort and sticking to it and help from folks like yourself, I am sure that it wont be too long before it does what I want it to do. Many Thanks

Regards

Braaimanook

---

### Post by Braaimanook on 2008-09-19
Hello Bucky Ball

Thanks for the advice. I am afraid that command is unknown. I input it as you have typed it sudo startx. The message came back :sudo :startx unknown command and then back to the prompt.


Regards


Braaimanook

---

### Post by caljohnsmith on 2008-09-19
So when you boot your Linux drive, do you get the Grub menu on start up where you can choose the different OSes? If not, then press ESC repeatedly when you start up, and you should get the Grub menu. When you get the menu, select the first Ubuntu entry, just not the one that says anything about "recovery mode". Let me know if that helps, because it may be for some reason you are booting into the recovery mode by default.

---

### Post by Braaimanook on 2008-09-20
Morning caljohnsmith (well it's morning here), the problem is sort of fixed. I did as you suggested in a previous post, that is I d/l a Live version and installed "inside windows". Now aside from a message about an unreadable partition it boots up properly with the xp ubuntu option. 

Now what I have to do is learn how to install the programs that came with the Studio version and give it a thorough test.

What I am hoping for is to be able to use  all the programs I have on the Windows system (or their Linux equivalents) so that I can say goodbye to Mr Gate's creation with its fragility and bloody activation nonsense everytime I do an upgrade.

I appreciate that this is likely to be a fairly hard learning curve, but with the help that I have received by this forums members so far, one that I am looking forward to.
Thanks again

---

