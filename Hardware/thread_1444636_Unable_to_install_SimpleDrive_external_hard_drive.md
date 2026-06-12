---
title: "Unable to install SimpleDrive external hard drive"
date: 2010-04-01
forum: Hardware
---

### Post by usfchick13 on 2010-04-01
Hi, I just made the switch from Windows to Ubuntu, so I'm still very confused on a lot of things. I backed up all of my files onto my SimpleDrive 500gb external hard drive, but now I can't figure out how to access it on Ubuntu. I've aleady plugged in the USB cable to my laptop, but it doesn't seem to be installing. Can someone please explain how to install my hard drive so that I can transfer my files? Thanks!

---

### Post by coffeecat on 2010-04-02
Hi

Sorry no one has answered you, so I hope you are still checking this thread.

Since you managed to write to the external drive using Windows, it must be formatted either FAT32 or NTFS, both of which Ubuntu can read and write to reliably. What *ought* to happen when you plug a usb drive in, is that it is automounted, a desktop icon appears and a Nautilus (file browser) window opens. You don't need to install anything. Since this isn't happening, we need to investigate.

First - try plugging in the drive and wait a few seconds. If no browser window opens, have a look in the main Places menu, probably under 'Removable Media'. Does it appear there?

Second - open a Nautilus window. Go to Places and select either 'Home Folder' or 'Computer' - it doesn't matter which. Now from the browser menu, Edit -> Preferences -> Media tab. Make sure the 'Browse media when inserted' box is ticked.

Third - most USB drives will work just fine in Ubuntu, but with a few the firmware (designed to work with Windows) interferes. Or sometimes there is autorunning software on the hard drive - some sort of Windows utility - which also interferes with drive mounting in Linux. Can you give us some more details of the drive? Is there any privacy or backup or similar software that came with the drive and which runs automatically when you plug it into Windows?

Lastly - let's see if Ubuntu is actually detecting the drive. Plug it in and then open a terminal (Applications > Accessories > Terminal). Post the output of the following two commands:

```
sudo fdisk -l
dmesg | tail
```That's a lower-case L at the end of the first command. You can copy and paste terminal output to the forum message box, but please note that the keyboard shortcut for copy in the terminal is crtl-**shift**-C. Also please enclose the terminal output in code boxes by highlighting the output text and clicking on the '#' button in the message toolbar.

---

### Post by usfchick13 on 2010-04-02
Hi, thanks so much for replying! I was about to just give up. 

1. I plugged in my hard drive and waited, but nothing ever showed up. It isn't appearing anywhere that I can see.

2. The box is ticked.

3. I don't think there is any privacy or backup software that came with the drive. When I had Windows, I would just plug it in and it would recognize the drive immediately. I'm not very good with computers and all of the technical stuff, so I could be wrong. This is the link to the exact drive I have, from the maker's website. [http://www.simpletech.com/parts/s500u.htm](http://www.simpletech.com/parts/s500u.htm)

4. Here are the results I got from the codes you gave me:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

```

```
ubuntu@ubuntu:~$ dmesg | tail
[  277.922389] wlan0: associated
[  277.938183] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  288.040082] wlan0: no IPv6 routers present
[ 2939.402258] EXT4-fs (sda1): barriers enabled
[ 2939.403726] kjournald2 starting: pid 4472, dev sda1:8, commit interval 5 seconds
[ 2939.404654] EXT4-fs (sda1): internal journal on sda1:8
[ 2939.404664] EXT4-fs (sda1): delayed allocation enabled
[ 2939.404671] EXT4-fs: file extents enabled
[ 2939.414878] EXT4-fs: mballoc enabled
[ 2939.414897] EXT4-fs (sda1): mounted filesystem with ordered data mode
ubuntu@ubuntu:~$ 

