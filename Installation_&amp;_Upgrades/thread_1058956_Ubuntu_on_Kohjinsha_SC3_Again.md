---
title: "Ubuntu on Kohjinsha SC3 Again"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by dothedog on 2009-02-03
All, I have been chasing this thing for a while, it appears there are a number of people trying to get Ubuntu on their SC3's. I just haven't found anyone that has succeeded. A quick search on these forums gives these threads:

[http://ubuntuforums.org/showthread.php?t=1034283&highlight=kohjinsha+sc3](http://ubuntuforums.org/showthread.php?t=1034283&highlight=kohjinsha+sc3)
no responses

[http://ubuntuforums.org/showthread.php?t=1034283&highlight=kohjinsha+sc3](http://ubuntuforums.org/showthread.php?t=1034283&highlight=kohjinsha+sc3)
again no responses

[http://ubuntuforums.org/showthread.php?t=883275&highlight=kohjinsha+sc3](http://ubuntuforums.org/showthread.php?t=883275&highlight=kohjinsha+sc3)
no resolution

I've also found some Japanese sites:
[http://www31.atwiki.jp/d4linux/pages/13.html#id_275847c0](http://www31.atwiki.jp/d4linux/pages/13.html#id_275847c0)
this is actually for a Sharp/Willcom D4 but has similar hardware

[http://whitesc3.blog7.fc2.com/blog-date-200808.html](http://whitesc3.blog7.fc2.com/blog-date-200808.html)
this guy uses grub for dos

[http://d.hatena.ne.jp/yamato-y/](http://d.hatena.ne.jp/yamato-y/)
This guy looks like he chainloads from vista bootloader

OK, so here is the issue, I am trying to install using 8.04.2 (actually a custom liveCD from [http://mockety.zapto.org/ubuntu-ja-8.04.1-ws016sh-20090118.iso](http://mockety.zapto.org/ubuntu-ja-8.04.1-ws016sh-20090118.iso) for the D4 it gives you the correct screen resolution 1024x600) This custom cd is in Japanese, but it also has a modified grub/menu.lst that includes:
irqpoll all_generic_ide
That last line is required for the live cd to "see" the hard disk.

So, I have tried a whole bunch of distros and they all have the same symptoms. Since, the SC3 doesn't have a DVD Drive, I am using unetbootin to load it on to a bootable USB Drive. With the irqpoll all_generic_ide line in grub/menu.lst the hard drive shows in the liveCD environment as /dev/sdaX. You can install from the liveCD. Ensure that you install grub at the end. However, on reboot, the grub boot menu shows up, select any item in the menu, add the irqpoll all_generic_ide to it, then click "b", and it immediately goes to a blank screen with a blinking cursor in the upper left had corner. The other thing I have tried is boot with the liveCD, then at the grub menu select boot from first hard drive. That gets it moving but it hangs on detecting the hard drives. For some reason it is picking up a sdb and an sdc when i only have a USB drive and a hard drive so you would think it should only have a sda and sdb?

This netbook has a Poulsbo Chipset SCH 500M Onboard Graphics and Atom proc. and an ATA hard drive. Which for some reason is not supported in Intrepid.

Also, when I tried the Ubuntu-mobile Menlow image, it overwrote my windows XP partitions, (should have looked a little closer before installing oops) so chainloading from windows won't work either...

Anyone with an SC3 that has had success please let me know how you did it!!!

Thanks,
DoTheDog

---

### Post by dstew on 2009-02-03
> However, on reboot, the grub boot menu shows up, select any item in the menu, and it immediately goes to a blank screen with a blinking cursor in the upper left had corner.At the grub menu, highlight a menu item, and instead of pressing 'return' press 'e' for edit. Select the kernel line, press 'e' again, and add the same kernel parameters to the end of the line that you used to get the Live CD to work (**irqpoll** and **all_generic_ide**). After editing the line, press 'return' to save it, the 'b' to boot. See if that makes a difference.

---

### Post by dothedog on 2009-02-03
thanks for the reply. Yeah I kind of mis-typed that. I have changed the grub/menu.lst on the hard drive to include the irqpoll all_generic_ide. It does the same thing. Just blank screen and blinking cursor in the upper left corner. 

I also just tried booting to the USB stick then selecting "Boot from first Hard disk", editing the kernel params and booting. It actually starts booting then ends with:
	Attached scsi generic sg2 type 0
	Done.
	Check root= bootarg cat /proc/modules ls /dev
	ALERT! Does not exist. Dropping to shell!

and I get an initramfs prompt...

Ok, I just got it to boot from the USB Stick "Boot from first Hard disk". the line originally looked like this:
/ubnkern initrd=/ubninit -
I added irqpoll all_generic_ide root=/dev/sda1 to it and it booted!

the whole line looks like this:
/ubnkern initrd=/ubninit irqpoll all_generic_ide root=/dev/sda1 -

Now I have to figure out how to boot this thing without the USB Stick...

---

### Post by dothedog on 2009-02-03
Ok, since I can boot to the installed OS with the USB stick, I tried making the same changes to boot/grub/menu.lst. So I changed the "kernel" record from root=UUID=lotsoflettersandnumbers to root=/dev/sda1.

Still no love. 

Any ideas?

---

### Post by dothedog on 2009-02-03
When I boot from the USB stick, even though it says boot from the first hard drive, it is actually booting the /ubnkern and /ubninit so I guess what it's not doing when booting from the hard drive with no USB is it can't find the kernel and initrd files?

Here is the record in the menu.lst
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-22-ws016sh ro irqpoll all_generic_ide root=/dev/sda1
initrd /boot/initrd.img-2.6.24-22-ws016sh

Those files do exist in the /boot directory.

Any ideas why grub wouldn't be able to find them?

---

### Post by dstew on 2009-02-03
Maybe the root statement is wrong (the grub root I mean, not the kernel root). You can try different root arguments like (hd1,0) to see. To do it more systematically, you can boot grub, and press 'c' to get a grub command line. On the command line you can do 'geometry (hd0)' to see which disk grub is calling (hd0), if you can figure that out from the disk geometry.

---

### Post by dothedog on 2009-02-03
dstew, 
Thanks for the reply. Ok, when in the "boot from first hard disk" environment the 
grub> geometry (hd0)
returns
what looks like the correct disk 2 ext3 partitions and 1 swap and it says that it is /dev/sda which is what I thought.

When booting and at the grub menu, I enter "c" and type geometry (hd0)
it returns the correct disk, all 3 partitions but calls it LBA.

DoTheDog

---

### Post by dstew on 2009-02-03
The LBA might be a clue. It means your BIOS is set to address the disk in the LBA fashion. If the BIOS is working correctly, grub should be able to do LBA. However, from your description of your problems with accessing the disk using the Linux kernel (you needed to use all_generic_ide, correct?) it might be that the BIOS has some non-standard activity in LBA mode that is messing up grub (and the Linux kernel too).

If you can, go into the BIOS and see if you can change the disk addressing system to CHS or some other "legacy" mode.

---

### Post by dothedog on 2009-02-03
dstew,
The bios on this thing is super simple. You can barely change the time in it ;) No IDE settings that I could find. I think the problem is the Poulsbo/Menlow chipset is too new. It drives the video, IDE, etc. I am not sure why you need the all_generic_ide. That is like an old IDE driver right?

Any other ideas?

DoTheDog

---

### Post by dothedog on 2009-02-04
Any SC3 owners out there that have a working Ubuntu installation?

---

### Post by dstew on 2009-02-04
I think you are right, the chipset probably has some kind of non-standard behavior with respect to the IDE interface that makes it behave oddly with Linux software. The "all_generic_ide" parameter tells the linux kernel to use a simple IDE interface. It's kind of like using the plain VGA of a graphics adapter -- it usually works, but is not fancy, and may be slower.

IDE interface trouble might also be at the root of the failure of the grub setup command. If you use grub from a Live CD, it is running the **grub shell**, which is a program that runs under the Linux kernel on the Live CD. It might be interesting to try to do the grub setup from a **grub native boot**, which is grub running by itself, with no Linux system at all. You can do this by making a [bootable grub floppy]("http://www.gnu.org/software/grub/manual/grub.html#Creating-a-GRUB-boot-floppy") or [CD]("http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD_002dROM.html"). Since this is such a difficult problem, it might be worth a try to use native grub. Who knows, you might actually solve the problem for all mankind!

---

### Post by ultimatedevr on 2009-02-04
I have this same problem with my Kohjinsha SC3; I've found that by installing Opensuse it boots up properly; however, opensuse doesn't have support for the psb video driver (then again it barely works on ubuntu...). So you might want to install opensuse, have it setup it's /boot, then install ubuntu over it (keeping the /boot intact from the opensuse install), and try booting into ubuntu from opensuse's grub install. If that doesn't work you could try booting into ubuntu using opensuse's kernel.

---

### Post by dothedog on 2009-02-04
ultimatedevr,
Thanks for the reply. Which version of OpenSuSE are you using that worked? I might give that a try. I haven't used SuSE in years... might be worth a shot.

dstew,
I tried something completely different. I installed lilo and gave that a shot. I think I am getting a little further. I get to the menu, select the kernel, then I get:

Loading 2.6.24-22-d4...........................................
...............................................................
..........

then it hangs. Dang, I thought it was working...

DoTheDog

---

### Post by ultimatedevr on 2009-02-04
I used opensuse 11, but 11.1 should work too.

---

### Post by dothedog on 2009-02-05
ultimatedevr,
Did you have to do anything special? I just tried openSuSE 11.1 and it didn't get any farther...I get a rebootexception trying to mount the media (I'm using a usb drive). I tried the initrdud someone built but that didn't seem to work either. 

Did you put "irqpoll all_generic_ide" in the kernel line in grub? Or "ide-core ide-generic" in the initramfs? Also, do your partitions show up as /dev/sda or /dev/hda?

DoTheDog

---

### Post by ultimatedevr on 2009-02-05
I probably should've mentioned this...I had to use yast to configure the initrd image to contain the ide_generic module; follow the directions [URL=I probably should've mentioned this...I had to use yast to configure the initrd image to contain the ide_generic module; follow the directions here (http://en.opensuse.org/Kernel_module_configuration#YaST:_Loading_kernel_modules_at_boot)

---

### Post by dothedog on 2009-02-05
ultimatedevr,
Thanks for the reply, it does look like openSuSE 11.1 goes right on. I am just finishing the install, there was some goofiness trying to partition the disk, the liveCD would mount /dev/sda1 and it wouldn't format... I just opened a terminal and umount 'd everything then it worked. I didn't have to do an ide-generic or all_generic_ide or anything like that. It looks like it picked up a pata_sch module from libata, that I don't think Ubuntu grabs.

Now to see if I can get the LAN and wlan working on openSuSE. ;)

---

### Post by dothedog on 2009-02-09
So, I finally have a "working" ubuntu Hardy install on my Kohji SC3. It was a pretty nasty hack but it works for now. What I did is install Hardy using Unetbootin. Then on a separate partition installed openSuSE 11.1. The openSuSE bootloader picked up that I had Hardy on another partition. Now when I boot the SC3, the openSuSE grub menu pops up, I select Ubuntu, it then goes to the Ubuntu grub menu, I select the first record and it boots. 

Not sure what the problem is with Hardy that it can't boot straight up (even with the irqpoll all_generic_ide in the grub kernel line). The other posts that I have seen, are chainloading from Windows.

If anyone can figure out why Hardy won't boot on this menlow/poulsbo chipset, please let me know. 

thanks,
DoTheDog

---

### Post by ultimatedevr on 2009-02-11
I've been having a weird problem lately; my Kohjinsha will only boot when it's plugged into the wall; it won't work otherwise (it hangs with the blinking cursor, just like when using Ubuntu's grub loader instead of a live cd or the openSUSE grub loader). Is this happening to you?

---

### Post by Sangdrax on 2009-03-08
Hello, I am one of the first to try to install the Ubuntu in the Kohjinsha SC3. 

In the end I resigned and tried Debian, net-isntallation. In the beginning, before the install I had to load the module "ide_generic" to detect the HD. 

After the install, it didn't boot, and someone suggested me to change the kernel to install. By default, it installs a Kernel-686 compatible. In the personalyzed environmnet of net-install i choose Kernel-486 and the computer booted without any problems. Maybe with Ubuntu can we repeat the trick ? can we choose the kernel to install ? (I remember that during the package installation of the Live CD, it installed the i686 kernel). 

Any someone should try that. 


------

[http://web.mac.com/jordi.calveras](http://web.mac.com/jordi.calveras)

---

### Post by LitE2 on 2009-03-10
Hi,
I have the same problem on my Kohjinsha SX3 (using the same chipset).
However, I can load the ubuntu 8.10 using the liveCD->boot from harddisk.

I wanna try changing the kernel to see if it works or not.
But which version of kernel I have to seek for i486?
2.6.XX ?

Thanks~

---

### Post by abaldas47 on 2009-03-10
Hi there,
Try Mint Linux. It installs well. Problems: 
1) Wifi not supported but vt6656 site has the source code which compiles easily and then the wifi is recognized and works well.
2) The screen can only work at 800x600 resolution, its workable but not ideal. No solution as yet.
3) The touchscreen works after installation but not accurate. Again the penmount site has the source code for ubuntu 8.10 which compiles easily and works well,
Good luck,
Aris:D

---

### Post by hanzenegger on 2009-04-21
I finally managed to get my SC3 booting Ubuntu directly using extlinux instead of grub. I used [these]("http://www.vyvy.org/main/en/node/181") instructions for the extlinux part. (Thanks vyvy!) 

This is how I did it:

1.) Install Ubuntu as normal. I used Jaunty beta, but I am now reinstalling Hardy due to the graphics driver issue. 

2.) Boot into your newly installed system. To get my install to boot, I used the 8.10 Desktop CD from an external drive and selected the option "boot from first hard drive". For some reason, the SC3 then boots.

3.) Install the syslinux package, which includes extlinux:
```
sudo aptitude install syslinux
```

