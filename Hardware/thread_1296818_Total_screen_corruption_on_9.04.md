---
title: "Total screen corruption on 9.04"
date: 2009-10-21
forum: Hardware
---

### Post by Foxfan100 on 2009-10-21
I've been running 9.04 in a dual boot XP system on a Dell Dimension 9100 with ATI Radeon display without any problems. However, I installed Gnome Terminal Manager (think that's the name, but can't exactly check-see following).

When I start up in GRUB and select 9.04, the Ubuntu system starts booting up OK, with the last visible command being to start GNome Terminal. At that point, I get a corrupted screen flash 3 times, the screen "on" light goes "off" and I can't get anywhere near Ubuntu. Same happens if I start up in secure/safe mode.

The screen corruption is really bad but seems to include some Windows elements. I might be able to photo it with a digital camera. Otherwise, Ubuntu is totally inaccesible. I don't have a spare screen to try with.

It looks like the answer is to disable this Gnome Terminal thing, and presumably I cold do this from the command line in safe mode startup.  Unfortunately I don't know where or how to begin.

I also have a 9.04 iso boot and installation disk, but I don't want to have to reinstall the whole of Ubuntu from scratch if I can help it.

---

### Post by wojox on 2009-10-21
Boot from the live cd mount the file system and run:

```
sudo apt-get --purge remove gnome-terminal
```

---

### Post by Foxfan100 on 2009-10-21
I tried that, but couldn't get very far off the Boot CD.

I tried this from the root command line after a safe start, and it told me that it had removed gnome-terminal and perhaps ubuntu desktop (2 packages).

However, the screen is still bombing out after 3 "flashes", although it does now show some brown ubuntu wallpaper which it didn't before.

I think that the package is actually called Gnome Display Manager, as this seems to still be starting in the boot up sequences.

---

### Post by prshah on 2009-10-21
> **Foxfan100 said:**
> 
I think that the package is actually called Gnome Display Manager, as this seems to still be starting in the boot up sequences.

The GDM is your GUI; please don't remove it.

Instead, see [this post]("http://ubuntuforums.org/showpost.php?p=7132514&postcount=2") for a solution. It has screenshots, so you can identify if you have the same problem. If you do, you can follow the instructions on how to fix it.

Post back here if you run into any difficulties, or need further assistance.

---

### Post by Foxfan100 on 2009-10-21
Thanks. I've had a look at that link which I don't think is the answer to the problem.

For a start, I do not have /etc/x11/xorg.conf as far as I can see.

I've uploaded with this some pix of the screen, which show evidence of a Windows splash screen!

Interestingly, I have Acronis Disk Director in XP, which shows my Linux partition as Ext3. I feel sure that when I last "explored" this partition with ADD, I could clearly see the obvious file structures of my Linux partition.

However, when I now explore it, it shows no details other than being C: drive. In actual fact, C: is the first drive which contains XP (sda), and Linux is on a second drive (previously identified as sdb1, where sdb4 is an NTFS partition on the second drive for Firefox profiles etc, and sdb6 is XP pagefile).

Until Ubuntu gets to the end of the boot up it behaves as usual, at which point it produces these screens. This would suggest to me that it is looking for something in the first hard disk C: and finding Windows stuff, when presumably it should be looking in the Linux partition on the second hard drive. However, GRUB gets it going in the usual way and if it set out to boot from the wrong place then it wouldn't find the boot scripts.

All that I've done is enable a few more apps in Ubuntu, and then shut down. The problem now is that without being able to get back to it I can't get a list of those installed!

---

