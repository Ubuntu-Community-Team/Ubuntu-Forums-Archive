---
title: "Ubuntu 8.10 on IBM Thinkpad 600E Type: 2645-4BU Sound, PCMCIA Slot, and Shutdown Fix"
date: 2009-01-28
forum: Hardware
---

### Post by Pyro121Psycho on 2009-01-28
Introduction:
Hello, I am your average kind of "I'm a PC" user who has recently discovered the joy's of Linux, but have had some troubles along the way. Hopefully if you have the same laptop I do, then hopefully this walktrough will save you a big headache.


What this is all about:
When Loading Ubuntu 8.10 Out of Box (Downloaded, then Burned to Disk for me) on this laptop (IBM Thinkpad 600E Type: 2645-4BU), The sound is non-functional, as well as most PCMCIA cards. Also the Shutdown feature does not turn off your laptop, It just hangs at the very end due to some ACPI config problems.


PCMCIA Card Slot: (The Slot thingy on the right side of this laptop)
Lets deal with the PCMCIA Card problems first.

Most network cards will work right off the bat, especially the ones that are made by 3Com (Mine being a 3Com Model: 3CCFE575BT).

Since the basic PCMCIA LAN cards work, I reccomend you use this card first as it should work.

When you plug in the PCMCIA LAN card, Ubuntu will auto-detect the card.

After this you should now be able to connect to the internet using Firefox (Great Mozilla Browser).


Getting Updates:
Since you now have a working network connection, you will want to first get all the needed updates. Do so by clicking "System"->"Administration"->Update Manager". After the Application starts, Click the "Check" button.

At this time, you should be asked for your Sudo (Admin) Password. This password is most likely the password you set for your account. The password prompt may appear or not appear randomly through-out these steps depending on how quickly you move through them.

Now go ahead and install all available updates by clicking the "Install" button and follow the steps accordingly.

You will be prompted to restart your computer. Go ahead and do so (Assuming you have either Printed or Bookmarked these instructions).


Installing other PCMCIA Items: (Mainly for wireless but may work for other types)
Now your computer has started back up. Lets go ahead and install that fancy Wireless card of yours (If you have one). If you do not have a wireless card, Skip these steps. 

Make sure you still have your network card plugged in still as you will need a working internet connection to get updated drivers for the wireless.