4.) Make a directory for extlinux in the boot diretory:
```
sudo mkdir /boot/extlinux/
```

5.) Install extlinux in the directory you just made:
```
sudo extlinux -i /boot/extlinux/
```

6.) Change the MBR to start up extlinux instead of grub:
Install the Master Boot Record
```
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sd***X***
```
Please replace the ***X*** with the correct letter for your /boot partition

7.) Make a  /boot/extlinux/extlinux.conf configuration file based on the grub menu.lst file using the following "translation":
_grub:_
title title
kernel kernel_file kernel_options
initrd initrd_file

_extlinux:_
LABEL title_without_whitespaces
  KERNEL kernel_file
  APPEND initrd=initrd_file kernel_options
 
8.) Your SC3 should now be able to boot! :-)

Note 1: I had a little trouble with the correct path to the kernel and initrd. I have a separate partition for /boot, and it seems that the path extlinux.conf expects is relative to the extlinux directory, i.e. ../kernel_file in my case

Note 2: Your extlinux.conf file will not be automatically updated when you update the kernel, so you will have to update the configuration manually.

---

### Post by Brunello on 2009-04-30
Hi to all,

I have just buy a kohjinsha SC3, I'm waiting it from Korea,
and I'm really excited to receive it.

The first operation that I will do will be install Ubuntu on it.

