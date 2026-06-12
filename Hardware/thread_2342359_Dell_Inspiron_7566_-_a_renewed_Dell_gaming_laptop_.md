---
title: "Dell Inspiron 7566 - a renewed Dell gaming laptop and linux compatibility"
date: 2016-11-05
forum: Hardware
---

### Post by soukup77 on 2016-11-05
Dell has released a new laptop at the end of October 2016 - model 7566 Inspiron - a successor of Inspiron 7559 - still marketted under the same name - Dell Inspiron 15 7000 gaming - 
[http://www.dell.com/sg/p/inspiron-15-7566-laptop/pd?oc=w51755724sgw10](http://www.dell.com/sg/p/inspiron-15-7566-laptop/pd?oc=w51755724sgw10)

The 7566 has got the same CPU, GPU and display as 7559 but comes with DDR4 RAM and SSD disk and slightly changed look, for the worse, I think ... :) Since it has been around for only a few days, there is virtually no information on how it works with linux, so I wonder if anyone has got any experience with this Dell 7566 Inspiron on linux. The 7559 had a few issues on linux, most of them solvable more or less, with the issue of cpu fans running even when cpu was cold persisting for quite a few users ...  

I guess I can only extrapolate whether it's going to have the same issues as the 7559 and potetially higher risks since it has not been tested.

---

### Post by haraldviste on 2016-12-01
Dell Inspiron 7559 is no longer available in my country so I just got the new model Dell Inspiron 7566 without thinking whether there would be new issues with Ubuntu on this model.