When you plug in your wireless card, you will get a popup at the top within about 60 sec. letting you know there is a driver for your wireless. (If the popup does not occour (I do apologize for the lack of info as I only had 1 card to work with and it was a Broadcom compatible card)

Go ahead and download your wireless drivers and restart your machine.


Configuring your Wireless:
You will be required to Manually configure your wireless (Unfortunatly). To manually configure, Right click on the Network Connection (Next to the Broken Sound Icon) toward the top-right of your screen and choose "Edit Connections".

Now click on the "Wireless" tab and choose "Add". Name your connection whatever you would like (Ex: Home or Friends House), as naming it "Wireless connection 1" is a little lame (Especially if you configue more than 1 wireless, the connections only by number may get confusing). Enter in the SSID* . Click on the "Wireless Security" tab and choose your Security Level* (If you have any) and enter your Security Key*. All other options will set themselves up. Now click OK
(* Your SSID, Security Level, and Security Key are within your routers settings. If you do not know them, read your routers manual on how to find out what they are as all routers are different). Now click "OK". If it does not connect, Check your settings against the router settings.

You will now be prompted to create a "KeyRing" you will have to enter this any time you connect to a wireless connection (Including your own every time you connect). Continue with creating your keyring (I made min the same as the Sudo (Admin) Password.

You should now be connected wirelessly.


Configuring your Sound Card in this laptop:
You will now have to work with a Terminal (DOS/CMD Type) Window. To open a Terminal window, Go to "Applications"->"Accessories"->"Terminal".

When the Terminal Window Opens, Type:

gksudo gedit /etc/modules

Make sure to include the spaces and hit the "Enter Key" (You may be prompted for your Sudo (Admin) Password). When the Document comes up, We need to add:

snd-cs4236

to the end of the pre-existant lines so you go from This:

**************************************************************************
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
**************************************************************************

to This:

**************************************************************************
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp

# IBM Thinkpad 600E
snd-cs4236
**************************************************************************

As you can see I threw in a little extra item of "# IBM Thinkpad 600E" in there. This is only for my future reference, but you can do the same if you wish because as you can see, Lines beginning with "#" are ignored in this file.

Click on "File" Then choose to "Save". You can now close this window.
Now for the next step. In your already existant Terminal Window, Type:

gksudo gedit /etc/modprobe.d/blacklist

and click "Enter" (May or May not be asked for Password). Now add:

# IBM Tinkpad 600E
blacklist snd-cs46xx
blacklist cs46xx

to the end of the document(As before, "# IBM Tinkpad 600E" is optional) and now save and close as we did before. On to the next step. In your Terminal window, Type:

gksudo gedit /etc/modprobe.d/alsa-base

and hit "Enter" (May be asked for password). We will now need to add a big chunk to the end of this, also, the line that starts with "options snd-cs4236" is to end with "dma1=1 dma2=0" from the next line as it was too long to show on one line in this forum. So, Copy and paste this at the bottom of the open document:

# IBM Thinkpad 600E
alias char-major-116 snd
alias char-major-14 soundcore
alias snd-card-0 snd-cs4236
options snd-cs4236 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0
alias sound-slot-0 snd-card-0
alias sound-slot-1 snd-card-1

alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

alias /dev/mixer snd-mixer-oss
alias /dev/dsp snd-pcm-oss
alias /dev/midi snd-seq-oss


Told ya it was long. Don't forget to make lines 5 and 6 into one line (May already show as One Line depending on your screen resolution). Save and close the document. Now for the very last change. Go to your open terminal window and type:

gksudo gedit /boot/grub/menu.lst

And hit "Enter" (May get password). Now, Add:

acpi=force pci=noacpi

to the first Kernal Line you get to, there are a few at the bottom of the page,  also, the line that starts with "kernel		/boot" is to end with "quiet splash acpi=force pci=noacpi" from the next line as it was too long to show on one line in this forum.For example, Mine went from:
**************************************************************************
## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		8e166a24-e75c-42ef-add5-e2a90ba25aff
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8e166a24-e75c-42ef-add5-e2a90ba25aff ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet
**************************************************************************

To:

**************************************************************************
## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		8e166a24-e75c-42ef-add5-e2a90ba25aff
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8e166a24-e75c-42ef-add5-e2a90ba25aff ro quiet splash acpi=force pci=noacpi 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet
**************************************************************************

The Kernel (Line 9 above) and the Next line (Line 10 above) are actually One Line, as from earlier on (May already show as One Line depending on your screen resolution). You may have to re insert the "acpi=force pci=noacpi" setting each time the Kernel gets an upgrade.

The Command of "acpi=force" fixes the sound and the shutting down problem but then causes the PCMCIA slot (For your Network/Wifi cards) to stop working and that is why you also have to add "pci=noacpi" as well to keep your PCMCIA card slot working.

Now all you have to do is perform a final restart and all should work well
I may later add information on getting the Dialup Modem port working on this thread.

---

### Post by garydion on 2009-02-01
Thank you very much for posting this!  Not only did it solve the sound problem on my 600e, but also a 2-minute delay in the boot sequence.  Most likely, the kernel commands are what fixed that wicked pause.

Take care - Gary

---

### Post by anthropop on 2009-03-25
For some reason it did not work on my 600E.  I checked and rechecked all the steps.  In fact, it would not boot into 8.10.11, only 8.10.7.  In 8.10.7 it has sound before I log in, it does that "bling" for user name.  Once I log in the sound does not work and no device is detected. "aplay -l" reports "no soundcards found".


> **garydion said:**
> Thank you very much for posting this!  Not only did it solve the sound problem on my 600e, but also a 2-minute delay in the boot sequence.  Most likely, the kernel commands are what fixed that wicked pause.

Take care - Gary

---

