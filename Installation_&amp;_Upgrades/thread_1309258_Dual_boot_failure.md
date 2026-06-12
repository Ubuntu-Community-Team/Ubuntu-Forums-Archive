---
title: "Dual boot failure"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by altufaltu on 2009-11-01
I used to have dual-boot between XP / Ubuntu with GRUB installed on sda9, using Windows boot.ini to boot to Ubuntu.

To achieve this, I used to go to Advanced options when installing Ubuntu and select sda9 for GRUB installation.

After complete installation, I used to copy first 512 bytes of sda9 to C:\ubuntu.lnx using following commands in a terminal, in Live CD:
mkdir win
sudo mount /dev/sda1 win
sudo dd if=/dev/sda9 of=win/ubuntu.lnx bs=512 count=1
sudo umount win

This worked till 9.04 but for 9.10, when I select Ubuntu boot option, I just get a blank screen.

Looking at few posts in forum, I installed GRUB to MBR using:
sudo grub-install /dev/sda

This worked, but this is not what I want. I want to keep using old method of booting Ubuntu through Windows boot.ini file.

Please help!

- Altu

---

### Post by MahmudRahman2009 on 2009-11-02
I had the same problem on a Dell Dimension 8400. In the end, I followed some instructions I could find on reverting to grub legacy, then I still had the problem that there was no stage1 file in the grub folder. I had to place it there, then the old methods -- copying the boot sector from the partition to c:\ worked.

---

### Post by altufaltu on 2009-11-02
OMG... so GRUB2 doesn't support this method???

---

### Post by Egi_Power on 2009-11-02
Hi and welcome to Ubuntu Forums!

Unfortunatly, I don't know how to solve your problem.
But here is the link to the Ubuntu Documentation on GRUB2.
If you read it, maybe you find answer to your question.
[https://help.ubuntu.com/community/Grub2#Reinstalling]("https://help.ubuntu.com/community/Grub2#Reinstalling")
Good luck!

Take it easy.

Egi_Power

---

### Post by MahmudRahman2009 on 2009-11-02
I'm not exactly sure if grub2 won't support this method. I installed 9.10 on three machines on Thursday and Friday. One was an ancient Compaq Armada M300 laptop, this one was a dual boot with Linux Mint. That would not work with ext4, so I had to install with ext4. The second was a Compaq V2000 laptop, dual booting with XP. Now, this one gave me no trouble when installing and I could boot into Ubuntu from the Windows bootloader. So, I was very surprised when I had trouble with my desktop using the same system. There's a mystery here. I searched a lot for help, but two days ago I found no solutions so that's when I went for legacy grub. But I believe there must be a way, since it seems to work from my V2000 laptop; I rechecked and it is using grub2 and the Windows bootloader. 

When you install Ubuntu, just before the install, there's an advanced option where you specify where you want grub installed. In both cases I didn't want grub on the MBR of the hard disk so I chose what I thought was the right Ubuntu partition (sd?). I believe in the case of my laptop, it did create grub in the right partition, but for some reason on my desktop it didn't. There must be a way to fix this. I haven't searched again -- I have a working desktop with dual boot and legacy grub.

---

