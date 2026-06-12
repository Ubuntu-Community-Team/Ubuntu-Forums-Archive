---
title: "Help with sound card of my IBM 380Z"
date: 2006-04-01
forum: Hardware &amp; Laptops
---

### Post by Audiophiliac on 2006-04-01
Ubuntu 5.04 did not install soun card drivers for my IBM 380Z. How do I go about installing my sound card? 

I also need to install my wifi pcmcia card. I am an absolute newbie and totally zero with Terminal. 

Thanks.

---

### Post by FarEast on 2006-04-01
Hi Audiophiliac,

Unfortunately, your PC seems to have a sound chip on ISA bus...
It cannot be detected automatically.  So you have to know which chip it is.
Execute ' lspnp ' in a terminal window for infomation.

---

### Post by Audiophiliac on 2006-04-01
Did that and got this:

lspnp: /proc/bus/pnp not available

---

### Post by FarEast on 2006-04-01
OK
Now I am googling for information of the sound chip.
It may be cs4232...

I am not sure, but give a try;) .

$ sudo modprobe cs4232 io=0x530 irq=5 dma=1 dma2=0 mpuio=0x330 mpuirq=5

If it is not successful, execute:
$ cat /proc/interrupts
and paste the output.

---

### Post by Audiophiliac on 2006-04-01
First command resulted in an error: no such device

Second command yielded:

 CPU0
  0:    5100882          XT-PIC  timer
  1:        755          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  3:     236607          XT-PIC  serial
  5:          4          XT-PIC  1.0
  7:          0          XT-PIC  parport0
  8:          1          XT-PIC  rtc
  9:       1115          XT-PIC  acpi
 10:     100000          XT-PIC  uhci_hcd:usb1
 11:     200000          XT-PIC  yenta
 12:     238640          XT-PIC  i8042
 14:     168604          XT-PIC  ide0
NMI:          0
LOC:          0
ERR:          0
MIS:          0

---

### Post by FarEast on 2006-04-01
You need to reserve 'IRQ5' for the sound chip(ISA pnp device).
Enter BIOS setting on boot and look for an item for that.
When you have done, execute the first command once more;) .

---

### Post by Audiophiliac on 2006-04-01
Sorry but how do I go to Bios in linux?

---

### Post by FarEast on 2006-04-01
Restart the computer and hit some key(probably del or F2, etc), as shown on the screen;) .
It is the same to what you used to do(did you?) when you were using Windows.