But I read that there are many problems.

The first problem is the boot, but [hanzenegger]("http://ubuntuforums.org/member.php?u=103020") found a good procedure to resolve this problem.

I'd like understand which are the other problems. I read something goes wrong about the ethernet device. and some about touch screen. Others?

I'm not an expert, but I love Ubuntu and I'd like it run correclty on this good netbook.
Did you try other linux ditributions, that haven't broblems??
Which is the best result?

My dream is to have linux like main operating system and a virtual machine with an image with windows. But if there are so many driver problems, it will be really difficult.

What do you think?

Thank you to all.
(excuse me for orrible eglish)

Bruno

---

### Post by allankyoto on 2009-05-07
I want to do the same thing Bruno but honestly you're better off installing the new beta of Windows 7 until these driver issues get ironed out. I can't get wi-fi working plus the graphics driver is broken so we only have vesa 800x600. IMHO its not even worth the space to dual boot at this current point. 

I am  keeping an eye on [http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/) for new builds and testing them by making bootable USB sticks. When I get one that detects my wi-fi and the correct screen resolution I'll be getting rid of Windows. :)

Oh and I tested the May 6th build at the daily live link above and still no wi-fi or proper screen resolution

---

### Post by Brunello on 2009-05-08
Hi allankyoto,

 finally SC3 arrived yesterday, it is really small, I like it :)
I tried boot it with USB pen with Ubuntu 8.10 desktop and 9.04 desktop. 
But in 8.10 and 9.04 I can't find Ethernet device.
If I write "ipconfig" I see only loopback device :(
I tried also Backtrack 4 beta, but the result was the same.

So I can't see 

- Ethernet 
- Wireless device
- Display goes only in 800X600 mode

Did you see this link? :
[http://forums.opensuse.org/hardware/laptop/407080-help-kohjinsha-sc3-wireless-vt6656.html#post1939886](http://forums.opensuse.org/hardware/laptop/407080-help-kohjinsha-sc3-wireless-vt6656.html#post1939886)

Now I'm downloading ubuntu mobile that I read in your post. I'd like try if Ethernet run correctly.

I don't like Vista, and I think probably also Windows 7 is too recent, I prefer install WinXP, that probably works more fast.

Ciao :)
Bruno

---

### Post by allankyoto on 2009-05-09
@Brunello

Mine came with WinXP which works fine. I upgraded to 2gb of ram because I thought I might want to keep a few apps open in order to reduce load times. It didn't really make a big difference. I switched to Windows 7 and everything seems much more responsive. I'm not sure what MS has changed but it seems to work better to me. 

Ideally I want Ubuntu or some Linux on this thing but right now its just not possible without severely limiting the functionality of the device. 

I was able to detect ethernet using the latest Ubuntu Netbook Remix build but since I need the wireless and I need a the native screen resolution I just can't switch yet. 

Keep me posted if you find any workarounds

---

### Post by Brunello on 2009-05-11
Hi,

@allankyoto

I tried Ubuntu Netbook Remix on a USB pen, it find my ethernet eth0 :)
Thank you
Now I'm trying to downgrate Vista to XP, then I want set dual boot with XP and Ubuntu.
Then there are two problems: Wlan and Video Drivers.
I'd like try use Wireless XP driver on Ubuntu, what do you think about it?

