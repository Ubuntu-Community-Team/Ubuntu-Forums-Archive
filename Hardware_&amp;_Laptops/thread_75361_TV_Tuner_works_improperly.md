---
title: "TV Tuner works improperly"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by web250 on 2005-10-13
My TV Tuner, a Hauppage WinTV Radio 401, is having some problems. It is detected correctly, right modules etc under lsmod. that in itself is a great improvement from Hoary to Breezy.

However, the card will not tune into channels correctly. It will only tune the last channel viewed in XP. 
ie: I watched channel 6 in XP, Ubuntu will only play channel 6, channel 11 shows channel 6, etc.

Where are the tuner settings to fix this. Editing /etc/modprobe.d/aliases does not override this as it did in hoary (which had perfect tv tuner support once you edited aliases).

---

### Post by syntaxerror64 on 2005-10-13
Hello, I don't have an answer to your problem but I have a Hauppauge WinTV Radio card as well.  What software are you using with it?  I just installed Ubuntu 5.10 and figured that WinTV is something I would just have to do under Windows.

---

### Post by web250 on 2005-10-13
I use tvtime, but xawtv is another often used program.

---

### Post by web250 on 2005-10-16
A bump, because this is my only problem holding me back from using Linux 24/7.

I just need to know how to either change the autoconfig (hotplug?) of the tv tuner mentioned above, or to disable it completely so I can define it in /etc/modprobe.d/aliases like I used to do.

---

### Post by SickTwist on 2005-10-16
Which module(s) is/are used for your card?

I know you're running Breezy but you mentioned Hoary--did you ever get this card to work correctly in Hoary?

Have you checked dmesg for any relevant information about the card (and possible errors)? If so, could you post that information here as well?

---

### Post by web250 on 2005-10-16
[QUOTE=SickTwist]Which module(s) is/are used for your card?

I know you're running Breezy but you mentioned Hoary--did you ever get this card to work correctly in Hoary?

Have you checked dmesg for any relevant information about the card (and possible errors)? If so, could you post that information here as well?[/QUOTE]

I use the cx88xx modules for the card. I had it working great in Hoary. In hoary I would edit /etc/modules.d/aliases and add:```
char-major-81-1 cx88xx
options cx88xx tuner=43
```
and voila, it would work.

I'll have to reboot for dmseg

---

### Post by web250 on 2005-10-16
Here's the dmesg output (i copied the part about the tuner)
```
[4294701.091000] Linux video capture interface: v1.00
[4294701.129000] cx2388x v4l2 driver version 0.0.4 loaded
[4294701.130000] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[4294701.130000] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [APC2] -> GSI 17 (l evel, high) -> IRQ 17
[4294701.130000] cx88[0]: subsystem: 0070:3401, board: Hauppauge WinTV 34xxx mod els [card=1,autodetected]
[4294701.292000] tveeprom: Hauppauge: model = 34132, rev = J158, serial# = 78155 61
[4294701.292000] tveeprom: tuner = Philips FM1236 MK3 (idx = 58, type = 4)
[4294701.292000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000 )
[4294701.292000] tveeprom: audio_processor = MSP3416 (type = 14)
[4294701.343000] cx88[0]: registered IR remote control
[4294701.343000] cx88[0]/0: found at 0000:01:09.0, rev: 5, irq: 17, latency: 32,  mmio: 0xe7000000
[4294701.355000] tda9885/6/7: chip found @ 0x86
[4294701.404000] cx88[0]/0: registered device video0 [v4l2]
[4294701.404000] cx88[0]/0: registered device vbi0
[4294701.405000] cx88[0]/0: registered device radio0

```

Its saying that the tuner type is 4. The correct tuner type should be 43. How can I override this?

---

### Post by web250 on 2005-10-16
Another bump, how can I make hotplug recognize my tuner correctly? This will affect many Ubuntu users, and should be fixed, as it should be very easy to do so!