Edit:
Sorry, I have to go to bed now.
Here are some clues.
[http://ubuntuforums.org/showthread.php?t=83451](http://ubuntuforums.org/showthread.php?t=83451)
[http://usalug.org/phpBB2/viewtopic.php?p=40759](http://usalug.org/phpBB2/viewtopic.php?p=40759)

---

### Post by Audiophiliac on 2006-04-01
Got to the Easy Screen using F1. My luck, nowhere can I reconfigure irq. It doesn't have the typical dos bios setup menu. Some gui by IBM.

---

### Post by Audiophiliac on 2006-04-02
You are on to something. Some guy did the following on his 380z. But I can't find the file.:

" added "modprobe -v cs4232 io=0x530 irq=5 dma=1 dma2=0" to line 138 of /etc/rd.1/rc.local0 for full soundcard support."

Still can't change irq on bios.

---

### Post by FarEast on 2006-04-02
> It doesn't have the typical dos bios setup menu. Some gui by IBM.

I have Thinkpad 390X and when I hit F1 the following message is shown:
Press Ctrl + S to enter the Setup program...

If I press the keys, I can enter 'IBM BIOS Setting Utility' with items:
-Config
-Date/Time
-Password
-Startup
-Restart

Edit:
If you cannot enter it, but see a blue-background screen, power off the computer and restart.
Hit F1 and you will see the blue screen again.  Then hit Esc and the computer restarts again.
Hit F1 again.  And you will be able to enter the setup.  Good luck!

---

### Post by Audiophiliac on 2006-04-02
I can enter that IBM Bios screeen. But nothing there to suggest IRQ assigment.

---

### Post by FarEast on 2006-04-02
OK...  Let's try the tip you found.

" added "modprobe -v cs4232 io=0x530 irq=5 dma=1 dma2=0" to line 138 of /etc/rd.1/rc.local0 for full soundcard support."

It can be done manually in the following way:
$ sudo modprobe cs4232 io=0x530 irq=5 dma=1 dma2=0

If it is successful, I will tell you how to describe the setting so that the system loads the module automatically on boot.

---

### Post by Audiophiliac on 2006-04-02
I got this message:

FATAL: Error inserting cs4232 (/lib/modules/2.6.12-9-386/kernel/sound/oss/cs4232.ko): No such device

---

### Post by FarEast on 2006-04-02
Now...

If you can disable the parallel port which uses IRQ7, give a try:
$ sudo modprobe cs4232 io=0x530 irq=[COLOR="SeaGreen"]7[/COLOR] dma=1 dma2=0

---

### Post by Audiophiliac on 2006-04-02
I didn't quite understand that. So I just typed that in the Terminal. Same error message: no device found. 

In case you meant at the bios, I went there and found no menu on parallel ports.

---

### Post by FarEast on 2006-04-02
Yes, I meant the bios setting by 'disable parallel port'.
With Thinkpad 390X, I can edit options for it as follows:
Config > Advanced Setup > Parallel Port
If there is no menu item for parallel port, it will be hard to keep an IRQ for the sound chip:-k .
I have helped some people who had problem with configuring sound chips on ISA bus.  But this time, I am at a loss what to do:( .

---

### Post by Audiophiliac on 2006-04-02
I appreciate all your help. Thanks.

On another subject, I recall when I installed Ubuntu, I initially installed 'server' instead of default. Then realizing my mistake, I installed the Ubuntu Gnome. Is that ok or should I reinstall default?

---

### Post by FarEast on 2006-04-02
I do not think you should reinstall the whole system.  I have not installed Ubuntu as server.  But I think there are some services which you do not need for desktop use.
Execute the command 'ps -A' and paste the output.

BTW According to information on the internet, Thinkpad 380z has only 64MB of RAM.  
Does Gnome run comfortably;) ?

---

### Post by Audiophiliac on 2006-04-02
Opening different windows and apps are sluggish. But once in one application like Firefox, it is ok. Overall it is manageable. Of course Win 2000 is a lot quicker. NT even faster. I am running Ubuntu 5.04 now.

This is acutally a test laptop. My everyday laptop is an Ibook G4. I am just curious about Linux.

---

### Post by FarEast on 2006-04-02
Try the Live-CD for PowerPC.  It will be much more comfortable.
I bought a used PC with Pentium III 1G, 512MB yesterday.  It did not come with a hard drive, so I am runnning a Live CD of Breezy (5.10).  It runs quite comfortably:) .

---

### Post by Audiophiliac on 2006-04-02
Does LiveCD run off from the cdrom and the internet? So my  OS X will be intact?

---

### Post by FarEast on 2006-04-03
Live CD remains OS-X intact, for it writes nothing on the hard drive.  And it configures the NIC automatically and sets an IP Adress with DHCP.

---

### Post by Audiophiliac on 2006-04-03
I see. That is cool.

It seems you are right. My irq situation is most likely culprit for my probs. Any solution I try and the card cannot be seen. Unfortunately, I cannot find a way to fix irq on my lappy. Anyway, I find the laptop functional at the moment. It is a slow machine anyway so I cannot watch videos.

---

### Post by Audiophiliac on 2006-04-04
I found the IBM tool but don't know what to do. Please view for reference:

[http://tpctl.sourceforge.net/PS2-ref.txt](http://tpctl.sourceforge.net/PS2-ref.txt)

---

### Post by FarEast on 2006-04-04
You have found interesting information.
Now I think the cause of your problem may be 'PnP BIOS'.

[http://tpctl.sourceforge.net/](http://tpctl.sourceforge.net/)

> isa-pnp driver
On my ThinkPad the PnP BIOS always configures ISA PnP devices at boot time, so the Linux isa-pnp driver (which was formerly distributed with the ALSA drivers but is now in the official kernel sources in the drivers/pnp/ directory) sees nothing to configure and reports "No Plug & Play device found" when it loads.  Therefore it's not of any use. 

Edit:

Anyway, if you are interested in the tool, you can install it in the following way:
$ sudo apt-get install tpctl

---

