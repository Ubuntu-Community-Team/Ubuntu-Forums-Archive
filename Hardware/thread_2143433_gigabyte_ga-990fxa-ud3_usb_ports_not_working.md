---
title: "gigabyte ga-990fxa-ud3 usb ports not working"
date: 2013-05-09
forum: Hardware
---

### Post by lorderrorprone on 2013-05-09
I've tried booting ubuntu 13.04 and 10.04 on this board, when I get to the desktop on the live cd I can't use the mouse and keyboard. I've tried different usb ports to no avail, has anyone been able to get ubuntu or any distro of linux working properly on this board?

---

### Post by Mark Phelps on 2013-05-10
Have a similar Gigabyte board and have had no problems with it.  You should go into the BIOS settings and see what is there that will allow you to enable Legacy USB support.  You will probably need to turn that on.

Also, if these are USB 3.0 ports, you are going to have major problems.  Legacy mode may allow them to work in USB 2.0 mode, which should then work for you.

---

### Post by gandalfbz on 2013-05-21
> **lorderrorprone said:**
> I've tried booting ubuntu 13.04 and 10.04 on this board, when I get to the desktop on the live cd I can't use the mouse and keyboard. I've tried different usb ports to no avail, has anyone been able to get ubuntu or any distro of linux working properly on this board?

I had se same issue. In my case I have Gigabyte GA-990xa-UD3 (revision 3.0) and I ma trying to install ubuntu server from USB. The install starts till I select "Install Ubuntu Server" and when it commes back to the select Language the keyboard is dead as all USB ports.

If I try to install Desktop version from USB I do not even manage to load the live desktop. This is normal as I am trying to install from USB and as part of the installation process start-up It loads kernel or modules that are incompatible with USB on the board and fails. In your case as you are with a live CD is not a problem at the same point because it cas still read from CD even the USBs are already dead.

It is a pain in the as that this board is listed [here ]("https://friendly.ubuntu.com/12.04/Gigabyte%20Technology%20Co.,%20Ltd./GA-990XA-UD3/A:BaYp:Gy0:BEG:CNU:BWK/") and [here ]("https://friendly.ubuntu.com/12.04/Gigabyte%20Technology%20Co.,%20Ltd./GA-990XA-UD3/A:BaYp:Gy0:BEG:CNU:BWK/devices/")as Ubuntu friendly. Provably it is just that revision 1.0 and 1.1 are ubuntu friendly but not the new version. I will tray to enter this to ubuntu friendly and see if it helps someone.

My plan is to use an PS/2 keyboard and see if I can install ubunto from a DVD reader, a windows harddirver. I think  now there is a friendly way to do this but I do not want to compromise performance or depend on windows to run. I will remove windows HDD later.

Once I have the ubuntu server running try to fix this USB issue. Also I think there is a problem with the LAN driver that would need to be fixed.

I found some information on ubuntu.fr ([here]("http://doc.ubuntu-fr.org/gigabyte_ga-990xa-ud3")) . Sorry I do not speak french and I used google to transalte it to my mother language.  My understanding is that once ubuntu is up and running you can fix this 

Best regards.

---

### Post by Mark Phelps on 2013-05-21
gandalfbz: You should check your BIOS USB settings as I had suggested in post #2. 

Also, I have tried myself using a ps/2 keyboard to install Ubuntu over the years, and in all cases, it was unable to detect the keyboard. And, that was using motherboards that had ps/2 plugs.  If yours does not, you will probably have to use a ps/2-to-USB adapter -- which puts you back in the same state using USB ports.

---

### Post by gandalfbz on 2013-05-28
> **Mark Phelps said:**
> gandalfbz: You should check your BIOS USB settings as I had suggested in post #2. 

Also, I have tried myself using a ps/2 keyboard to install Ubuntu over the years, and in all cases, it was unable to detect the keyboard. And, that was using motherboards that had ps/2 plugs.  If yours does not, you will probably have to use a ps/2-to-USB adapter -- which puts you back in the same state using USB ports.

Hi Mark

I did already checked USB bios settings with no luck at all. It does not make any change.

