---
title: "New PC Hardware Compatibility"
date: 2016-08-21
forum: Hardware
---

### Post by nanth on 2016-08-21
I recently built my first pc but ever time I have tried to install Ubuntu it doesn't work. There are a lot of different types of errors that show up depending on what I do.

Erase and Install or Something Else:
When ever I try to do either of those methods it fails to mount or format a seemingly random partition. When I tried pressing continue on the error message it started the download but after failing to download scrollbar overlay it would only output a few other random errors but for the most part it would add time to the estimated download time. I let it try to download for a couple days but still nothing.

GParted then install:
When I try to use GParted it always failed to create or mount a partition in the same way as above. I never got to start the download when I did that.

Parted Magic from Ultimate Boot CD then install:
I used GParted on the Parted Magic distro from the UBCD live cd and the partitioning worked but when I went to install Ubuntu I clicked "Something else" and set up the partitions properly it gets to the download but does the same thing when I clicked continue in the formatting/mounting error.

Eventually I found a form post saying that my hard drive (a Western Digital) didn't like Ubuntu. So I bought a new one installed it but now I'm getting the same problems as before. I almost certain I've got the pc assembled right and the custom partions set up properly since my friend who helped me build it has built a lot of other computers (but always uses windows) and my brother is really good at Ubuntu and computer system stuff.

System Part List:
CPU: [AMD FX-6300 3.5GHz 6-Core Processor]("http://pcpartpicker.com/product/PnxfrH/amd-cpu-fd6300wmhkbox")
CPU Cooler: [Cooler Master Hyper T2 54.8 CFM Sleeve Bearing CPU Cooler]("http://pcpartpicker.com/product/FNXfrH/cooler-master-cpu-cooler-rrht228pkr1")
Motherboard: [Gigabyte GA-970A-UD3P ATX AM3+ Motherboard]("http://pcpartpicker.com/product/Vrdqqs/gigabyte-motherboard-ga970aud3p")
Memory: [Kingston HyperX Fury Black 8GB (2 x 4GB) DDR3-1600 Memory]("http://pcpartpicker.com/product/M63RsY/kingston-memory-hx316c10fbk28")
Hard Drive: [Seagate Barracuda 1TB 3.5" 7200RPM Internal Hard Drive]("http://pcpartpicker.com/product/dCxfrH/seagate-internal-hard-drive-st1000dm003")
Graphics Card:[ MSI GeForce GT 740 2GB Video Card]("http://pcpartpicker.com/product/bhyxFT/msi-video-card-n7402gd3v1")
Case: [BitFenix Nova ATX Mid Tower Case]("http://pcpartpicker.com/product/hJM323/bitfenix-case-bfxnov100kkxskrp")
Power Supply: [EVGA 400W ATX Power Supply]("http://pcpartpicker.com/product/86M323/evga-power-supply-100n10400l1")
Optics Drive: [Lite-On iHAS124-14 DVD/CD Writer]("http://pcpartpicker.com/product/6fJwrH/lite-on-optical-drive-ihas12414")

If you need any more info I'd be happy to provide it.

Thank you so much in advance!

Edit:
[SIZE=6]
SOLVED
[/SIZE]
All I had to do was:

Enable IOMMU,
Install Ubuntu,
Do this [https://ubuntuforums.org/showthread.php?t=2188370](https://ubuntuforums.org/showthread.php?t=2188370),
And now everthing seems to be working!

Thank you so much everyone who replied and a big THANK YOU to [**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=852711")!

---

### Post by mörgæs on 2016-08-22
Hi, welcome to the fora.

I suggest that you do a live boot of the development version (16.10) for comparison. If it works then you have a proof that the hardware is fine.

---

### Post by oldfred on 2016-08-22
Those motherboards have IOMMU setting in UEFI and often need other boot parameters.

 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370) 

      
 UEFI/gpt partitioning in Advance:
[URL="http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu"]http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu
[/URL]
 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 

      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
    [URL="http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu"]
[/URL]

---

### Post by gordintoronto on 2016-08-22
You're listening to bad advice if you think a WD hard drive "doesn't like Ubuntu."

Did you run memtest?

---

### Post by manish21thakur on 2016-08-23
Motherboard:                         Asus M5A97 evo 2.0
Processor:                AMD FX 6300
Cooler:                     AMD stock copper 125W
Graphics:                  ATI Radeon HD6770 1GB
Power:                     Powercool 750W ATX Power
Case Fans:               92mm
OS:                          Window10 Home/Pro x64
Storage:                   Sata 1TB Hard Drive
Case/Body:                Aerocool v3x Black Edition ATX

---

### Post by nanth on 2016-08-23
Thank you all for your replies,

 	[**[COLOR=#DD4814][B]mörgæs**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=939075") 	 

I have tried ubuntu 14.04, 16.04 and mint 18 all of them did the same thing but I will try 16.10.

[**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=852711")
Thank you, I havn't gotten through all the links in detail yet but I hope they will fix the problem.

[**[COLOR=#000000]gordintoronto[/COLOR]**]("https://ubuntuforums.org/member.php?u=507940")
The post I found was a little vague on it. I did run a test and ever bit was in perfect condition. Thank you for clarifying that but I've already got the other one installed and the old one sent back.

[**[COLOR=#000000]manish21thakur[/COLOR]**]("https://ubuntuforums.org/member.php?u=2041846")
Is that your suggested revision to my hardware?

---

### Post by nanth on 2016-08-23
[SIZE=6]SOLVED
[/SIZE]
All I had to do was:

Enable IOMMU,
Install Ubuntu,
Do this [https://ubuntuforums.org/showthread.php?t=2188370](https://ubuntuforums.org/showthread.php?t=2188370),
And now everthing seems to be working!

Thank you so much everyone who replied and a big THANK YOU to [**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=852711")!

---

