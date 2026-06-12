---
title: "Toshiba SATELLITE P50-C"
date: 2016-02-08
forum: Hardware
---

### Post by irvine_himself2 on 2016-02-08
Having recently bought a new laptop, I am becoming increasingly alarmed about the data collection habits of Windows 10. As a result, I am seriously considering installing Ubuntu. The problem is that, after some research, I have read several reports about Toshiba laptops having problems loading the Grub boot file. It seems to be something to do with the UEFI Bios?

Can anybody shed more light on this? 

Additionally, since easy installs tend not to be reported, I would love to hear from people who have successfully installed Ubuntu onto similar machines.

The basic hardware is as follows:

Manufacturer ---------                Toshiba
Model Name ----------                   SATELLITE P50-C
OS Version -----------                  Microsoft Windows 10 Home 
BIOS Version --------                 1.40
CPU ------------------                         Intel(R) Core(TM) i7-6500U CPU @ 2.50GHz
Hard Drive -----------                     SSD 256 GB
Physical Memory ----             16384MB RAM
Video-----------------                        Intel(R) HD Graphics 520 
                             ------------------------NVIDIA GeForce 930M  
Screen Resolution --            1920 x 1080 Pixels
Sound ---------------                        Conexant SmartAudio HD 
                             ------------------------Intel(R) Display Audio 
Network  ------------                     Generic Mobile Broadband Adapter
                             ------------------------Intel(R) Dual Band Wireless-AC 3165  
                             ------------------------Realtek PCIe GBE Family Controller
Modem--------------                        Vodaphone PAYG


Thanks in advance, Irvine

---

### Post by mörgæs on 2016-02-08
Your fear could be real. UEFI is slowly approaching a Windows-only facility, giving increasingly more trouble to free software. 

I don't use UEFI myself so can't guide you. Best option is probably to search for Oldfreds post on the topic.

---

### Post by sudodus on 2016-02-08
With a new computer, it is a good idea to try with a new version of Ubuntu, so 15.10 or even the next version, which is still in the development phase, Xenial Xerus, to become 16.04 LTS, because you might need the new hardware drivers that come with new linux versions.

Try Ubuntu live (booted from a USB pendrive before installing. See these links and links from them:

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick), particularly (but not only) the paragraph about [UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI), which also links to a tutorial thread by *oldfred*.

If the computer boots and runs nicely live (maybe with the boot option nomodeset), it should also be possible to install that version of Ubuntu.

-o-

Do you want to keep Windows and make a dual boot system with Ubuntu and Windows (more difficult), or would you prefer an Ubuntu only system (easier)?

---

### Post by irvine_himself2 on 2016-02-08
Thanks for your replies, it looks like this is going to be a non-trivial exercise!

At the moment I am just doing basic research. My main internet connection is through a PAYG dongle with very expensive, tight data limits. When I am ready to make the install, I will have to visit a friend to use his network WiFi.

I am only into my second week with the laptop and, to maintain the warranty, I need to keep Windows 10 along with the OEM firmware. Unfortunately, the deeper I delve into Windows 10, the more  worried I become about basic privacy and security. Even simple things like the help files are only available on-line! In other words, irrespective of what privacy settings I choose, Microsoft is gathering data about what I am doing, what I am interested in .... etc, etc. Even scarier, is what Windows 10 allows installed apps to do .... ugh! ... Just do not get me started.

My ultimate aim, once the warranty is over, is to have a single boot Ubuntu system with an open source Bios, but, for the moment, have to settle for installing Ubuntu as a dual boot alongside Windows.
 
Thanks for the links. I had already read the post by OldFred and found it quite intimidating, but  after re-reading it in the context of "InstallingFromUSB", it makes more sense. 

Anyway, there are other things I need to consider. For example, according to the salesman, getting the Vodafone modem working will take at least 15 minutes. So, I shall plod away with some basic research into likely problems and, hopefully, will feel confident enough to attempt an install by the next Monday. 

Since this is of topical interest, I will keep you posted, and if anybody has anything useful to contribute, I would love to hear from you.

Irvine

---