Please, note that my board HAS a PS2 port --> [http://www.gigabyte.com/products/product-page.aspx?pid=4434#sp](http://www.gigabyte.com/products/product-page.aspx?pid=4434#sp)

Yet I did not have a chance to test. I will keep you posted.

---

### Post by quattro_cs on 2013-05-28
In the BIOS, set IOMMU to "Enabled". That fixed both USB and networking for me.

---

### Post by gandalfbz on 2013-06-03
> **quattro_cs said:**
> In the BIOS, set IOMMU to "Enabled". That fixed both USB and networking for me.

That worked like charm!!! I had played with all USB related options at BIOS but never touched IOMMU... Never thought that it was related. Actually I didn't knew what was for. 

Just to remind that I am using gigabyte ga-990**xa**-ud3  and not [B]fxa


Thanks a lot![/B]

Once I was able to boot into linux I found some errors about AMD-VI that I am still looking into. At some point I readed that they might be related to IOMMU set-up... I hope it is something else and I can fix it. Mainly I want to run Virtual Servers here for testing :-D

---

### Post by komensky on 2013-06-10
a·maz·ing!  I've been trying to install 13.04 on this new box w/the gigabyte ga-990fxa-uda since last Thursday.  Every time I encountered mouse+keyboard locking.  Tried many things:  clone drive w/13.04 on it from another puter, linuxmint, fedora livecds.  The only thing that I could install was Meerkat Maverick.  I also tried enable/disable legacy/uefi this, legacy/uefi that in the bios.

Then tonight before bed I googled "is GIGABYTE GA-990FXA-UD3 compatible with ubuntu?" and clicked on this very first link.  Not much hope reading the first responses... til I got to quattro_cs'.  Success.

Thank you a lot :)

How did you find the solution?  And what does 'iommu' even mean?

---

### Post by linuxisgoed on 2013-06-21
my Gigabyte 990XA-UD3 also had this problem but the change in bios did the trick thanks quatto_cs,[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1108818")

---

### Post by martin-echter on 2013-09-03
Thanke you.

---

### Post by kevin.nyman on 2013-11-30
Thank you as well. I was getting the error "(initramfs) Unable to find a medium containing a live file system" for trying to install from both a disk and a usb drive.

I have the GA-990FXA-UD3 rev 4.0.

---

### Post by karmablur on 2013-12-06
Post #6 did the trick, Thanks Quattro!

---

### Post by amartinson on 2013-12-11
Absolutely amazinggggggggg! I've been at this issue for hours and hours. I kept getting "(initramfs) Unable to find a medium containing a live file system" when trying to install. I thought I had tried everything! I tried three different ISO images (Xubuntu 12.10, 13.10 and Ubuntu  12.04), installed on two different flash drives (Sandisk 8GB and 32GB),  with two different programs (LiLi USB Creator and Universal USB  Installer). I had messed with all the BIOS settings except for this.

Enabling "iommu" in this BIOS was the fix. Thank you all!

Tags: Gigabyyte 990FXA-UD5

---

### Post by aka2 on 2014-01-21
> **quattro_cs said:**
> In the BIOS, set IOMMU to "Enabled". That fixed both USB and networking for me.

THANK YOU SO MUCH quattro_cs. You saved me losing my mind !! :)

---

### Post by liste on 2014-02-01
Hello.  I'm experiencing the same issue here.  None of my USB 3.0 ports are working and all of my USB 2.0 ports are.  I have enabled IOMMU and legacy USB support in my BIOS, but to no avail.  Into the USB 3.0 ports I have plugged a USB3 HDD and a USB2 pendrive, neither of which worked; however they both work in the USB2.0 ports.

I can't remember the exact settings I had in the time, but at one point the problem was reversed: all 3.0 ports were working and all 2.0 ports were non-functional.  Are there any other settings I can try?  I have the GA-fx990 ud3, rev. 4, running Ubuntu 12.04.  Should I try an update of Ubuntu?

---

### Post by Willyweasel on 2014-02-01
First iommu stands for input output memory management unit, as for getting usb 3.0 working do this:

open a terminal and input this: ```
sudo gedit /etc/default/grub
```
input your password
then find the line that says: GRUB_CMDLINE_LINUX=""
then make it this: GRUB_CMDLINE_LINUX="iommu=soft"
save the file
then run this in the terminal: ```
sudo update-grub
```
reboot and disable iommu in the bios

After this all usb 3.0, usb 2.0, and ethernet should work.

---