[http://bugzilla.ubuntu.com/show_bug.cgi?id=16060](http://bugzilla.ubuntu.com/show_bug.cgi?id=16060)
That is the bug I filed when I ran into this problem with the 5.10 preview and Colony 5. Still have this problem with final.

---

### Post by web250 on 2005-10-18
Ok, next step in attempting to fix:

I read somewhere about editing /etc/modules to include a line about either:
```
cx88xx tuner=43
```
or
```
cx88xx card=##
```where ## is a number.


Would this work. I'm going to hopefully try tomorrow.

---

### Post by web250 on 2005-10-18
Ok. I tried blacklisting the modules and modprobing them manually.
Here's what happens:
```
sudo modprobe -v cx8800
insmod /lib/modules/2.6.12-9-386/kernel/drivers/media/video/videodev.ko
insmod /lib/modules/2.6.12-9-386/kernel/drivers/media/video/btcx-risc.ko
insmod /lib/modules/2.6.12-9-386/kernel/drivers/media/video/v4l2-common.ko
insmod /lib/modules/2.6.12-9-386/kernel/drivers/media/video/v4l1-compat.ko
insmod /lib/modules/2.6.12-9-386/kernel/drivers/media/video/tveeprom.ko
insmod /lib/modules/2.6.12-9-386/kernel/drivers/media/common/ir-common.ko
insmod /lib/modules/2.6.12-9-386/kernel/drivers/media/video/video-buf.ko
insmod /lib/modules/2.6.12-9-386/kernel/drivers/i2c/algos/i2c-algo-bit.ko
insmod /lib/modules/2.6.12-9-386/kernel/drivers/media/video/cx88/cx88xx.ko tuner=43
insmod /lib/modules/2.6.12-9-386/kernel/drivers/media/video/cx88/cx8800.ko

```

Now this *seems* right, as tuner=43 is the correct setting. However, I still only get one channel and TVtime complains about not getting the correct frequency from the tuner.

---

### Post by web250 on 2005-10-18
This is my last shot at things, I've exhausted all my options.

Ubuntu is a fantastic system, and 5.10 fixes numerous problems from 5.04 (remote control works, sounds takes no tweaking, more stable, Dell DJ works, etc.) but losing the ability to watch tv from 5.04 to 5.10 is incomprehensible.

This is a major stumbling block for me adopting Linux 24/7.

Someone please help. Don't force me to wait for 6.04 to hope my problem be solved.

---

### Post by SickTwist on 2005-10-18
I know it's fustrating but sometimes these things just take time. You own a piece of hardware that I would venture to guess is a bit uncommon among Ubuntu users so as a result this thread won't get as much attention. No doubt there will be others in your position but they are few and far between.

Since the card worked in Hoary there must be some way to make it work in Breezy, we just haven't discovered it yet.

Did you try putting "cx88xx tuner=43" (without quotes) on a new line in /etc/modules (you must reboot for this to take effect). I don't think you need to put any modules on the blacklist as that will prohibit them from loading. I'm not sure if any other parameters are necessary but the following is from modinfo cx88xx:

parm:           ir_debug:enable debug messages [IR] (int)
parm:           audio_debug:enable debug messages [audio] (int)
parm:           i2c_scan:scan i2c bus at insmod time (int)
parm:           i2c_debug:enable debug messages [i2c] (int)
parm:           nocomb:disable comb filter (int)
parm:           nicam:tv audio is nicam (int)
parm:           card:card type (array of int)
parm:           tuner:tuner type (array of int)
parm:           latency: pci latency timer (int)
parm:           core_debug:enable debug messages [core] (int)

You may also want to try looking for help in the Video For Linux community as they might be more equipped to handle this issue:
[Video4Linux Wiki]("http://linuxtv.org/v4lwiki/")
[Video For Linux Resources]("http://www.exploits.org/v4l/")
[Video4Linux Mailing List]("https://listman.redhat.com/mailman/listinfo/video4linux-list")

Could you please list the output of lspci?

---

### Post by web250 on 2005-10-18
[QUOTE=SickTwist]Could you please list the output of lspci?[/QUOTE]

[https://bugzilla.ubuntu.com/show_bug.cgi?id=16060](https://bugzilla.ubuntu.com/show_bug.cgi?id=16060)

That has two lspci outputs (-v and -vv)

---

### Post by SickTwist on 2005-10-19
I was studying the output from dmesg and lspci when I noticed this:

Tuner = Philips FM1236 MK3 (idx = 58, type = 4)

And I just found this on the video4linux wiki:

tuner=43 - Philips NTSC MK3 (FM1236MK3 or FM1236/F)

so the tuner definitely should be 43. I also read that you may need to add tda9887 to /etc/modules as well so it should look like this:

```
cx88xx tuner=43
tda9887
```

Save it and **turn off your computer**. I read that some cards don't get reinitialized unless the power is cut off. Then start it up again and see if that does it.

---

### Post by web250 on 2005-10-19
Ok, i added cx88xx tuner=43 to /etc/modules and it didn't change anything.

Here's what lsmod looks like (copied the important stuff):
```
cx88xx                 54176  1 cx8800
i2c_algo_bit            9480  1 cx88xx
video_buf              21316  2 cx8800,cx88xx
ir_common               7620  1 cx88xx
btcx_risc               4936  2 cx8800,cx88xx
tveeprom               13208  1 cx88xx
i2c_core               21328  6 i2c_acpi_ec,tda9887,i2c_nforce2,cx88xx,i2c_algo_bit,tveeprom
videodev                9536  2 cx8800,cx88xx

```

---

### Post by SickTwist on 2005-10-19
Are you in the United States or somewhere else that uses the [NTSC]("http://en.wikipedia.org/wiki/NTSC") TV format? That is how your card is currently configured.

EDIT: Also, see my note above about tda9887

---

### Post by web250 on 2005-10-19
[QUOTE=SickTwist]Are you in the United States or somewhere else that uses the [NTSC]("http://en.wikipedia.org/wiki/NTSC") TV format? That is how your card is currently configured.

EDIT: Also, see my note above about tda9887[/QUOTE]

I saw your edit above, and I added that line and did a hard boot. 

Now I have no video whatsoever, yet TVtime is not giving any errors.

And yes, im in the US, im NTSC

---

### Post by web250 on 2005-10-19
Some more lsmod lines:
```
cx8800                 31692  0
v4l1_compat            14788  1 cx8800
v4l2_common             5824  1 cx8800

```

I know this card needs the cx88xx module, shouldn't v41 reflect that the cx88xx module is using it?

---

### Post by SickTwist on 2005-10-19
I'm not sure how to check if v4l is using it.

I'm reading [this]("http://tvtime.sourceforge.net/problems.html#undetected") information on the TVtime website to see if it gives us any ideas.

---

### Post by web250 on 2005-10-19
This is now repeated over and over again in dmesg

[4295534.966000] cx88[0]: irq pci [0x1] vid*

---

### Post by SickTwist on 2005-10-19
I'm trying to verify what your card # should be but I'm having difficulty finding that information.

---

### Post by web250 on 2005-10-19
Ok, i removed the lines in /etc/modules as that only seemed to cause problems. However, even after reverting back, I still have no signal whatsoever now.

---

### Post by web250 on 2005-10-19
An lspci -v output:

```
0000:01:09.1 Multimedia controller: Conexant: Unknown device 8801 (rev 05)
        Subsystem: Hauppauge computer works Inc.: Unknown device 3401
        Flags: bus master, medium devsel, latency 32, IRQ 12
        Memory at e8000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <available only to root>

```

See how it shows Unknown device?

The other entry for multimedia controller shows it as a Winfast 2000xp. Thats wrong.

Somethings not being detected right...

---

### Post by SickTwist on 2005-10-19
Yeah I noticed that. The problem is I can't seem to find a list of cards so you can pass it the correct number. We know tuner=43 but I'm not sure what number the card parameter should be. I've looked through the kernel documentation but it only has a list of the tuners. I also checked the v4l wiki but I did not see it there either. Maybe I'm just missing it.

EDIT: I'm looking through the Hauppauge website for ideas and I noticed that there are [two versions]("http://www.hauppauge.com/pages/support/support_pci_boards.html") of the WinTV-Radio card. Are you able to verify the chipset that your card is using? I know that the driver thinks it is 34132 but I can't verifiy that without physical access.

---

### Post by web250 on 2005-10-19
It's the second one IIRC, the 881 chip. 
The original guide I followed for Hoary is this:
[http://newinteractive.linuxjournal.com/article/8116](http://newinteractive.linuxjournal.com/article/8116)
With some obvious modifications to make it run for Ubuntu rather than Fedora (which the guide is written for). Important to take note on is the notes that talk about the newer versions using the cx88xx module instead of the cx8800 module, ie: my cards situation

---

### Post by SickTwist on 2005-10-19
The 881 chip has "CX23881-27" printed on it on Hauppauge's site. This is the same chip described in the Linux Journal article that you linked. Have you tried using the cx8800 module in Breezy as that article describes? Perhaps it would work? Again, I would try all this after a hard reboot so that the TV card is completely reinitialized.

Another option that might be worth considering: You could install the Hoary kernel in Breezy-- that might take care of the problem (although it might break other packages in Breezy that were not tested with 2.6.12).

---

### Post by web250 on 2005-10-19
I'm not gonna try the Hoary kernel, as many features added with breezy i also want. I dont want to fix the tv and lose the other things.

Another user has identified this problem as well (the channel sticking). He has posted in the bugzilla thread confirming his problem. 

Now that this is certainly not a 1 user problem the developers will take a look into it?

---

### Post by SickTwist on 2005-10-19
I believe you can run the Hoary kernel with Breezy. You'd basically have to add the Hoary repositories to /etc/apt/sources.list then install a new kernel forcing it to be the version from Hoary. Like I said though, not sure if it would break anything else. At least that way you could keep all of the other packages from Breezy.

Perhaps the Ubuntu developers will look into it but it will be difficult if they do not own the same card that you do. Most likely Ubuntu will pass your bug upstream.

I think that you should send an e-mail to the Video4Linux list describing your problem. Include the dmesg and lspci info. Also let them know which distro you're running and the kernel version. That list may be able to suggest a solution. Also be *very* specific when you tell them what card you have (model, chipset, revision--don't rely on lspci, look at the card itself or the box if you can).

I really do hope it works out. I wish I could give more assistance but I don't have a card like yours so that makes it a bit more complicated for me to diagnose.

One last thing: If you do figure out how to make it run with the Breezy kernel, post it here so anybody else with the same issue will have an easier time fixing it.  Best of luck! :)

---

### Post by fragmental on 2005-10-30
looke like you need to set "card=x" when loading the module

From  [http://tvtime.sourceforge.net/problems.html#undetected](http://tvtime.sourceforge.net/problems.html#undetected)
> 6. Unable to tune to channels using the bttv, saa7134 or cx88 drivers

The bttv, saa7134, and cx88 drivers each support a wide variety of cards which all use the same chip. In particular, these cards differ in what tuner they use, how many inputs they have, and how it is configured.

Often, these drivers cannot autodetect the card type, or detect the incorrect card. To debug this, you must watch your kernels logs by running the "dmesg" command, potentially loading and unloading the driver with different options until the driver is successfully loaded.

Some hints:

   1. If your card appears as UNKNOWN/GENERIC, then the tuner driver will not be loaded and the card will likely not work. You will need to load the driver with the correct card number.
   2. If your tuner reports that it is using type -1, it is not loaded and you will not be able to tune any stations.
   3. If you are an NTSC user, make sure the tuner you are using announces itself as an NTSC tuner. 

For example, if you are using the bttv driver, the common procedure for setting up a card is as follows:

   1. Run "modprobe bttv" with no options.
   2. Run "dmesg". Check to see if your card is autodetected, and if the tuner is correct. If everything looks fine, you're done.
   3. If the card appears as UNKNOWN/GENERIC, find the CARDLIST file in your kernel documentation and find your card in the list.
   4. Unload bttv and tuner using "rmmod bttv" and "rmmod tuner".
   5. Run "modprobe bttv card=X" where X is the number of your card.
   6. Run "dmesg" again. See if the card loaded properly and if the tuner is correct.
   7. If not, unload bttv and tuner again, and try specifying the tuner type as well using "modprobe bttv card=X tuner=Y".
   8. Curse Linux for being so complicated. 

I found a card list at [http://linuxtv.org/v4lwiki/index.php/Cx88_devices_%28cx2388x%29](http://linuxtv.org/v4lwiki/index.php/Cx88_devices_%28cx2388x%29)

---