Bye,
Bruno

---

### Post by 5to5thirty on 2009-05-12
Hi, this is in regard to the original installation problem, blank screen, blinking cursor.

Currently on my sc3, I have 1 instance of ubuntu hardy 8.02.4, 2 instances of ubuntu jaunty 9.04, besides Vista and its recovery partition. Yes all are being booted from grub. I should mention here that alongside grub you will need syslinux (not extlinux), for a small but vital part, and a very small fat32 primary partition to hold syslinux.

In a nutshell, here's how I did it. Grub chainloads syslinux and syslinux in turn chainloads grub back again. The syslinux chainloading grub is exactly what happens in the livecd. The syslinux boot loader somehow fixes grub's problem with loading the kernel and initrd image and so you can boot ubuntu from the grub boot menu when it pops up the second time.

Please note I use System Rescue CD v1.1.6 on USB for steps 1,2,3 and 4. You may use ubuntu live usb. For using Ubuntu 8.04.2, you need to specify the kernel parameter generic.all_generic_ide=1 for the hard disk to be detected. For the live usb press F6 and add the parameter to the bootstring. 8.04.2 live doesn't have syslinux. 8.10 and 9.04 have.

1. Firstly, backup all your data. Best way in our case is to use your favourite complete disk imager or my personal favourite, dd.

```
dd if=/dev/sda of=/mnt/myexternaldrive/sc3.img 
```You can pipe the dd output to gzip to get a compressed and somewhat smaller image. Please note, you run dd at your own risk, exchange the if= and of= parameters or a typo in them and your data is burnt toast. If you have not used dd before, do lots of googleing before you do.

Bravehearts can skip this step. The obvious reason for this step is to backup you precious data. The reason for dd or alike is because the recovery partition is usually launched through hidden vendor code embedded in the sectors after the MBR. If you so much as move these partitions or the empty space before them with a partition editor/manager the vendor code is lost or corrupted. Now if you use partimage or similar software to backup the individual partitions the embedded code is not backed up since it is not part of any partition and eventually when grub is installed it will overwrite whole or part of it. You may decide that you don't require whole disk imaging and individual partition backup is enough. The choice is yours.

Note: To access the recovery partition after ubuntu installation, you will either have to put its entry in the grub boot menu or winxp/vista boot menu (boot.ini/BCD)

2. Create a small fat32 partition (a few MB's, or more if you round to cylinders in gparted) for syslinux. Make sure it is a primary partition, which means that if you keep your winxp/vista and recovery partitions,then ubuntu will have to be on a logical partition.

Note: If you want to save a primary partition you can put syslinux on a logical partition (not recommended). Easier said than done, for as soon as you do it you realize that grub simply [cannot chainload to a boot loader in a logical partition]("http://bugs.gentoo.org/show_bug.cgi?id=230905#c0"). So you end up compiling grub + [patch]("http://bugs.gentoo.org/attachment.cgi?id=159669&action=diff") from source. And then you realize that successful compilation doesn't mean it runs. You end up with a [segmentation fault]("http://ubuntuforums.org/showthread.php?t=426399"). When you finally [work around]("http://ubuntuforums.org/showthread.php?p=7144711") the seg faults you realize that now grub can only see the kernel and initrd images in its partition. Seriously, only an option if you want to get your hands dirty and have atleast a couple of days or more to waste. This is the down side.

However its entirely due to it that today I have a 8 Gig super system rescue usb with 6 different system tool cds and 7 different OS live cds all booting from grub chainloading to their syslinux bootloaders in their [logical partitions]("http://forums.gentoo.org/viewtopic-t-648314-postdays-0-postorder-asc-start-25.html?sid=26420556b0680f117dc986a270363d8c"). This is the upside. Never regretted it.

3. If /dev/sda3 is your fat32 partition for syslinux, then execute :

```
syslinux /dev/sda3    (on system rescue cd)
sync
```or
```
sudo syslinux /dev/sda3    (on ubuntu)
sync
```4. Then mount the fat32 partition and create the file syslinux.cfg with the following contents

```
default disk1
#timeout 300
#prompt 0
label disk1
  localboot 0x80
#label disk2
#  localboot 0x81
#label floppy
#  localboot 0x00
#label nextboot
#  localboot -1
```The lines with # is ignored. This code tells syslinux to boot from hard disk just like it happens in the live cd. now unmount the syslinux partition.

5. Install ubuntu as usual with grub

6. Edit grub menu.lst and add the following under other operating systems

```
title        Syslinux
rootnoverify    (hd0,2)
chainloader    +1
```assuming your syslinux partition is (hd0,2). also ensure hiddenmenu is disabled and timeout is 10 seconds or more

For Ubuntu 8.04.2, you need to specify the kernel parameter generic.all_generic_ide=1 for the hard disk to be detected. For menu.lst add as below

```
title        Ubuntu 8.04, kernel 2.6.24-23-generic
uuid        592873fd-a453-48c2-a538-83787c0ecadb
kernel        /boot/vmlinuz-2.6.24-23-generic generic.all_generic_ide=1 root=UUID=592873fd-a453-48c2-a538-83787c0ecadb ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet
```Please note that the uuid will be different for your partition.

7. Thats it, we are done. Now reboot and grub will show the boot menu. Select syslinux option. The syslinux loader will execute and reload grub from hard disk just like the live cd. Depending on your version of syslinux when it executes it might show a boot: prompt or not. If shown simply press return/enter. Now from the newly loaded grub boot menu select the ubuntu option. It should boot without problem.

I feel this grub syslinux recursive chainloading approach is fairly generic and should also work with other non-ubuntu distributions on sc3, though never tried with other distros myself. Compared to this, adding drivers to the kernel and recompiling the kernel which i originally intended to do now seems a huge waste of time and effort and quite frequent to keep up with new kernel releases.

If someone succeeds using this approach with other distro's please let me know.

I think the original problem blank sceen, blinking cursor is most probably due to a buggy bios as many have speculated. Has anyone tried with the [new bios]("http://www.umpcportal.com/modules/newbb/viewtopic.php?topic_id=4821&forum=19")?

Ofcourse we could all be wrong and the problem might be with grub legacy which as we all know is badly unmaintained.

Hope this was helpful.
cheers

---

### Post by stevetsai on 2009-05-15
The new bios does not fix the problem. Does anyone try to rebuild grub?

---

### Post by damianmarti on 2009-05-17
I made it works with grub2!!! :-)

