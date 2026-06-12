---
title: "Toshiba Satellite R830-145 wired and wireless connections"
date: 2011-08-08
forum: Hardware
---

### Post by airper on 2011-08-08
Hi folks,

Neither Wired and Wireless connections working.

I've just got a new Toshiba Satellite R830-145 laptop and I'm having some difficulties getting any Internet connections working so I can install 11.04 properly

Both the wired and wireless cards won't establish a connection from the iso I downloaded, 32bit version. 

The wireless card is an Atheros AR9285, and registers okay as wlan0 using the ATH9K driver although lsmod lists these modules/drivers which are loaded by default

ath9k
ath9k_common
ath9k_hw
ath

I'm not sure if these are duplicate drivers which need to be blacklisted or are dependences. 

iwconfig looks like driver(s) is installed okay, but it cannot associate with the router.

if I ping the loopback on 127.0.0.1 it all seems to respond okay so the card and the driver(s) seem to be working properly. 

Just clicking on the wireless connection in network manager and it tries to connect, it searches, but does not actually establish the link with the router, although it identifies it correctly.

I searched here and worked my way through the Wiki troubleshooting guide on wireless, but I've not yet succeeded in establishing a connection.


So to wired

The laptop has a new Intel 82579v Ethernet controller. I know this is new and I have found the driver for it e1000e-1 from sourceforge which is a tar file.

Now this is a very basic question and I've search all over the place this evening for an answer obviously searching on the wrong thing, but how do I install a driver from a tar file?

I think all I have to do is untar the file (I assume just clicking on it will do that?)

Then is is just open a terminal, cd into the directory created above and then

sudo make
sudo install

Sounds rather too simple, but i didn't seem to be able to find a guide on this anywhere and I was not sure if a driver needed different treatment to a normal file.

Any pointers or hints on where to look, gratefully received

Thanks

---

### Post by airper on 2011-08-09
Can anyone offer any advice with this, getting rather desperate to get any Internet connection working in Ubuntu. 

I know there are Linux drivers out there for these cards as the Fedora forums are saying Fedora 15 already has support, particularly for the e1000e-1, but I prefer Ubuntu to Fedora if possible.

---

### Post by svast on 2011-08-09
everything is in the provided README file:
```
1. Move the base driver tar file to the directory of your choice.  For
   example, use /home/username/e1000e or /usr/local/src/e1000e.

2. Untar/unzip archive:

     tar zxf e1000e-x.x.x.tar.gz

3. Change to the driver src directory:

     cd e1000e-x.x.x/src/

4. Compile the driver module:

     # make install

   The binary will be installed as:

     /lib/modules/<KERNEL VERSION>/kernel/drivers/net/e1000e/e1000e.[k]o

   The install locations listed above are the default locations.  They
   might not be correct for certain Linux distributions. 

5. Load the module using either the insmod or modprobe command:

     modprobe e1000e

     insmod e1000e

   Note that for 2.6 kernels the insmod command can be used if the full
   path to the driver module is specified.  For example:

     insmod /lib/modules/<KERNEL VERSION>/kernel/drivers/net/e1000e/e1000e.ko

   With 2.6 based kernels also make sure that older e1000e drivers are 
   removed from the kernel, before loading the new module:

     rmmod e1000e; modprobe e1000e

6. Assign an IP address to the interface by entering the following, where
   x is the interface number:

     ifconfig ethx <IP_address>

7. Verify that the interface works.  Enter the following, where <IP_address>
   is the IP address for another machine on the same subnet as the
   interface that is being tested:

     ping  <IP_address>

```

---

### Post by svast on 2011-08-09
By the way, I also have installed Ubuntu 11.04 on a Satellite R830 (-136 edition), and the network was working out-of-the-box as far as I can remember...

---

### Post by airper on 2011-08-09
Thanks svast,

Will try this later today. I did read up here about the R700 and noted the Internet connections worked out of the box, so it was a good part of the decision to go for the R830 almost the same machine in theory.

I also got the store to let me boot up the demo machine into Ubuntu. Network Manager, clearly recognised the wireless card as it listed all the available networks in the store, the only thing I couldn't do was connect to one of them.

So it is a bit of a pain that the final bit or the wired connection didn't want to play.

Buying a new machine (laptop) is a bit of a challenge if you want to use Ubuntu at the moment, I've had two new machines recently this one and an Acer, both have had basic problems with Internet connections.

Will try and get this working as above and many thanks for the guidance.

---

### Post by svast on 2011-08-09
I agree with you on this: it is really a challenge to choose the right laptop hardware in order to use Ubuntu.

Please let me know if you finally make it work.
Is it working with the original Win$ OS? 
What are the detailed specs (cpu, ram, hdd...) of your R830-145 (did not find it)? 

Best regards

---

### Post by airper on 2011-08-09
Hi svast,

The Toshiba Satellite R830 is supposed to be the same as the R700, but with Win Home as opposed to Win Pro. 

And yep in Win OS everything is working okay. I normally removed Win and just install Ubuntu, it's taken me a while but I really like Linux and can now manage with it as my only operating system.

On this machine I was going to try a dual boot installation as it has a 640Gb hard drive.

The spec of the R830 is

Intel 5i processor
Intel HM65 chipset
6Gb ram (so on install I need the Internet connection to make sure pae is loaded up)
640 Gb harddrive
Atheros AR9285 wireless card
 Intel 82579v Ethernet controller

If I can get the basics working I'll start a thread like they have for the R700 so everyone knows about the Ubuntu install and driver setup processes, but I thought I ought to get at least the Internet connections sorted out first. 

Video seems fine, sound is fine, not sure yet about hot keys and stuff or sleep modes etc.

It's going to be fun no doubt. I noticed for the R700 series machines people are installing the latest 3.0 series kernels to overcome the lockup and cpu fan over speeding problems when on batts. I'm assuming I might have to do that for the R830 as well.

---

### Post by airper on 2011-08-09
> **svast said:**
> everything is in the provided README file:
```
1. Move the base driver tar file to the directory of your choice.  For
   example, use /home/username/e1000e or /usr/local/src/e1000e.



6. Assign an IP address to the interface by entering the following, where
   x is the interface number:

     ifconfig ethx <IP_address>



```

Sorry where you say assign an IP address to the interface, is that a standard address, or can I use anything here and does it matter if the router is set up for DHCP addressing?

Thanks

---

### Post by svast on 2011-08-09
> **airper said:**
> Hi svast,

The Toshiba Satellite R830 is supposed to be the same as the R700, but with Win Home as opposed to Win Pro. 

And yep in Win OS everything is working okay. I normally removed Win and just install Ubuntu, it's taken me a while but I really like Linux and can now manage with it as my only operating system.

On this machine I was going to try a dual boot installation as it has a 640Gb hard drive.

The spec of the R830 is

Intel 5i processor
Intel HM65 chipset
6Gb ram (so on install I need the Internet connection to make sure pae is loaded up)
640 Gb harddrive
Atheros AR9285 wireless card
 Intel 82579v Ethernet controller

If I can get the basics working I'll start a thread like they have for the R700 so everyone knows about the Ubuntu install and driver setup processes, but I thought I ought to get at least the Internet connections sorted out first. 

