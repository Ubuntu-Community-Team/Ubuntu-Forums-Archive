---
title: "eeePC 701 - Ubuntu won't install"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by ian.gralinski on 2009-09-02
Hi all,

I've been trying to install ubuntu (many different versions: 9.04, 8.04, easy peasy) using a usb drive, but none of them seem to work. I used uNetBootin to copy the ubuntu iso onto a 4GB usb drive. This works fine, no problems.

I then change the boot priority in BIOS to boot from usb, which it does. It loads what it needs to and presents me with the first few screens of installation (language, keyboard settings). However, when it reaches detecting network hardware, it stays at 0% and doesn't go any further. 

I've tried looking around for similar problems, but it seems like everyone can get ubuntu installed at least, before they get their first problems.

I have a 4G 701 eeePC with the stock standard BIOS that came with it (v 0703)

Does anyone know what might be causing this problem, and how to fix it?

---

### Post by aysiu on 2009-09-02
Well, it can be only one or more of the following problems:

1. The .iso of Ubuntu got corrupted during the download process
2. Something is wrong with your 4 GB USB drive
3. Something happened during the copying process when you used UNetBootIn to extract the .iso to your USB drive
4. Something is wrong with your Eee PC (hardware-wise)

Assuming #2 and #4 are not the case (not saying they can't be... just that it makes things a lot more difficult), there are a few things you can do to rule out #1 and #3, too.

Re-download the Ubuntu .iso using BitTorrent and then (if you know how to) verify the download by checking the MD5SUM.

Completely erase everything on your USB drive (including hidden files--very important).

Then use UNetBootIn again to extract the .iso to your USB drive.

---

### Post by ian.gralinski on 2009-09-02
Thanks for the quick reply. :)

I've borrowed a different USB stick and I will also re-download the ubuntu iso and give it a go sometime tonight or tomorrow. 

I did have ubuntu 7.04 on my laptop a little while ago, but I was playing around and deleting files to try to do a net update (net update kept wanting more free space) and managed to remove the terminal and all menus. At this stage, I can boot into 7.04 and it accepts my username and password, but then only the background loads.

---

### Post by ian.gralinski on 2009-09-03
I still can't get ubuntu to install. Here is what I have done:

1. Re-downloaded ubuntu-9.04-alternate-i386.iso and checked the MD5SUM, all OK. 
2. Formatted a different USB stick to FAT32 and checked that there were no files (hidden, system, etc), all OK
3. Used UNetBootIn to extract the iso to the USB drive, no errors
4. Put the USB stick into my eeePC and press Alt+F2 during the startup screen -> this loads the EZ Flash utility and looks for 701.ROM

I tried disabling quick boot and quiet boot, the same problem persists. I also tried putting a new BIOS, 701.ROM, onto the USB, but it gets stuck at 'Reading file "701.ROM"'. It does however complete 'Checking for USB Device..." & "USB Device found.". 

Is there any way to stop the EZ Flash from running in preference to the USB image? Or to stop EZ Flash from running at all?

---

### Post by aysiu on 2009-09-03
I'm sorry... are you trying to flash the BIOS? Or are you trying to install Ubuntu? I don't understand why you're doing this 701 rom thing.

And the alternate CD doesn't always work with UNetBootIn. Forget the alternate CD. Just use the regular desktop CD.

---

### Post by aysiu on 2009-09-03
I'm sorry... are you trying to flash the BIOS? Or are you trying to install Ubuntu? I don't understand why you're doing this 701 rom thing.

And the alternate CD doesn't always work with UNetBootIn. Forget the alternate CD. Just use the regular desktop CD.

---

### Post by ian.gralinski on 2009-09-05
I am trying to install Ubuntu, I tried the 701.ROM file because I read somewhere (can't remember exactly where) that the eeePC 701 has issues with the old BIOS version. 

I downloaded ubuntu-9.04-desktop-i386.iso, did the MD5SUM check, formatted the USB to FAT32 and used UNetBootIn to load it onto the USB, but the same thing happens. If I press Alt+F2 when booting, it goes into EZ Flash. If I leave it alone, it loads the old version of Ubuntu which is installed.

---

### Post by aysiu on 2009-09-05
Forget about Alt-F2. Clearly that's for flashing the BIOS and not for booting Ubuntu.

Now that you have Ubuntu loaded onto the USB stick, plug the USB stick into your Eee PC.

When you boot up, press Escape until a blue screen comes up. From there, you should be able to pick which device to boot from (select the USB stick).

---

### Post by aysiu on 2009-09-05
Forget about Alt-F2. Clearly that's for flashing the BIOS and not for booting Ubuntu.

Now that you have Ubuntu loaded onto the USB stick, plug the USB stick into your Eee PC.

When you boot up, press Escape until a blue screen comes up. From there, you should be able to pick which device to boot from (select the USB stick).

---

### Post by ian.gralinski on 2009-09-06
I'm getting some error messages a bit after Ubuntu starts loading. Here's what I did:

1. Pressed ESC to get into the blue menu to select boot device and chose the USB stick
2. UNetBootIn appears and I select default
3. /ubnkern and /ubninit load successfully
4. The Ubuntu logo with load bar appears. The yellow bar moves side to side for some time and then it disappears. Below is the error messages I get:

```

sd 3:0:0:0: timing out command, waited 180s
end_request: I/O error, dev sdc, sector 1935344
Buffer I/O error on device sdc, logical block 241918

```

---

### Post by aysiu on 2009-09-06
Sounds as if something is wrong with your USB stick.

---

### Post by jnorthr on 2009-09-06
do you have access to another p/c that you could try the USB key on ? That might provide a clue as to whether it's your key setup or the kit.

---

### Post by ian.gralinski on 2009-09-06
Looks like it's the eeePC that's not working properly. I just tried the same USB stick on my home computer and no problems at all. 

I guess this one is for ASUS support :(

---

### Post by jnorthr on 2009-09-06
That's the beauty of have more than one box to try it out on, so now you can ubuntu all you like on that portable key, take it with you anywhere. Just looked on the eeepc 701 website but cannot see the spec for your system. You may need to dig a bit to find out how to get your usb key to run on the eeepc. Sounds like you are almost there. :KS

---

### Post by mn_voyageur on 2009-09-06
I had the same PC for a week. (eeePC 701)  I never could load from a USB stick.  I was able to load from a liveCD using a external DVD drive.

I thought it was my lack of knowledge, until I spoke with my friend who programs super computers.  He stepped me through the same process you have done.  New USB stick.  Different mirror sites.  Different distros.   He had me running command lines that I will probably never use again.

After I fought that battle, I learned that the camera was not working and returned it for a full credit.  

Nice netbook.  Just a little frustrating for me.  If you really want to keep it, I would suggest investing in an external DVD.

MN

---

### Post by ian.gralinski on 2010-03-24
I know this is a very old thread, but I did eventually manage to get linux to boot by choosing the liveCD option. It kept coming up with the same errors as listed above at 180s intervals, but after leaving it for about 20 minutes, it started loading and managed to boot. 

After this I was able to install eeebuntu from the live desktop.

---

### Post by mn_voyageur on 2010-03-25
I hope you enjoy your netbook.  As I said earlier, other than the camera, and the inability to load from a flash drive, it was a nice computer.  

In fact, I have looked for a netbook for my kids.

MN

---