I'm working in the wireless, video, gps and tv turner. Anyone has made these worked?

---

### Post by damianmarti on 2009-05-17
This [http://tinkabit.wordpress.com/2009/05/15/soporte-en-debianubuntu-para-wifi-via-vt6656-point-of-view-mobii-10/](http://tinkabit.wordpress.com/2009/05/15/soporte-en-debianubuntu-para-wifi-via-vt6656-point-of-view-mobii-10/) worked for the wireless!

---

### Post by dothedog on 2009-05-18
5to5thirty, that works great! Thanks for posting that. I originally had to install OpenSuSE 11.1 and then chainload Ubuntu from that. I just followed your instructions and now have Jaunty working. Does anyone know if this is an Ubuntu bug or a Grub bug? It would be great if the Ubuntu install on the SC3 would "Just Work(tm)" . ;)

---

### Post by dothedog on 2009-05-19
damianmarti, video works on 9.04 lpia if you add the ppa for ubuntu-mobile. Good instructions here: [http://www.tipsandthoughts.com/?p=4](http://www.tipsandthoughts.com/?p=4)
However, it only works for 2D. Apparently there is not a 3D driver in Jaunty yet...

Also, I am trying to get mplayer-vaapi working and have not had much luck. I have compiled the vaapi enabled mplayer but it won't play video (audio works) saying something like bad video codec or something. I can get the actual error, if someone can help.

---

### Post by Brunello on 2009-06-04
Hi to all!!

With Ubuntu 9.04 for the boot I used Syslinux, wifi works, ethernet works.
Video goes to 800x600 :(

Do you run Video driver in 1024x600 resolution on Ubuntu??

Thanks :)

---

### Post by dothedog on 2009-06-09
Brunello, You have to enable the PPA, then apt-get install the xserver-xorg-video-psb. There is a good tutorial here: [http://www.tipsandthoughts.com/?p=4](http://www.tipsandthoughts.com/?p=4)

---

### Post by Brunello on 2009-06-10
WOW!!!
Ubuntu in 1024x600 is really wonderful!!!
Thanks a lot!!!! :)

Do you try to use external monitor with linux? ...and dual monitor!

Bruno

---

### Post by PreviousN on 2009-06-11
Hi everyone, sorry to jump in at the end of the thread. I just recently purchased an SC3 for my mom. I have an SH8, which works pretty **much without a flaw** with ubuntu. I've had some trouble outputting to an external display and had to mess around with wireless, but I've had it working months now no problems.

Apparently, according to this thread, the SC3 doesn't work. Damn. I did notice that damianmarti wrote:

> **damianmarti said:**
> I made it works with grub2!!! :-)

I'm working in the wireless, video, gps and tv turner. Anyone has made these worked?

How do you install it/configure it with grub2? You know after you're done installing and it prompts if you want to restart, is that when you somehow magically use grub2? 

I also read in this thread that linuxmint works. Is that still the case? Mint is close enough to ubuntu that I would prefer that to Suse. 

*In fact, I would almost prefer to install linux mint vs. ubuntu, since this is for my mom and mint has a lot of tweaks already installed (video codecs, for one). So, if anyone else has had luck with mint please say so and I'll just go that route to begin with...*

Finally, responding to damianmarti: If the wireless is the same as the SH8, then yes. One can get wireless to work without flaw. Re: the gps/tv tuner... Well, my sh8 doesn't have a gps so I don't know. The tv tuner is useless outside of Japan/Korea, since it is 1seg only. So even if you could get it to work, there would be no stations to tune into, assuming you live **anywhere** else (including europe, etc.). I think the only exception besides korea/japan is brazil. 

Check this out for more info: [http://en.wikipedia.org/wiki/1seg](http://en.wikipedia.org/wiki/1seg)

I'm looking to get the laptop, install and configure ubuntu for my mom, then kind of hand it off and let her 'have at it'. This was her idea, as she's interested in ubuntu. I just don't want to hand off something that won't even boot.

---

### Post by Brunello on 2009-06-11
Hi,

 for boot problem I read [hanzenegger]("http://ubuntuforums.org/member.php?u=103020") howto, you can find in this thread (page 3).
I solved this problem with extlinux, and now it works very well, 
I have also customized the boot screen (dual boot XP + Ubuntu) :D.

Does someone try external monitor configuration and/or dual monitor?

Thank you :)

---

### Post by PreviousN on 2009-06-11
Hey, thanks for getting back to me, Brunello. A quick question: could you please post your extlinux config file? Since it's the same model computer (SC3) it should look similar. Don't worry, I'll be careful and look it over and edit it for my laptop. It would be nice to have a base, though.