Video seems fine, sound is fine, not sure yet about hot keys and stuff or sleep modes etc.

It's going to be fun no doubt. I noticed for the R700 series machines people are installing the latest 3.0 series kernels to overcome the lockup and cpu fan over speeding problems when on batts. I'm assuming I might have to do that for the R830 as well.

6GB RAM: I suggest you to give a try with Ubuntu 64bit, so you won't need PAE trick.

In reality there is a true difference between R700 and R830 serie in the hardware side: R700 is core i5 1rst generation (like i5-480M), R830 is holding sandy-bridge platform with new core i5 CPUs (like i5-2510M).
Also, the graphics is different because the intel GPU is included in the CPU on the R830, requiring new Intel drivers.
This has been leading to several problems in making Linux working properly on these new platform, especially when you want multiple monitors.

My own R830 motherboard just broke, so I returned it to be repaired.
I will post/participate with my tips and tricks when I receive my laptop.

---

### Post by svast on 2011-08-09
> **airper said:**
> Sorry where you say assign an IP address to the interface, is that a standard address, or can I use anything here and does it matter if the router is set up for DHCP addressing?

Thanks

This is not necessary if you already have a DHCP server on your LAN.
You may just try :
```
sudo /etc/init.d/networking restart
sudo ifconfig eth0 up
```
That should be enough

---

### Post by airper on 2011-08-09
Hi svast,

That's great, I do quite like the thread the R700 guys have created to help people config and sort out their machines, I was planning on doing the same thing here for the R830(s) 

I'll try using a G3 Dongle to get an Internet connection this evening and install the 64 bit version of 11.04, but it might take a little while to get all the updates downloaded using 3G. I'll dual boot it for now, just in case there are BIOS updates to do later, I know the R700 needed that.

I might also try installing the new 3.0 Kernel, which will give a new boot option in Grub if the old one is left in place, I understand more Internet (wired and wireless) drivers are included in the new 3.0 Kernel builds and they apparently work okay with 11.04 and the R700 and hopefully R830 machines.

My plan is to turn this thread into a how-to for the R830 series laptops, basically they are very good machines I think, so all help gratefully received.

Okay going to try and install 11.04 64bit, wish me luck!!!

---

### Post by svast on 2011-08-09
Good luck then, I will follow this thread and post any tip I can get

---

### Post by airper on 2011-08-10
Okay, 11.04 64 bit version of Ubuntu appears to have installed on my Toshiba Satellite R830-145, but not without a few problems. 

With no wireless or wired Internet connection, I used a 3G dongle to get an Internet connection for the install, this was fine albeit it took nearly three hours.

So far I've found a 3G dongle works with every install I've tried on any computer, laptop or otherwise. The drivers for these seem very solid and are a good last resort.

The install proceeded up to the point of cleaning up temporary files, when the install crashed, then I got Xwindows errors, which were in a loop, because the dialog box just kept reappearing. Ended up just having to hit the off button shutting the thing down. 

Anyway tried a normal start, grub loaded okay and yes, it was installed and seems okay. Unity seems functional, video and sound appear to be working fine.

Got Internet back up using the 3G dongle again and ran update manager, there are more than 200 updates to download and install, including Xwindows and some Kernel headers. Than is going to take some time on a 3G card so a job for this evening.

I suspect I've got quite a lot of debris left over from the install as it didn't complete properly, I'm hoping Janitor will clean it up a bit.

Then I'm going to try installing an updated Kernel 3.01 which reading here will give me another boot option in Grub. I'm hoping that might sort out some of the wired driver issues at least with the Intel 82579v Ethernet controller, if not I'll try installing the new driver e1000e as discussed here previously.

Then it's wireless and I think the madwifi drivers might be the way to go here with the Atheros AR9285 wireless card, but that is probably for tomorrow.

---

### Post by airper on 2011-08-11
So, a little progress since yesterday, but still no Internet.

I've got 11.04 64bit installed okay, the basic systems are running and seem stable. 

[SIZE=1]I've successfully managed to install an updated kernel 3.0.1-030001-generic and that too is running fine, but still no Internet, wired or wireless.[/SIZE]

I've run through the process in Post 3, to install the latest driver for the  Intel 82579v Ethernet controller, which is e1000e version 1.4.4 but I don't seem to be able to make it permanent, once I reboot it reverts to the older version of the driver.

[SIZE=1]Once I've done the update

  	 	 	 	[/SIZE] 	 	  [FONT=Liberation Sans, sans-serif][SIZE=1]**sudo lshw -C network** gives[/SIZE][/FONT]
[SIZE=1] [/SIZE][SIZE=1]
[/SIZE] 
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]*-network               [/SIZE][/FONT] 
[SIZE=1] [/SIZE]       [FONT=Liberation Sans, sans-serif][SIZE=1]description: Ethernet interface [/SIZE][/FONT] 
[SIZE=1] [/SIZE]       [FONT=Liberation Sans, sans-serif][SIZE=1]product: 82579V Gigabit Network Connection [/SIZE][/FONT] 
[SIZE=1] [/SIZE]       [FONT=Liberation Sans, sans-serif][SIZE=1]vendor: Intel Corporation [/SIZE][/FONT] 
[SIZE=1] [/SIZE]       [FONT=Liberation Sans, sans-serif][SIZE=1]physical id: 19 [/SIZE][/FONT] 
[SIZE=1] [/SIZE]       [FONT=Liberation Sans, sans-serif][SIZE=1]bus info: pci@0000:00:19.0 [/SIZE][/FONT] 
[SIZE=1] [/SIZE]       [FONT=Liberation Sans, sans-serif][SIZE=1]logical name: eth0 [/SIZE][/FONT] 
[SIZE=1] [/SIZE]       [FONT=Liberation Sans, sans-serif][SIZE=1]version: 04 [/SIZE][/FONT] 
[SIZE=1] [/SIZE]       [FONT=Liberation Sans, sans-serif][SIZE=1]serial: e8:9d:87:eb:5f:28 [/SIZE][/FONT] 
[SIZE=1] [/SIZE]       [FONT=Liberation Sans, sans-serif][SIZE=1]capacity: 1Gbit/s [/SIZE][/FONT] 
[SIZE=1] [/SIZE]       [FONT=Liberation Sans, sans-serif][SIZE=1]width: 32 bits [/SIZE][/FONT] 
[SIZE=1] [/SIZE]       [FONT=Liberation Sans, sans-serif][SIZE=1]clock: 33MHz [/SIZE][/FONT] 
[SIZE=1] [/SIZE]       [FONT=Liberation Sans, sans-serif][SIZE=1]capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation [/SIZE][/FONT] 
[SIZE=1] [/SIZE]       [FONT=Liberation Sans, sans-serif][SIZE=1]configuration: autonegotiation=on broadcast=yes **driver=e1000e driverversion=1.4.4-NAPI** firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair [/SIZE][/FONT] 
[SIZE=1] [/SIZE]       [FONT=Liberation Sans, sans-serif][SIZE=1]resources: irq:46 memory:c4800000-c481ffff memory:c482a000-c482afff ioport:3060(size=32) 
[/SIZE][/FONT]