tldr;
I have added a second SSD (Samsung EVO 850 512GB) and installed Ubuntu 16.04 on this.
+ Ubuntu works fine
- The Toshiba 512GB SSD that came with the computer in the M.2 slot is not detected from Linux, so I could not install Ubuntu there, nor use it as an extra data disk (If I ever wanted I could use it to boot Windows 10 :( )
- Suspend (Power save) does not work (same as on 7559)
- The keyboard and touchpad is not optimal (is it just me?)
For the record: the model I have is a Dell Inspiron 7566 with 4K display, 16GB DDR4 RAM and 512 GB SSD (M.2), where I added a second SSD (2.5") in the empty bay.

The "tricks" were:
* I had to disable SecureBoot in BIOS
* I had to disconnect and reconnect the USB key when trying to boot the Ubuntu installer from this (*)
* I had to add a 2.5" SSD since linux was not able to detect the M.2 SSD that came with my PC
* Turn of "suspend" under System Settings -> Power

Here are the details:

1. Create a bootable Ubuntu 16.04 USB stick  (I used UNetBootin on my MBP: [https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx))
2. Connect the Ubuntu USB key
3. Power on the PC
4. Press F2 when DELL logo appears (POST / Power On Self Test) to enter BIOS
5. Disable SecureBoot
6. Exit
7. Press F12 when DELL logo appears
8. Select the Ubuntu USB key in the boot options
9. When the grub boot menu appears, Select "Install" (or "Test" if you just want to test Ubuntu without installing)
10. After ~5 seconds, disconnect and reconnect the USB key (*)
11. Wait for Ubuntu to boot and follow the install instructions (UEFI)
12. After install has finished, remove USB, reboot, press F12, select to boot from the newly installed Ubuntu disk
13. Open System settings -> Power
14. Select "Do nothing" under "When the lid is closed" (Power save/suspend does NOT work)

(*) Why did I disconnect/reconnect the USB key during Ubuntu USB key boot?
The Inspiron 7566 comes with 3 USB3 ports (no USB2-only ports). 
When I tried to boot/install Ubuntu 16.04 from USB memory stick (it has no optical drive), the booting of the Ubuntu 16.04 kernel hung after a few seconds.
Investigations of the kernel log (type 'e' in grub screen and remove "quiet splash" from the boot arguments) showed that the USB was the culprit (ehci/xhci messages, most likely related to changing USB speed between USB2 and USB3), so a quick disconnect/reconnect was required in order to make the USB key re-enumerate and become visible to linux.

I am really happy with the new PC and with running Ubuntu 16.04

* The keyboard and touchpad takes some getting used to (I come from a MacBookPro where the keyboard and touchpad are centered on the laptop, on the DELL it is shifted slightly to the left to give space for the numeric keyboard).
I experience a bit too many missed keypresses (in particular towards the left, e.g. 'A', 'S', etc), occasional double keypresses and annoying touchpad events.  I haven't yet figured out whether it's me, the DELL quality, or Ubuntu issues.  I expect the first :), will probably have to turn off "tap to click" for the touchpad.

* The lack of suspend feature does not annoy me.  I typically run on wall power, and after setting "Do nothing" when lid is closed, the battery is more than sufficient for dragging the PC between home and office.  For longer travels I simply turn the PC off -- booting from SSD is really fast

One more point...
The Samsung SSD I added has OPAL support (self encrypted disk/full disk encryption in hardware).  I have enabled this successfully using sedutil from [https://github.com/Drive-Trust-Alliance/sedutil](https://github.com/Drive-Trust-Alliance/sedutil).
It works nicely, although the DELL BIOS/firmware sometimes plays trick on me (and I have to edit/reorder the boot options).

---

### Post by soukup77 on 2016-12-09
Thanks for your reply and share of information,

I think I heard people having the suspend working on 7559. The cause might be the nouveau driver, the nVidia driver might remedy the issue. I myself have had on-and-off relationship with the suspend feature on my linux machines - I got it working on my old Fujitsu-Siemens laptop with NVidia card, it worked on my desktop PC with NVidia card and Debien Wheezy, when I switched to Debian Jessie, it ceased to work, but I am pretty confident I could get it working again if I was not lazy to do so :). 

I am mainly considered about the fan issue that plagued 7559 - once the CPU fans start spinning, they seem to spin forever and they don´t stop (as they do in Windows once the CPU has cooled down) unless the CPU cools down to a really low temperature, and while they seem to run on low speed and not really that loud they seem to lower the battery life by about 2 hours compared to Windows. People have had various levels of success in dealing with this issue, as described here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1602888](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1602888) and here [https://bugzilla.kernel.org/show_bug.cgi?id=153281](https://bugzilla.kernel.org/show_bug.cgi?id=153281) . This issue seems to target the models with core i7 more often than those with core i5 and may be harder to notice since the fans are really not that loud. So I am wondering whether your 7566 suffers from the same issue and also would like to know if you have core i7 or core i5 ... I know you said you don´t care about the battery life that much, but for me this issue would be a little pain in the ass ... 

Thanks, appreciate your help.

---

### Post by haraldviste on 2016-12-13
Thanks for the tip about nVidia drivers.  Unfortunately I haven't found the time to play with it yet.

My laptop is a quad core  i7-6700HQ. 
The fan behaves well for me / my use cases:

I typically use the laptop to build Android ROMs from source.
During the build process (`make -j 8`, takes about half an hour) the fan runs most of the time, but shortly after it has finished it goes back to normal (no fan noise).
I rarely run anything more than a couple of terminal windows (Android builds) and a FireFox browser (mail, web, slack, ...)  
If you have any suggestions for how I can stress-test the system more (e.g. video drivers), I'll be happy to try it out.

---

### Post by soukup77 on 2016-12-17
OK, I got it this Monday (even before your second answer :) I had been considering buying it for almost 2 months, so I have told myself: I had waited long enough ... :)
I think your workload is fine, for what I know, people have complained about the fans during normal workload, nothing extreme ... 

>> "after it has finished it goes back to normal (no fan noise)." - This looks good, although I think I´ve heard people saying that fans are almost silent on the lowest speed, so the question remains whether one can actually mishear them. So the definite answer would probably come from lm-sensors or similar fan speed measuring utility. Anyway, I won´t be bothering you with more questions as I can check that myself now, so thank you very much for all your help and shared experience. I will probably post the results of my testing, (I haven´t installed Linux yet :)), since I am the one that started this thread and other people may find it useful eventually.

By the way, you were right, the touchpad sucks really badly ... :) So over-sensitive ... Hopefully I will be able to reconfigure it somehow ... luckily I have a travel-size bluetooth mouse, so I won´t be using the touchpad that often ... Otherwise I love the most parts of the machine, I am really dissapointed by the absence of numlock and hdd activity lights. All my previous laptops had them - even cheaper ones, so I would expect a 1000$ machine to have them too ... 

On the other hand, I like the keyboard. It feels firm and robust. On my last laptop Fujistu-Siemens, the keyboard was bending down while typing, which I quite disliked  ...

---

