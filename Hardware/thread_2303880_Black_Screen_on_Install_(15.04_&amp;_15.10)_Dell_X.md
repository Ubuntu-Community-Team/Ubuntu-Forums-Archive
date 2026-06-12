---
title: "Black Screen on Install (15.04 &amp; 15.10) Dell XPS 8900"
date: 2015-11-22
forum: Hardware
---

### Post by archcynic on 2015-11-22
Hi All,


I just (Nov 15) bought a new Dell XPS 8900 and thought I would document my journey to get (X)Ubuntu working for the benefit of those who come later.

Summary: Hardware too new for 14.04 LTS. Switched to 15.10 to get support for drivers and needed grub command update to get it installed. Then all good.

Attempting to get 14.04 LTS working

Initial install from DVD went to a black screen shortly after the splash screen first shown. The problem was the lack of output from the video card (Nvidia GTX 745). I plugged the monitor into the on-board video's HDMI socket and all went well and switched back to card output once installed.(There seems to be a &#8220;NOMODESET&#8221; option that helps on the grub command line that deals with this also.)

Wireless was a bit flaky (crashed after 20 mins) and it turned out the Ethernet port was not recognised (no &#8220;eth0&#8221; from 'ifconfig'). No sound from outputs.

The output from lspci -nn

```
00:00.0 Host bridge[0600]: Intel Corporation Sky Lake Host Bridge/DRAM Registers[8086:191f] (rev 07)
00:01.0 PCI bridge[0604]: Intel Corporation Sky Lake PCIe Controller (x16) [8086:1901](rev 07)
00:14.0 USB controller [0c03]: Intel Corporation Sunrise Point-H USB 3.0 xHCIController [8086:a12f] (rev 31)
00:14.2 Signal processing controller [1180]: Intel Corporation Sunrise Point-HThermal subsystem [8086:a131] (rev 31)
00:16.0 Communication controller [0780]: Intel Corporation Sunrise Point-HCSME HECI #1 [8086:a13a] (rev 31)
00:17.0 RAID bus controller [0104]: Intel Corporation SATA Controller [RAID mode][8086:2822] (rev 31)
00:1c.0 PCI bridge[0604]: Intel Corporation Sunrise Point-H PCI Express Root Port #1[8086:a110] (rev f1)
00:1f.0 ISA bridge[0601]: Intel Corporation Sunrise Point-H LPC Controller [8086:a145](rev 31)
00:1f.2 Memory controller [0580]: Intel Corporation Sunrise Point-H PMC [8086:a121](rev 31)
00:1f.3 Audio device[0403]: Intel Corporation Sunrise Point-H HD Audio [8086:a170] (rev31)
00:1f.4 SMBus[0c05]: Intel Corporation Sunrise Point-H SMBus [8086:a123] (rev 31)
00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V[8086:15b8] (rev 31)
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM107 [GeForce GTX745] [10de:1382] (rev a2)
01:00.1 Audio device[0403]: NVIDIA Corporation Device [10de:0fbc] (rev a1)
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]

```

(For those that don't know the [xxxx:xxxx] is a device ID that is unique to a type of chip you are dealing with and lets you run to ground the driver that would support it. The first four chars is the vendor &#8211; 8086=Intel &#8211;the last four is the device itself).

For Ethernet, Googling &#8220;8086:15b8&#8221; and &#8220;cateee&#8221; (the Linux driver database) gets you to 

[http://cateee.net/lkddb/web-lkddb/E1000E.html](http://cateee.net/lkddb/web-lkddb/E1000E.html)

which, towards the end, has the line

```
lkddb pci 8086 15b8 .... .... ......: [CONFIG_E1000E]("http://cateee.net/lkddb/web-lkddb/E1000E.html") [CONFIG_ETHERNET]("http://cateee.net/lkddb/web-lkddb/ETHERNET.html") [CONFIG_NET_VENDOR_INTEL]("http://cateee.net/lkddb/web-lkddb/NET_VENDOR_INTEL.html") : [drivers/net/ethernet/intel/e1000e/netdev.c]("http://lxr.linux.no/source/drivers/net/ethernet/intel/e1000e/netdev.c") #in 4.1&#8211;4.2, 4.4-rc+HEAD

```

which indicates the driver is only supported by Linux Kernels 4.1-4.2 & 4.4.

Likewise

Audio&#8220;8086:a170&#8221; &#8594; 3.18&#8211;3.19,4.0&#8211;4.2, 4.4-rc+HEAD
Wireless&#8220;10ec:b723&#8221; &#8594; 3.17&#8211;3.19,4.0&#8211;4.2, 4.3+HEAD

So this hardware combination is not going to fly with a Kernel below 4.1.

```
14.04   Trusty Tahr      3.13
14.10   Utopic Unicorn   3.16
15.04   Vivid Vervet     3.19
15.10   Wily Werewolf    4.2
```

So it was time to install Ubuntu (Xubuntu in my case) 15.10.

Attempting to install 15.10 (or 15.04)

Similar to above, shortly (around 30sec) after the install splash screen appeared it faded to black not to be replaced. No playing with video outputs helped this time. I pressed Ctrl-Alt-F1 to see the virtual console and errors scrolled past faster than the eye could see. I'm not aware of any way of slowing these down to be readable.

I installed 14.04 and upgraded to 15.04 and the same thing happened on reboot. Now however I could boot using a 14.04 liveUSB to view the logs in /var/log. Syslog and kern.log were around 2GB(!) each. Filled with entries similar to:

```
[41.93] pcieport 0000:00:1c.4: AER: Multiple Corrected error received:id=00e0
[41.93] pcieport 0000:00:1c.4: PCIe Bus Error: severity=Corrected,type=Physical Layer, id=00e0(ReceiverID)
[41.93] pcieport 0000:00:1c.4: device [8086:a110]error status/mask=00000001/00002000
[41.94] pcieport 0000:00:1c.4: [ 0] Receiver Error (First)

```
Seemed to be related to the PCI Bridge device (8086:a110). After a bit of a google, a bug report from 5 years ago suggested a similar issue went away if you disabled &#8220;PCI power management&#8221;.

When trying to install, at the initial 'grub' screen that asks you to select (1) Try Ubuntu (2) Install directly (3) OEM install etc. Place the selector over option 1 and press the letter &#8220;e&#8221; to edit the grub boot command. On the third line just after &#8220;quiet splash&#8221;add the string &#8220;pcie_aspm=off&#8221; and press F10 to continue the boot. This will allow you to start 15.10 from a USB/DVD and install to disk. 

That just installs to disk. You will have to manually update the Grub boot command every time you boot into Linux until you implement the fix in the grub config file. For this edit &#8220;/etc/default/grub&#8221; using your favourite editor and make sure the follow line is present:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=off"

```
This file is a &#8220;script that generates a script&#8221; so you have to run&#8220;sudo update-grub&#8221; to propagate this to the real Grub configfiles (&#8220;/boot/grub/grub.cfg&#8221;);

(Notethat I did a clean install &#8211; not dual boot &#8211; so no grub screen appeared once installed on disk. Holding down the shift key that is supposed to trigger the grub screen did not function. I had to boot using a 14.04 liveUSB, mount the disk file system and manually update&#8220;/boot/grub/grub.cfg&#8221; to include &#8220;pcie_aspm=off&#8221; to allow for an initial boot to implement the long term fix.)

After all that the PC is now up and running. The sound is working. The Ethernet is operational (though the wireless still shows signs of being a bit flaky). Everything else seems great and the dual monitors are working just fine off the Nvidia card with proprietary drivers.

Thanks,as always, to those who take the time to contribute to these forums.I'd not have got very far without them.

---

### Post by shashakoe on 2015-12-18
Thank you so much! I followed your instructions and was able to successfully install ubuntu on my xps 8900!! My only problem is that my display sometimes does not show some letters or show a distorter (i.e. bolder) text. I'm wondering how did you get the your video card to display correctly. I mean when you say, you use proprietary drivers, how do you set it up?

Thanks so much!


Here's what I tried:

Following what I found here: [http://ubuntuhandbook.org/index.php/2014/03/install-nvidia-driver-334-21-ubuntu-linux/](http://ubuntuhandbook.org/index.php/2014/03/install-nvidia-driver-334-21-ubuntu-linux/)
I ran the following commands:

sudo apt-get purge nvidia*; sudo apt-get install nvidia-319-updates-dev

sudo service lightdm stop     ## For the default LightDM

sudo service gdm stop     ## For the Gnome GDM #not needed

sudo service mdm stop     ## For the Linux Mint default MDM #not needed

Then I downloaded the NVIDIA driver from
[http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86_64/358.16/NVIDIA-Linux-x86_64-358.16.run&lang=us&type=GeForce](http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86_64/358.16/NVIDIA-Linux-x86_64-358.16.run&lang=us&type=GeForce)

chmod +x ~/Downloads/NVIDIA-Linux-*-358.16.run && sudo sh ~/Downloads/NVIDIA-Linux-*-358.16.run

When I rebooted, the monitor was just blank.
Any ideas?

---

### Post by john505 on 2016-01-05
Thank you! I was really struggling to get Ubuntu installed on the XPS 8900 until I found this post. I was having similar problems, at first trying to follow generic guides for installing Ubuntu alongside Windows 10 - none of which worked and just mounted frustration, but your instructions got me most of the way there finally. I had a few other hangups, including the strange distorted text/missing letters in menus and gui windows that shashakoe was experiencing. So, I'll just lay out everything that I had to do before I had a successful and complete installation of Ubuntu 15.10 running alongside Windows 10 - for the record, as this is a new computer with new unresolved issues regarding Linux - and I hope other people post their insights as well.

I got it working a few days ago. I should have posted this while it was still fresh, but I think I can remember the crucial points...
I should mention that I'm not a Linux installation expert, but I have used it occasionally and done a couple of installations in the past

First of all:
I have the Dell XPS 8900 with Core i7, 3.4Ghz, 16 GB DDR4, with NVIDIA GeForce GTX 745, Windows 10 pre-installed

So I got Windows all set up (Fast startup should be turned off, but I didn't need to disable 'secure boot' like some people recommend), and immediately downloaded Ubuntu 14 64-bit, which I got to boot from a USB that I set up using Unetbootin. And it worked in the 'Try Ubuntu mode' flawlessly; I didn't have the same issues archcynic encountered with the black screen, and my wireless connection was fine - but once I tried to install it, the installer would crash every time with a "Not enough free disk space" error. I tried everything, for about 10 hours straight. Also, when I had to restart the computer after failed installations, I got the pcieport messages that archcynic mentioned scrolling frantically and endlessly and had to manually restart. Then I finally found this thread and got on the right track.

First step:
Create bootable USB with Ubuntu 15.10, using Rufus. Set it up to have a GPT partition scheme for UEFI, FAT32 file system, and an 8192 byte cluster size.

Second step (repost from archcynic):

Note: This is where I first encountered the text distortion problem. Fortunately I had already gone through the installation steps so many times with version 14 (this problem did not exist with that version) that I knew the text by heart , and I had already partitioned my drive, so the disappearing text didn't ruin me. If your screen looks anything like mine did, you might have some difficulty making it through the installation process.
I believe there is a fix that I didn't find in time to try, which archcynic mentioned. When you are editing the grub commands on startup, add "nouveau.modeset=0" to the end of the linux line.

> When trying to install, at the initial 'grub' screen that asks  you to select (1) Try Ubuntu (2) Install directly (3) OEM install etc.  Place the selector over option 1 and press the letter “e” to edit the  grub boot command. On the third line just after “quiet splash”add the  string “pcie_aspm=off” and press F10 to continue the boot. This will  allow you to start 15.10 from a USB/DVD and install to disk.

I selected the "something else" option on the installer to set up my  partitions manually (with a /, swap, and /home directory), and proceeded  with the installation.


Third step:
Step 2 should get you through the installation and restart. You will end up at the grub menu, where you should highlight Ubuntu and press 'e' and repeat the steps in 2.
The text issue will still be there, but you should be able to work through it. Here is where I ran into another problem; based on research, this may just be a isolated problem with the source of the Ubuntu download. If you make it to the desktop, you can skip the following part. Anyways, Ubuntu asks for a username and password on the first startup, before requiring you to set up an account - and the suggested solutions online (username: "ubuntu", password: blank or "utnubu") did not work for me. So, the only way I found around this was to press Ctrl+Alt+F1, which takes you to a command line. Enter "ubuntu" on the command line, and just press enter at the password prompt; this combination just doesn't work on the GUI I guess. Type "ls". You should see a file named .Xauthority. You need to remove it. Type "sudo rm .Xauthority" and press enter. "ls" again to make sure it's gone.
Now press Ctrl+Alt+F7 to revert back to the GUI home screen. Reboot the computer. Follow the previous steps to edit the grub commands, and it should take you to the desktop.

Fourth step:
Edit the “/etc/default/grub” file as archcynic suggested with:
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=off"
Now next time the computer is rebooted, you don't have to edit the grub command by hand.

Fifth step:
Fix the disappearing text. In a terminal, type "sudo apt-get install nvidia-352" and restart. There is a nvidia-358, but I haven't tried it. 352 works for me.


That's it. Everything is working fine so far, although I haven't used it too heavily yet. Hope this helps.
Thank you again archcynic.

---

### Post by dookie2 on 2016-01-10
Thanks guys!  I got my new XPS 8900 yesterday and I ran into the same issues as everyone on this thread.  I am glad that I saw this post and I was able to get my 8900 setup today.

After installation, for some reason I wasn't able to get to the grub menu at bootup time.  I was holding the "shift" key after power-on but the menu never showed up.  I ended up having to update the grub configuration through the LiveCD.  The whole installation process went really smoothly.

Thanks again!

---

### Post by aitortxo on 2016-02-17
Thanks for this post, I'm considering buying this box for my work and install Ubuntu. Can you give us a little insight about how does the hybrid HD+SSD cache combination works? Did you do any tweak for this to work or was it straightforward?

---

### Post by sharmajncasr on 2016-03-11
[COLOR=#000000]Hi Archcynic and others,[/COLOR]
[COLOR=#000000]Thank you very much for the details which you have provided. I am almost there, but, I couldn't reach it yet. I was also doing a plain installation. I am not getting the grub once I restart after installation (as expected). **Could you just let me know how did you update the grub through 14.04 live CD?** I didn't find any grub folder in /boot of my hard-disk (after mounting) while checking from the live-CD (I have used 15.10 only). I tried to create a grub folder and grub.cfg file (by just keeping "pcie_aspm=off" command) in the boot but it didn't work for me. Can you help me at this point? Please ...[/COLOR]

[COLOR=#000000]Thanking you,[/COLOR]
[COLOR=#000000]Sincerely,[/COLOR]
[COLOR=#000000]Sharma. [/COLOR]

---

### Post by sharmajncasr on 2016-03-13
Hi all,

I was able to install 15.10 with the above suggestions. Below I have given some information which is little different from what others have mentioned (which may be helpful for someone else). 
For installing 15.10 on Dell XPS 8900 (NOT dual boot):
1) After placing the 15.10 DVD/pen-drive, change the boot order (press F2 or F12 after restart --> boot sequence --> bring the DVD/pen-drive to the first among the others) such that it will read the DVD/pen-drive first and press enter.
2) Once the system starts booting, press SHIFT key to enter into the ubuntu 15.10 live CD grub menu (if you not pressing the shift menu, you will get a blank screen). 
3) In the grub menu, I saw four options where the first one is "Try to install ubuntu" (this will be highlighted automatically). Below these options you will see some description regarding function keys. Among them, press F6 and select (press Enter) the first one (similar to pressing 'e' in the [COLOR=#000000]Archcynic's post[/COLOR]). After selecting the first one, press Esc. This will give you a single line of commands (above function keys) and here you need to write "pcie_aspm=off" before "---" and after "quiet splash". After this, press Enter to start the installation (This is similar to F10 in Archcynic's post). You will be taken directly to the ubuntu 15.10 desktop and here you will have an option to install.
4) After you complete your installation, you can mount your hard disk (simply by double clicking on the hard-disk) and go to the /media/ubuntu/<somenumber/etc/default/grub file.
Edit this file as archcynic suggested with:
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=off" and edit the line
5) copy and paste the above command in  the grub.cfg file located at /media/ubuntu/<somenumber>/boot/grub/ (if you don't have one, just create a grub folder inside the /boot of your hard-disk and create a grub.cfg file. I have copied the /boot/grub/grub.cfg file located on the live CD to /media/ubuntu/<somenumber>/boot/grub/ and edited it). **This is very important if you are NOT making your system dual boot** (i.e. a plain ubuntu installation). Changing the grub.cfg file allows you to log-in your system after a system restart.
6) Final step is to run "sudo update-grub" (after system restart).
7) As mentioned in the above posts "sudo apt-get install nvidia-352" helped me to resolve the text breaks on the screen.

Once again thanks to all the earlier posts' owners for their valuable information. A special thanks to Archcynic for his help.

Hope this helps some one else!

---

### Post by nedjo2 on 2016-04-26
@sharmajncasr:

Thanks for the succinct summary of steps.

I successfully followed your steps through #3 but, due to my weak sysadmin skills, there are two steps I'm not sure how do follow.

#5: The grub configuration file is owned by root and by default I can't save edits to it. How do I do so?

#6: When I reboot after installing, after the Dell logo, I get a purple screen that then goes blank. I never see text (e.g., a boot menu). How do I get to a command line to issue the command "sudo update-grub"?

Thanks for any tips!

---