[FONT=Liberation Sans, sans-serif][SIZE=1]But after a reboot it reverts to 
[/SIZE][/FONT]


   	 	 	 	 	 	  [FONT=Liberation Sans, sans-serif][SIZE=1]*-network                [/SIZE][/FONT]
[SIZE=1] [/SIZE]       [FONT=Liberation Sans, sans-serif][SIZE=1]description: Ethernet interface [/SIZE][/FONT]
[SIZE=1] [/SIZE]       [FONT=Liberation Sans, sans-serif][SIZE=1]product: 82579V Gigabit Network Connection [/SIZE][/FONT]
[SIZE=1] [/SIZE]       [FONT=Liberation Sans, sans-serif][SIZE=1]vendor: Intel Corporation [/SIZE][/FONT]
[SIZE=1] [/SIZE]       [FONT=Liberation Sans, sans-serif][SIZE=1]physical id: 19 [/SIZE][/FONT]
[SIZE=1] [/SIZE]       [FONT=Liberation Sans, sans-serif][SIZE=1]bus info: pci@0000:00:19.0 [/SIZE][/FONT]
[SIZE=1] [/SIZE]       [FONT=Liberation Sans, sans-serif][SIZE=1]logical name: eth0 [/SIZE][/FONT]
[SIZE=1] [/SIZE]       [FONT=Liberation Sans, sans-serif][SIZE=1]version: 04 [/SIZE][/FONT]
[SIZE=1] [/SIZE]       [FONT=Liberation Sans, sans-serif][SIZE=1]serial: e8:9d:87:eb:5f:28 [/SIZE][/FONT]
[SIZE=1] [/SIZE]       [FONT=Liberation Sans, sans-serif][SIZE=1]capacity: 1Gbit/s [/SIZE][/FONT]
[SIZE=1] [/SIZE]       [FONT=Liberation Sans, sans-serif][SIZE=1]width: 32 bits [/SIZE][/FONT]
[SIZE=1] [/SIZE]       [FONT=Liberation Sans, sans-serif][SIZE=1]clock: 33MHz [/SIZE][/FONT]
[SIZE=1] [/SIZE]       [FONT=Liberation Sans, sans-serif][SIZE=1]capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation [/SIZE][/FONT]
[SIZE=1] [/SIZE]       [FONT=Liberation Sans, sans-serif][SIZE=1]configuration: autonegotiation=on broadcast=yes** driver=e1000e driverversion=1.3.10-k2** firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair [/SIZE][/FONT]
[SIZE=1] [/SIZE]       [FONT=Liberation Sans, sans-serif][SIZE=1]resources: irq:40 memory:c4800000-c481ffff memory:c482a000-c482afff ioport:3060(size=32) [/SIZE][/FONT]
[SIZE=1] [/SIZE] 
[SIZE=1] [/SIZE]
Can anyone tell me how to make this driver update stick after a reboot?

Thanks

---

### Post by airper on 2011-08-11
[SIZE=1]This is the output of lsmod, as you can see, e1000e is moved to the head of the list and is marked 'permanent'

However, it reverts post a reboot.

  	 	 	 	[/SIZE] 	 	  **[FONT=Liberation Sans, sans-serif][SIZE=1]lsmod – pre update and post a reboot[/SIZE][/FONT]**
**[SIZE=1] [/SIZE]**[SIZE=1]
[/SIZE]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]lsmod [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]Module                  		Size  	Used by [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]ppp_deflate            		12950  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]zlib_deflate           		27274  1 ppp_deflate [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]bsd_comp               		12981  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]ppp_async              		17579  1  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]crc_ccitt              		12667  1 ppp_async [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]option                 		25516  2  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]usb_wwan               		20594  1 option [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]usbserial              		43106  7 option,usb_wwan [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]usb_storage            		54051  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]uas                    		18136  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]cryptd                 		20647  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]aes_x86_64             		17208  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]aes_generic            		34183  1 aes_x86_64 [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]binfmt_misc            		17646  1  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]bnep                   		18517  2  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]btusb                  		18712  1  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]bluetooth             		165324  10 bnep,btusb [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]parport_pc             		37530  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]dm_crypt               		23725  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]ppdev                  		17141  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]snd_hda_codec_hdmi     	33027  1  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]snd_hda_codec_realtek   	332834  1  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]snd_hda_intel          		34236  2  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]snd_hda_codec         		106725  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]snd_hwdep              		13782  1 snd_hda_codec [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]snd_pcm                		98306  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]snd_seq_midi           		13370  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]snd_rawmidi            		30488  1 snd_seq_midi [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]snd_seq_midi_event     		14899  1 snd_seq_midi [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]snd_seq                		62088  2 snd_seq_midi,snd_seq_midi_event [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]arc4                   		12529  2  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]snd_timer              		30240  2 snd_pcm,snd_seq [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]snd_seq_device         		14528  3 snd_seq_midi,snd_rawmidi,snd_seq [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]ath9k                 		128744  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]uvcvideo               		69124  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]mac80211              		310164  1 ath9k [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]ath9k_common           		13819  1 ath9k [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]ath9k_hw              		315929  2 ath9k,ath9k_common [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]videodev               		92905  1 uvcvideo [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]snd                    		68651  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]soundcore              		12680  1 snd [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]lp                     			17868  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]parport                		42788  3 parport_pc,ppdev,lp [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]mei                    		42004  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]v4l2_compat_ioctl32    		17341  1 videodev [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]psmouse                		70193  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]serio_raw              		13294  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]ath                    			24428  2 ath9k,ath9k_hw [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]cfg80211              		196651  3 ath9k,mac80211,ath [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]snd_page_alloc         		18572  2 snd_hda_intel,snd_pcm [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]toshiba_bluetooth      		12807  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]toshiba_acpi           		18577  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]joydev                 		18043  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]sparse_keymap          		13995  1 toshiba_acpi [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]usbhid                 		48081  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]hid                   			100109  1 usbhid [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]ahci                   		30380  2  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]libahci                		31326  1 ahci [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]i915                  			565970  3  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]xhci_hcd               		88842  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]sdhci_pci              		18112  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]sdhci                  		32450  1 sdhci_pci [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]drm_kms_helper         		43171  1 i915 [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]drm                   			238079  4 i915,drm_kms_helper [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]i2c_algo_bit           		13436  1 i915 [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]video                  		20027  1 i915 [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]e1000e                		161918  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][SIZE=1]
[/SIZE]
[SIZE=1] [/SIZE][SIZE=1]
[/SIZE]
[SIZE=1] [/SIZE]**[FONT=Liberation Sans, sans-serif][SIZE=1]lsmod – Post update and pre a reboot[/SIZE][/FONT]**
**[SIZE=1] [/SIZE]**[SIZE=1]
[/SIZE]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]lsmod [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]Module                  		Size  Used by [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]e1000e                		158034  3707880987 [permanent] [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]ppp_deflate            		12950  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]zlib_deflate           		27274  1 ppp_deflate [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]bsd_comp               		12981  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]ppp_async              		17579  1  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]crc_ccitt              		12667  1 ppp_async [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]option                 		25516  2  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]usb_wwan               		20594  1 option [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]usbserial              		43106  7 option,usb_wwan [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]usb_storage            		54051  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]uas                    		18136  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]cryptd                 		20647  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]aes_x86_64             		17208  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]aes_generic            		34183  1 aes_x86_64 [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]binfmt_misc            		17646  1  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]bnep                   		18517  2  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]btusb                  		18712  1  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]bluetooth             		165324  10 bnep,btusb [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]parport_pc             		37530  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]dm_crypt               		23725  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]ppdev                  		17141  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]snd_hda_codec_hdmi     	33027  1  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]snd_hda_codec_realtek   	332834  1  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]snd_hda_intel          		34236  2  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]snd_hda_codec         		106725  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]snd_hwdep              		13782  1 snd_hda_codec [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]snd_pcm                		98306  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]snd_seq_midi           		13370  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]snd_rawmidi            		30488  1 snd_seq_midi [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]snd_seq_midi_event     		14899  1 snd_seq_midi [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]snd_seq                		62088  2 snd_seq_midi,snd_seq_midi_event [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]arc4                   		12529  2  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]snd_timer              		30240  2 snd_pcm,snd_seq [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]snd_seq_device         		14528  3 snd_seq_midi,snd_rawmidi,snd_seq [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]ath9k                 		128744  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]uvcvideo               		69124  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]mac80211              		310164  1 ath9k [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]ath9k_common           		13819  1 ath9k [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]ath9k_hw              		315929  2 ath9k,ath9k_common [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]videodev               		92905  1 uvcvideo [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]snd                    		68651  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]soundcore              		12680  1 snd [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]lp                     			17868  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]parport                		42788  3 parport_pc,ppdev,lp [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]mei                    		42004  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]v4l2_compat_ioctl32    		17341  1 videodev [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]psmouse                		70193  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]serio_raw              		13294  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]ath                    			24428  2 ath9k,ath9k_hw [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]cfg80211              		196651  3 ath9k,mac80211,ath [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]snd_page_alloc         		18572  2 snd_hda_intel,snd_pcm [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]toshiba_bluetooth      		12807  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]toshiba_acpi           		18577  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]joydev                 		18043  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]sparse_keymap          		13995  1 toshiba_acpi [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]usbhid                 		48081  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]hid                   			100109  1 usbhid [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]ahci                   		30380  2  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]libahci                		31326  1 ahci [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]i915                  			565970  3  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]xhci_hcd               		88842  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]sdhci_pci              		18112  0  [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]sdhci                 			32450  1 sdhci_pci [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]drm_kms_helper         		43171  1 i915 [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]drm                   			238079  4 i915,drm_kms_helper [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]i2c_algo_bit           		13436  1 i915 [/SIZE][/FONT]
[SIZE=1] [/SIZE][FONT=Liberation Sans, sans-serif][SIZE=1]video                  		20027  1 i915 [/SIZE][/FONT]
[SIZE=1] [/SIZE]

