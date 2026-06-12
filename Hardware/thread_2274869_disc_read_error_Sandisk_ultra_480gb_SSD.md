---
title: "disc read error Sandisk ultra 480gb SSD"
date: 2015-04-22
forum: Hardware
---

### Post by salam-semaan on 2015-04-22
Hello I recently purchased a new sandisk ultra 2 480gb SSD and when it  arrived in the mail I went to install it. After the install it said that  there was a disc read error, I read online that that could be a  hardware failure so I sent it back and got another one.... Same thing  happened again, so this time I read more and it said it could be memory,  bios, bad cables, etc etc. here is the thing though I have ubuntu  running on this set up and it works fine. also when I go into ubuntu I  can see the other drive and all of the windows files. Any Ideas? as for  system specs I have an AMD  FX-8150, gigabyte ga-990fxa-ud3, 8gb of  kingston ddr3 hyperx Ram, 1tb Hybrid drive (currently ubuntu) a 1220  watt kingwin mach 1 power supply Thanks in advance.

---

### Post by dino99 on 2015-04-23
First take time to read the ssd doc you got, then also read some howto:
[http://karuppuswamy.com/wordpress/2014/06/26/everything-you-need-to-know-about-ssd-support-in-ubuntu-14-04/](http://karuppuswamy.com/wordpress/2014/06/26/everything-you-need-to-know-about-ssd-support-in-ubuntu-14-04/)
[http://bbb-solutions.blogspot.fr/2014/10/install-and-optimize-ssd-for-ubuntu-1404.html](http://bbb-solutions.blogspot.fr/2014/10/install-and-optimize-ssd-for-ubuntu-1404.html)

[http://kb.sandisk.com/app/answers/detail/a_id/8167](http://kb.sandisk.com/app/answers/detail/a_id/8167)
[http://downloads.sandisk.com/downloads/um/ssd-install-guide.pdf](http://downloads.sandisk.com/downloads/um/ssd-install-guide.pdf)

---

### Post by Bucky Ball on 2015-04-23
With the drive plugged try launching Gparted and see what that comes up with.

* Off-topic, but if you only have a hard drive, a motherboard, the RAM and a vid card hanging off that massive PSU, it is way overkill. You could save yourself some money and a few trees by going to half that size, or even less. Just mentioning it. ;)

---

### Post by salam-semaan on 2015-04-23
Hello Bucky Gparted shows NTFS 480gb file. Also I was just commenting on what I thought was relevant at the time and what was also currently connected. I also have 3 hard drives, liquid cooling, 6 fans, blu ray player and some other stuff that isn't really relevant to this issue. This power supply was from an old build I had, but you don't need to worry about excess power consumption, power supplies these days are switched so they only pull the power they need. Thanks :-)

---

### Post by salam-semaan on 2015-04-23
Hello Dino99 I installed the SSD exactly how it is shown in the documents, also the solutions shown are if the drive isn't seen and that isn't the issue here. The other documents are for installing ubuntu 14.04, but I am having problems with windows. :-(

---

### Post by Mark Phelps on 2015-04-23
> Hello Bucky Gparted shows NTFS 480gb file. You mean a single partition, right?

Also, if the entire drive is formatted NTFS, how are you having Ubuntu problems with that drive?

Note: I had similar problems with a Kingston SSD.  Started having filesystem corruption just after install.  This went on day after day.  Imaged off the SSD, grabbed a spare HDD, applied the image to that -- and ran for two weeks with no problems at all!  So, reimaged from the HDD, applied that to the SSD, rebooted using that -- and got filesystem corruptions immediately!

Was able to get the drive replaced through RMA with Kingston and haven't had problems since.

Sorry, looks like some of the SSDs are just "bad".

---

### Post by salam-semaan on 2015-04-24
So I figured out that the problem was a BIOS setting where I had to change the drive type to EFI. It got the windows to install and the ubuntu was working okay, but I wanted Grub to see the windows drive so I tried boot repair. It said that it was in legacy mode so I researched that and it said the only way to fix that was to reinstall ubuntu. I did that, but now I am getting an error that says /boot/grub/i386-pc-norma.mod followed by Grub rescue> I tried boot repair again, but the same error occurs. I tried reading online, but nothing I have done so far helps.

---

### Post by salam-semaan on 2015-04-24
Hello so just an update for everyone. I was able to use this link [http://askubuntu.com/questions/266429/error-file-grub-i386-pc-normal-mod-not-found](http://askubuntu.com/questions/266429/error-file-grub-i386-pc-normal-mod-not-found) to fix the issue, however now I have a new issue where it shows windows 7, but when I go to enter the drive it says invalid signature and then pushes me back to grub. Anyone know how to fix that? when I try to go into windows 7 drive it just gives me an underscore that keeps flashing in the top left as well. Thanks in advance, I will be trying this Link in the mean time and posting the results later [http://ubuntuforums.org/showthread.php?t=1264151](http://ubuntuforums.org/showthread.php?t=1264151)

---

### Post by salam-semaan on 2015-04-25
Not sure if anyone is interested, but no matter what I tried I couldn't get Ubuntu and windows 7 to work together in EFI mode. So my final solution is to just pick which Hard drive I want to load into on restart and go from there. Thanks for all the help :-)

---

