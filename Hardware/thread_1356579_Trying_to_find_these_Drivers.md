---
title: "Trying to find these Drivers"
date: 2009-12-16
forum: Hardware
---

### Post by mahorrocks on 2009-12-16
Hi

I have been searching Hi and Low

Please help me

I am trying to find the below drivers

nForce4 Linux drivers
AMD Turion(tm) 64 X2 Mobile Technology TL-60
CK804 Serial ATA Controller(nVidia Corporation (CLEVO/KAPOK Computer))
CK804 AC'97 Audio Controller
CI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
DVB Device
RTL8111/8168B PCI Express Gigabit Ethernet controller ( I think this will be with the nForce4)
AR5006X Wireless Network Adapter
SynPS/2 Synaptics TouchPad

Is anyone able to help me??

Regards

Mark

---

### Post by IcarusR on 2009-12-17
Most of this should work out of the box.
Have you 'just tried' ubuntu to see if anything works ??
Boot from live CD to test hardware.

If already installed & none of this hardware works then we need more info..
Which Ubuntu.

Post output of the following commands...

```
lspci
```

```
lsusb
```

Then we maybe able to help you get stuff to work.

---

### Post by 73ckn797 on 2009-12-17
Keep in mind that this is not Windows and does not need to have the motherboard driver disk, which would not work in Ubuntu anyway. There is sometimes the need for a wireless driver but that can be easily remedied. Follow the recommendations of "IcarusR" and see how it goes.

---

### Post by mahorrocks on 2009-12-19
mark@mark-laptop:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:04.1 Modem: nVidia Corporation CK804 AC'97 Modem (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 RAID bus controller: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 RAID bus controller: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
03:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce Go 7950 GTX] (rev a1)
04:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce Go 7950 GTX] (rev a1)
05:07.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
05:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
mark@mark-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Tried the wireless but it doesnt seem to behave. It seems to go in and out of connectivity whereas windows is very stable. All is in there but I am so unfamiliar with Linux I dont know what is working and how to install things. Like Quicktime... I downloaded it, unzipped it but then it would not install. How do I install these things too. But my main concern is my wireless driver as to why it is so unstable


I am using Ubuntu 9.10 latest update

---

### Post by coffeecat on 2009-12-19
> **mahorrocks said:**
> mark@mark-laptop:~$ lspci
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

<snip>

Tried the wireless but it doesnt seem to behave. It seems to go in and out of connectivity whereas windows is very stable. 

I'm sorry to hear the AR5001 wireless chipset is not working well. I've got the same AR5001 rev 01 in my Asus netbook and it works well for me - which doesn't help you much. But what might help is to install some backported kernel modules. These are updated drivers. They fixed a similar problem for me with a different Atheros chipset in another machine, and they've helped a number of people around the forum. At the very least, installing them won't do any harm.

Connect to your router with an ethernet cable so you have stable internet. Now go to System > Administration > Synaptic and select these two packages for installation:

linux-backports-modules-karmic-generic
linux-backports-modules-wireless-karmic-generic

That will also mark a third package with a 2.6.31-xx number to match your running kernel. Install them and reboot. Now try wireless again. Is it any better?

As far as your other hardware is concerned, all the drivers come in the kernel. As someone has already said, Linux is very different from Windows. The main exception is your NVIDIA card. Once you've got (hopefully) stable wireless, open Synaptic again and click on 'reload'. That updates the package metadata. Now close Synaptic and open System > Administration > Hardware Drivers. Is it prompting you for the proprietary nvidia driver? If so, activate it. That will require another reboot.

---

### Post by mahorrocks on 2009-12-19
Thank you COffee Cat I will give it a try and see what happens. Its tough understanding Linux and I do know what you mean by its a hell of a lot different to Windows, a lot less plug and play

Can anyone explain how to install downloads from a zip like Quicktime for instance???:confused:

---

### Post by coffeecat on 2009-12-19
Is that Quicktime for Windows or Quicktime for Mac? They won't work in Linux and I don't know whether you can get the Windows Quicktime working in Wine.