Also is there any clue here as to why I can't get wireless up. I've got networking and wireless up in Network Manager and it is listing the available wireless connections properly. If I click on one, it tries to connect, but it looks like it fails to authenticate the link using WPA2 

Thanks for any pointers here, I'm finding this a bit of a challenge :(

---

### Post by airper on 2011-08-12
[SIZE=1]Okay back to this little problem this morning.

I can change the driver  e1000e shipped with[/SIZE] [FONT=Liberation Sans, sans-serif][SIZE=1]the Kernel 3.0.1-030001-generic[/SIZE][/FONT][SIZE=1] which is:[/SIZE] [FONT=Liberation Sans, sans-serif][SIZE=1]driver=e1000e driverversion=1.3.10-k2 
[/SIZE][/FONT][FONT=Liberation Sans, sans-serif][SIZE=1]to [/SIZE][/FONT][FONT=Liberation Sans, sans-serif][SIZE=1]driver=e1000e driverversion=1.4.4-NAPI[/SIZE][/FONT]

[FONT=Liberation Sans, sans-serif][SIZE=1]and this is reported by lshw -C network, see above, but it doesn't stick after a reboot and even if I try and establish a connection without a reboot I get nothing. [/SIZE][/FONT][FONT=Liberation Sans, sans-serif][SIZE=1]I've posted the output from lsmod above, before and after the change.[/SIZE][/FONT]

[FONT=Liberation Sans, sans-serif][SIZE=1]The only thing I was having a problem with in the process in post 4 is this [/SIZE][/FONT][SIZE=1]

> 
        
6. Assign an IP address to the interface by entering the following, where
   x is the interface number:

[/SIZE]>  [SIZE=1]      ifconfig ethx <IP_address>
[/SIZE][SIZE=1][FONT=Liberation Sans, sans-serif]
[/FONT][/SIZE]
[SIZE=1] 

I don't know what[/SIZE] IP address to use here, or where to get it from but it was susgested to try thiis, given my router uses DHCP

> **svast said:**
> This is not necessary if you already have a DHCP server on your LAN.
You may just try :
```
sudo networking restart
sudo ifconfig eth0 up
```That should be enough

But in my terminal typing **sudo networking restart **produces a command not recognised response[B]. 

[/B]I am getting a wired connection specified in Network Manager called **Auto Ethernet **which tries to connect to the router, but just times out [B].

[/B]Stuck now as to what to try next???

---

### Post by svast on 2011-08-12
@airper: sorry, I meant :
```
/etc/init.d/networking restart
```
Also, what's the terminal giving when typing
```
ifconfig
```
I am curious to see what network interfaces are showing up

---

### Post by airper on 2011-08-12
Good Morning svast, nice to hear from you again, not to worry about the little code thing I can try it again, but I'm out today, so can't easily test either wired or wireless connections. I'm on 3G at the moment. 

That said hopefully I can still make some progress with this and test this evening.

ifconfig produces this

```

ifconfig
eth0      Link encap:Ethernet  HWaddr e8:9d:87:eb:5f:28  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:c4800000-c4820000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:188.29.201.30  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:317 errors:0 dropped:0 overruns:0 frame:0
          TX packets:299 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:322816 (322.8 KB)  TX bytes:33093 (33.0 KB)

wlan0     Link encap:Ethernet  HWaddr d0:df:9a:22:c4:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by airper on 2011-08-12
[FONT=Liberation Sans, sans-serif][SIZE=2]The wireless connection looks to be even closer to a solution. I am getting all the wireless networks listed in Network Manger and on power up it gives the little dialogue box 'wireless networks available'

But trying to click on mine, which is WPA2 just times out.

There was a new driver shipped with kernel I'm using 3.0.1-030001-generic, which lshw -C networks lists like this

[/SIZE][/FONT]```

 [FONT=Liberation Sans, sans-serif][SIZE=2]*-network [/SIZE][/FONT] 
 [FONT=Liberation Sans, sans-serif][SIZE=2]description: Wireless interface [/SIZE][/FONT] 
 [FONT=Liberation Sans, sans-serif][SIZE=2]product: AR9285 Wireless Network Adapter (PCI-Express) [/SIZE][/FONT] 
 [FONT=Liberation Sans, sans-serif][SIZE=2]vendor: Atheros Communications Inc. [/SIZE][/FONT] 
 [FONT=Liberation Sans, sans-serif][SIZE=2]physical id: 0 [/SIZE][/FONT] 
 [FONT=Liberation Sans, sans-serif][SIZE=2]bus info: pci@0000:04:00.0 [/SIZE][/FONT] 
 [FONT=Liberation Sans, sans-serif][SIZE=2]logical name: wlan0 [/SIZE][/FONT] 
 [FONT=Liberation Sans, sans-serif][SIZE=2]version: 01 [/SIZE][/FONT] 
 [FONT=Liberation Sans, sans-serif][SIZE=2]serial: d0:df:9a:22:c4:06 [/SIZE][/FONT] 
 [FONT=Liberation Sans, sans-serif][SIZE=2]width: 64 bits [/SIZE][/FONT] 
 [FONT=Liberation Sans, sans-serif][SIZE=2]clock: 33MHz [/SIZE][/FONT] 
 [FONT=Liberation Sans, sans-serif][SIZE=2]capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless [/SIZE][/FONT] 
 [FONT=Liberation Sans, sans-serif][SIZE=2]configuration: broadcast=yes driver=ath9k driverversion=3.0.1-030001-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn [/SIZE][/FONT] 
 [FONT=Liberation Sans, sans-serif][SIZE=2]resources: irq:18 memory:c2600000-c260ffff [/SIZE][/FONT] 
 
