---
title: "SanDisk 32GB USB3.0 is very slow"
date: 2014-07-17
forum: Hardware
---

### Post by pavelexpertov on 2014-07-17
I know this seems a very random post, but I am in trouble with my usb stick. 2 days ago I received this memorystick as a present and then I used it to burn an dmg image of a mac osx (coz transmac expands the image to 17.5 gb and don't know why) and it seemed the memorystick was partitioned after the burn was complete. After, I could not use windows to format the stick, and I used gparted in order to wipe out partitions and create brand new partition with fat 32 format. Furthermore, after that, I have formatted the stick again in windows, because I noticed the formatter prefers to allocate 16kilobytes for a sector (or something else). 

Once, I was copying stuff (bunch of folders with docs worth up to 1.1gb) from ssd of my machine to usb stick using usb3 port, the speed was........... SLOW like hell. 7.5 mb per second. I swear on the box it says 100 mb/s speed.
Is there any way to solve the issue?
The link of the usb stick is [http://www.amazon.co.uk/SanDisk-SDCZ80-032G-G46-Extreme-Flash-Drive/dp/B00DZPUOU8/ref=sr_1_1?ie=UTF8&qid=1405635456&sr=8-1&keywords=sandisk+usb+32gb+usb3](http://www.amazon.co.uk/SanDisk-SDCZ80-032G-G46-Extreme-Flash-Drive/dp/B00DZPUOU8/ref=sr_1_1?ie=UTF8&qid=1405635456&sr=8-1&keywords=sandisk+usb+32gb+usb3)

---

### Post by sudodus on 2014-07-18
I have two pendrives of the same brand and model (but probably from different production batches). Both were fast, but one of them was damaged after some year of using it, and it is very slow in USB 3 ports, but has it's normal 'USB 2 speed' in USB 2 ports, 25-30 MB/s with big files.

If yours is bad after two days, I think something is wrong, either bad hardware or bad configuration. Or you are writing a very large number of extremely small files? Sandisk Extreme is better than most pendrives for such tasks, but it might be slower that you expect anyway.

-o-

If you wipe the first megabyte with [mkusb]("http://ubuntuforums.org/showthread.php?t=1958073") and then create a new partition table with ***gparted***, and then create partitions, it should help if bad configuration. Otherwise it is probably some very basic configuration, that normal mortal people can't tweak, or simply a hardware issue. And a hardware issue after 2 days means you should get the pendrive replaced with a new one.

See also these links 

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

Flash drive tests are described by C.S.Cameron in  [this link, post #5]("http://ubuntuforums.org/showthread.php?t=2130234"). [URL="http://usb.userbenchmark.com/"]

Link to USB 3.0 Flash Drive Speed Tests[/URL] [URL="http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085"]
Link to USB 2 and USB 3 speed tests for installers[/URL]

---

### Post by pavelexpertov on 2014-07-25
Thanks man, but I have to close this post as solved, because I haven't got enough time to test that, for now.

---