...It sounds like the steps are rather time consuming/complicated. BTW: does anyone know how to install windows xp via usb? The OS on my SC3 will be Japanese only. I've got a legit license and a disk for XP (english), but no DVD/CD drive!

Just a little note:
> **5to5thirty said:**
> 
1. Firstly, backup all your data. Best way in our case is to use your favourite complete disk imager or my personal favourite, dd.

```
dd if=/dev/sda of=/mnt/myexternaldrive/sc3.img 
```You can pipe the dd output to gzip to get a compressed and somewhat smaller image. Please note, you run dd at your own risk, exchange the if= and of= parameters or a typo in them and your data is burnt toast. If you have not used dd before, do lots of googleing before you do.


When you use dd to make a 1:1 copy of the disk, you will actually make an image including empty data. Meaning that if you only have ~4gigs used, and the hdd is 60GB, then the resulting image will still be 60GB. You're right about using gzip, but from what I understand this will still result in a file several times larger than the original data. 

I've read about clonezilla. That may be something to look into. Do you have any other suggestions about ways to backup only the restore partition and the windows partition? I can backup the MBR and put them in the same location... saving time and not having to back up the ubuntu partition.

Relatedly, I don't have an external disk. Did you get the ethernet to work? I know you can do this (use dd) over ethernet... but if the SC3 does not have working ethernet, then it will be impossible for me to backup the data without having to buy an external hdd.

---

### Post by Brunello on 2009-06-11
Hi,

@PreviousN
I installed winXP in dual boot with CDROM external, because I had it. But with USB pen or ethernet I haven't idea, I'm sorry.

This is my extlinux.conf:

DEFAULT /usr/lib/syslinux/vesamenu.c32
PROMPT 0
TIMEOUT 600

MENU TITLE Panic List Partitions

LABEL Ubuntu
 MENU LABEL ^Ubuntu 9.04, kernel 2.6.28-11-generic
 KERNEL /boot/vmlinuz-2.6.28-11-generic
 APPEND initrd=/boot/initrd.img-2.6.28-11-generic root=UUID=a8b46be5-cd28-4c57-b010-d92fbab181ec ro quiet splash

LABEL Ubuntu_Recovery
 MENU LABEL Ubuntu 9.04, kernel 2.6.28-11-generic (^recovery mode)
 KERNEL /boot/vmlinuz-2.6.28-11-generic
 APPEND initrd=/boot/initrd.img-2.6.28-11-generic root=UUID=a8b46be5-cd28-4c57-b010-d92fbab181ec ro  single


LABEL Ubuntu_memtest
 MENU LABEL Ubuntu 9.04, ^memtest86+
 KERNEL /boot/memtest86+.bin
 

LABEL Win
 MENU LABEL ^Windows XP
 KERNEL /usr/lib/syslinux/chain.c32
 APPEND hd0 1

---

### Post by PreviousN on 2009-06-11
I was going to "give thanks" to the people in this thread, but apparently ubuntu forums removed the "thanks" feature. So, thanks **Brunello**, and the guys on the third page... (5to5thirty & hanzenegger).

---

### Post by dothedog on 2009-06-12
Brunello, I have gotten the SC3 to output to a projector with dual monitor setup. But I haven't really played with it much. If I recall the FN keys work.

---

### Post by PreviousN on 2009-06-12
For documentation purposes ;-), how did you get it to output to a projector?

---

### Post by dothedog on 2009-06-14
The external monitor, projector in my case, Just Worked(tm). It did come up in mirror mode at first. in order to get an extended desktop, I had to open System->Preferences->Display and play around with it a bit. Hit detect displays, move the two displays around a little (in the display configuration dialog, the two may be overlapping, so just grab the top one and move it to the side), fix the resolutions, hit apply a couple of times, log-off/on a couple of times. I couldn't get full resolution on the projector (1920x1080) but 1365x768 works fine.

---

### Post by Brunello on 2009-06-15
Hi all!
Thank you guys!!! :D
Mirror screen & extended desktop work fine!!! :D
I'm an happy man!!!
Byeeee:popcorn:

---

### Post by PreviousN on 2009-06-15
So, let me put this in one post...

[LIST]
[*]Getting the SC3 to Boot: Use grub2 and instructions off of page 3
[*]Wireless: compile the wireless driver from source, instructions in this thread
[*]Correct resolution: You have to enable a PPA, then apt-get install the xserver-xorg-video-psb. There is a good tutorial here: [http://www.tipsandthoughts.com/?p=4](http://www.tipsandthoughts.com/?p=4)
[*]Using an external display: use the default display's tool in preferences.
[*]Touchscreen calibration: install the Penmount driver
[/LIST]

Did I miss anything? Thanks to everyone in this thread!
By the way, did anyone get suspend/hibernate to work?

---

### Post by PreviousN on 2009-06-20
Hi All again,

I want to keep this thread alive, for all of us SC3 owners out there with trouble and wanting everything to work perfectly. I currenty have it booting, at full resolution, and a perfectly calibrated touchscreen.

I want to fix suspend/hibernate and get 3d working (so I can use the dynamic zoom of compiz, the screen is small!).

Does anyone else have a problem of when they close their SC3 lid the screen goes black and when they reopen it (the screen) won't turn on again? I think this all is related to each other. 

I think the 3d issue is related to the difficulty with suspend and hibernate. I've read that the dell mini uses similar screen drivers. Some seem to have enabled desktop effects on a dell mini (I've read in this forum) by downgrading the kernel. 

Any ideas?

---

### Post by 5to5thirty on 2009-08-01
Not sure if everyone knows that grub2 is the solution to the original booting problem - blank screen, blinking cursor.

Its been hinted to in a number of posts, though never detailed upon. So thought i'd fill in the gap and clearup a few other queries while am at it (yeah i'm late, but what can i say, i'm too lazy). As such the grub<->syslinux chainloading hack mentioned in my earlier post (on pg3) is no longer required nor recommended. After that post, I got busy with some other stuff (like setting up the winxp installer on usb) so checking out grub2 got delayed. Always knew that patching grub legacy was useless 'cos its going to be throwaway once grub2 replaces it anyway. And that, it seems is the truth, now that its declared 9.10 is going to have grub2 (though only for new installs - not upgrades)

