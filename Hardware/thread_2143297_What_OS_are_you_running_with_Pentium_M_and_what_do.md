---
title: "What OS are you running with Pentium M and what do you want next?"
date: 2013-05-08
forum: Hardware
---

### Post by sudodus on 2013-05-08
Hello Pentium M users,

If you have a laptop with Pentium M CPU, what OS are you running? And how are you using it?

I think most if not all of these laptops came with Windows XP, but if you read this post, you have probably tried some Ubuntu version and flavour.

- Ubuntu 8.04 LTS ... 10.04 desktop LTS (past end of life)
- Xubuntu 8.04 LTS ... 12.04 LTS (end of life April 2015)
- Lubuntu 10.04 ...12.04 (end of life October 2013)
- kansasnoob's 12.04 LTS / Precise Classic (No effects) Tweaks and tricks (end of life April 2017)
- LXLE (based on Lubuntu 12.04) intended to be maintained as an LTS release (end of life April 2017)
- Windows XP (end of life April 2014)

There are many high quality professional laptops with Pentium M CPUs, that are still in good shape. But the available operating systems are decreasing in number. I think there will be a lot of computers, that will be abandoned at Windows XP end of life, which is less than one year from now. This is an opportunity to get an old but still high quality laptop very cheap. If you know how to run it with supported versions and flavours of Ubuntu, it can be a good companion for some more years. See also this link

 [https://wiki.ubuntu.com/Lubuntu/CommunicationsTeam/WOWLubuntu/StartUbuntu](https://wiki.ubuntu.com/Lubuntu/CommunicationsTeam/WOWLubuntu/StartUbuntu)

If you want to run a new version of the Ubuntu flavours, you will have problems because these have only PAE kernels, and many old Pentium M CPUs have no PAE flag. But the good news is that these CPUs have PAE capability, and there is a method to run the versions 12.10 and 13.04 with fake-PAE by 7bit.

See these links

[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)
[COLOR=#008000]***New: Instructions how to ***[/COLOR][COLOR=#008000]***make install USB drive***[/COLOR][COLOR=#008000]*** from Windows with graphical user interface tools***
[/COLOR]
-o-

I suggest that we can describe our hardware and software, and how we intend to run these laptops.

I have an IBM Thinkpad T42 and a friend of mine has an IBM Thinkpad T41. We use them for daily activities (of course no HD video or numbercrunching). Both laptops are still going strong with Lubuntu 12.04. But I am preparing for Lubuntu's non-pae end of life in October, and have made Lubuntu-fake-PAE, that uses fake-PAE to help installing Lubuntu 13.04 directly.

---

### Post by kansasnoob on 2013-05-08
Well done :D

---

### Post by papibe on 2013-05-08
Hi.

I have 2 working Pentium M laptops.

**Toshiba Satellite (5150-S501).**
Long time ago it was converted to Linux. It has run Debian, Debian with KDE, Crunchbang, but I settled with Ubuntu 8.10. It was upgraded to every new Ubuntu release until it got problems with the screen: anything in graphic mode crashed. I installed Ubuntu Server, and it's been running perfectly since then. I use it mainly for video and audio conversion ("closet computing" as I called it ;) ). Currently running Server 12.04.

**HP (compaq nc6120).**
This was my wife's main computer back in the day. After EOL, she bought it for one dollar :). It was a excruciatingly slow. It was a XP + some-almost-impossible-to-remove-antivirus machine. Since her main purpose of refurbishing the laptop was to use Firefox, and VLC, I installed Xubuntu. Ohh, the difference! Currently running Xubuntu 12.04.

Regards.

---

### Post by mörgæs on 2013-05-08
What we really need is one very small operation: The **test for** PAE flag should be removed from the standard PAE ISO. 

7bit's PPA (and hence our wiki pages) is only a workaround.

---

### Post by roten on 2013-05-09
These are real alternatives for me

> **sudodus said:**
> 

- Xubuntu 8.04 LTS ... 12.04 LTS (end of life April 2015)
- Lubuntu 10.04 ...12.04 (end of life October 2013)
- kansasnoob's 12.04 LTS / Precise Classic (No effects) Tweaks and tricks (end of life April 2017)


Interesting:
> 
There are many high quality professional laptops with Pentium M CPUs, that are still in good shape. But the available operating systems are decreasing in number. I think there will be a lot of computers, that will be abandoned at Windows XP end of life, which is less than one year from now. This is an opportunity to get an old but still high quality laptop very cheap. If you know how to run it with supported versions and flavours of Ubuntu, it can be a good companion for some more years. See also this link

 [https://wiki.ubuntu.com/Lubuntu/CommunicationsTeam/WOWLubuntu/StartUbuntu](https://wiki.ubuntu.com/Lubuntu/CommunicationsTeam/WOWLubuntu/StartUbuntu)



I will check fake-pae for upgrading Lubuntu.

---

### Post by elbarbudo on 2013-05-09
I have 2 old laptops : HP Compaq nx6110 and nc6000
Both are running Ubuntu 12.04 non-pae remix.

They work fine, but startup is rather slow.

I tried the fake-pae patch and upgraded the nc6000 to 12.10 : the upgrade succeded perfectly.
 BUT I lost the dns resolution and hence it was unusable.

My aim was to upgrade to 13.04 which is said to have less memory footprint in order to be used on tablets.
But as I was unable to resolve names in URL, I was unable to continue, so I downgraded to 12.04.

---

### Post by mörgæs on 2013-05-09
According to
[http://www.cnet.com/laptops/hp-compaq-nx6110/4507-3121_7-31281875.html](http://www.cnet.com/laptops/hp-compaq-nx6110/4507-3121_7-31281875.html) 
the nx6110 has one of the newer Pentium M, so you can install any version straight away. 

As explained on the wiki page the problem is only for the versions with 400 MHz front side bus, and you have 533.

---

### Post by sudodus on 2013-05-09
> **elbarbudo said:**
> I have 2 old laptops : HP Compaq nx6110 and nc6000
Both are running Ubuntu 12.04 non-pae remix.

They work fine, but startup is rather slow.

I tried the fake-pae patch and upgraded the nc6000 to 12.10 : the upgrade succeded perfectly.
 BUT I lost the dns resolution and hence it was unusable.

My aim was to upgrade to 13.04 which is said to have less memory footprint in order to be used on tablets.
But as I was unable to resolve names in URL, I was unable to continue, so I downgraded to 12.04.

Welcome to the Ubuntu Forums :-)

The reason that you lost the DNS resolution might be, that the upgrade of the nc6000 to 12.10 was not completely successful.

If you want to try a new version again, this time Lubuntu 13.04, you can make a live USB drive

- with the method 'grub-n-iso' if you have a 1 GB or 2 GB USB pendrive or
- with the method 'installed system' if you have a 16 GB USB drive.

See this link for details:

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

Use that USB drive to run a live session (with installing anything to your internal HDD) and test if DNS is working. If it works, it should work also after installation to the HDD.

-o-

I agree with *mörgæs* concerning the nx6110. It should not need the fake-pae to run 32-bit pae operating systems.

---

### Post by ImConfused on 2013-05-09
Pentium M 1500MHz running Mint Linux 13 Maya XFCE.  I have it mounted on a USB hard drive partition and I use a CD with isolinux to bootstrap the system to work.  Can't boot from a USB with my Bios.

Started looking at Gentoo.  I don't know if I will give up on it but I know that Gentoo allows you to configure the kernel to the computer instead of trying to get a computer to fit to the kernel.  It looks really difficult but if I can get it to work it should be well worth the aggravation.  

The discussions I see about trying to get Cannonical to do the right thing by not abandoning a perfectly good computer system remind me of what a friend told me.  When you argue with a fool, who is the fool?

---

### Post by mightyiam on 2013-05-09
My client has an IBM T42 with a Pentium M that we want to use as an LTSP thin client but since we upgraded to 13.04 we have to resort to a workaround and it is not worth the effort.

---

### Post by sudodus on 2013-05-09
> **ImConfused said:**
> Pentium M 1500MHz running Mint Linux 13 Maya XFCE.  I have it mounted on a USB hard drive partition and I use a CD with isolinux to bootstrap the system to work.  Can't boot from a USB with my Bios.

Started looking at Gentoo.  I don't know if I will give up on it but I know that Gentoo allows you to configure the kernel to the computer instead of trying to get a computer to fit to the kernel.  It looks really difficult but if I can get it to work it should be well worth the aggravation.  

The discussions I see about trying to get Cannonical to do the right thing by not abandoning a perfectly good computer system remind me of what a friend told me.  When you argue with a fool, who is the fool?

If you are interested, you can try Lubuntu-fake-PAE [https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

We are not sure that older Pentium M CPUs can run well with it. So, at an early stage after booting into Lubuntu 13.04, check that

```
cat /proc/cpuinfo
```

reports 36 bit physical address size! (While you are running Linux Mint 13, the cpuinfo will probably report only 32 bits.)

---

### Post by sudodus on 2013-05-09
> **DawnLight said:**
> My client has an IBM T42 with a Pentium M that we want to use as an LTSP thin client but since we upgraded to 13.04 we have to resort to a workaround and it is not worth the effort.

Your client and you decide what to do, but I think the extra effort is very small (to use fake-pae to help in the upgrading process).

But if you want a pure official release, because you do not rely on this work-around, I can understand and accept it, although I have an IBM T42 myself and Lubuntu 13.04 runs beautifully with its Pentium M processor.

---

### Post by sudodus on 2013-05-09
We have issued this poll in order to know how much effort to focus on the Pentium M problems with PAE kernels.

[http://ubuntuforums.org/showthread.php?t=2143502](http://ubuntuforums.org/showthread.php?t=2143502)

---

### Post by kansasnoob on 2013-05-09
> **DawnLight said:**
> My client has an IBM T42 with a Pentium M that we want to use as an LTSP thin client but since we upgraded to 13.04 we have to resort to a workaround and it is not worth the effort.

This is exactly why Edubuntu supports the "classic gnome" DE in 12.04:

[ATTACH=CONFIG]242374[/ATTACH]

And both Ubuntu and Edubuntu 12.04 are supported until April 2017.

---

### Post by kansasnoob on 2013-05-09
Where, and how well, does this PPA play into this game:

[https://launchpad.net/~prof7bit/+archive/fake-pae](https://launchpad.net/~prof7bit/+archive/fake-pae)

---

### Post by sudodus on 2013-05-09
> **kansasnoob said:**
> This is exactly why Edubuntu supports the "classic gnome" DE in 12.04:

[ATTACH=CONFIG]242374[/ATTACH]

And both Ubuntu and Edubuntu 12.04 are supported until April 2017.
So I should add Edubuntu 12.04 to the list of available systems in post #1?

---

### Post by mightyiam on 2013-05-09
Excuse me, kansasnoob, but what does Edubuntu and classic gnome have to do with pae, please?

---

### Post by |{urse on 2013-05-09
Mint 13 also, 14 seems slower/buggier. On a Lenovo G580. I also have a Dell D400 (also a pentium m) running Porteus, it is even faster.

---

### Post by |{urse on 2013-05-09
With that proc, I'd explore distributions that feature the razor-qt desktop. I'm very impressed with it's speed and ease of configuration.

---

### Post by sudodus on 2013-05-09
> **|{urse said:**
> Mint 13 also, 14 seems slower/buggier. On a Lenovo G580. I also have a Dell D400 (also a pentium m) running Porteus, it is even faster.
Do you know by heart the end of life of Mint 13 and Porteus? And are you running the main flavour of Mint 13?

---

### Post by |{urse on 2013-05-09
I sure don't, I'm running cinnamon. :)

---

### Post by kansasnoob on 2013-05-09
> **DawnLight said:**
> Excuse me, kansasnoob, but what does Edubuntu and classic gnome have to do with pae, please?

Nothing other than the fact that you can still install a non-pae 12.04 version of Ubuntu and use the lightweight metacity window manager up until April 2017.

And in that reply I was specifically referring to the OP's reference to LTSP :)

---

### Post by sudodus on 2013-05-09
> **kansasnoob said:**
> Where, and how well, does this PPA play into this game:

[https://launchpad.net/~prof7bit/+archive/fake-pae](https://launchpad.net/~prof7bit/+archive/fake-pae)

*7bit*'s fake-pae ppa is used by both *mörgæs* and me to make the pae operating system accept Pentium M CPUs. It works well; we have seen no problem. But we need to warn, that some Pentium M CPUs may not work with pae, so we ask each user to run

```
cat /proc/cpuinfo
```

and check if it reports 36 bit physical address size.

---

### Post by kansasnoob on 2013-05-09
> **sudodus said:**
> So I should add Edubuntu 12.04 to the list of available systems in post #1?

No. Only Lubuntu and Xubuntu 12.04 live images shipped with non-pae kernels, but there are still updated non-pae 12.04 netboot images available:

[http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/installer-i386/current/images/netboot/non-pae/](http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/installer-i386/current/images/netboot/non-pae/)

I only suggest using the "classic gnome" UI because I know it's supported by Edubuntu until April 2017 whereas Xubuntu 12.04 chose only a 3 year support cycle, and Lubuntu chose only an 18 month support cycle :)

---

### Post by sudodus on 2013-05-10
[COLOR=#008000][I][B]New: Instructions how to make install USB drive from Windows with graphical user interface tools

[/B][/I][URL="https://help.ubuntu.com/community/Lubuntu-fake-PAE"]https://help.ubuntu.com/community/Lubuntu-fake-PAE
[SIZE=3]
[/SIZE][/URL][/COLOR]*Edit*: Now the current detailed instructions also reside at the  Ubuntu wiki and are easily available from the page above.

---

### Post by sudodus on 2013-09-07
There is a new alternative to install Ubuntu based operating systems into computers of various age and kind, also Celeron M and Pentium M computers, the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971"), the 'OBI'.

The OBI is designed to be easy to use and have a very small foot-print and uses only standard programs and shell-scripts in text mode. Installed systems with non-PAE kernels or fake-PAE are portable between many computers, and they are stored in compressed tar archive files, ***tarballs***.

```
GnomeClassic1204-oem.tar.gz
GnomeClassic1204.tar.gz
lubuntu-10.04.tar.gz    # good for old systems but past end of life of desktop packages
Lubuntu_13.04sept1.tar.gz
lxle-2013-08-19.tar.gz
OneButtonInstaller_blank-noswap.tar.gz
saucyalfa2.tar.gz
saucybeta1.tar.gz       # new 
ubuntu-10.04.tar.gz     # good for old systems but past end of life of desktop packages
```

The OBI helps you make such a tarball of your own system and use it as a backup or to port the system to another computer.

---

### Post by sudodus on 2013-09-07
There is a new alternative to install Ubuntu based operating systems into computers of various age and kind, also Celeron M and Pentium M computers, the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971"), the 'OBI'.

The OBI is designed to be easy to use and have a very small foot-print. It uses only standard programs and shell-scripts in text mode. Installed systems with non-PAE kernels or fake-PAE are portable between many computers, and they are stored in compressed tar archive files, ***tarballs***.

```
GnomeClassic1204-oem.tar.gz
GnomeClassic1204.tar.gz
lubuntu-10.04.tar.gz    # good for old systems but past end of life of desktop packages
Lubuntu_13.04sept1.tar.gz
lxle-2013-08-19.tar.gz
OneButtonInstaller_blank-noswap.tar.gz
saucyalfa2.tar.gz
saucybeta1.tar.gz       # new 
ubuntu-10.04.tar.gz     # good for old systems but past end of life of desktop packages
```

The OBI helps you make such a tarball of your own system and use it as a backup or to port the system to another computer.

---

### Post by kurt18947 on 2013-09-07
I'm using a less-discussed install on a Thinkpad R31 Celeron -- Snow Linux 4.0 XFCE.  XFCE worked but it wasn't snappy.  I discovered I also had Gnome classic as an option.  That works pretty well.  The Intel graphics chip - 82801?? - seems like a real problem child.  I tried their E17 live CD but couldn't get it to load into a live session.  This is using a modern kernel, 3.5.x or 3.8.x and is supported until I think 2016.

---

### Post by sudodus on 2013-09-07
Sometimes it helps to change the Xorg acceleration method to UXA. See this excerpt from a conversation in the Lubuntu community mail.

> John Hupp <lubuntu@prpcompany.com> wrote:

There was this helpful bug report on file at [http://bugs.launchpad.net/ubuntu/+source/linux/+bug/1178982](http://bugs.launchpad.net/ubuntu/+source/linux/+bug/1178982).

It described behavior on Dell PC's with integrated Intel graphics, in which Adobe Flash Player would display only with shades of purple and green in a horizontally compressed window (or at least that's how I would describe what I see on a Dell Dimension 2400).

The work-around (Comment #1) was to change the Xorg acceleration method to UXA. 

User reported a work-around:

-o-

Edit (or create) /etc/X11/xorg.conf as follows: (ugh, can't format, should be a tab before each line except the first and the last).

```
Section "Device"
 Identifier "Intel Graphics"
 Driver "intel"
 Option "AccelMethod" "uxa"
EndSection

```
Restart X (reboot, restart your display manager, whatever). Colors are back to the way they used to be and flash works.

-o-

I forgot to include, however, that the bug workaround messes up the login screen (LightDM).  You can make out an entry box that one assumes is for the password entry, but everything else is largely unidentifiable.

So as a workaround it leaves a lot to be desired, unless we can also figure out how to fix the login screen.

-o-

Nio Wiklund wrote:

This method works for me to restore good graphics in an old IBM Thinkcentre with Lubuntu Saucy alpha-2 and the following Intel graphics.

VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

There is no issue with the login screen.


---

