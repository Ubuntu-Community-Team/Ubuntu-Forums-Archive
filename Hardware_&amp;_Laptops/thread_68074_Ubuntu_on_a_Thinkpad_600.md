---
title: "Ubuntu on a Thinkpad 600"
date: 2005-09-22
forum: Hardware &amp; Laptops
---

### Post by zapaces on 2005-09-22
Hi there, I would like some kind of help...
I decided to run Ubuntu Linux 5.04 Hoary Hedgehog on my IBM ThinkPad 600, model - type 2645 51U. It's a pretty a pretty old lady but works greats. Unfortunately it doesnt seem to get along smooth with Ubuntu Linux.

After installing, some issues came up. Please consider Im quite a newbie in Linux.
- I cant hear a single thing through the speakers, I've read that the TP600 comes with a "cs4237b" sound device or something... no idea what this is about.
- I cant get my pendrive to work.
- I need to swith between English and Spanish Keyboards and, even thou I know how to swith them through System-Preference-Keboard, I would like to know how can I switch them while working on any document.
- My networking is finally being recognized but it takes about 5 minutes to load google.

What have I done so far.... (After quite a reading in some groups I've taken priority over the networking and the pendrive issues. This because so far I cannot "copy and paste" what I get in Linux and post it in here", so with networking or pendrive working I could do so.) :

- the networking thing, I think i got it to eth0 something to work but I really don't have a clue how to speed it up.

- the pendrive issue (which has taken my entire afternoon) .... is
   - "mkdir /media/pendrive" (directory)
   - I edited the "/etc/fstab" adding: "/dev/sda1 /media/pendrive vfat rw,noauto,users 0 0" and i got the "pendrive icon" on the computer window.
   - I edited the "/etc/hotplug/blacklist" and commented (added #) to "usb-uhci" and "usbcore" (just thinking that being in blacklist would keep them off recognizing the USB drive).
   - Then I tried "mount /dev/sda /media/pendrive" and "...sda1,2,3" (crazy 'cause the TP600 only has 1 USB) but no good it did, it said "/dev/sdax does not exist".
   - then I typed "fdisk -l" and got only "devs.... hda1 hda2 hda5", so impossible to haveit if fdisk doesnt recognize it.
   - at last, the dmesg said something like:
 "usb 1-1: new full speed USB device using uhci_hcd and address 10
  usb 1-1: khubd timed out on op0in
  usb 1-1: device descriptor read/64m error -110
  usb 1-1: khubd timed out on op0in
  usb 1-1: device not accepting address 10, error -84
  usb 1-1: new full speed USB device using uhci_hcd and address 11
  usb 1-1: khubd timed out on op0in
  usb 1-1: device descriptor read/64m error -110
  usb 1-1: khubd timed out on op0in"
 
and... IT WONT MOUNT IT grrgrrrrrrrr.

Okay, please help. I would love to fix this four things and learn in the proccess of doing so what the heck im doing, so any explanation that kills u while writing, it makes life much more interesting from this side.

THANKS IN ADVANCE, and Greetings from Chile.

---

### Post by mlomker on 2005-09-22
I don't have any answers for you.  It can be difficult to get a newer version of linux to run on an older laptop due to driver issues.  You may need to run an older distribution based on a 2.4 kernel in order to get adequate hardware support.

Have you run across this site yet?  [http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki)

---

### Post by sb73542 on 2005-09-23
[QUOTE=mlomker]I don't have any answers for you.  It can be difficult to get a newer version of linux to run on an older laptop due to driver issues.  You may need to run an older distribution based on a 2.4 kernel in order to get adequate hardware support.

Have you run across this site yet?  [http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki)[/QUOTE]
 Hoary works fine on a Thinkpad 600.  I have one myself, and it runs Ubuntu Hoary.

---

### Post by mlomker on 2005-09-23
[QUOTE=sb73542]Hoary works fine on a Thinkpad 600.  I have one myself, and it runs Ubuntu Hoary.[/QUOTE]

Then I hope you'll answer the poster's questions.  Everything that I found on Google states that the USB will only work with specific patches applied to a 2.4 kernel.

---

### Post by sb73542 on 2005-09-24
[QUOTE=mlomker]Then I hope you'll answer the poster's questions.  Everything that I found on Google states that the USB will only work with specific patches applied to a 2.4 kernel.[/QUOTE]
 USB works out of the box on almost every distro I've tried on this laptop, including ones that use kernel 2.6.  The problem with the above user's USB key lies with udev/HAL.  Unfortunately, I'm clueless there!  :-)  Sorry.  Try re-posting a new message with a more descriptive title.

As for sound, disable quick boot is BIOS, boot with the options "apm=on acpi=off" and then manually do in terminal:

modprobe snd-cs4236 port=0x530 cport=0x538 isapnp=0 dma1=1 dma2=0 irq=5 
modprobe snd-pcm-oss

And then ask someone smarter than myself how to make it work automatically on each bootup.  BTW, Ubuntu's sound support stinks on older ISA cards.  I wish it would get fixed...

As for the keyboard layout, right click in gnome panel, "Add to panel..." and pick "Keyboard Indicator"

---

### Post by fordfan753 on 2005-09-24
[QUOTE=zapaces]
- the networking thing, I think i got it to eth0 something to work but I really don't have a clue how to speed it up.
[/QUOTE]
Try going into firefox, and typing "about:config" as the address. In the filter bar type "ipv6" it should come up with "network.dns.disableIPv6" it will be set as false. Change it to true and restart firefox. Is it any faster now?

[QUOTE=zapaces]
- the pendrive issue (which has taken my entire afternoon) .... is
   - "mkdir /media/pendrive" (directory)
   - I edited the "/etc/fstab" adding: "/dev/sda1 /media/pendrive vfat rw,noauto,users 0 0" and i got the "pendrive icon" on the computer window.
   - I edited the "/etc/hotplug/blacklist" and commented (added #) to "usb-uhci" and "usbcore" (just thinking that being in blacklist would keep them off recognizing the USB drive).
   - Then I tried "mount /dev/sda /media/pendrive" and "...sda1,2,3" (crazy 'cause the TP600 only has 1 USB) but no good it did, it said "/dev/sdax does not exist".
   - then I typed "fdisk -l" and got only "devs.... hda1 hda2 hda5", so impossible to haveit if fdisk doesnt recognize it.
   - at last, the dmesg said something like:
 "usb 1-1: new full speed USB device using uhci_hcd and address 10
  usb 1-1: khubd timed out on op0in
  usb 1-1: device descriptor read/64m error -110
  usb 1-1: khubd timed out on op0in
  usb 1-1: device not accepting address 10, error -84
  usb 1-1: new full speed USB device using uhci_hcd and address 11
  usb 1-1: khubd timed out on op0in
  usb 1-1: device descriptor read/64m error -110
  usb 1-1: khubd timed out on op0in"
[/QUOTE]
It looks like an IRQ problem :S I noticed you were trying sda1,2,3....this would be like mounting partitions on sda, which wouldn't work. You need to try sda, sdb, sdc, sdd instead. Have you tried other pen drives? I have seen cases where certain pen drives just **wont mount** for no particular reason at all! It really is annoying, but if you can, borrow someone's pen drive to test.

Good Luck, your persistance is great, so many people I know would have given up by now. Oh, and thankyou for not pulling out the "oh, but on Windows I just...." that really gets to me.

---

### Post by shaka107 on 2005-09-25
Hi!, I have the same problem as you, with the sound card...

I have an IBM Thinkpad 770E.  My sound card is a CS4237B, and I have yet to try and get it working. When I try the fix here I get device not found etc... I was very lucky with my W-lan as Ubuntu supported and Orinoco Silver PC Card, but I would really like to get my sound working. If any of you have a simple and effective fix, please help

---

### Post by zapaces on 2005-09-29
Thanks to all.
After more than a few struggles I accept im only a user...
but a User who can't stand Window$, so I moved to something easier...
PC-BSD. Just fitted me... cool.
Hope ya'll the best.

---

### Post by sb73542 on 2005-10-14
[QUOTE=zapaces]Thanks to all.
After more than a few struggles I accept im only a user...
but a User who can't stand Window$, so I moved to something easier...
PC-BSD. Just fitted me... cool.
Hope ya'll the best.[/QUOTE]

Does your 600's soundcard work on PC-BSD??  How about suspend to RAM?  I'd switch myself if it worked out of the box.

---

### Post by sidd-tx on 2005-10-16
Sound not working on my ThinkPad 600E type 2645 either... This has been a problem with every distro though...  I had hoped, since Ubuntu has amazed me before with hardware support, that sound would work...

sb73542...
I used your suggestions: 
1)disable quick boot.....
2)added the "apm=on acpi=off" options to Grub...
3)modprobe snd-cs4236 port=0x530 cport=0x538 isapnp=0 dma1=1 dma2=0 irq=5 
modprobe snd-pcm-oss

and received the same error as shaka107

I just downloaded Breezy... I'll install that and see what happens....

If there are any other suggestions, I would really appreciate....

Sidd

---

### Post by REInvestor on 2005-11-02
I do not yet have sound working on my Thinkpad 600 using Ubuntu either, but I did get it running on Suse 9.1 and SimplyMEPIS using "alsaconf" and probing for cs4231, so I know it can be done.  Once I get my ethernet problem resolved, I will download alsasource and try to install it (yikes, don't really know how, but..).  I do want to point out I tried with great pains for a very long time to fix the sound to no avail until I turned off quickboot in the BIOS, if you do not know what that means and have been trying in vain, figure it out before trying anything else.

---

### Post by gotaserena on 2005-12-20
try to "setpnp <address> on" where address are the hexadecimals related to the sound card given by the "lspnp" command. The setpnp commands should be issue before modprobing the drivers.

Strangely, ubuntu turns the sound card **off** by default when booting.

---

### Post by conxorxa on 2005-12-21
I managed to get sound working on my Thinkpad 600 under Ubuntu 5.04.  I just put "apm=on acpi=off" in my /boot/grub/menu.lst and
then manually "sudo modprobe cs4232".
I was not able to get it to work under Ubuntu 5.10 though.

But I can't get my wireless card (Dlink DWL-G650) to work.  I compiled the madwifi-ng source but when I try:
sudo wlanconfig ath0 create wlandev wifi0 wlanmode sta,
I get: "wlanconfig: ioctl: No such device".
"sudo iwconfig" gives:
"lo     no wireless extensions.
sit0  no wireless extensions."
Nothing about ath0 or wifi0.
"sudo ifconfig ath0 up" gives
ath0: ERROR while getting interface flags: No such device.

I found some reports of problems with the TI PCI1250 cardbus bridge and "newer" pcmcia cards but nothing about how to fix the problem.

Any suggestions?

Thanks,

Steven.

---

### Post by zapaces on 2006-07-24
Ok, people, thanks to everyone for posting...
As I told you, I had moved to PC-BSD, which is aight, nice KDE enviroment but wow... SLOOOOW in this machine (tp600, I accept it's old and almos falling apart, but great nonetheless). It took me about 1 month to realize I was wasting too much time waiting for everything to happen in PC-BSD. So I installed WinXP light and worked all right. But I strongly dislike Window$ so as I knew Dapper was coming out, I decided to give it a try.
I went for something lighter, GNOME and KDE are way big for a 266 MHz and 128 MB Ram computer. So I downloded Xubuntu. I installed once and didn't like the Xfce, it's close to GNOME and still to slow. So... what's up with my machine now?.
I forgot about desktop enviroments (like GNOME, KDE or even Xfce) and searched for a window manager. After trying some of them I'm working with Fluxbox and it's great!.
My recomendation is, if you have a TP600 go for Flubuntu, nice taste.
I have the screen ok (after reseting it to 16 bits), the sound is working (thanks to [http://www.ubuntuforums.org/showthread.php?t=188736&highlight=tp600]("http://www.ubuntuforums.org/showthread.php?t=188736&highlight=tp600")  for all the information related to this).
I went for light software instead of things like OOo's stuff.
I have the full installation, even with LaTeX motor included for nothing else than 1GB. It takes some time to load certain software, like synaptic, but overall works great.
Im still working on Sleep/Hibernate, I don't know a lot of this stuff, but apparently they have something to do with ACPI (which I don't know what it means).

So Flubuntu on a tp600, that's mi choice.

---

