---
title: "Atheros 5006 242X troubleshooting log It works!!"
date: 2008-06-07
forum: Hardware
---

### Post by moomtaz on 2008-06-07
Linux Atheros installation troubleshooting log

I am starting this log because of the installation problems that I am having with my Atheros card and kubuntu 8.04. I have tried both routes both Madwifi and the ndiswrapper course of action with no success. So this time I have stripped all support files I deleted everything and now I will start from scratch going with the madwifi course of action first. I am using Hamza's how to found [here]("http://hamzakc.wordpress.com/2006/12/11/atheros-wireless-setup-ubuntu/") it is an excellent how-to very easy to follow. I hope there are some people out there that can help me figure out where it is that I am going wrong with this thing. I have a Toshiba P205D-S7454 Satellite. I am trying to make a break from  Windows Vista that came installed with my machine. I am tired of my hard drive spinning and spinning and having a terrible time. Vista is ok but goodness it is a hog stuck in molasses. Linux is much more responsive but the learning curve is a killer but I think if I can figure out the last couple of hardware glitches dealing with this operating system I will be more than happy to use it all the time. The number one thing is the wifi card, after that my ATI Radeon X1200 controller card, then my system webcamera and lastly my volume knob that worked under 7.10. I think if I can resolve these hardware issues then I can go full penguin.

1.The first thing in the How-to is the apt-get build-essential command. I did that already. Done.
2.Then apt-get install subversion I already installed that too.
3.In the how-to he writes that the command is subversion svn checkout [http://svn.madwifi.org/trunk](http://svn.madwifi.org/trunk) madwifi however this is incorrect after you get the subversion program the command is svn checkout [http://svn.madwifi.org/madwifi/trunk](http://svn.madwifi.org/madwifi/trunk) so I did that. Cool. It went better than I thought. Now if I can just turn off my mouse when I type that would be great!!
4.Switched over to directory /lib/modules/2.6.24-18-generic$  however you will need to type in uname -r to get the name of your directory so that yours will work.
5.I did the following already but I will include them here for your benefit.
Delete the net lib files : sudo rm -rf net
Delete the madwifi files : sudo rm -rf madwifi
Delete this folder if it exists : sudo rm -rf madwifi-ng
6.Find the modules currently installed that you need to unload : lsmod | grep ath I deleted these already too, but you should have some if you are just starting out.
7.From this output above issue a rmmod command for all the modules : sudo rmmod modulename
8.Go back to where you downloaded the new subversion drivers and run : sudo make and then sudo make install answer yes to remove the old module. Mine downloaded into home/trunk you can use the find command to find the file *BuildCaps* to find the directory where they went. I think that is the easiest way to do it. That is just a file included in the build.
9.The next thing you do is Load all of the modules you have just unloaded using modprobe. These should be: 
sudo modprobe ath_pci
sudo modprobe ath_rate_sample
sudo modprobe wlan
sudo modprobe ath_hal
10.I tested my configuration after I did this with the lsmod | grep ath command and I get the following
ath_rate_sample        	17152  0
ath_pci               	242752  0
wlan                  	253984  2 ath_rate_sample,ath_pci
ath_hal               	280448  2 ath_rate_sample,ath_pci
11.Check to see if modules have been loaded by typing dmesg and looking at the system log.
12.So I do that and where my wifi card is I get the dreaded message [28247.775172] MadWifi: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
13.At this point my wifi should be working but it isn't because of this stupid message.
14.The first time I tried to start it my wifi switch was off so I turned it on and tried again I did all of the turning the modules on sudo modprobe ath_pci stuff and typed the dmesg thing again and got a ton of errors so I decided to reboot the machine.
15.So I rebooted my machine and then checked the dmesg thing and it didn't show my wireless card at all so I did the sudo modprobe  thing and enabled them all again and this is what I got. 
[  340.210897] ath_hal: 0.9.30.13 (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133)
[  340.283487] wlan: svn r3711
[  340.326021] ath_pci: svn r3711
[  340.326768] ACPI: PCI Interrupt 0000:17:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[  340.326777] PCI: Setting latency timer of device 0000:17:00.0 to 64
[  340.337268] MadWifi: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[  340.337309] ACPI: PCI interrupt for device 0000:17:00.0 disabled
[  345.769853] ath_rate_sample: 1.2 (svn r3711)
16.So it appears that everything is working however there is a conflict with my ACPI that is causing my card not to work. I think that the HAL status 13 has to do with the button thing but I will research it to find out.
17.So that didn't work. I'm at a dead end with the whole ACPI thing. So I try my next option ndiswrapper [as stated is the way to go here]("http://induscreep.blogspot.com/2007/08/linux-on-toshiba-satellite-p205-s6307.html"). I didn't delete all of my Madwifi files and just installed the drivers with ndiswrapper using the ndgtk app. So we will see what happens next after my ATI drivers finish downloading. I went with the 64 bit version of the XP driver net5211.inf. Still no juice!!
18.So I do the ndiswrapper thing via ndisgtk. It installed fine, but then I get this when I type the dmesg thing.
[ 2379.857438] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 2379.875037] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[ 2379.876724] ndiswrapper: driver net5211 (,07/26/2007,5.3.0.67) loaded
[ 2379.877431] PCI: Enabling device 0000:17:00.0 (0000 -> 0002)
[ 2379.877440] ACPI: PCI Interrupt 0000:17:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[ 2379.877485] ndiswrapper (ZwClose:2227): closing handle 0x0 not implemented
[ 2379.877666] PCI: Setting latency timer of device 0000:17:00.0 to 64
[ 2379.878494] ndiswrapper (NdisWriteErrorLogEntry:191): log: C0001389, count: 4, return_address: ffffffff882a45de
[ 2379.878499] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x74cf8c00
[ 2379.878501] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x28
[ 2379.878503] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x9e6000
[ 2379.878505] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x9e6000
[ 2379.878598] ndiswrapper (mp_init:216): couldn't initialize device: C000009A
[ 2379.878604] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[ 2379.878617] ndiswrapper (mp_halt:259): device ffff810073b4b700 is not initialized - not halting
[ 2379.878620] ndiswrapper: device eth%d removed
[ 2379.878633] ACPI: PCI interrupt for device 0000:17:00.0 disabled
[ 2379.878650] ndiswrapper: probe of 0000:17:00.0 failed with error -22
[ 2379.878701] usbcore: registered new interface driver ndiswrapper
[ 2399.776706] APIC error on CPU0: 40(40)
[ 2399.771034] APIC error on CPU1: 40(40)
19.So I will reboot again hoping that this would fix the problem. If it hangs because both Madwifi and the ndiswrapper drivers are installed then I will have to go in and delete the Madwifi stuff and try to reboot again.
20.I found that my Web Cam works. So that is one less thing. Also I have full resolution on my video card with the current set up 1440 X 900 @ 60hz so I suppose I can live without all of the ATI bells and whistles. I don't play games so I don't really need all of the super functions of the card. Just to be able to view my pictures.
21.Lo hicimos! I rebooted and my wifi came up fine Oh yeah son I hope this little How-to can help ease the frustration of those trying to get their wifi to work. 4 days of frustration, endless reboots, tons of web pages now this solution. Try it you will like it. Now on to bigger and brighter things I'm on my way to going full penquin. YAY!!