### Post by liste on 2014-02-01
Thank you, Willyweasel!  That's nearly it.  Now my Kingston USB2 stick is functioning in the USB 2 and 3 ports, but my external USB3 HD is only functioning in the USB 2 ports.

---

### Post by Willyweasel on 2014-02-02
So usb 2.0 devices work in both the usb 2.0 and usb 3.0 ports, but usb 3.0 devices don't work in the usb 3.0 ports? I'm not sure what the problem would be if the usb 3.0 port recognizes usb 2.0 devices it should at least recognize usb 3.0 devices that are backward compatible with usb 2.0. It could be a driver issue, look on Gigabytes website and see if you can find a usb 3.0 linux driver for your motherboard. I don't think there are any usb 3.0 linux drivers for your board yet, but it wouldn't hurt to look. Honestly it should recognize the usb 3.0 drive when plugged in to the usb 3.0 port, can you tell me exactly what hard drive you have?

---

### Post by liste on 2014-02-03
That's right.  USB 2.0 devices were working in both USB 2.0 and USB 3.0 ports, but USB 3.0 devices were only functional in USB 2.0 ports.  For some reason, it is working today.  I don't know what the problem was because I even tried multiple reboots and cold boots to try to resolve the issue.  Anyway, thank you for your help; everything (usb-wise) seems to be functioning now.  I'm having some peculiar, random power-offs, but that's for another thread, and probably a different forum.

---

### Post by systemstech on 2014-02-17
> **Willyweasel said:**
> First iommu stands for input output memory management unit, as for getting usb 3.0 working do this:

open a terminal and input this: ```
sudo gedit /etc/default/grub
```
input your password
then find the line that says: GRUB_CMDLINE_LINUX=""
then make it this: GRUB_CMDLINE_LINUX="iommu=soft"
save the file
then run this in the terminal: ```
sudo update-grub
```
reboot and disable iommu in the bios

After this all usb 3.0, usb 2.0, and ethernet should work.

Thanks Willyweasel. Thanks to this quick fix I now have a working usb 3.0 , 2.0 ports and most of all the onboard nic.

---

### Post by astepintothedark on 2014-02-26
Enabliing IOMMU worked for me too. I have Rev 3.0.

I had been at this for hours trying different flavors of Ubuntu. Thank you so all so much.

Although, I'm now wondering why this worked. Can anyone explain?

---

### Post by john168 on 2014-03-04
I have the rev 4 board and I finally gave up nothing worked.  I tried iommu, legacy USB, IDE mode, USB 2.0 only ports.  And latest builds of Ubuntu and xubuntu installers from both a flash drive created with Rufus and t
trim an install DVD burned from iso.  No matter what I did the furthest I could get it to go was the install ubuntu screen would spin the circle logo and lockup.  I also tried option try ubuntu or try xubuntu instead of install. Same result. It's almost like it didnt want to initialize the vide or something. Frustrated after 8 hours straight I finally went back to win 7 64 bit.  
Rev 4 of the board with 1 asus gtx 750 ti oc.  (The stack of 5 more of these babies is on the desk)

for what it was worth my original goal was to USB flash install either ubuntu or xubuntu to another USB flash drive to run Linux from on my mining rig.

---

### Post by prophet6 on 2014-09-02
> **john168 said:**
> I have the rev 4 board and I finally gave up nothing worked.  I tried iommu, legacy USB, IDE mode, USB 2.0 only ports.  And latest builds of Ubuntu and xubuntu installers from both a flash drive created with Rufus and t
trim an install DVD burned from iso.  No matter what I did the furthest I could get it to go was the install ubuntu screen would spin the circle logo and lockup.  I also tried option try ubuntu or try xubuntu instead of install. Same result. It's almost like it didnt want to initialize the vide or something. Frustrated after 8 hours straight I finally went back to win 7 64 bit.  
Rev 4 of the board with 1 asus gtx 750 ti oc.  (The stack of 5 more of these babies is on the desk)

for what it was worth my original goal was to USB flash install either ubuntu or xubuntu to another USB flash drive to run Linux from on my mining rig.

The proposed solutions do not work for me either. Tried each separately and no joy. As an aside, disabling the hardware IOMMU (iommu=soft) seems a like a workaround vs. an actual fix to me, but to each their own.