```[FONT=Liberation Sans, sans-serif][SIZE=2]

But there are a lot of entires in lsmod for the ath9k driver, I'm not sure if they are all valid or there is a clash, like the acer-wmi driver causes on this wireless card.

Is there anything I can try, it seems tantalizingly close to working?
[/SIZE][/FONT]

---

### Post by svast on 2011-08-12
> **airper said:**
> Good Morning svast, nice to hear from you again, not to worry about the little code thing I can try it again, but I'm out today, so can't easily test either wired or wireless connections. I'm on 3G at the moment. 

That said hopefully I can still make some progress with this and test this evening.

ifconfig produces this

```

ifconfig
eth0      Link encap:Ethernet  HWaddr e8:9d:87:eb:5f:28  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:c4800000-c4820000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:188.29.201.30  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:317 errors:0 dropped:0 overruns:0 frame:0
          TX packets:299 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:322816 (322.8 KB)  TX bytes:33093 (33.0 KB)

wlan0     Link encap:Ethernet  HWaddr d0:df:9a:22:c4:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
Hi airper,
if you're not familiar with this:
[LIST]
[*]eth0 is your wired link
[*]lo is the local interface for internal use
[*]ppp0 is your 3G link, currently having IP address
[*]wlan0 is your wireless link
[/LIST]
now the point is to give eth0 and/or wlan0 an IP address, which is normally done automatically.

I am used to have them working out of the box, so I really don't know why it does not work with you.
With the laptop wired to the router, to obtain a fresh IP address from DHCP server (located on your router):
```
sudo dhclient
```
But if it does not work (please let us know what kind of message is displayed), you can try
```
sudo ifdown eth0
sudo ifup eth0
```
and check if you get an IP address with the "ifconfig" command. If not, retry the "sudo dhclient" and check again?

kind regards

---

### Post by airper on 2011-08-12
svast I think you might have solved it.

I tried rerunning the code in post 3 and 4 again to upload the new e1000e driver, but with you new code to complete it

I've got a wired line here, but it is secure so I can't actually use it, nevertheless I plugged it in and yes, it seems to have connected, I got the two arrows in Network Manager system tray and Auto Ethernet was highlighted and had a disconnect line.

I've run the suggested terminal queries and here's the output, eth0 seems to have an address

```

wayne@wayne-SATELLITE-R830:~$ sudo dhclient
[sudo] password for wayne: 
wayne@wayne-SATELLITE-R830:~$ sudo ifdown eth0
Ignoring unknown interface eth0=eth0.
wayne@wayne-SATELLITE-R830:~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
wayne@wayne-SATELLITE-R830:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr e8:9d:87:eb:5f:28  
          inet addr:10.246.53.59  Bcast:10.246.53.255  Mask:255.255.255.0
          inet6 addr: fe80::ea9d:87ff:feeb:5f28/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1193 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:82721 (82.7 KB)  TX bytes:20584 (20.5 KB)
          Interrupt:20 Memory:c4800000-c4820000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:188.29.201.30  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4942 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4652 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:5057354 (5.0 MB)  TX bytes:722167 (722.1 KB)

wlan0     Link encap:Ethernet  HWaddr d0:df:9a:22:c4:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wayne@wayne-SATELLITE-R830:~$ 

```Now I don't know yet if the driver change will stick as I haven't rebooted yet, but the connection at least looks promising. I won't be able to finally test it until this evening but I'm hopeful.

Should I reboot now and see if the driver change holds?

---

### Post by airper on 2011-08-12
So went for the reboot and the e1000e driver dropped back to the previous revision here's the output of lshw -C network post the reboot.

```

*-network               
       description: Ethernet interface
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: e8:9d:87:eb:5f:28
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:40 memory:c4800000-c481ffff memory:c482a000-c482afff ioport:3060(size=32)

```But even with this revision of driver, if I plug in the ethernet cable here I still seem to be getting a connection, pity I can't test this properly right now.

ifconfig gives this with the cable connected.

```

ifconfig
eth0      Link encap:Ethernet  HWaddr e8:9d:87:eb:5f:28  
          inet addr:10.246.53.59  Bcast:10.246.53.255  Mask:255.255.255.0
          inet6 addr: fe80::ea9d:87ff:feeb:5f28/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9164 (9.1 KB)  TX bytes:9933 (9.9 KB)
          Interrupt:20 Memory:c4800000-c4820000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr d0:df:9a:22:c4:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```So I'm not understanding this at all. I'm not getting this kind of output from my router at home, but I know it is working okay, as I'm using the same cable and connection on another computer.

Confusing or what, however, I guess it would be good to find a way to make the driver update stick, I am rmmod'ing the old one first before using insmod to install the updated driver, is that the right thing to do, or am I still missing a step somewhere?

---

### Post by airper on 2011-08-12
Another frustrating day with not much progress, maybe I am millimetres closer to either wired or wireless connection but I can't see that at moment. I seem to have some sort of connection established, but neither are actually useable.

sudo lshw -C network and ifconfig give this output

```

wayne@wayne-SATELLITE-R830:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: e8:9d:87:eb:5f:28
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.4.4-NAPI duplex=full firmware=0.13-4 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:40 memory:c4800000-c481ffff memory:c482a000-c482afff ioport:3060(size=32)
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: d0:df:9a:22:c4:06
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.1-030001-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:c2600000-c260ffff
wayne@wayne-SATELLITE-R830:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr e8:9d:87:eb:5f:28  
          inet6 addr: fe80::ea9d:87ff:feeb:5f28/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18378 (18.3 KB)  TX bytes:8071 (8.0 KB)
          Interrupt:20 Memory:c4800000-c4820000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr d0:df:9a:22:c4:06  
          inet6 addr: fe80::d2df:9aff:fe22:c406/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37608 (37.6 KB)  TX bytes:46248 (46.2 KB)

```Just can't see where to go next, searched the forum all day, but nothing I've come across has worked so far.

---