Now, this grub2 upgrade procedure is pretty straightforward, but guess what, sh't happens when you don't expect it. Since its a boot loader and you are going to modify the MBR, its extremely risky. And if you are one of those poor souls for whom the procedure doesn't work for god-knows-what-reason, you WILL end up with an unbootable system. Since grub2 is not yet off the mint, information to fix problems with it can be hard to come by (I will not be on support - too lazy and too ignorant you see). Don't blame me then for hoodwinking you into this procedure ;) So, do that backup NOW. Also please have a Ubuntu live USB with you before you start.

1. Install grub2 from synaptic. This will also uninstall grub legacy (uninstall, does not remove grub legacy from MBR or grub files from /boot/grub)

2. On the 'Configuring grub-pc' screen ensure 'Chainload from menu.lst' is selected and click 'Forward'. Now it is important that we do not reboot the machine until step 3 and 4 is completed. Please ignore the urge to reboot and test the chainloading.

3. Backup all your files in /boot/grub into your home folder. Now, upgrade to grub2. This will remove grub legacy files from /boot/grub

```
sudo upgrade-from-grub-legacy
```4. Make sure that of the 100 or so new files in /boot/grub, one of them is grub.cfg If not

```
sudo update-grub
```The file should now be there. Check its contents as well.

5. Reboot and pray :<

You should now see the grub 2 menu and automatically boot into ubuntu. Thatz it, we are done, walk in the park, wasn't it.

The config files for grub 2 are quite different from grub legacy and are in different locations. The ubuntu [grub2]("https://wiki.ubuntu.com/Grub2") wiki page is very informative and provides a lot of troubleshooting tips as well. No graphical mode yet, but coming soon i presume, though [splash images]("http://blogs.koolwal.net/2008/12/16/how-to-grub2-and-grub-pc-installing-splash-images/") are supported as in [grub legacy]("http://blogs.koolwal.net/2008/12/12/how-to-add-a-grub-splash-screen-image-in-debian-linux/").

6. In case you run into problems and cannot boot into your machine, boot into the live usb. Mount the ubuntu partition from disk and copy the backed up grub legacy files from your home folder back into /boot/grub (Remember, on the disk not the usb, so more likely /media/disk/boot/grub). Unmount. Now, open a terminal and

```
sudo grub

grub> find /boot/grub/stage1
```find returns one or more partitions where the grub legacy stage1 file was found. Assuming (hd0,0) was our original partition with the grub files, we embed grub legacy into the MBR with these commands.

```
grub> root (hd0,0)

grub> setup (hd0)

grub> quit
```Now reboot and remove the live usb. You should now be rebooted into your legacy grub boot loader menu.

On a tangent (skip if you wish): Now, with regards to making a backup image with dd, it has been pointed out that piping dd to gzip doesn't really decrease the image size by any significant factor. What can I say mate, you are absolutely right. But wait...aha! there's a solution. First lets understand the problem (I have lots of time, btw). dd reads every byte on the disk, it doesn't skip anything, even unused space on the file system. So if you have random data (think data from deleted files, here - what! and I thought those pics were really deleted ;), you must be joking, right?) on the unused space it is still passed on to gzip, and since its random data, the compression algorithm doesn't work very well. So the solution is to remove the random data beforehand, in other words, zero out those unused blocks. And here's the beauty of the solution, you can use dd to that as well. Simply boot from the ubuntu live usb, mount all the partitions one after the other and issue the following commands for each:

```
sudo dd if=/dev/zero of=/media/disk/zero.tmp bs=1M
sync
sudo rm /media/disk/zero.tmp
```Now unmount the partition and on to the next one. What we are doing here is effectively filling up the partition's unused blocks with zero-bytes. Open file for writing, stuff in 0-bytes until the partition is full, then close the file and remove it.

Now lets try the dd|gzip solution, for backup

```
sudo dd if=/dev/sda bs=1M | gzip -9 > /media/myexternaldrive/sc3.img.gz
sync
```The result might surprise you if you had a lot of unused space on your filesystem (give it a few hours btw). On the sc3, I have noticed, blocksize of 1M,2M,4M give faster backups. The default, 512 bytes, is way too slow .

To restore,

```
gzip -dc /media/myexternaldrive/sc3.img.gz | dd of=/dev/sda bs=1M
sync
```Still on the tangent: If you only want to backup particular partitions, partimage is the way to go. But if you are looking at backing up the windows recovery partition you will also have to backup the MBR+custom-vendor-code. That usually means the MBR(sector0)+all-sectors-until-the-first-sector-of-the-first-partition (including all unallocated space before the first partition). fdisk, parted, gparted, etc. will tell you which sector the first partition starts. Then you can use dd to backup the sectors including MBR. Alternatively, screw the vendor code, use partimage to backup the recovery partition, and when you restore it, put an entry for it in vista's BCD/xp's boot.ini and pray it works. Safest option is still the complete disk image.

Really long tangent, this, oh boy: Also if you don't have an external hard disk we can pipe dd over ssh, for backup

```
sudo dd if=/dev/sda bs=1M | ssh user@myotherlinuxmachine 'gzip -9 > sc3.img.gz'
sync
```and, to restore

```
ssh user@myotherlinuxmachine 'gzip -dc sc3.img.gz' | sudo dd of=/dev/sda bs=1M
sync
```assuming the other machine has more processing power, and bandwidth is not an issue, else, to backup

```
sudo dd if=/dev/sda bs=1M | gzip -9c | ssh user@myotherlinuxmachine 'cat > sc3.img.gz'
sync
```and, restore

```
ssh user@myotherlinuxmachine 'cat sc3.img.gz' | gzip -dc | dd of=/dev/sda bs=1M
sync
```To be frank I haven't tried dd over ssh on the sc3.

