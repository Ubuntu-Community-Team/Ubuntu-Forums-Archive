---
title: "Installing Ubuntu on ASUS EeeBox"
date: 2010-08-22
forum: Hardware
---

### Post by md328 on 2010-08-22
Hey guys,

Admittedly I'm pretty new to Ubuntu and Linux in general. I've been a windows user for as long as I can remember and have little experience on macs (never owned one). I just recently started getting into Linux/Ububtu when my roommate botched his computer up with another virus that pretty much did his windows os in. He was about to trash his computer all together until I on a whim told him about ubuntu. I've been reading about the incredible usability and versatility in the past couple years and I decided to finally give it a shot. Long story short: I installed ubuntu 10.04 on his lenovo successfully, started playing around with it before I gave it back to him (and it was a good week until that happened lol), and instantly fell in love with it.

So I decided that I want to have the same experience on my computer, which is a ASUS Eee Box nettop.

Below are some of my basic system specs:

Processor: Intel Atom CPU 330 1.60GHz
RAM: 2 GB (1.5 usable)
OS: Windows 7 32-bit

It also includes a nVIDIA Ion graphics card, wireless keyboard/mouse interface that came with the computer, DVD-RW Drive, 2 USB 2.0 ports, basic audio jacks, DVI port etc.

So I'm actually in the process of trying to install it on my computer now, but I'm having a problem: my computer won't boot from the Ubuntu liveCD. I triple checked to make sure that I'm not missing hitting a key to enter boot mode and I've tried some anyway (no luck). I tried other distros such as openSUSE 10.3 and PCLinuxOS and no luck with those either, although when I put the livecd in while in windows openSUSE installed some sort of bootloader screen as shown below.

[ATTACH]167262[/ATTACH]

You would that would have solved the problem but I can't move the selection choice at all so it stays stuck on windows and boots up automatically to that. I also installed an ubuntu boot loader from the live cd and ubuntu now shows up on that list below openSUSE, but I still can't highlight a different choice.

Wile I like to think of myself as fairly decent with computers, I'm pretty much stumped here. I really want to install Ubuntu on my system, but at the same time, I don't want to mess up my computer beyond repair because I will be needing it for school this year.

Any help would greatly be appreciated. Thanks.

-Mike

---

### Post by MooPi on 2010-08-22
Can you access the Bios and make certain that an external cdrom is boot first ? If not you may have to use another computer to create a usb startup drive. All you will need is a flash drive 2 gig or larger and the Ubuntu CD. Boot the other computer with the CD and go to Prefernces/Administrator/USB Creator. Actually I'm not certain on the path to the utility but I'm close. Once you have the drive ready set your system to boot from usb drive and install.

---

### Post by md328 on 2010-08-22
moopi,

I tried using a usb boot from UNetbootin on my computer. Still didn't work.  I'll try your method and see what that results in. Thanks.

---

### Post by sandyd on 2010-08-22
> **md328 said:**
> moopi,

I tried using a usb boot from UNetbootin on my computer. Still didn't work.  I'll try your method and see what that results in. Thanks.
many computers have a boot choice button at startup. F8, F12 or something like that

---

### Post by Paul T. on 2010-08-23
On my Asus eeepc netbook, pressing the 'esc' key on boot up brings up a menu whereby you can choose which device to boot from.

---

### Post by md328 on 2010-08-24
@ Carlee and Paul T: Thanks for the help, but the boot screen is completely non-responsive to anything I press. It's almost like it's just an image, and after that the computer loads directly into windows. Before I installed that opensuse boot screen, as soon as you turned it on it loaded straight to windows too, Hmm...seems like a certain company worked a deal with ASUS to keep the competition out on this one.

I think I'm just going to consider it a loss and keep windows 7. I honestly don't know enough about bios and booting in general to feel comfortable going any further.

I'll just wait until I get my high performance laptop and install ubuntu first thing.  Thanks for all the help guys.

---

### Post by cuongjj on 2010-08-24
@md328 - Keep at it man. I have a ASUS EEE PC as well and I recently downloaded and installed Ubuntu Netbook remix.  It runs so well and I highly recommend it to any netbook owners.  Just download it from the site [here]("http://www.ubuntu.com/netbook")

Then create a start-up disk using a USB via System > Administration > Start up disk creator.