### Post by irvine_himself2 on 2016-02-20
[COLOR=#000000][SIZE=2]As promised, here is an update on installing Ubuntu on a Toshiba Satellite laptop. [/SIZE][/COLOR] 
 

 [COLOR=#000000][SIZE=2]I have tested Wiley Werewolf  releases of both Ubuntu Studio and Lubuntu and both work out of the box. However, there are a couple of points one should take note of. [/SIZE][/COLOR] 
 
 [COLOR=#000000][SIZE=2]**1)** Because of possible issues with the way a USB is formatted,when creating a bootable external hard disk using the PenDrive utility,  (see link below,) make sure to check the “Auto Format” box, (see the PenDrive FAQ)
[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=2]**2)** Assuming you are switching from windows 10, make sure to switch off secure boot. Do this by:[/SIZE][/COLOR]
 
[LIST=1]
[*][COLOR=#000000][SIZE=2]Hold     down shift and click restart:[/SIZE][/COLOR] 
[*][COLOR=#000000][SIZE=2]At     the reboots splash screen: >> Troubleshoot >> Advanced     >> EFI/FIRMWARE >> Secure Boot OFF >> Save and     exit.[/SIZE][/COLOR] 
[*][COLOR=#000000][SIZE=2]Optionally,     you can also change the boot order to make the EFI USB the primary     boot device[/SIZE][/COLOR] 
[*][COLOR=#000000][SIZE=2]Alternatively,     you can boot into the EFI USB from the previous splash screen.[/SIZE][/COLOR] 
[/LIST]
 
 **[COLOR=#000000][SIZE=2]Observations:[/SIZE][/COLOR]**
 
[LIST=1]
[*][COLOR=#000000][SIZE=2]The     EFI firmware that comes with the Ubuntu ISO seems to works well with     the laptop hardware, and, apart from Nvidia Optimus, (see below,)     playing with the live system has not revealed any problems.[/SIZE][/COLOR] 
[*][COLOR=#000000][SIZE=2]There     were no problems with the Vodafone PAYG dongle. It is interpreted to     be an Ethernet connection, and, when in an environment with multiple     available networks, clicking auto Ethernet worked for me.[/SIZE][/COLOR] 
[/LIST]
  
 **[COLOR=#000000][SIZE=2]Nvidia Optimus[/SIZE][/COLOR]**[COLOR=#000000][SIZE=2]**:** 
Basically, in comparison to Intel's onboard GPU, external GPUs use a lot of power and generate a lot of waste heat. As a result, in windows 10, all programs default to Intel's built in GPU. With this in mind, the Nvidia Optimus utility  allows the user to assign specific programs to the Nvdia GPU. Sadly, Nvidia's support of Linux received a two fingered salute from Linus Torvalds. [/SIZE][/COLOR] 

 [COLOR=#000000][SIZE=2]Thankfully, there are a number of alternatives, see this article for details: [http://www.thelinuxrain.com/articles/the-state-of-nvidia-optimus-on-linux](http://www.thelinuxrain.com/articles/the-state-of-nvidia-optimus-on-linux)[/SIZE][/COLOR]

 **[COLOR=#000000][SIZE=2]In conclusion:[/SIZE][/COLOR]**[COLOR=#000000][SIZE=2] 
Bearing in mind that I have some experience of running both dual and single boot boxes. I have more or less decided to make an image of my current Windows 10 installation, and then install Ubuntu Studio as a single boot. From the  point of view my main interests in computing, this gives me nearly everything I need without the privacy buster called Windows 10.[/SIZE][/COLOR]
 
 [COLOR=#000000][SIZE=2]On this topic, as an aside, with all settings at their most restrictive, Windows 10 uploaded over 30MB of data over the last week.. Then, as a final insult, when I connected to an unmetered connection, it uploaded a further 300MB.  Nvidia bloatware, along with various other non-essential Apps, are equally as bad.[/SIZE][/COLOR]
 
 [COLOR=#000000][SIZE=2]**Note 1:** PenDrive is available at  [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)[/SIZE][/COLOR]

 [COLOR=#000000][SIZE=2]**Note 2:** Finally, installation is progressing very slowly because my primary internet connection is a very expensive PAYG modem, and I can only afford major downloads when connecting through a friends network.

PS, 
How do I mark this post as solved?
[/SIZE][/COLOR]

---

### Post by sudodus on 2016-02-20
I'm glad it works for you :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by mörgæs on 2016-02-20
Thanks for a thorough description.

Could you please add a brief post to the [compatibility thread]("http://ubuntuforums.org/showthread.php?t=1543006")?

---

### Post by irvine_himself2 on 2016-02-20
> **mörgæs said:**
> ........ Could you please add a brief post to the [compatibility thread]("http://ubuntuforums.org/showthread.php?t=1543006")?

Done!

---