Volume control knob would be nice and also the ability to adjust my screens brightness would be great too to save battery life, but I have wifi and that is all that I really need.

[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

### Post by moomtaz on 2008-06-07
I'm sorry that all of my formatting was dropped it would read better with that formatting in place. My bad so I will give you a little review of my system. 

Processor - AMD Turion 64 x2 Dual-Core  --Works just fine
Memory 2 Gigs                           --Works
Hard Disk 160 Gigs                      --Works
Fixed Optical Drive DVD +/-R double layer with label flash --Works haven't burned anything though.
Display 17" full resolution of 1440 x 900 --Works Haven't tested the 3d rendering.
Graphics ATI Radeon Xpress X1200M  haven't fully tested yet.
Sound-
Built in speakers --Work
Sound Volume control -- Worked under 7.10 not under 8.04 as of yet.
Keyboard works I want to find a way to enable the windows key menu button works though.
Mouse works
Media buttons work.
WebCam works haven't checked the microphone.
Modem come on now haven't checked it.
Ethernet Works great.
Wireless Atheros ar5006 Works with ndiswrapper and xp 64-bit driver
Express card haven't tested
5-in-1 media card works
Video
haven't checked the RGB or S-Video output
Haven't checked the Microphone jack
Headphone Jack works.

So I will find a place on the net for this and post it somewhere, but I think that this is one of the best places that I can put it. :guitar:

I hope peeps can use this info. Peace out.

---

### Post by moomtaz on 2008-06-07
UUUUUUGGGGGGGGHHHHHHH!!!!!
I shutdown my machine or I had a friend do it because I haven't researched the .deny all all thing and I had left it on so I am sure that he just pressed the power button but anyway it doesn't work now. Well that isn't entirely true it sees the card and it starts to connect but then it doesn't log on at all. I know I know the password to my router so I don't know what the deal is.:confused:

---

### Post by moomtaz on 2008-06-08
Well I think that it was something in my KDEWallet that threw everything for a loop. I deleted those files and now it works fine. Don't know, but I'm thinking that is it.

---