### Post by soukup77 on 2017-01-20
OK, I finally managed to push myself to install Linux after about a month when I had been using the laptop with Windows (for games, mostly). I installed Debian testing (Stretch) that comes with Kernel 4.8.0. I have to say, the installation went smoother than I expected. After turning off Secure boot, everything worked perfectly. I didn´t even need to the trick with the USB stick you described. USB stick was present during the entire installation without problems. My Linux even detects both disks that come with the laptop. I decide to keep Windows where they were for the time being so I placed Linux on the second "classical" HDD. I got the wireless working nicely after installing proprietary Intel drivers. I haven´t tested the sleep function yet ... 

As for the fan issue I was most concerned about, so far it looks promising: at least according to lm-sensors - it shows CPU temperature betw 35 - 45 °C and CPU fan RMP as 0 during "normal" office work - typing, emails, browsing Internet. There is really soft, weak sound I can hear when I place my ear on the laptop but that could be disk spinning, so I unless lm-sensors shows wrong data, it looks like 7566 does not suffer from the fan issue his predecessor was plagued by ...

---

### Post by soukup77 on 2017-01-21
An update: I have got the sleep function also working out of the box with Debian Stretch using only the nouveau driver ... Amazing :)

---

### Post by soukup77 on 2017-01-27
An update: OK, I can now confirm for any potential new buyers, that Dell, model 7566 (with Skylake i7) does not have the fan issue described in this thread, unlike its predecessor, Dell 7559, under Linux - I'm running Debian testing (Stretch) with kernel 4.8.0.2 and nouveau driver. The fans behave correctly - they only kick in once the CPU temperature exceeds 60-65 C and stop after CPU cools down to 50 C. 

Install runs smoothly (with safe boot turned off) and everything else (including the sleep function) seems to run well too.

---

### Post by trylks on 2017-03-11
[FONT=arial]Hi all,

[/FONT][FONT=arial]I bought a Dell 7566 some time ago, and I have decided that now is time to install GNU/Linux, more precisely Ubuntu. I guess this is the best thread for this content, please let me know if otherwise.

[/FONT][FONT=arial]I hope that all the driver issues are solved by now, because if not, then that could be a problem.

[/FONT][FONT=arial]This is what I would like to do:

[/FONT]
[LIST=1]
[*][FONT=arial]Configure SSD to have two partitions: One for swap for Ubuntu, the other one for cache with intel smart response (which I guess only works on windows).[/FONT]
[*][FONT=arial]Configure the Nvidia GPU and Intel's integrated GPU so that the Linux desktop uses Intel's GPU and Nvidia GPU is saved for other stuff (mostly TensorFlow, I also plan to use it for gaming, but possibly only on Windows).
[/FONT]
[*][FONT=arial][/FONT]Configure everything to only generate as much heat as possible.
[*]Proper management of the battery would be fine.
[/LIST]

[FONT=arial]Here are the questions for now:
[/FONT]
[FONT=arial]
[LIST=1]
[*]Are driver issues solved/solvable? I would prefer not to have to change the SSD or HDD yet.
[*]Is there any way to check if some Ubuntu distribution works with those drives? Mounting them and checking the files inside should be enough, I guess.
[*]Is there any possibility to have Intel smart response working with the dual boot? If not feasible I will stick to the plan of partitioning the SSD, otherwise I may not.
[*]Can I use both GPUs at the same time? The integrated for the Desktop, the Nvidia GPU for Deep Learning and similar stuff. I don't know if there is anything preventing them from being both active at the same time.
[*]Maybe some flavor of Ubuntu is better than the others for the previous point, like Ubuntu Mate, Xubuntu, or something else,
[*]I would like the speed of the clock in both CPU and GPU to regulate depending on the use of them, (less power consumption on battery and less heat, so maybe it doesn't break too soon) any chance to get this working? (maybe it works by default, but I wouldn't like to be too optimistic and then disappointed)
[/LIST]
[/FONT]
[FONT=arial]If driver issues are not solved, then I will check the Linux subsystem for Windows to get more information about this, as it could be a suitable replacement. I would prefer dual boot, though. I assume it is a temporary thing and if they are not supported at this time, they will probably be supported soon.
[/FONT]
[FONT=arial]Sorry for the long post and numerous questions. Please don't feel pushed to answer all of them, every little helps.
[/FONT]
[FONT=arial]Thank you all for your help.[/FONT]

---