Now take all we discussed on this tangent + all that we did not discuss + throw in a lot many goodies + give it a wizard and we have wonderful clonezilla. Its many options however can confuse a lot many newbies.

Check out the dd [goldmine]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/") for more dd uses. Unfortunately no mention of ways to use dd to solve world hunger, poverty and bring peace to mankind. Everything else is pretty much there. 

Ya, I know, shouldn't have turned this into a dd lovefest, not the proper thread for it. Many apologies to those offended.

---

### Post by dothedog on 2009-08-13
5to5thirty, nice post. I am still using your syslinux hack. I think I will try the grub2 one next because syslinux, requires you to sit there and wait for grub to come up while booting...

Also, with the new poulsbo-3d stuff from ubuntu-mobile ppa I have compiz working as well. Just make sure you add the following to your xorg.conf or you will get freezes.
```

Section "Device"
	Identifier	"Configured Video Device"
        Option "AccelMethod" "EXA"
        Option "DRI" "off"
        Option "MigrationHeuristic" "greedy"
EndSection

```

Next subject - mplayer-vaapi
I am soooo close to getting this to work. I actually posted this on a different thread so I will copy it here:

I am very close to getting mplayer-vaapi working but have some video corruption on playback. I get a black bar about 1/5 from the bottom of the screen that goes about half way across the screen. This happens with VC-1 and h264 video (haven't tried others) [http://dothedog.home.comcast.net/~dothedog/pwpimages/Screenshot.png]("http://dothedog.home.comcast.net/~dothedog/pwpimages/Screenshot.png")Here is what I am using:

I have a Kohjinsha SC3 with Atom z520 Proc and Poulsbo (GMA500) Graphics

```

dothedog@Kohji-SC3:~$ uname -a
Linux Kohji-SC3 2.6.28-14-lpia #47-Ubuntu SMP Fri Jul 24 22:10:52 UTC 2009 i686 GNU/Linux
```

Using ubuntu-mobile ppa for:
```
xserver-xorg-video-psb - X.Org X server -- Intel Poulsbo (2D)
psb-modules - Kernel module built for -generic or -lpia kernel
psb-firmware - Binary firmware for the Poulsbo (psb) 3D X11 driver
psb-kernel-source - Kernel module for the Poulsbo (psb) 2D X11 driver
psb-kernel-headers - Kernel module headers for the Poulsbo (psb) 2D X11 driver
xpsb-glx - X11 drivers for Poulsbo (psb) 3D acceleration
poulsbo-driver-3d - Metapackage for the 3D Poulsbo (psb) X11 driver.
poulsbo-driver-2d - Metapackage for the 2D Poulsbo (psb) X11 driver.

```

Note on psb-kernel-source - if you upgrade your kernel to -14 from something else, you need to (using synaptic) completely remove it, then reinstall, for some reason an upgrade pukes.

Libva is from [http://www.splitted-desktop.com/~gbeauchesne/libva/](http://www.splitted-desktop.com/~gbeauchesne/libva/)
I am using version
libva1_0.29-2+sds12_lpia.deb
libva-dev_0.29-2+sds12_lpia.deb

libva1_0.29-2+sds12_lpia.deb loaded just fine. However the -dev package needed to get the libdrm dependency fixed (Changed depends line in Control file from libdrm-dev to libdrm-poulsbo-dev) Also, the 0.30 versions had dependency conflicts with libdrm so I had to fall back to the 0.29 version.

I also needed to do a
```
sudo ln -s /usr/X11R6/lib/modules/dri/psb_drv_video.so /usr/lib/va/drivers/psb_drv_video.so

```
to get libva working.

here is the output from vainfo:
```
dothedog@Kohji-SC3:~$ vainfo
libva: va_DRI_GetDriverName: 0.1.0 psb (screen 0)
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/psb_drv_video.so
libva: va_DRI_GetDriverName: 0.1.0 psb (screen 0)
libva: va_openDriver() returns 0
vainfo: VA API version: 0.29
vainfo: Driver version: Intel GMA500 - 5.0.1.0046

```

for mplayer-vaapi I used the latest from here: [http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/mplayer-vaapi-20090804.tar.bz2](http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/mplayer-vaapi-20090804.tar.bz2)

Make sure you have all the dependencies (e.g. svn) then do a
```
./checkout-patch-build.sh

```
It takes a while but mplayer-vaapi should build. Then play with
./mplayer -vo vaapi -va vaapi filename

Let me know if you get the black bar or if this is something that is peculiar to my setup.

DoTheDog

---

### Post by dothedog on 2009-08-14
Followup to above. The video corruption goes away if I turn off Compiz. I tried to identify which effect was causing it but even after turning all effects off it still caused the black bar. The black bar completely goes away with Compiz off (Preferences->Appearance->Visual Effects->None)

---

### Post by kentsin on 2009-08-25
Thanks a lot, I follow this thread and it WORKS!

Are there anyone make the GPS works? What applications to install if I want to work for openstreetmap?

Thanks again, best regards,

Kent

---

### Post by jeroppi on 2009-11-03
Hi people, I am green fresh new (still haven't even seen Linux a single time in my life).

But not long ago I managed to switch from IE to FireFox, then from MSOffice to OpenOfficeOrg... So now my next goal in life is to switch from Windows to Linux (Ubuntu).

This thread is quite frightening for me, but I am determined to learn all this stuff from scratch.

Guys, I just wanted to ask you 2 questions:

1)
Do the instructions on this thread consider the possibility of keeping a dual boot configuration, just in case I need to boot XP to run some specific peripherals or applications?

2) 
Do you think that some of the following tasks will NOT be possible to perform with Ubuntu on my SC3?:

In my classes (I am language teacher) Everyday I must show following things to my pupils connecting my SC3 to several classrooms projectors and loudspeakers:
- OpenOffice files, 
- PDFs, 
- audio (mp3) 
- video (flv, mp4)
- online websites 
- online applications
And of course I must be able to surf the web and download text, audio and video (Youtube, etc) files.

Thank you very much in advance for any comment, warning or suggestion.

---

