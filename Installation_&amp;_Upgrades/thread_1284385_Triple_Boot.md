---
title: "Triple Boot"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by Wa1k3rTXRang3r on 2009-10-06
I want to install Ubuntu 9.10 on my laptop which already has Windows Vista and Fedora 11 on it.

1. Would it be possible to install GRUB on the first sector of the boot partition as it is during the Fedora install?

2. If i have already installed GRUB while installing Fedora, would Ubuntu even need to install it again?

Any help would be greatly appreciated.

---

### Post by Sef on 2009-10-06
> 1. Would it be possible to install GRUB on the first sector of the boot partition as it is during the Fedora install?


GRUB should automatically install on the first sector of your hard disk. 

> 2. If i have already installed GRUB while installing Fedora, would Ubuntu even need to install it again?


GRUB will be reinstalled and should see Fedora and Windows.  The default os will be Ubuntu.

---

### Post by oldfred on 2009-10-06
Are you talking about the MBR or the partition. I am running XP and two copies of 9.04 (32bit & 64bit) and installed 9.10 but put the grub2 into the partition so I am still using my old grub and ubuntu 9.04 to boot. I then added a chainboot entry to link the the grub2 in Karmic's partition.

It depends on which grub you want in control. Grub2 should find all the operating systems but Fedora has had issues being found based on other posts.

To install Grub anywhere else that the MBR you have to select the advanced button on the screen to install grub.

---

### Post by Wa1k3rTXRang3r on 2009-10-06
Thanks for the help.

Installation went smoothly. But GRUB does not detect my Fedora installation, which is a problem since I need for school lol.

Also, is there anyway to enable a driver for my NVIDIA Quadro NVS 140M?

---

### Post by hantechbl on 2009-10-06
Ususally in the install process the installer detects current the current OSes and will add them to it's boot loader.

---

### Post by Wa1k3rTXRang3r on 2009-10-06
Yea I know, but it seems like it didn't this time. Maybe its something with GRUB, because I know that 9.10 uses a new version?

---

### Post by oldfred on 2009-10-07
I found this before as the way it is supposed to work
Even still, the latest Karmic Alpha needs some help to find other os.
sudo apt-get install os-prober
sudo os-prober
sudo update-grub2

You do not have a menu.lst and the grub.conf is not to be edited. 
Per Herman:
[http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html)
**3.** If you want to customize your /boot/grub/grub.cfg file yourself, you first need to edit either /etc/default/grub or one of the files in /etc/grub.d and then run '[sudo ]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#update-grub")[update-grub]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#update-grub")' or '[sudo grub-mkconfig]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#grub-mkconfig")'.

---

### Post by Wa1k3rTXRang3r on 2009-10-07
i installed and ran os prober and it still didnt find fedora lol

---

### Post by oldfred on 2009-10-07
This thread asks the same question on Fedora, but I did not see an answer. I do not know Fedora but suggest installing Fedora's grub to its boot partition, and creating a custom entry as shown in Herman's site, and run the update grub command to incorporate the new file.

[http://ubuntuforums.org/showthread.php?t=1186045&page=2](http://ubuntuforums.org/showthread.php?t=1186045&page=2)


[http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html)


[FONT=Bitstream Vera Sans Mono]gksudo gedit /etc/grub.d/06_custom[/FONT]

[FONT=Bitstream Vera Sans Mono][/FONT][FONT=Bitstream Vera Sans Mono]#! /bin/sh -e
echo "Adding custom boot entry(s)" >&2
 cat << EOF
[/FONT][FONT=Bitstream Vera Sans Mono]menuentry "Chainload Fedora" {
    set root=(hd0,1)
    chainloader +1    
}[/FONT][FONT=Bitstream Vera Sans Mono]
EOF

Let us know if anything works.
[/FONT]

---

### Post by Wa1k3rTXRang3r on 2009-10-07
i actually decided that having 2 linux oses was rather redundant. so i kept ubuntu and removed fedora.

i can just virtualize fedora if need be.

thanks anyways!

---