### Post by svast on 2011-08-15
Hi airper, 
one question comes to my mind: it looks like your home router does not accept any connection attempt from your laptop, either wired or wireless.
What is the brand/model of your router?

Some access-points or routers do disallow connections from unknown devices, unless you do declare them onto the router (or unlock temporary to register the device).
Is that the case ?

---

### Post by airper on 2011-08-15
Hi svast,

The router is a standard BT router, supplied by my Internet provider. It hasn't required any registering of devices in the past and Win7 on this laptop connects fine with it.

Working on the wired connection this evening as I've discovered a bit more.

What I have realised this evening is that I've loaded the 64 bit version of Ubuntu, there is another set of files in a directory called /lib64/...

I've complied the new driver again and am in the process of copying it across. I think this is the directory the laptop is booting up from (I hope) and changing the driver here might make it stick in the reboot.

If not I've done a bit more analysis this evening which I can post up, a much more careful step though the driver issue at least. Also a new driver was issued yesterday 1.5.1 so I'm trying to upload that.

I'll post back how I get on.

Thanks for your thoughts, your help is much appreciated.

---

### Post by airper on 2011-08-15
[FONT=Liberation Sans, sans-serif][SIZE=2]I'm having great difficultly in making the driver change stick, the driver update using the procedure in the readme file seems to result only in a temporary change, rebooting the computer to make the system restart with the new driver, results in the old driver being loaded.[/SIZE][/FONT]
 

 [FONT=Liberation Sans, sans-serif][SIZE=2]So this is what I've tried to do. Incidentally a new driver was released yesterday version 1.5.1 downloaded from Sourceforge, this is the  version I've tried to use this evening. [/SIZE][/FONT] 
 

 [FONT=Liberation Sans, sans-serif][SIZE=2]I've broken this down into three posts in an attempt to make it more readable.[/SIZE][/FONT]
 

 [FONT=Liberation Sans, sans-serif][SIZE=2]Ubuntu 11.04[/SIZE][/FONT]
 [FONT=Liberation Sans, sans-serif][SIZE=2]Toshiba Satellite R830-145
Intel 5i processor
Intel HM65 chipset
6Gb ram
640 Gb harddrive
Atheros AR9285 wireless card
Intel 82579v Ethernet controller[/SIZE][/FONT]
 

 

 [FONT=Liberation Sans, sans-serif][SIZE=2]**sudo lshw -C network (initial boot)**[/SIZE][/FONT]
 [FONT=Liberation Sans, sans-serif][SIZE=2][sudo] password for wayne: [/SIZE][/FONT] 
   [FONT=Liberation Sans, sans-serif][SIZE=2]*-network               [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]description: Ethernet interface [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]product: 82579V Gigabit Network Connection [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]vendor: Intel Corporation [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]physical id: 19 [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]bus info: pci@0000:00:19.0 [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]logical name: eth0 [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]version: 04 [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]serial: e8:9d:87:eb:5f:28 [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]capacity: 1Gbit/s [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]width: 32 bits [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]clock: 33MHz [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]configuration: autonegotiation=on broadcast=yes **driver=e1000e driverversion=1.2.20-k2** firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]resources: irq:46 memory:c4800000-c481ffff memory:c482a000-c482afff ioport:3060(size=32) [/SIZE][/FONT]

---

### Post by airper on 2011-08-15
[FONT=Liberation Sans, sans-serif][SIZE=2]**Summary of procedure to replace the driver module, in the readme file**[/SIZE][/FONT]
 

 

 [FONT=Liberation Sans, sans-serif][SIZE=2]1. Untar/unzip archive:  tar zxf e1000e-x.x.x.tar.gz[/SIZE][/FONT]
 

 [FONT=Liberation Sans, sans-serif][SIZE=2]2. Change to the driver src directory:   cd e1000e-x.x.x/src/[/SIZE][/FONT]
 

 [FONT=Liberation Sans, sans-serif][SIZE=2]3. Compile the driver module:  sudo make install. The binary will be installed as: /lib/modules/<KERNEL VERSION>/kernel/drivers/net/e1000e/e1000e.[k]o[/SIZE][/FONT]
 

  [FONT=Liberation Sans, sans-serif][SIZE=2]4.With 2.6 based kernels also make sure that older e1000e drivers are  removed from the kernel, before loading the new module: rmmod e1000e;[/SIZE][/FONT]
 

 [FONT=Liberation Sans, sans-serif][SIZE=2]5. Load the module using modprobe command: modprobe e1000e[/SIZE][/FONT]
 

 [FONT=Liberation Sans, sans-serif][SIZE=2]Note full path to the driver module is /lib/modules/<kernel version>/kernel/drivers/net/e1000e/e1000e.ko[/SIZE][/FONT]
 

 [FONT=Liberation Sans, sans-serif][SIZE=2]6. sudo /etc/init.d/networking restart[/SIZE][/FONT]
 

 [FONT=Liberation Sans, sans-serif][SIZE=2]7. sudo ifconfig eth0 up[/SIZE][/FONT]
 

 [FONT=Liberation Sans, sans-serif][SIZE=2]8. the result of all this is, the driver module seems to be replaced [/SIZE][/FONT] 
 

 [FONT=Liberation Sans, sans-serif][SIZE=2]**sudo lshw -C (network driver module replaced as per procedure above)**[/SIZE][/FONT]
   [FONT=Liberation Sans, sans-serif][SIZE=2]*-network               [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]description: Ethernet interface [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]product: 82579V Gigabit Network Connection [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]vendor: Intel Corporation [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]physical id: 19 [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]bus info: pci@0000:00:19.0 [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]logical name: eth0 [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]version: 04 [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]serial: e8:9d:87:eb:5f:28 [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]capacity: 1Gbit/s [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]width: 32 bits [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]clock: 33MHz [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]configuration: autonegotiation=on broadcast=yes **driver=e1000e driverversion=1.5.1-NAPI** firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]resources: irq:46 memory:c4800000-c481ffff memory:c482a000-c482afff ioport:3060(size=32) [/SIZE][/FONT] 
 

 




 [FONT=Liberation Sans, sans-serif][SIZE=2]However after a reboot the driver is now reported to be the old version again[/SIZE][/FONT]
 

 

 [FONT=Liberation Sans, sans-serif][SIZE=2]**sudo lshw -C network (and again after a reboot)**[/SIZE][/FONT]
 [FONT=Liberation Sans, sans-serif][SIZE=2][sudo] password for wayne: [/SIZE][/FONT] 
   [FONT=Liberation Sans, sans-serif][SIZE=2]*-network               [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]description: Ethernet interface [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]product: 82579V Gigabit Network Connection [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]vendor: Intel Corporation [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]physical id: 19 [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]bus info: pci@0000:00:19.0 [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]logical name: eth0 [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]version: 04 [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]serial: e8:9d:87:eb:5f:28 [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]capacity: 1Gbit/s [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]width: 32 bits [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]clock: 33MHz [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]configuration: autonegotiation=on broadcast=yes **driver=e1000e driverversion=1.2.20-k2** firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair [/SIZE][/FONT] 
        [FONT=Liberation Sans, sans-serif][SIZE=2]resources: irq:46 memory:c4800000-c481ffff memory:c482a000-c482afff ioport:3060(size=32) [/SIZE][/FONT]