Save yourself some heartache and use native Linux apps. :) Multimedia? Here goes. Once you've got that wireless card working :wink:, open Synaptic and mark ubuntu-restricted-extras for installation. That will give you some multimedia stuff, flash, java and - um - MS core fonts. (If you can whistle the last one, I'll sing it!) Now install VLC, one of the best all-round video players - it will handle .mov files.

Now mosey over to [www.medibuntu.org]("http://www.medibuntu.org") and follow the directions for enabling the repository. Once you've done that, use Synaptic to install libdvdcss2 (for playing encrypted DVDs) and either w32codecs if you're running the 32-bit version of Ubuntu or w64codecs if the 64-bit.

With all those codecs and stuff, the already installed Movie Player (Totem) will handle most video formats as well as DVDs, as will VLC. And if you want even more choice, install mplayer.

What was that you said about Quicktime? :p

---

### Post by mahorrocks on 2009-12-19
Thanx 

So when I download something in a tar file say to have a nice login screen how do I perform installs from those, im Most confused

Just if I download an app for linux I am trying to understand how to install from a zip
eg f-secure-linux-security-7.03.81803.tgz

---

### Post by Cheesemill on 2009-12-19
This should help you get your head round the way things are done in Ubuntu:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by mahorrocks on 2009-12-20
Thanks Guys

You've all been very patient with a newbie like me, and because its open source it is very good and I am enjoying the experience. So much so that the wifey is watching the Ubuntu and getting jealous and wants to use it too

Is it any good on Sony Vaios?

---

### Post by coffeecat on 2009-12-20
> **mahorrocks said:**
> Is it any good on Sony Vaios?

Posting from a Sony Vaio VGN-NS20S running Karmic with **everything** working out of the box. :cool: Well - not the inbuilt dial-up Winmodem, but everything else - wireless, webcam, SD card reader, FN keys, etc, etc.

But that's not to say every Vaio will be as unproblematic. It depends on the hardware. What model is yours, or are you thinking of buying one? If the latter, avoid ATI graphics. And if you get the chance, see if you can run a live CD live before committing to buying. That way you can test the hardware, particularly the wireless.

---

### Post by mahorrocks on 2009-12-20
> **coffeecat said:**
> Posting from a Sony Vaio VGN-NS20S running Karmic with **everything** working out of the box. :cool: 

Its my wifes Laptop, she wants it too. She feels left out. What is Karmic?

---

### Post by coffeecat on 2009-12-20
> **mahorrocks said:**
> Its my wifes Laptop, she wants it too. She feels left out. What is Karmic?

The 'Karmic Koala', the latest (9.10) version of Ubuntu. The version number references the year and month of release, and each release has an alliterative name as well. Hence:

9.04 - released April 2009 - Jaunty Jackalope
9.10 - released October 2009 - Karmic Koala

and for next year:

10.04 - to be released in April 2010 - Lucid Lynx.
The name of 10.10 is, as yet, confined to Mark Shuttleworth's subconscious. :wink: "Mutating Mongoose" perhaps? :p

Post the model number of your wife's Vaio, and I'll google the specs. But you can boot up from the live CD and check everything out without committing to a hard disc install.

---

### Post by mahorrocks on 2009-12-20
Thank you coffee cat

Another Question?

I have been trying to disable the trackpad on my rock laptop but it does not disable completely. Is there any way to disable it?

SONY VAIO MODEL PCG-7D2L

---

### Post by coffeecat on 2009-12-20
> **mahorrocks said:**
> I have been trying to disable the trackpad on my rock laptop but it does not disable completely. Is there any way to disable it?

There are a few options in System > Preferences > Mouse, under the 'Touchpad' tab, but they don't include completely disabling it. That is, if the touchpad tab appears at all. I've seen a few posts from people who don't see the touchpad tab - mostly with Acer laptops. I guess it depends on the make of touchpad.

If you look in Synaptic package manager (an awkwardly confusing name considering many touchpads are 'Synaptics' :?) or in Software Centre, there's a package called 'gpointing-device-settings' which might do the job. I have no experience of it, but I might have a play with it later today.

> **mahorrocks said:**
> SONY VAIO MODEL PCG-7D2L

