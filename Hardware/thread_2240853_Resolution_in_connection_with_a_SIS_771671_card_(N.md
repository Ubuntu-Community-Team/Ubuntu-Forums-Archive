---
title: "Resolution in connection with a SIS 771/671 card (Need a portuguese translation)"
date: 2014-08-22
forum: Hardware
---

### Post by bergfex2 on 2014-08-22
Hello.

I have installed Ubuntu 14.04 LTS on my old Nettop. In General everything works, but the resolution is now 640 x 480. Is there a possibility to change this. 

```
peter@peter:~$ lspci -nnk | grep -i "VGA\|'Kern'\|3D\|Display" -A2
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter [1039:6351] (rev 10)
    Subsystem: Pegatron Device [1b0a:0007]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03) 
``` 

```
 peter@peter:~$ xrandr --prop
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected primary 640x480+0+0 0mm x 0mm
   640x480        73.0* 
```

But now I have found this webside (unfortunately written in Portugese). But it seems to me that this person has found a solution.
[http://www.vivaolinux.com.br/dica/Configurando-SIS-67172-no-Ubuntu-1404](http://www.vivaolinux.com.br/dica/Configurando-SIS-67172-no-Ubuntu-1404)

Please can you say to me, if this website is an guideline for the SIS?

Thanks a lot.

Bergfex.

---

### Post by ajgreeny on 2014-08-22
Here's a translation made with google-translate that may help you.
> [h=1][SIZE=3]Configuring SIS 671 | 72 in Ubuntu 14:04 [/SIZE][/h]  Greetings. 

  For anyone who owns a micro with *SIS 671* notorious *| 2,*  like me, with the release of Ubuntu 14:04, being LTS, giving us an  extra term in the weariness of [re] configure device drivers and will  want to configure , properly, of course, such a plate. 

  Well, this tip is aimed at this and already provides the files, which, being scarce, present no great cost low. 

   I followed the release, both by owning Notebook with this poorly video  card, for use at work, Ubuntu (home, Fedora), since the Beta versions,  through the Final RC. 

  In all, including the official version, this tip has worked.   Nothing guarantees that in the near future, this version of the  sisimedia driver to crash, due to incompatibility between this version  and the graphical server. 

  I will provide a way to keep the two interoperable as far as possible.  I'm reporting the version of X: X.Org X Server 1.15.1.  As well. 

  My first approach, which worked, was download DVD Mageia (distro version: 4) and test on my note (CCE LP212).  Worked satisfactorily.  Graphics in 1280 x 800, 60 Hz. SisCtrl stated in [color=#5C5C5C]xorg.conf[/COLOR] and running. 

  Second approach, only download RPMs Mageia / Mandriva.  That's it.  Not need the Debs, it is not necessary to install anything.  If necessary, we could use [color=#5C5C5C]alien[/COLOR] to convert the formats of the packets.  Was not.  Extract with [color=#5C5C5C]Ark,[/COLOR] the packages to a temporary folder with enabled option "Preserve Paths in Extraction" or similar.  This is critical. 

  I copied the temporary folder with all the Path to the root.  Compactei everything including the [color=#5C5C5C]xorg.conf,[/COLOR] properly configured, which follows in the [color=#5C5C5C]zip:[/COLOR] 
[LIST]
[*]  [sisimedia1404.zip]("http://img.vivaolinux.com.br/imagens/dicas/comunidade/sisimedia1404.zip")
[/LIST]

  I installed *Ubuntu 14:04,* testing each available with these compressed files.  In all instances, I reiterate, it worked satisfactorily.  You just need to do the reverse way, ie, unzip the contents of the [color=#5C5C5C]zip,[/COLOR] honoring the "Preserve Paths in Extraction" in this moment. 

  When using the terminal, we use the [color=#5C5C5C]unzip[/COLOR] with [color=#5C5C5C]x[/COLOR] option to preserve the Path compression. 

  - How to keep up, to break compatibility in a future update of X? 

   Well, in theory, just download the latest RPM package because, as I  said, no need to install both the driver of sisimedia as the SisCtrl [color=#5C5C5C](x11-driver-video-0.9-sisimedia. *. Rpm[/COLOR] and [color=#5C5C5C]0.0-sisctrl * .20051 .rpm[/COLOR] are recent, until now). 

  Search, instead of taking the full name.  Therefore, the asterisks, purposely.  After all, besides the version of the package has the architecture [color=#5C5C5C](i386[/COLOR] or [color=#5C5C5C]x64)[/COLOR] and do as I did.  Extract it and copy the folder with all the route ("Path") to the root system. 

  Yes, one detail: the zipped file has a shortcut (SIS SisCTRL.Desktop).   He is responsible for implementing the SisCtrl, which allows you to  manipulate the outputs of SIS card (TV, second monitor, etc). 




---

### Post by mörgæs on 2014-08-22
You could also take a look at [http://ubuntuforums.org/showthread.php?t=2215422](http://ubuntuforums.org/showthread.php?t=2215422)

---

### Post by dorian.schramm on 2014-08-22
His portuguese is weird and looks like it is already a translation from another language but I'll do my best to give you a summary.
_The underlined are my comments on it. Not a part of the original post._

> He says that he has been doing this since the Betas of the Ubuntu, going through the Final RC. It has been working but he doesn't know for sure how long.
He is reffering to the version of X: X.Org X Server 1.15.1.

The first thing that he did was to download Mageia (distro 4 version) DVD and test it on his laptop (CCE LP212). It worked fine in 1280 x 800, 60 Hz. SisCtrl declared on [color=#5C5C5C]xorg.conf [/COLOR]and working.

The second thing he did was to download only the RPMs of Mageia/Mandriva. He said that you don't need the Debs, since you don't need to install. If necessary you could use [color=#5C5C5C]alien[/COLOR] to convert the packets format. It wasn't necessary for him. He then extracted the packets with [color=#5C5C5C]Ark[/COLOR] to a temporary folder with the option "Preserve Extraction Paths" or similar enable. That is fundamental.

He copied the temp folder with the hole Path to the root. Compacted everything, including the o [color=#5C5C5C]xorg.conf[/COLOR] already configurated, which is in the .zip

[sisimedia1404.zip]("http://img.vivaolinux.com.br/imagens/dicas/comunidade/sisimedia1404.zip")

He installed Ubuntu 14.04 testing each release _(not sure if that is the correct translation)_ with the compacted files. It worked in all times. You only need to do the reverse path, which is, decompact the .zip contents, honoring the "Preserve Extraction Paths" option.

If you use the terminal, utilize [color=#5C5C5C]unzip[/COLOR] with the option [color=#5C5C5C]-x[/COLOR] to preserve the extraction paths.

How to keep updated, if it breaks compatibility in a future version of X?

Well, in thesis, you only need to download the most recent RPM packet, you don't need to install, the sisimedia driver and either the SisCtrl ([color=#5C5C5C]x11-driver-video-sisimedia-0.9.*.rpm[/COLOR] e [color=#5C5C5C]sisctrl-0.0.20051*.rpm[/COLOR] are the most recent now).

Search instead if using the hole name _(I know this phrase doesn't make much sense but that is what he wrote)_. That's why he putted the asterisks. Because there are not only versions of the packets but also the architecture ([color=#5C5C5C]i386[/COLOR] or [color=#5C5C5C]x64[/COLOR]). Extract it and copy the whole folder with all the path to the system root.

A detail: in the zipped file there is a shortcut (SIS SisCTRL.Desktop). He is responsible for the execution of the SisCtrl, which allows to manipulate the outputs of the SIS board (TV, display, etc)

If have any doubts about what he meant ask me and I'll see if I can help.

---

