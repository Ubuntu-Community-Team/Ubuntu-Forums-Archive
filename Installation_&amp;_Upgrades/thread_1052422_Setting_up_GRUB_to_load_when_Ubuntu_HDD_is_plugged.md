---
title: "Setting up GRUB to load when Ubuntu HDD is plugged in."
date: 2009-01-27
forum: Installation &amp; Upgrades
---

### Post by MillerD on 2009-01-27
Okay its a long title but its pretty much my problem.  Pretty much what I want to do it have it to GRUB will check if the HDD containing Ubuntu is attached, if not boot into windows automatically.  I pretty much need this because I can't use GRUB or anything else unless the HDD is hooked in (I think its an Error 21). This can be problematic since Ubuntu is on an external USB Hard drive and this is a laptop. 

So I ask you guys, any help? If I need a new boot program tell me, I jsut need this figured out.

Thanks.

---

### Post by caljohnsmith on 2009-01-27
Can you change your BIOS boot order so that the Ubuntu drive boots before your internal Windows drive? If so, I think that would be the most ideal solution to your situation, because then when you have the Ubuntu drive connected, you will boot Ubuntu, and when the Ubuntu drive is disconnected, you will boot directly into Windows (assuming that's how you want it set up). If that sounds good to you, how about first doing:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of the commands before typing "quit"; those commands will install Grub to the MBR of your Ubuntu drive. If the commands are successful, go ahead and reboot, set your BIOS to boot the Ubuntu drive, and let me know how far you get. We can work from there if you want.

---

### Post by MillerD on 2009-01-27
This is the output:

 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,1)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

So now with this, I just quit out of it.

And now to change my boot order what would I do? I think its the either one of the escape or functions, I think escape.  So I press it when the little logo thing comes up once the computer boots? I'm sorry if it sound like I'm asking a lot but I'm just wanting to be sure.

---

### Post by caljohnsmith on 2009-01-27
Which key to press to get into BIOS varies from BIOS to BIOS, so I don't know what yours would be. When you see the logo screen on start up, does it tell you which key to press to get into BIOS? Sometimes they do. Otherwise you could try the function keys, or maybe check your computer documentation. It might be the ESC key, you can always try.

---

### Post by MillerD on 2009-01-27
Ok well I missed the logo to press a button but the bottom said "ESC to change Boot Order", would that be it?

---

### Post by caljohnsmith on 2009-01-27
The "ESC to change boot order" sounds like it might just be the quick boot menu where you temporarily choose which drive to boot from, but the changes aren't permanent. If you can't figure out how to get into your BIOS though, try ESC and see if you can boot the Ubuntu drive.

---

### Post by MillerD on 2009-01-27
Wait hold on, just to clarify just because I think you might not know exactly what I'm wanting after re-reading what you think I want.

pretty much this:

if (UbuntuHDDConnected = true) {
      Open grub with only a few seconds (about 5) to switch to windows if I 
      want, to, if it times out open ubuntu;
   } else if (UbuntuHDDConnected = false) {
      go directly to Windows;
}

I'm jsut making sure you know, from reading what you think I'm wanting you make it seem as if i never want to open windows if the HDD is connected.

---

### Post by caljohnsmith on 2009-01-27
Yes, that's exactly what I thought you wanted, and the main thing preventing you from having that scenario is that Grub is installed to the MBR of your Windows drive, while Grub's boot files are on the Ubuntu drive. That means in order to boot at all you have to have both drives connected. I'm trying to help you with a solution that will allow you to disconnect the Ubuntu drive whenever you want, and you will still be able to boot into Windows. Then when the Ubuntu drive is connected, you can boot into Ubuntu, or still be offered the choice to boot Windows. But it all hinges on being able to boot the Ubuntu drive from your BIOS on start up.

---

### Post by MillerD on 2009-01-27
Okay I think I figured out how to set it, I found the part in the BIOS setup there I can change the boot priority currently floppy is at top, then CDROM, then my built in HDD, then something else, then the USB HDD, so all I would need to do is move the USB HDD up to above the built in HDD, right?

EDIT:

Okay I just tried it and still ERROR 21 once I disconnected the HDD, I know the boot order is right, I just think I set the GRUB to the wrong thing or something, any help should have I done "setup (hdX)" with x being the ubuntu HDD? because I just did the X as what was returned to me in the find.  How can I have my HDDs listed so I can chose the right one?

EDIT EDIT:

I found this: [http://www.pendrivelinux.com/grub-error-21-after-full-install-to-usb-hard-drive/](http://www.pendrivelinux.com/grub-error-21-after-full-install-to-usb-hard-drive/)

Would this work? All I would have to do is reinstall it to my Ubuntu partition right?

EDIT EDIT EDIT:

So from what I understand, GRUB is on my internal but configs are on external, so are we trying to move configs to internal or GRUB to external

(Should have I made a /boot partition when I installed 'cause I didn't)

:-?

---

### Post by MillerD on 2009-01-27
Sorry, I hate bumping as much as you guys but I'm trying to fix this problem ASAP. Another link I sound was: [http://www.linuxforums.org/forum/ubuntu-help/83959-ubuntu-external-hard-drive-when-discoed-grub-error-21-fix.html](http://www.linuxforums.org/forum/ubuntu-help/83959-ubuntu-external-hard-drive-when-discoed-grub-error-21-fix.html)

---

### Post by caljohnsmith on 2009-01-27
You did the Grub commands fine it looks like based on the output you posted in post #3. Also, we would still expect that you would get an error 21 when you disconnect the Ubuntu drive because you haven't yet reinstalled a Windows MBR to your Windows drive. How about going ahead and doing that, and then it will be more clear which drive you are booting on start up:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Then reboot, and if you have your Ubuntu drive disconnected, you should boot straight into Windows if all goes well. When you hook up the Ubuntu drive again, you should get Grub if your BIOS is set to boot the Ubuntu drive. Let me know how that goes.

---

### Post by MillerD on 2009-01-27
Thank you so much, it seems to be working now. May I ask what you AIM/MSN is incase I have any other troubles?

---

### Post by caljohnsmith on 2009-01-28
> **MillerD said:**
> Thank you so much, it seems to be working now. May I ask what you AIM/MSN is incase I have any other troubles?
Glad to hear that did the trick; if you run into any more problems, just post back to this thread and I'll try to help. Cheers and enjoy Windows and Ubuntu. :)

---

### Post by javaman1909 on 2009-02-02
Then, how about if I have both Ubuntu and Windows installed on internal HDD, but I only want the GRUB of Ubuntu installed in thumb drive so that if I don't plug my thumb drive, it will boot to Windows, and if I plug thumb drive, it will appear GRUB which I can choose Ubuntu.

---

