---
title: "Why am I having so much trouble playing DVD's?"
date: 2006-02-11
forum: Hardware &amp; Laptops
---

### Post by hellomynameisphil on 2006-02-11
Kubuntu 5.10. Easy Kubuntu installed. 1 GHz AMD. 256 MB RAM. 128 MB VRAM.

uzer@ubuntu:~$ lspci
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 0 (rev c1)
0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
0000:02:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

Can't play DVD's properly. 

Kaffeine plays them with fine high-frequency static all over the audio, doesn't support menus, and often has jerky playback. 

Mplayer also doesn't support menus and doesn't properly support fullscreen. Jerky playback here too. 

VLC: jerky playback.

xine: jerky playback.

The jerkiness of video playback seems correlated to the age of the DVD. I did manage to perfectly play a newly released DVD on VLC, but still couldn't properly play it on Kaffeine or Mplayer.

---

### Post by kingsidy on 2006-02-11
i assume u have libdvdcss2 installed as it is necessary to play encrypted dvds. if so make sure that you are using the latest version which i think is 1.2.9. Also make sure that dma us enabled. 
as far as mplayer not supporting fillscreen do this:
> sudo cp /etc/mplayer/mplayer.conf /etc/mplayer/mplayer.conf_backup
sudo gedit /etc/mplayer/mplayer.conf

find this line
> vo=x11,                  # To specify default video driver (see -vo help for

and replace it with
> vo=xv,                  # To specify default video driver (see -vo help for

save. then go into the settins for mplayer, under video select xv as the defaul video renderer (or something like that). see screenshot
after that it will support fullscreen

---

### Post by heimo on 2006-02-11
Not sure if this is cause for those DVD playback problems, but it's worth checking out that you have DMA enabled:
[https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)

---

### Post by hellomynameisphil on 2006-02-11
Thanks! The DMA thing seems to make things work better now (though Mplayer now plays DVD's in French by default; I can probably figure out how to fix this on my own). I'll re-post if I have any further issues.

---

### Post by macewan on 2006-02-11
[quote=heimo]Not sure if this is cause for those DVD playback problems, but it's worth checking out that you have DMA enabled:
[https://wiki.ubuntu.com/DMA]("https://wiki.ubuntu.com/DMA")[/quote]

thanks for the link - did the trick for me

sudo hdparm -d1 /dev/hdc

---