Specifically, my external USB3 drive (Seagate GoFlex) will not mount when plugged into any USB3 port. It will work when plugged into a USB2 port. Interestingly, USB3 flash drives *will* work when plugged into the USB3 ports.

I tested the external drive on a completely different linux-based machine, and when plugged into its USB3 port I got transfers around real-world USB3 speeds (~100MB/s when copying to a SATA2 drive).

Ubuntu 3.13.0-24.46-generic 3.13.9
Gigabyte GA-990FXA-UD3 motherboard
-rev. 4.0
-BIOS version F2 (latest at time of writing)
-USB controller - VIA VL805 "Support various Linux kernels"

Gritty details are reported at [Bug #1353050 ]("https://bugs.launchpad.net/linuxmint/+bug/1353050")

---

### Post by tommy-tomloz on 2014-09-10
> **systemstech said:**
> Thanks Willyweasel. Thanks to this quick fix I now have a working usb 3.0 , 2.0 ports and most of all the onboard nic.

Same goes for 
**gigabyte ga-990fxa-ud5 motherboards, up running a treat,**

though ive seen other information on kernel eol stating fix with blacklist Etron EJ168 ect, my current kernel is lower 3.11.0-26-generic both low speed usb2 and high speed usb3 work fine.
ie:-
[    1.810832] usb usb11: Product: xHCI Host Controller
[    1.810836] usb usb11: Manufacturer: Linux 3.11.0-26-generic xhci_hcd
[    1.810840] usb usb11: SerialNumber: 0000:06:00.0
[    1.810913] hub 11-0:1.0: USB hub found
[    1.863934] usb 2-3: new high-speed USB device number 2 using ehci-pci
[    2.129955] usb 2-3: New USB device found, idVendor=046d, idProduct=0990
[    2.129963] usb 2-3: New USB device strings: Mfr=0, Product=0, SerialNumber=2
[    2.129968] usb 2-3: SerialNumber: 8D2EA44A
[    2.506363] usb 5-4: new low-speed USB device number 2 using ohci-pci
[    2.676461] usb 5-4: New USB device found, idVendor=1bcf, idProduct=0007
[    2.676469] usb 5-4: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    2.676474] usb 5-4: Product: USB Optical Mouse
[    2.689500] usbcore: registered new interface driver usbhid
[    2.689505] usbhid: USB HID core driver
[    2.692323] input: USB Optical Mouse as /devices/pci0000:00/0000:00:13.0/usb5/5-4/5-4:1.0/input/input0

copies and pastes from sata3 to usb3 stick at 40MB/sec which is ok. approx 60 sec for a movie.
was hoping for more i will need to check further.




open a terminal and input this:  	Code:
 	sudo gedit /etc/default/grub 
input your password
then find the line that says: GRUB_CMDLINE_LINUX=""
then make it this: GRUB_CMDLINE_LINUX="iommu=soft"
save the file
then run this in the terminal:  	Code:
 	sudo update-grub 
reboot and disable iommu in the bios

After this all usb 3.0, usb 2.0, and ethernet should work. 				



















9

---

### Post by tommy-tomloz on 2014-09-10
[INDENT]                     First iommu stands for input output memory management unit, as for getting usb 3.0 working do this:

open a terminal and input this:      Code:
     sudo gedit /etc/default/grub 
input your password
then find the line that says: GRUB_CMDLINE_LINUX=""
then make it this: GRUB_CMDLINE_LINUX="iommu=soft"
save the file
then run this in the terminal:      Code:
     sudo update-grub 
reboot and disable iommu in the bios

After this all usb 3.0, usb 2.0, and ethernet should work.                 
[/INDENT]

---

### Post by tommy-tomloz on 2014-09-10
see one post of mine approx 2 years ago, where i added an external dvd player and connected it to the other satta port set. then unplugged it after install basically to get it working ...ie: i simply had it booting one sata port the the other.. grey one...black one they are different or putting it another way it boots from one then installs the driver for the other itself and boots from that set of sata ports (the faster one) cd/dvd players use the slower one.
a bit like changing boot order in the bios, but doing it myself instead.

that message was for john 168....above

he gave up before he started ...mines the [h=2]ga-990fxa-ud5 motherboard[/h]

---