That seems to be of a similar vintage to my older Vaio VGN-FS215B. Useful google hits are sparse, but [this one](http://novatechgadgets.com/sovace11gb10.html) has some useful information. 512GB RAM will be OK for Ubuntu. You should be OK with the Intel GMA900 graphics. It doesn't say what wireless chipset, but with 'Centrino technology package' that's likely to be Intel - possibly the 2200 chipset. If so, it should 'just work'.

The bits you are likely to find problems with are the dial-up Winmodem and the Sony Memorystick holder. Not that I ever used a Sony memory stick on my old Vaio, and the new Vaio comes with a SD card reader. Also - the Fn keys didn't work in Linux with my old Vaio unless I compiled a special driver. But I think the FS series was particularly problematic in this respect. Sony have used different technologies at different times for their Fn keys, so you may be lucky. But as I said, fire up the live CD in it and try everything out.

Good luck!

---

### Post by 73ckn797 on 2009-12-20
> **coffeecat said:**
> Not that I ever used a Sony memory stick on my old Vaio, and the new Vaio comes with a SD card reader.

See laptop specs in signature. The Sony memory stick works on the Toshiba using a USB adapter but not with the SD adapter.

---

### Post by mahorrocks on 2009-12-20
The Synaptics thing worked a treat it is now fully disabled.... 

I will give it a spin on the wife's see if she likes it but I dont know..

But she seems to like it lol

After all if you want an app you just download it, you dont have to go out and buy it lol

---

### Post by mahorrocks on 2009-12-20
> **coffeecat said:**
> 

If you look in Synaptic package manager (an awkwardly confusing name considering many touchpads are 'Synaptics' :?) or in Software Centre, there's a package called 'gpointing-device-settings' which might do the job. I have no experience of it, but I might have a play with it later today.




I couldnt find that in the menu

However I found gsynaptics. It works sporadically but I think that is because i had gpointing-devices. If I install it surely it would go to the Preferences within system as I cant see g pointing devices anywhere when I install it. However it seems to reenable itself after time

:(

---

### Post by coffeecat on 2009-12-20
> **mahorrocks said:**
> I couldnt find that in the menu

Neither could I. It's in the Universe repository, therefore not a Canonical-supported package. You can see which are - they have the Ubuntu logo by them in Synaptic.

Anyway, you can open it with ALT-F2 which opens the 'run' application' utility. Then type 'gpointing-device-settings' in the field and click on 'run'. But don't worry. I've tried it. You're not missing much. :|

I think I might try gsynaptics. After all, as you've now discovered, it's all free. :)

---

### Post by coffeecat on 2009-12-20
> **coffeecat said:**
> type 'gpointing-device-settings' in the field and click on 'run'. But don't worry. I've tried it. You're not missing much.

Whoops! I take that back. I was trying it an an Acer laptop with a somewhat inferior touchpad. It seems as though it's using a generic mouse driver which is why I can't do much with it. On my Sony Vaio - with a decent Synatics touchpad - gpointing-device-settings appears quite different and looks to be very useful.

A pity that the package maintainers forgot to make sure the package added a menu entry. If you want to do that, here's what to do: right-click anywhere on the main menu, and choose 'Edit Menus'. In the right pane highlight 'Preferences' if that's where you want to put it - you can choose somewhere else if you prefer. Click on 'new item', put 'Gpointing Device Settings' in the Name field, and 'gpointing-device-settings' in the command field. OK that and you have a menu entry.

---

### Post by mahorrocks on 2009-12-20
Just trying to get this flash to work.... Tried installing it from the Software centre but it is not playing.

**Not available for your hardware archetecture** That is for the flash 10 plugin and I can not enable the channel :(

If I do it via the website it fails too

**Could not find package 'adobe-flashplugin**

Thanks so much for your help so far... I am slowly getting to grips with things. Like most things it takes time to get use to

The only problem I have with the synaptics is my mouse keeps re-initialising itself when I turn it off, which is rather worrying on why my settings will not stick :S

---

### Post by coffeecat on 2009-12-20
> **mahorrocks said:**
> 
**Not available for your hardware archetecture**

That is curious because it sounds like a 32-bit/64-bit mismatch type error message. As far as I understand the flash plugin for the 64-bit version is still the 32-bit flash player "wrapped" for 64-bit Firefox. Out of interest, which version of Ubuntu did you install: 64 or 32-bit?

Anyway, have you already installed 'ubuntu-restricted-extras' as I suggested? Because if you did that would have included flash. If so, perhaps the system is getting confused over its error messages.

Close Software Centre and go to System > Administration > Synaptic and look for 'flashplugin-installer'. Is it showing as installed (green)? If not, try marking it for installation and click on 'Apply'. Although if that doesn't work in Software Centre it probably won't work in Synaptic.

---

### Post by mahorrocks on 2009-12-20
Its showing green and I am on 64 Bit Karmic

Yeah I installed the restricted ubuntu extras too

---

### Post by robio376 on 2009-12-20
Did you have a web browser open when installing flash? I ran into that problem before. Reinstall flash from Software Center with all browsers closed and reboot. Worked for me.

---

### Post by coffeecat on 2009-12-20
> **robio376 said:**
> Did you have a web browser open when installing flash? I ran into that problem before. Reinstall flash from Software Center with all browsers closed and reboot. Worked for me.

@mahorrocks, that sounds like a good idea. If the flashplugin-installer is showing green in Synaptic, it means that flash is installed so try simply restarting firefox and going to a flash page. If that doesn't work try the reinstall as above. You can use software centre or Synaptic - it doesn't matter.

---

### Post by mahorrocks on 2009-12-21
I did both and its just hit or miss whether or not it plays.

I dunno why but its playing up, same with the track-pad, I disable it and it seems to re-enable itself even though I have my USB mouse plugged in

---

### Post by coffeecat on 2009-12-21
> **mahorrocks said:**
> I did both and its just hit or miss whether or not it plays.

Flash in 64-bit. I'm afraid it's hit or miss whether the 32-bit flash works at all in 64-bit at the moment. But there is a way if you're happy to use the alpha version of the proper 64-bit version of flash. I'm afraid we're in the hands of Adobe with this. Flash is proprietary and Adobe have been dilatory developing a 64-bit version for Linux.

Have a look here:

[http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/](http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/)

Copying/moving the libflashplayer.so file into /home/myusername/.mozilla/plugins works for me, although I only had occasional problems with the repository version of flash.

There are terminal and GUI methods described there. What they forget to say is that if you've installed the repository version, you need to uninstall it otherwise the two will clash.

For this, follow step 1 in this link:

[http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)

The rest of that link is essentially the same as the first, and has useful pictures. But the first is a bit more up-to-date, and you want to use the download link in the first to get the newer alpha refresh of flash.

---

### Post by mahorrocks on 2009-12-21
Thanks I will have a look into this and let you know how it goes.

Any ideas why my trackpad will not disabled and just re-activate later?

Some programs I would like to start up at the beginning never do like Desktop Drapes. Any ideas?

---

### Post by coffeecat on 2009-12-22
Flash - I'd be interested to hear if that works for you.

Touchpad - sorry, I don't know.

Desktop Drapes - I've never used that. I had to google it to find out what it was. Is that the 'drapes' package? Whatever, I don't know.

---

### Post by mahorrocks on 2009-12-22
Coffee Cat,

Sorry for the late reply. It works but it is sporadic at times, but im sure it will sort itself out as I get more to grips with Linux :D Thanks for all your help and you have a good Xmas 

Mark

---

### Post by coffeecat on 2009-12-23
Happy Christmas, too!

> **mahorrocks said:**
> It works but it is sporadic at times

If you've followed that howto for putting the flash .so file in your ~/.mozilla/plugins folder, make sure you've uninstalled all the repository installed bits of flash.

Also - I came across this in my wanderings around the forum:

[http://ubuntuforums.org/showthread.php?t=1361955](http://ubuntuforums.org/showthread.php?t=1361955)

Have a look at post #2. That's a fix for the repository-installed flash. I have no idea how it is meant to work, but I'm posting it if only for my own benefit if the weather stops me from getting out and about on New Year's day. :p

---