---

### Post by airper on 2011-08-15
[FONT=Liberation Sans, sans-serif][SIZE=2]Next I managed to find a pre-complied version of the driver module for Debian 6, here:[/SIZE][/FONT]
 

 [FONT=Liberation Sans, sans-serif][SIZE=2][http://perfect-co.de/2011/04/intel-82579v-gigabit-ethernet-driver-for-debian-squeeze/](http://perfect-co.de/2011/04/intel-82579v-gigabit-ethernet-driver-for-debian-squeeze/)[/SIZE][/FONT]
 

 [FONT=Liberation Sans, sans-serif][SIZE=2]So I just navigated to the directory /lib/modules/<2.6.38-8-generic>/kernel/drivers/net/e1000e/e1000e.ko[/SIZE][/FONT]
 

 [FONT=Liberation Sans, sans-serif][SIZE=2]and replaced the driver module manually, (copied then deleted the original and replaced with the one above)[/SIZE][/FONT]
 

 [FONT=Liberation Sans, sans-serif][SIZE=2]Same result lshw -C network reports the original driver is loaded driverversion=1.2.20-k2.[/SIZE][/FONT]
 

  [FONT=Liberation Sans, sans-serif][SIZE=2]Next I deleted the driver in this location completely, with the same result, what's more the original driver is back in the location  /lib/modules/<2.6.38-8-generic>/kernel/drivers/net/e1000e/e1000e.ko[/SIZE][/FONT]
  

  [FONT=Liberation Sans, sans-serif][SIZE=2]So next I did a search of the file system and found another whole set of directories under /lib64/...[/SIZE][/FONT]
  

  [FONT=Liberation Sans, sans-serif][SIZE=2]So starting all over again, I recompiled the new driver version 1.5.1 checked it was compiled in the proper directory again ( /lib/...)  then I logged on as root and copied the new driver across to /lib64/...[/SIZE][/FONT]
  

  [FONT=Liberation Sans, sans-serif][SIZE=2]Having first confirmed sudo lshw -C network listed the new driver. [/SIZE][/FONT] 
  

  [FONT=Liberation Sans, sans-serif][SIZE=2]Rebooted, but checking again the old driver is still loaded, driverversion=1.2.20-k2.[/SIZE][/FONT]
  

  [FONT=Liberation Sans, sans-serif][SIZE=2]At this point I've lost the plot, how do I change the driver module permanently. I assume there is another copy somewhere which is being loaded up on boot up and copied into the directory above, but searching the hard drive does not find it.[/SIZE][/FONT]


[FONT=Liberation Sans, sans-serif][SIZE=2]I really am at the limit of my knowledge here and I'm not even sure this will cure the problem and my head hurts!!! learning a lot though.[/SIZE][/FONT]


[FONT=Liberation Sans, sans-serif][SIZE=2]
[/SIZE][/FONT]


[FONT=Liberation Sans, sans-serif][SIZE=2]
[/SIZE][/FONT]

---

### Post by airper on 2011-08-17
A couple of other people are having exactly the same problems with the wireless card Atheros AR9285. There are more posts and investigations here.

[http://ubuntuforums.org/showthread.php?t=1821721](http://ubuntuforums.org/showthread.php?t=1821721)

Still not solved the problem yet, continuing to work on it, not making much progress at the moment.

---

### Post by svast on 2011-08-19
Hi airper,

just got my laptop back from toshiba tech support.
I can now confirm that I have the same network chip as you, with the same e1000e driver: so I'm gonna make further tests and keep you posted.

---

### Post by airper on 2011-08-20
Thanks svast, I'm away from home over the weekend, but I have Internet access so I'll keep looking. I'm back home on Monday and will be able to check things out properly them. 

Great stuff and thanks.

Regards

Airper.

---

### Post by airper on 2011-08-23
Hi svast, 

Back home now and working on my Internet connections. 

For the wireless connection there is a very good thread running here:

[http://ubuntuforums.org/showthread.php?t=1821721](http://ubuntuforums.org/showthread.php?t=1821721)

It's somewhat technically challenging and something of a learning experience to say the least. I've followed along right up to page three and installing the compat-wireless drivers. Just watching the next bit, which is going down another level.

I've got an unsecured connection working with BT OpenZone, but nothing via my router, even with encryption off. That said it works fine with Windows on the R830-145 and my other laptops in Ubuntu, so it is not directly a hardware issue with the router.

Chili555 (Master Guru on these things) is of the opinion the ATH9K driver is broken, there are loads of postings everywhere about connection issues with this driver and many new Atheros wireless cards. See thread above, but there is still hope.

On the ethernet front not much progress I'm afraid, I've tried just about every config option on the router to no avail. On the surface it looks like the same issue as the wireless connection (symptoms anyway) It tries to connect, finds the router, picks up an IP address, but can't associate and times out.

Anything you can see via your laptop would be useful in terms of finding the right place to look deeper. I'm not sure I've got the very latest e1000e driver installed properly (version 1.5.1) I can get it loaded okay and reported as just via sudo lshw -C network, but a re-boot sees it revert to the old version. Not at all sure what I've not done here to make it survive a re-boot.

Best Regards

Wayne

---

### Post by svast on 2011-08-25
Hi Airper,

I am facing some other issues here: suddendly the laptop freezes and fan goes crazy. I have to manually switch it off :-(
Also, I cannot use my mouse with VMware Player, and fighting for a solution.
But on the network side, it looks great: both wired and wireless are working.

I heard some glitches regarding the support of all that new hardware (sandy bridge platform). Therefore I am going to test newer linux kernel (v2.6.39 and v3.0.1 are available, and the next 3.1 is on its way too, with hardware support enhancements).
I follow the recipe there:
[http://www.khattam.info/howto-install-linux-kernel-3-0-in-ubuntu-11-04-natty-narwhal-2011-06-03.html](http://www.khattam.info/howto-install-linux-kernel-3-0-in-ubuntu-11-04-natty-narwhal-2011-06-03.html)
Briefly:
1/ Download from Kernel-PPA: for instance v3.0.1 [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0.1-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0.1-oneiric/)
```
linux-headers-3.0.1-030001_3.0.1-030001.201108060905_all.deb
linux-headers-3.0.1-030001-generic_3.0.1-030001.201108060905_amd64.deb
linux-image-3.0.1-030001-generic_3.0.1-030001.201108060905_amd64.deb
```
2/ Install them in that order:
```
sudo dpkg -i linux-headers-3.0.1-030001_3.0.1-030001.201108060905_all.deb
sudo dpkg -i linux-headers-3.0.1-030001-generic_3.0.1-030001.201108060905_amd64.deb
sudo dpkg -i linux-image-3.0.1-030001-generic_3.0.1-030001.201108060905_amd64.deb
```
3/ Reboot after that, and "cross the fingers".

The forums suggest me trying the one located here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39.4-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39.4-oneiric/)

More information in next episode :-)
Best regards

---

### Post by airper on 2011-08-25
Hi svast,

Have you seen this thread:-

[http://ubuntuforums.org/showthread.php?t=1760568&highlight=toshiba+R830](http://ubuntuforums.org/showthread.php?t=1760568&highlight=toshiba+R830)

It is all about the fan speed issues and updating the Kernel. In trying to solve my wireless issues, I successfully updated my Kernel to 3.1.0 no problems and everything except the wireless and ethernet were working fine. I used ppa, but just went for the latest kernel without rc. Once you look it is fairly obvious what to do.

There is a link to a step by step guide with this thread, so it's easy to follow and fairly intuitive.

Hope it helps.

I'm still persisting with wireless at the moment, chili555 is on the case, who is providing excellent expert help. I'll keep you posted on progress, at the moment we are trying to configure ndiswrapper.

Regards

Wayne

---

### Post by svast on 2011-08-25
Yes thank you, I even posted a little bit on that thread.

Hope you will manage to make your wireless working!

---

### Post by airper on 2011-08-28
Hi svast,

No luck with my wireless, super help from Chili, but still we couldn't get it working. Tried the latest ath9k drivers, compat-wireless an ndiswraper, but no success with any of them right now.

Chili has advised using a USB wifi dongle **(**Asus USB-N13), there is a page here about using it if anyone else is looking at this option.

[https://help.ubuntu.com/community/WifiDocs/Device/Asus%20USB-N13_Natty%2011.04](https://help.ubuntu.com/community/WifiDocs/Device/Asus%20USB-N13_Natty%2011.04).

I've ordered one so will let you know how I get on with it. Hopefully it will give me a option for wifi at home on this machine.

How you doing with your fan problem? So far I don't seem to experience this on the R830-143, with any Kernel from 2.6.38-8-generic and up.

Regards

Wayne

---

### Post by svast on 2011-08-28
This is really weird: we both seem to run the same hardware and the same distro, and yet we are dealing with very different issues.

kernel freeze and crazy fan: still there, but less frequent on 2.6.39...
So I am still digging the forums :-)

---

### Post by airper on 2011-08-28
Yep, it is very odd that two machines so close in spec can have such different problems.

I wonder what version of the BIOS we are both running. I'll check mine on the next boot up and post up. I would have thought other differences between the machines are very subtle, so it is difficult to explain why they seem to have such a variation when running Linux.

It seems to me most of the problems are at the Kernel level not the Distro, but that might just be my perception of this, I don't have any real facts to support this, other than I tried booting into Fedora, Mint, Suse, and Bodhi, they all produced the same issues on this laptop.

Will get back to you about the BIOS version.

---

### Post by magicvince on 2011-08-29
I don't if you have tried before: I try to configure network on a r83O and it works in wifi with ubuntu 10.04 but no ethernet.

I read a post where some one seems to make lan work on with a recent archlinux install:
[http://danielj.se/2011/08/07/no-eth0wlan0-in-arch-linux/]("http://danielj.se/2011/08/07/no-eth0wlan0-in-arch-linux/")

I'll send him a question to know if it works with his mint installation.

---

### Post by airper on 2011-08-29
Hi magicvince,

Thanks for the info. I haven't tried 10.04. I'll burn an iso and give it a go. Hopefully as the ethernet card is Intel a good fix will find it's way into the generic kernels fairly quickly. There was a recent update to 2-38-11-generic for Ubuntu which I haven't tried yet as well. 

I'm planning to try that first tomorrow when I can download all the updates properly on a new install.

Will let you know how I get on with both. 

Thanks

Wayne

---

### Post by airper on 2011-08-29
Hi svast,

checked my BIOS version, it is 2.80 (EC version 1.10) I'm not sure if that is the latest version?
[U]

[/U] Regards

airper

---

### Post by airper on 2011-09-03
Hi svast and others,

I tried 10.04, but still no joy with the AR 9285 card. However my Asus USB-N13 wifi dongle arrived from Amazon yesterday. 

Plugged it in and followed the instructions on the link above. You have to blacklist the rt2800usb driver and then reboot. Much to my surprise you don't have to blacklist the ath9k driver. 

Both the N13 and the AR9285 show up in Network Managers list, you just have to click on the right one and yep, it connected to the router no problems.

A decent internet connection at last. :P:P:P

Hope you are having some success with you fan issues, I've still not experienced that problem so far.

Best Regards

Wayne

---

### Post by svast on 2011-09-03
great news! I am happy you now have regular network access, even if it may be a workaround.

For my fan going crazy, it is only when the laptop freezes (ie: no more display refresh, mouse and keyboard not working any more). That seems to be a kernel issue, although I still did not see the true cause of that.
It does not happen so often with 2.6.39 kernel, as long as the laptop stays on power supply. If it gets on battery, and some inactivity puts the power saving on: when I get back working on, it gets frozen after a while. But so randomly that I can not set up a scenario for launchpad.

---

### Post by svast on 2011-09-03
> **airper said:**
> Hi svast,

checked my BIOS version, it is 2.80 (EC version 1.10) I'm not sure if that is the latest version?
[U]

[/U] Regards

airper
Hi,
does the BIOS have anything to do with your wireless card?

---

### Post by airper on 2011-09-03
Hi svast,

No, I think the BIOS is a bit of a red herring (irrelevant) with the wifi problems, it seems this problem is all down to the ath9k driver. This seems to be broken for many new Atheros wireless chipsets, I really do hope it is on the Ubuntu fix list for 11.10 there must be many people suffering these issues with any PC with a new'ish Atheros chipset.

Not sure if it helps with the fan issue??? There was some suggestion on the other thread that he BIOS was an issue for the fan.

---

### Post by airper on 2011-09-30
Hi svast,

Good News,

  		 			 				  			  			The latest updates to Ubuntu have pushed out an updated driver, which  appears to be a very big step forwards.

All my laptops with  new'ish Atheros wireless cards (AR9285 and AR928X) have a good working  wireless connection, which appears to be fast as well.

Hope this is helpful info to others, if you've been struggling with the ATH9K driver.

---

### Post by svast on 2011-10-01
Hi airper,

this is really good news, I have to say that my laptop does not freeze as much as it used to... It does not freeze any more, as long as I stick with one power source (either battery or power supply). I noticed that if I unplugged my running laptop from the power adaptor and was working on battery for a while (and having some short rest blah blah), sometimes the laptop gets frozen and fan gets crazy. So I carefully avoid that now!

I am currently running a PPA kernel : 2.6.39-02063904-generic
And moreover, I made a small tweak (disable anti-aliasing) to LibreOffice which was causing X to hang (ie, no more keyboard, mouse moving but no effect on the screen).

What update are you talking about? The latest 2.6.38-11.50 kernel update?

best regards

---

### Post by airper on 2011-10-01
Hi,

Yes, kernel update 2.6.38-11.50 seems to have fixed lots of little problems. I'm looking forwards to 11.10. I was reading today it will be based on Kernel 3.0.11 or better and lots of driver issues have been sorted out. 

Unity is default for both 3d and now 2d graphics, but you can install gnome via CLI.

I've been playing with Unity for a couple of weeks and have finally got the hang of it, I'm actually beginning to like it, even the lefthand launcher panel.

So good progress this last month for both of us it seems.

Regards

Wayne

---

### Post by svast on 2011-10-01
Thank you very much for the tip; I will try that new kernel ASAP.

have a great week-end

---