### Post by RobTheBold on 2015-01-09
I just installed a new GA-990FXA-UD3 board in my system after my older one started flaking out and immediately ran into this problem. I first found [this thread]("http://ubuntuforums.org/showthread.php?t=2111223") for a similar GigaByte motherboard with the same problem, and applied the [COLOR=#000000]GRUB_CMDLINE_LINUX="iommu=soft" fix and *almost* all was well.

When I thought everything was working fine, I plugged my LaserJet 1020 into a USB port -- as I had before the hardware unpleasantness began -- and suddenly, the boot process got dragged out again, the "waiting for network" message appeared and also complaints about USB enumeration. Unplugging the printer fixed the problem immediately and Kubuntu started right up, keyboard, network and mouse all working fine. I can plug the printer back in after logging in, and everything still works (except the laserjet). lsusb shows it's plugged in, but the hplip tools can't talk to it or even see it. I know it's a crappy "winprinter" but I'm confused and surprised that this change broke things . . .[/COLOR]

---

### Post by oldfred on 2015-01-09
Did you also change the setting in UEFI?

       IOMMU for USB3 ports Gigabyte board
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)
Linux kernel enable the IOMMU – input / output memory management unit support - AMD 
[http://www.cyberciti.biz/tips/howto-turn-on-linux-software-iommu-support.html](http://www.cyberciti.biz/tips/howto-turn-on-linux-software-iommu-support.html)
[http://ubuntuforums.org/showpost.php?p=9203674&postcount=5](http://ubuntuforums.org/showpost.php?p=9203674&postcount=5)

---

### Post by RobTheBold on 2015-01-10
> **oldfred said:**
> Did you also change the setting in UEFI?



I enabled IOMMU support in the BIOS settings, which got the USB keyboard and mouse working enough to edit the grub file, fixed that and ran update-grub, then rebooted and turned IOMMU off in BIOS settings and booted again, at which point I thought all was fine. Except the printer . . . (And I haven't tested USB 3.0 support, since I don't have any hardware that uses that right now.)

UPDATE: I re-enabled the IOMMU support, and the computer boots and loads Kubuntu *with* the printer attached. No USB enumeration errors, USB works, network works. *And* the printer made its "initialization" sounds, suggesting the the HP proprietary driver had loaded the 1020's firmware and reset the unit. Test page printed.

I decided to push my luck. I rebooted, entered BIOS setup, disabled IOMMU support again. Saved the settings and rebooted. Again, system loads all the way to Kubuntu login with no problem, no USB errors, network working. Again, the printer makes its "initialization" sounds.

I can only conclude that the printer had lost its firmware (which has to be reloaded every time it's powered off) and the MB couldn't handle finding it sitting there brain-dead on the serial bus. After booting with IOMMU support enabled, the firmware could be loaded and subsequent boots were successful with or without IOMMU support turned on in the BIOS. I suspect -- but haven't verified -- thatI'll have to repeat the process any time the printer gets turned off or loses power (or just goes off in the weeds). Or I could leave IOMMU support enabled, although some users have suggested the USB 3.0 doesn't work it that case. As I mentioned above, I don't have any 3.0 devices yet to verify that.

---

### Post by lameazz15 on 2015-06-22
I have the same motherboard and the same problem. Not any more, thanks a million for sharing this solution. I went about 4 days using the dreaded microshaft operating system because I couldn't  get kubuntu working with the new mobo. I must have downloaded about 10 different versions of linux trying out different flavors but basically the same results. I been using kubuntu for quite a few years now and its by far my favorite flavor.

---

### Post by pikatu on 2015-06-25
We were in the dark for about 6 days until we fell on your solution.

Thanks a lot.

Ilan

---

### Post by GXdmWQH on 2016-03-19
> **Willyweasel said:**
> First iommu stands for input output memory management unit, as for getting usb 3.0 working do this:

open a terminal and input this: ```
sudo gedit /etc/default/grub
```
input your password
then find the line that says: GRUB_CMDLINE_LINUX=""
then make it this: GRUB_CMDLINE_LINUX="iommu=soft"
save the file
then run this in the terminal: ```
sudo update-grub
```
reboot and disable iommu in the bios

After this all usb 3.0, usb 2.0, and ethernet should work.

This did the trick for me - I assume it's related to a BIOS bug?

---

### Post by oldos2er on 2016-03-20
Old thread closed.

---