```

Thank you again so much for your help! I really appreciate it.

---

### Post by coffeecat on 2010-04-02
> **usfchick13 said:**
> 4. Here are the results I got from the codes you gave me:

And they have an interesting tale to tell. Basically, fdisk gives you information about all the drives and partitions attached to your computer whether or not they are mounted ready for use. The command dmesg gives you various kernel messages, the '| tail' bit giving you just the last few lines, otherwise you get overwhelmed with information. Normally, you should expect to see some activity at the end of dmesg when you plug a USB drive in.

Well - the odd news is that your system isn't detecting the physical presence of the USB drive, let alone mounting it. In fdisk, sda is your internal drive. THe USB drive should appear as sdb. It isn't there. Ditto dmesg - no mention of sdb.

Let's check one thing first. You did have the USB drive plugged in and powered when you did those commands, didn't you? Because, if so, this suggests a hardware rather than an Ubuntu problem. Possibly a faulty USB port.

I notice from your fdisk output that you have Ubuntu only on that laptop. What did you have before? Was the USB port working then? Is there another USB port on that machine that you can try?

When you post your answers, please also plug the drive back in (and switch it on) and post the terminal output of:

```
lsusb
```That might give us some more clues.

---

### Post by usfchick13 on 2010-04-02
> You did have the USB drive plugged in and powered when you did those commands, didn't you?

Yes, I did. The drive is spinning and the light is on.

> What did you have before? Was the USB port working then? Is there another USB port on that machine that you can try?

Before Ubuntu, I had Windows 7, and before that was Windows Vista. The port worked fine on both systems. I have a total of 4 ports on my laptop, and I did try using my drive with all 4. I don't think it is my USB ports though, because I have tested them with other devices, such as a flash drive or wireless mouse, and they have worked just fine.

It also isn't my external hard drive, because it worked just fine two days ago and it continues to work just as well when I plug it into a computer that is running Windows. 

```
ubuntu@ubuntu:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 07d1:3c04 D-Link System WUA-1340
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ubuntu@ubuntu:~$ 


```

---

### Post by coffeecat on 2010-04-02
Your lsusb looks OK. I presume the D-Link is a USB wireless device. So USB looks as though it is working OK.

I've had another look at your link and noticed something I didn't notice before:

> Turbo USB 2.0* interface, up to 25% faster than traditional USB 2.0Hmmm. Never heard of turbo USB. What concerns me is that this might be an example of device firmware interfering with the Linux usb drivers - what I mentioned before. Almost all USB hard-drives work just fine with Linux. I have a motley collection and they're OK, but I have seen threads where the OP is having a similar problem to you. The SimpleTech people will have tested it with Windows and MacOS, but not Linux - which doesn't get us very far.

A couple of suggestions:

If you can get hold of another USB drive - a flash/pendrive might be best - see if you can transfer some files from the Windows machine to that Ubuntu laptop. If you can, that proves that the USB ports are OK - which they almost certainly are.

Boot up the live CD on the laptop so that you get the live session. Try both the SimpleDrive and the pendrive in the live session. If the pendrive works and the SimpleDrive doesn't, that means almost certainly that the SimpleDrive isn't compatible with Linux - which would be a pity.

By the way - if you are tempted to buy another USB hard-drive, steer clear of Seagate. I doubt whether all Seagates are problematic, but some of the threads I mentioned concerned Seagate.

---

### Post by usfchick13 on 2010-04-02
I tried your suggestions and I still couldn't access the hard drive, so I guess I'll settle for transferring the more important files over with my flash drive. I don't think I'll invest in another hard drive, since I plan to purchase another computer within the next six months. I've really only transfered to Ubuntu to get rid of a problematic copy of Windows 7, and this laptop has a lot of other problems internally, so I'll just bear it for now.

Thank you again so much for helping me! :)

---

### Post by coffeecat on 2010-04-02
Ah well. Pity we couldn't get the hard drive recognised in Ubuntu. But good luck with your next purchase, and happy Ubuntu-ing! :)

---

### Post by coffeecat on 2010-04-03
@usfchick13, I hope you subscribed to this thread and get a notification because of this post, because I've just discovered something interesting that might be relevant to your problem.

I have a SATA docking station. This is a powered USB device into which you can plug bare SATA drives and use them (temporarily) as external USB drives. I've used it on a number of machines running Ubuntu, other Linux distros, Windows and/or MacOS. It works very well, I find it useful and so far it hadn't let me down. 

A little while ago I used it with one of my laptops - a Sony Vaio - to check something on a SATA drive. No response. Thinking that the HD may have failed, I tried it on my Ubuntu desktop and my MacMini. It worked in both. So I tried a second (working) SATA HD back on the Sony. Nothing. Just like you - not detected in fdisk or dmesg.

I guess I hadn't tried it on this Sony before. And, further, I guess there is some obscure conflict between Ubuntu, the Sony hardware and the USB docking station firmware.

All of which doesn't help you with that drive with that laptop, but your SimpleDrive may be OK after all when using another machine running Ubuntu. Just thought I'd let you know.

---