Finally give it a shot and boot with your usb.  Make sure you enter your BIOS setup to allow the system to boot from a USB first, otherwise, it will just boot using your HDD.

---

### Post by Paqman on 2010-08-24
> **md328 said:**
> Hmm...seems like a certain company worked a deal with ASUS to keep the competition out on this one.


No, Ubuntu definitely works on the Eeebox, check Google and you'll find tons of people who've done it. However, it seems like the BIOS on some of them is a bit weird and makes booting from USB more complicated than it needs to be. 

Apparently some of the oder BIOSes have a whole raft of other fun issues. You might want to check the [Asus site]("http://support.asus.com/download/Download.aspx?SLanguage=en-us") for a BIOS update. It seems like on newer BIOSes you'll be hitting the F8 key to select a USB device during boot.

---

### Post by littleiffel on 2010-08-24
I installed Ubuntu on an EEEBox 1501 recently. My Box also refused to boot anything but Windows at first.

Needed to Push F2 at start-up, enter bios check that CD boots first. (In fact this is not sufficient)
So I push F8 (or F12, don't remember) to select the CD again for installation. It works better and faster with an USB key as well...at least for my EEEBox 1501?

In the bios there are options like boot booster, for me at least?! Try to deactivate them..

---

### Post by md328 on 2010-08-24
ok well, I tried pushing every key mentioned above at the system start-up and got nothing still. It won't give me an option to even go to a BIOS menu, so there's no way I can even configure the priority of the drives (unless you can do that somehow in windows?) My last option is to trying making a usb from the ubuntu boot-up on another computer like moopi mentioned. If that doesn't work, I have absolutely no clue what to do after that.

---

### Post by alanlu on 2010-08-25
start button + esc gets choice of boot devices, arrow down to usb, 'enter' et voila.

i will run off the usb for awhile, but i smell liberation fron the ms empire.

---

### Post by farsight on 2010-08-25
Hey there,

Glad to see you are moving towards the better of the two operating systems. My asus eee pc 1000, as with others mentioned above, work great with Ubuntu Netbook Remix. I suggest the best way is the make a bootable USB flash drive with 10.04 Ubuntu NBR on it. This can be done in your existing Windows system.

Here is one option, but I did not use this as I had access to the Ubuntu USB maker: [http://www.pendrivelinux.com/put-ubuntu-netbook-remix-10-04-on-flash-drive-in-windows/#more-4178]("http://www.pendrivelinux.com/put-ubuntu-netbook-remix-10-04-on-flash-drive-in-windows/#more-4178"). You might ask your friend to make the USB bootable for you, especially as they  have access to the Ubuntu software :)

I believe when I load my system, holding F2 brings up the BIOS, in which you may later need to activate the webcam and bluetooth hardware (bare this in mind). 

Holding ESC after powering on the system and a list should be shown, from which you choose your correctly installed USB flash image of Ubuntu. The following installation is relatively simple IF you want to remove windows 7 entirely! If not, you will need to make a partition on the hard drive for your Ubuntu system to be installed on.

Another note from my own experience, don't both (if your netbook is fairly low spec or low on storage space) making what they call a swap space. I've never needed it and I think others would agree.

Keep persevering :)

Farsight

---

### Post by formaldehyde_spoon on 2010-08-25
I may be on the wrong track here, but you are trying to get to the bios or boot device menu pretty much as soon as tou turn the machine on aren't you?  Not at the GRUB menu where you choose the OS...

I have 10.04 on my Eee 1005PE, although I can't remember whether I had any trouble installing it.  I think from memory only one of the two methods for creating a flash drive install works, and pretty sure I had to select the flash drive myself in the boot menu, it wouldn't boot from it automatically - like someone else here said.

---

### Post by MadsDyrmannLarsen on 2013-02-16
I know this is a pretty old thread, but as I have the same computer and have had the same problem where the keyboard was disabled during start-up, I just want to share a solution:

1. Press the power button
2. Immediately after press and hold the power button to force close the computer
3. Turn on the computer again. Quick boot should now be disabled for one start-up to make it run a ram-check, and the keyboard should also work.
4. Press F2 to enter BIOS.

Sometimes you have to repeat the procedure listed above a few times before it works.

---

