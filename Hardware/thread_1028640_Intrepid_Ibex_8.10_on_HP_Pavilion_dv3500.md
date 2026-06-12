---
title: "Intrepid Ibex 8.10 on HP Pavilion dv3500"
date: 2009-01-02
forum: Hardware
---

### Post by A.Wingrove on 2009-01-02
I just thought I would post my (very good) experience of Ubuntu 8.10 on an HP Pavilion dv3500 series laptop (dv3507ea to be exact).

First of all, what works:

* Wireless networking works flawlessly. I connects to my router much faster than my old laptop. I believe it has an Intel 5100 AGN chip.

* Sound and volume worked correctly without any changes in settings.

* Multimedia softkeys work fine too.

* Hibernate seems to work fine. It does throw a couple of ACPI warnings, but works fine anyway.

What didn't work:

* Screen brightness was stuck on full by default (which is eye-strainingly bright!). I installed the latest version of nvclock from cvs and I can now control brightness with that. (Follow the screen brightness instructions as for [Ubuntu on a new MacBook]("https://help.ubuntu.com/community/MacBook%20Aluminum")).

* Remote control. Using xev, no key events are registered for any of the buttons. Will need to investigate with some Ir software.

* Fingerprint reader is not yet supported. It is made by Validity appears on fprint's [unsupported device list]("http://www.reactivated.net/fprint/wiki/Unsupported_devices#Validity_VFS101").

Overall:

I am very pleased with the laptop. It's fast, has good battery life, and is quite compact. The only significant problem was the screen brightness, but that was straight-forward to fix. I think anyone would be very happy running Ubuntu on this model.

---

### Post by fresneda on 2009-01-31
Hi, I have the same laptop (dv3525ef), which has an

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

as audio device. Using kernel 2.6.28, I don't get any sound output unless I pass the parameter model=dell-m4-1

Unfortunately, my capture device is not working: alsamixer shows two mics, but they only record noise. Have you managed to get your mic working? If so, with what kernel?
thanks.

---

### Post by A.Wingrove on 2009-02-01
I'm on standard Intrepid 64bit, which I believe is 2.6.27? Anyway, I just tried it and recording doesn't work on mine either. Sound output hasn't been a problem though.

You might try a newer version of Alsa if there is one.

---

### Post by A.Wingrove on 2009-02-02
OK, I've tried Alsa 1.0.19 on the latest Intrepid 2.6.27-11. Unfortunately it has made no difference and still cannot record anything.

---

### Post by fresneda on 2009-02-10
Hi, good news. With the help of Takashi Iwai, I managed to get my mic to work. This is what you do: 
compile the latest alsa-driver snapshot
edit /etc/modprobe.d/alsa-base to contain
options snd-hda-intel model=hp-dv5
then reboot
It is important to reboot, because simply unloading the module and loading it again with new parameters might not work.
good luck!

---

### Post by A.Wingrove on 2009-04-28
Thanks for highlighting that option. I haven't tried the mic, but playback is much better with Alsa 1.0.19.

It's a shame that Jaunty 9.04 doesn't include 1.0.19. I just upgraded the laptop and everything works just as well as before. Better actually as the integrated webcam worked first time in Cheese.

---

### Post by kazuo_teramoto on 2009-05-24
Someone have more info about the remote control? I cant find it listed on lsusb and lspci. Someone can post the output of lsusb and lspci?

EDIT Found it. Its listed on /sys/bus/acpi/devices/ITE8708:00

---

### Post by fresneda on 2009-05-28
So I assume it is a hid device...have you managed to get it working? xev does not recognize the imput from my remote, but maybe I am missing a kernel module. Any luck?

Note: I am using a self-compiled kernel 2.6.29 and debian lenny.

---

### Post by kazuo_teramoto on 2009-05-29
Lirc have a driver for a similar CIR (for ITE 8709 CIR) I'm trying to get the datasheet and see how similar they are. I tried the driver but I cannot get it to work (I dont know how to make lirc work too so someone can have success).

I gonna use this topic to post if I get so results (I'm using 2.6.29 Arch Linux)

---

### Post by fresneda on 2009-05-30
I compiled the latest source from lirc.org (0.8.5), and it doesn't contain drivers for ITE8708, but it does support  ITE8709. Now I get a lirc0 device in /dev, but mode2 -d /dev/lirc0 does not output anything, nor does xev pick up any signals. 
I guess we'll have to wait a little bit for irda support (perhaps the latest kernels have native support?).

---

### Post by kazuo_teramoto on 2009-06-04
I made contact with the makes of CIR, ITE tech, asking for specs so I can write the driver and they replied to me:

> Dear Sir,
>        Really thank you for your great job. We already have ITE8708 CIR 
> Linux driver. You can ask your NB maker for it! If not, you can ask us 
> for this generic driver.
>

^_^ When get some more info I will reply. (The ITE tech support is really friendly and fast)

---

### Post by eaglecros on 2009-06-07
Hm.

For some reason I am not able to find out, my microphone array is still not working. I compiled the newest version alsa libs/driver/utils, so that:
$ alsactl -v
alsactl version 1.0.20

and

$ cat /etc/modprobe.d/alsa-base
options snd-hda-intel model=hp-dv5

and rebooted, but my microphones are still not recording anything. I have activated capture in all the controls. Could you please lead me to some hint as of what the problem might be?

Follows a couple of details I think could be interesting:


$ arecord --list-devices
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1


and a link to pastebin with arecord --list-pcm and amixer output:

[http://pastebin.com/m66473cc8](http://pastebin.com/m66473cc8)

Any help is appreciated! And thanks for posting this thread in the first place!!

---

### Post by the_guv on 2009-07-27
HP Pavilion DV 3500 or DV 3000 on Jaunty 9.04, using IDT 92HD71B7X codec

..

surprisingly, pretend you have a Dell and use this ..

options snd-hda-intel model=dell-m4-1

.. working that out took far toooooooooo long. thank you, Ubuntans, for the guidance. (and sod off HP, whose Linux support is pathetic.)

---

### Post by sn3rd on 2009-09-07
> **kazuo_teramoto said:**
> I made contact with the makes of CIR, ITE tech, asking for specs so I can write the driver and they replied to me:

> Dear Sir,
>        Really thank you for your great job. We already have ITE8708 CIR 
> Linux driver. You can ask your NB maker for it! If not, you can ask us 
> for this generic driver.
>

^_^ When get some more info I will reply. (The ITE tech support is really friendly and fast)

I have the same device, the ITE8708. I also emailed them and explicitly stated that I needed the driver and my manufacturer (Dell) hadn't provided me with one.

So I received a friendly reply with two files attached:

lirc_it85.c
lirc_it85.h

That's great.

Except now I have no idea how to configure LIRC to work with these drivers? Any ideas?

---

### Post by kazuo_teramoto on 2009-09-09
I received some code from ITE, a skeleton drive.

But the problem is I dont know what chipset ITE8708 is. ITE8708 is bios pnp id not the real chipset.

I asked HP for the chipset but they redirect me to advanced support and they dont replied yet.

If someone find what chipset is used in dv3500 someone (me, maybe) can write a driver for it.

Someone willing to unpack the laptop and search for info?

---

### Post by kazuo_teramoto on 2009-09-13
Ok HP don't give *any* good answer. I tried to unpack my dv3510 to discover the chipset, but I not succeeded to open it :(

If some one unpack it a give us some pictures (and the text imprint) of the CIR I can ask for ITE for specs and write a driver.

Someone can try to unpack the laptop?

---

### Post by oliver.greg@gmail.com on 2009-09-20
Have you contacted the lirc people with those files?  I am in the same boat with my XPS 16...

---

### Post by tjodSK on 2009-10-04
i've done a little research on this. The ITE8708 seems to be combination of ITE8512 SuperIO with SIR chip...

i guess this is very similar to the ITE8709. I tried to dissect the lirc_ite8709... with some adjustments (i changed the IO to 0x310) the driver seems to pick up the device, dmesg (after modprobe lirc_ite8709) shows:

lirc_dev: lirc_register_driver: sample_rate: 0
lirc_ite8709: device found : irq=4 io=0x310

but mode2 nor irrecord does produce any output...

---

### Post by evil-noxx on 2009-12-29
It seams i have the same remote as you are discussing here. I'm also having trouble getting it to work...
Did anyone come up with a working solution?

---

### Post by costing on 2009-12-30
Could you please post the two files (lirc_it85.c and .h) ? I'm having the same kind of hardware that no drivers can use :)

---

### Post by tjodSK on 2010-01-02
> **costing said:**
> Could you please post the two files (lirc_it85.c and .h) ? I'm having the same kind of hardware that no drivers can use :)

unfortunately, those files are useless. most of the code is already part of the official lirc ite drivers (however, it is not for the ITE8708). They don't even compile with newest lirc...

---

### Post by bheremans on 2010-01-05
I googled a bit and have seen that the windows vista driver for the ite8708 and ite8709 is the same driver.

[http://komku.blogspot.com/2008/07/acer-aspire-6920g-windows-xp-and-vista.html](http://komku.blogspot.com/2008/07/acer-aspire-6920g-windows-xp-and-vista.html)

I downloaded the lirc sources and did some modifications in drivers/lirc_ite8709/lirc_ite8709.c
	- I renamed everything from ite8708 to ite8709
	- changed
	if (!pnp_irq_valid(dev, 0))
		return ite8709_cleanup(NULL, 0, -ENODEV, "invalid IRQ");
	if (!pnp_port_valid(dev, 2))
		return ite8709_cleanup(NULL, 0, -ENODEV, "invalid IO port");
	to
		if (!pnp_irq_valid(dev, 0))
		return ite8709_cleanup(NULL, 0, -ENODEV, "invalid IRQ");
	if (!pnp_port_valid(dev, 0))
		return ite8709_cleanup(NULL, 0, -ENODEV, "invalid IO port");
	-changed
	ite8709_dev->irq = pnp_irq(dev, 0);
	ite8709_dev->io = pnp_port_start(dev, 2);
	to
		ite8709_dev->irq = pnp_irq(dev, 0);
	ite8709_dev->io = pnp_port_start(dev, 0);

I compiled and loaded the drivers. lirc seems to find the device now : IRQ 4, IO 0x310 (same as windows resouce)
But mode2 or irrecord seems to do nothing.

I'm not a kernel expert, I just tried a bit ...

---

### Post by tjodSK on 2010-01-05
Hello,

i tried this already, but no success. Could you check with dmesg whether this line loads fine? 

```
	if (!request_region(ite8709_dev->io, 2, LIRC_DRIVER_NAME))
		return ite8709_cleanup(ite8709_dev, 3, -EBUSY,
				"i/o port already in use");
```

it is lirc_ite8708.c around line 480.

However, the combined drivers are mostly for 8705,8,9 and sometimes even 12,15 or 20.

i tried disassembling some drivers, but it seems to contain larger blocks of "if-then" blocks based on current hardware. I guess the main difference is in register address and maybe some differences in communication protocol. This would need probably someone with lirc knowledge. I read somewhere that this cir is blocked to be used with Windows only, but i doubt it's true.

cheers

---

### Post by bheremans on 2010-01-06
I added printk:


```
	if (!request_region(ITE8708_dev->io, 2, LIRC_DRIVER_NAME))
		return ITE8708_cleanup(ITE8708_dev, 3, -EBUSY,
						"i/o port already in use");
	else
		printk(KERN_INFO LIRC_DRIVER_NAME ": request region done");
```
	
(I have renamed alle ITE8709 to ITE8708 previously)

dmesg shows :

```
root@bhe-hp:~# dmesg | grep lirc
[   12.585890] lirc_dev: IR Remote Control driver registered, major 61
[   13.366776] lirc_dev: lirc_register_driver: sample_rate: 0
[   13.366816] lirc_ITE8708: request region done
[   13.366873] lirc_ITE8708: device found : irq=4 io=0x310

```

So I assume it loads fine

---

### Post by tjodSK on 2010-01-07
will you mind sharing the modified code?

---

### Post by bheremans on 2010-01-07
I uploaded it to pastebin

[http://pastebin.com/f7ee02b29](http://pastebin.com/f7ee02b29)

This is lirc-0.8.6/driver/lirc_ite8709/lirc_ite8709.c file that I modified

---

### Post by tjodSK on 2010-01-07
thank you.. 
can you post output of the ```
cat /proc/ioports
``` with module in and out of the kernel?

---

### Post by tjodSK on 2010-01-07
there seems to be a problem with release somewhere in the module, i'm not able to modprobe & rmmmod and modprobe again... and in the /proc/ioports i can see the 0310-0311 range taken even when module is unloaded...

---

### Post by bheremans on 2010-01-08
cat /proc/ioports

```
0060-0060 : keyboard
0064-0064 : keyboard
0070-0077 : rtc0
0080-008f : dma page reg
00a0-00a1 : pic2
00c0-00df : dma2
00f0-00ff : fpu
0310-0311 : lirc_ITE8708
03c0-03df : vga+
0400-047f : pnp 00:01
  0400-0403 : ACPI PM1a_EVT_BLK
  0404-0405 : ACPI PM1a_CNT_BLK
  0408-040b : ACPI PM_TMR
  0420-042f : ACPI GPE0_BLK
  0450-0450 : ACPI PM2_CNT_BLK
0500-0501 : pnp 00:01
0600-060f : pnp 00:01
0610-0610 : pnp 00:01
0700-073f : pnp 00:01
0800-080f : pnp 00:01
0810-0817 : pnp 00:01
0820-0823 : pnp 00:01
0cf8-0cff : PCI conf1
1000-1fff : PCI Bus 0000:05
2000-2fff : PCI Bus 0000:03
3000-4fff : PCI Bus 0000:02
  3000-30ff : 0000:02:00.0
    3000-30ff : r8169
5000-5fff : PCI Bus 0000:01
  5000-507f : 0000:01:00.0
6000-601f : 0000:00:1f.3
6020-603f : 0000:00:1f.2
  6020-603f : ahci
6040-605f : 0000:00:1d.3
  6040-605f : uhci_hcd
6060-607f : 0000:00:1d.2
  6060-607f : uhci_hcd
6080-609f : 0000:00:1d.1
  6080-609f : uhci_hcd
60a0-60bf : 0000:00:1d.0
  60a0-60bf : uhci_hcd
60c0-60df : 0000:00:1a.1
  60c0-60df : uhci_hcd
60e0-60ff : 0000:00:1a.0
  60e0-60ff : uhci_hcd
6100-6107 : 0000:00:1f.2
  6100-6107 : ahci
6108-610f : 0000:00:1f.2
  6108-610f : ahci
6110-6113 : 0000:00:1f.2
  6110-6113 : ahci
6114-6117 : 0000:00:1f.2
  6114-6117 : ahci
```

this seems not correct : 0310-0311 : lirc_ITE8708
in windows range is 0310-0317

maybe thats the reason in can be removed and modprobed again.

---

### Post by tjodSK on 2010-01-08
no. the problem is different... actually, the output of /proc/ioports shows io ranges claimed by drivers. In our ite_8709 we reserve port from base address 0x310 and 2 bits long.

however, the problem why we can't reload the module lies in releasing the claimed io range... see this in the driver:

```
        case 4:
                release_region(dev->io, 2)

```;

i guess your's does release region of size zero. After you fix and recompile, you'll have to reboot to release the claimed range completely.


But, you might be right with the IO range... i wondered why this driver uses only TWO bits, it seems rather strange. If the driver in windows uses 8bits it might suggest we started the examination of wrong driver :)

In lirc, there is a driver called lirc_it87. It won't load at all at first, but after some modifications it did - but does not work, it's just the same as the lirc_ite8709... However, the code in this driver looks promising. I digged up somewhere (will provide the link later, it was linuxbios or something) that the ITE8708 does need enable sequence of 0x87 0x87 to be sent when initializing. I was able to find something similar in this driver. This will need a bit of investigation, but i think it looks promising.

Another argument to support this theory is the ite driver i received from the ITE support. I'm sharing my modified lirc_ite87 along with the driver received from lirc, maybe you'll come up with something.

I included the original ITE's (*85) and modified lirc drivers (*87).

---

### Post by bheremans on 2010-01-08
i already fixed the unloading problem. but like you said it did not fix the io range problem. I also had modified the i87. driver. it did load and unload successful. it even shows the right io range. but it did do nothing in mode2. i will look at your files later this weekend.

---

### Post by bheremans on 2010-01-09
I renemad some stuff and changed a few lines in it_85.c then I copied them to the lirc_it87 driver direcotry renamed the files to it87.c and it87.h to comple them... mode2 showed some data :-) after 1 button press, then blocks..

dmesg (modprobe with debug=1)

```

[ 8624.327255] lirc_it87: found it8712.
[ 8624.327317] lirc_it87: I/O port 0x0310, IRQ 4.
[ 8624.327363] lirc_it87: Installed.
[ 8653.074250] lirc_it87: iir: 0x2 fifo: 0x2
[ 8653.074261] lirc_it87: data=00
[ 8653.074267] lirc_it87: t 16777215 , d 0
[ 8653.074272] lirc_it87: add flag 0 with val 16777146
[ 8653.074296] lirc_it87: data=00
[ 8653.074301] lirc_it87: t 35 , d 0
[ 8653.077945] lirc_it87: iir: 0x2 fifo: 0x3
[ 8653.077957] lirc_it87: data=00
[ 8653.077963] lirc_it87: t 3662 , d 0
[ 8653.077967] lirc_it87: GAP
[ 8653.077971] lirc_it87: add flag 1 with val 104
[ 8653.077989] lirc_it87: add flag 0 with val 3593
[ 8653.078008] lirc_it87: data=00
[ 8653.078014] lirc_it87: t 51 , d 0
[ 8653.078030] lirc_it87: data=00
[ 8653.078035] lirc_it87: t 21 , d 0
[ 8653.120034] lirc_it87: timeout add 1 for 141 usec
[ 8653.120042] lirc_it87: add flag 1 with val 141

```

mode2 :

```

root@bhe-hp:~/lirc-0.8.6/drivers/lirc_it87# rmmod lirc_it87
root@bhe-hp:~/lirc-0.8.6/drivers/lirc_it87# modprobe lirc_it87 debug=1
root@bhe-hp:~/lirc-0.8.6/drivers/lirc_it87# mode2 -d /dev/lirc0
space 16777180
pulse 122
space 3463
pulse 129
space 563
pulse 99
space 781
pulse 35
space 1291
pulse 35
space 1305
pulse 35
space 2183
pulse 35
space 875
pulse 92
space 855
pulse 72
space 747
pulse 35
space 858
pulse 35
space 845
pulse 35
space 868
pulse 88
space 803
pulse 92
space 776
pulse 35
space 855
pulse 35
space 856
pulse 35
space 1307
pulse 35
space 847
pulse 35
space 854
pulse 35
space 1291
pulse 35
space 851
pulse 35
space 854
pulse 35
space 853
pulse 35
space 854
pulse 35

```

Modifief files in attachement
I had to put line 977 in comment to compile.. didn't like that

But there is progres !

---

### Post by tjodSK on 2010-01-09
good job! this looks promising. I changed the commented line to 

```
	outb(it87_CIR_C0TCR1_TXRLE | it87_CIR_C0TCR1_TXENDF, io+it87_CIR_C0TCR);
```

now compiles fine, but the module seems to "hang" after i press key on my remote... do you experience the same behavior?

---

### Post by tjodSK on 2010-01-09
i fixed the hang-up issue! Just load the module with digimatrix parameter in config (or change #ifdef LIRC_it87_DIGIMATRIX to #ifndef LIRC_it87_DIGIMATRIX)

mode2 works,the irrecord works as well (does produce the dots as output).

UPDATE:

tried irrecord:

```
Press RETURN now to start recording.
................................................................................
Found const length: 71680
Please keep on pressing buttons like described above.
................................................................................
RC-6 remote control found.
No header data.
No repeat code found.
Signals are biphase encoded.
Signal length is 41
Checking for toggle bit mask.
Please press an arbitrary button repeatedly as fast as possible.
Make sure you keep pressing the SAME button and that you DON'T HOLD
the button down!.
If you can't see any dots appear, then wait a bit between button presses.

Press RETURN to continue.

No toggle bit mask found.
But I know for sure that RC6 has a toggle bit!
```

---

### Post by markitoxs on 2010-01-09
omg, I just found this thread and looks promising. 

I am gonna try to re read it all carefully and assist where possible.

---

### Post by tjodSK on 2010-01-09
i digged up more into this... I found out that the digimatrix support only does make a difference in the timeout method (line 462)... If the condition is changed to 

```
 	if (!digimatrix) { 
``` and digimatrix is zero
 then it *works* - i mean it does not hang at least... However, there seems to be problem with the toggle bit mask (as stated by irrecord).

I tried even using the template for RC6 remote from drivers/ directory of lirc installation. Then i get message "Something bad happened." if i try to press any button on the remote.

---

### Post by tjodSK on 2010-01-10
hello there,

few more fiddling with the driver, now i'm able to get a stable waveform (i can see it with xmode2), but still no success with irrecord... it's frustrating.

---

### Post by bheremans on 2010-01-10
Please post your modified code, I will have a look tomorrow if I find anything. I didn't had to much time this weekend.

---

### Post by tjodSK on 2010-01-10
of course, here you go.

what i've found so far...

it actually "partially" works when using "raw codes" in lirc config.
 i.e. try this as your lircd.conf: 

```
begin remote

  name   dv3
  flags CONST_LENGTH|RAW_CODES
  eps            30
  aeps          100

  ptrail           0
  repeat     0     0

  gap 51199

      begin raw_codes

          name power 
     2414     1174      206      691      206      691
      206     1105      206     1105     1034     1174
      206      691      206      691      206      691
      206      691      206      691      206      691
      206      691      206      691      206      691
      206      691      620      691      206      691
      206      691      206     1105      206      691
      206      691      206      691      206      691
      620     1174      206      691      206      691
      206      691      206      691      206      691
      620      691      206     1105      206      691
      206
      end raw_codes

end remote

```

and launch lircd and irw... pressing the power button repeatedly should work (but only every other time). I expected this behavior, you could easily see the cause with xmode2. This remote does constantly exchange two bits (i think it's the 20th and 21st signal) as you press the buttons so lirc can not match against the raw code... 

using ```
xmode2 -m -t 1
``` is very useful while debugging.

If i use digimatrix flag then the output is "smooth", without this it is somewhat "fuzzy". I changed the baud rate divisor to 0x8, this probably fixed hanging of the code.

Compiling lirc with debug support and then using lircd -D3 sheds some light on the obscure errors, as well the irrecord is much more verbose now...

See if you'll come up with something.

---

### Post by tjodSK on 2010-01-10
**UPDATE!**

i managed to get it working! it's pretty ugly hack, i admit, but works (for me, at least). Using driver attached in previous post.

output of irw:

```
sudo irw 
0000000000000001 00 power hp-dv3
0000000000000002 00 key_home hp-dv3
0000000000000003 00 key_repeat hp-dv3
0000000000000004 00 key_play hp-dv3
0000000000000005 00 key_dvd hp-dv3
0000000000000006 00 key_rewind hp-dv3
0000000000000007 00 key_stop hp-dv3
0000000000000008 00 key_fastforward hp-dv3
0000000000000009 00 key_prev hp-dv3
000000000000000a 00 key_up hp-dv3
000000000000000b 00 key_next hp-dv3
000000000000000b 00 key_next hp-dv3
000000000000000c 00 key_left hp-dv3
000000000000000d 00 key_ok hp-dv3
000000000000000e 00 key_right hp-dv3
000000000000000e 00 key_right hp-dv3
000000000000000f 00 key_exit hp-dv3
0000000000000010 00 key_down hp-dv3
0000000000000011 00 key_info hp-dv3
0000000000000012 00 key_volumedown hp-dv3
0000000000000013 00 key_mute hp-dv3
0000000000000014 00 key_volumeup hp-dv3
```

looks gooood ;)

and now, the butchered raw lircd conf:

```
#
# this bogus config file was butchered by hand by tjod 
# Mon Jan 11 01:30:00 2010
#
#Should work with HP dv3 remote

begin remote

  name   hp-dv3
  flags CONST_LENGTH|RAW_CODES
  eps            30
  aeps          100

  ptrail          0
  repeat     0     0

  gap 51199
 
      begin raw_codes

     name power 
      620     1174      137      760      137      760
      137      760      137      760      137      760
      620      691      137     1174      137      760
      137

    name key_home
      620     1174      206      691      206      691
      206      691      206      691      206      691
      620      691      206     1105      620
##

    name key_repeat
      206      691      206      691      206      691
      206      691      206      691      206      691
      206   

    name key_play
      620     1174      206      691      206      691
      620      691      206     1105      620      691
      206      691      206     1105      206   

    name key_dvd
      620     1174      206      691      206      691
      206      691      620     1174      206      691
      620     1174      206      691      206
##

    name key_rewind
      620     1174      206      691      206      691
      206      691      206      691      620     1174
      620     1174      620   

    name key_stop
      620     1174      206      691      206      691
      206      691      206      691      620      691
      206     1105      206      691      620 

    name key_fastforward
      620     1174      206      691      206      691
      206      691      206      691      620     1174
      620     1174      206      691      206
##
    
    name key_prev
      620     1174      206      691      206      691
      206      691      206      691      620      691
      206     1105      620      691      206

    name key_up
      620     1174      206      691      206      691
      206      691      206      691      620      691
      206      691      206      691      206     1105
      206     

    name key_next
      620     1174      206      691      206      691
      206      691      206      691      620      691
      206     1105      620     1174      206
##


    name key_left
      620     1174      206      691      206      691
      206      691      620     1174      206      691
      206      691      206      691      206      691
      206  

    name key_ok
      620     1174      206      691      206      691  
      206      691      620     1174      206      691
      206      691      620     1174      206   

    name key_right
      620     1174      206      691      206      691
      206      691      620     1174      206      691
      206      691      206      691      620
##

    name key_exit
      620     1174      206      691      206      691
      206      691      620     1174      206      691
      206      691      620      691      137
    name key_down
      620     1174      206      691      206      691
      206      691      206      691      620      691
      206      691      137      760      137      760
      206
    name key_info
      620     1174      206      691      206      691
      206      691      206      691      206      691
      620      691      206      691      206      691
      206
##

    name key_volumedown
      620     1174      206      691      206      691
      206      691      206      691      620     1174
      206      691      206      691      620 

    name key_mute
      620     1174      206      691      206      691
      206      691      206      691      206      691
      620      691      206      691      206     1105
      206 

    name key_volumeup
      620     1174      206      691      206      691
      206      691      206      691      620     1174
      206      691      206      691      206      691
      206




end raw_codes


end remote
#
```

the remote key names may not be appropriate, feel free to correct this. 

let me know if this works :)

---

### Post by bheremans on 2010-01-11
It works for me. I have setup xbmc now with lirc.
But the keys are a bit to fast. When I pres a key on the remote , like left. sometimes it goes 2 or 3 times left.

I will lokk in the lircd.conf file if I can hande the multiple repeat actions.

---

### Post by tjodSK on 2010-01-11
maybe you can take a look at the lircrc file..

```

begin
    remote = hp-dv3
    prog = moovida
    button = power
    config = close_key
    repeat = 0
    delay = 0
end

```

there are repeat and delay parameters... this maybe helps.

---

### Post by bheremans on 2010-01-11
Repeat doesn't work correctly , according to the lirc documentation :

if you hold down a button the output of irw should look like this.

```
	0000000000f40bf0 00 1_DOWN ANIMAX
	0000000000f40bf0 01 1_DOWN ANIMAX
	0000000000f40bf0 02 1_DOWN ANIMAX
	0000000000f40bf0 03 1_DOWN ANIMAX
	0000000000f40bf0 04 1_DOWN ANIMAX
	0000000000f40bf0 05 1_DOWN ANIMAX
```

Note how the second field gets incremented. Many people don't even notice if this does not work correctly. 

With our driver / config files :

```
0000000000000010 00 key_down hp-dv3
0000000000000010 00 key_down hp-dv3
0000000000000010 00 key_down hp-dv3
0000000000000010 00 key_down hp-dv3
0000000000000010 00 key_down hp-dv3
0000000000000010 00 key_down hp-dv3
0000000000000010 00 key_down hp-dv3
0000000000000010 00 key_down hp-dv3
0000000000000010 00 key_down hp-dv3
0000000000000010 00 key_down hp-dv3
0000000000000010 00 key_down hp-dv3
0000000000000010 00 key_down hp-dv3
```

---

### Post by tjodSK on 2010-01-11
i know, but, should the incrementing work with raw_codes as well?

---

### Post by sn3rd on 2010-01-19
How would I go about getting this running? I'm not sure how to compile the driver; surely I need a makefile?

---

### Post by tjodSK on 2010-01-19
> **sn3rd said:**
> How would I go about getting this running? I'm not sure how to compile the driver; surely I need a makefile?


sure, you do. This "driver" is in very "early" stage of development and has been hacked mostly by me and bheremans. This is not *standalone* kernel driver, you need to install "lirc" (lirc.org).

So, i'm adding a little how-to.

1, grab latest lirc from lirc.org (tested with 0.8.6)
2, download attached hacked drivers from post #39.
3, untar lirc installation and OVERWRITE original lirc it87.c and .h driver with provided hacked version (drivers are located in drivers/lirc_it87)
4, ./configure, you should select it87 (not ite8709) driver in configuration dialog
5, make && sudo make install
6, grab the lirc.conf from post #40 save it as /etc/lirc/lircd.conf
7, reboot
8, now, run sudo irw. You should get output indicating the remote is working.


let me know if this works...

---

### Post by sn3rd on 2010-01-19
No luck; still no output at the last step from from
```

sudo irw

```

No idea where to even begin looking

---

### Post by bheremans on 2010-01-19
is the module lirc_it87 loaded ?

bhe@bhe-hp:~$ lsmod | grep lirc
lirc_it87              17848  0 
lirc_dev               11046  1 lirc_it87

if not modprobe id : sudo modprobe lirc_it87
with dmesg you should see some info

I'm using it succesfully with xbmc, it still goes to fast (I'm not using lircrc with delay or repeat parameters)

But I'm already happy with the result :-)

---

### Post by sn3rd on 2010-01-19
Just removed everything related to lirc, and tried again; thought it may be something to do with a latent previous lirc install; still no dice, but different this time.

Instead of no output, I get
```

connect: No such file or directory

```

I also get no output from
```

dmesg | grep lirc

```

---

### Post by sn3rd on 2010-01-19
I had the lirc_dev module loaded. I proceeded to rmmod it, and tried to modprobe lirc_it87; got the following:

```

FATAL: Error inserting lirc_it87 (/lib/modules/2.6.31-14-generic/updates/dkms/lirc_it87.ko): No such device or address

```

---

### Post by evil-noxx on 2010-01-19
I've just removed everything related to lirc i had on my system, downloaded, compiled (with the different driver source) and installed lirc
I've also copied lircd.conf to the right place.
However, when i rebooted the module wasn't loaded. So i modprobed it and lsmod | grep lirc showed output similar to yours.
But when i try irw i get this:

noxx@linux-c6x1:~> sudo irw
connect: Connection refused

mode2 -d /dev/lirc0 does show some output...
do i still have to configure every key from the remote control? or is it suposed to work right away?

Edit: xev gives no output either...
Edit2: Don't know if it matters but i'm running opensuse, not ubuntu

---

### Post by bheremans on 2010-01-19
check /etc/lirc/hardware.conf if remote_device is correct, my hardware.conf

```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="ITE8709 CIR port"
REMOTE_MODULES="lirc_dev lirc_it87"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""


```

---

### Post by evil-noxx on 2010-01-19
as it turns out i didn't have one of those files...
it's getting kind of late so i'll test it tomorow

---

### Post by sn3rd on 2010-01-19
@bheremans: My /etc/lirc/hardware.conf is identical to yours.

I now have lirc_ite8709 listed by lsmod, ASWELL as lirc_dev. And still can't modprobe lirc_it87

---

### Post by tjodSK on 2010-01-20
> **sn3rd said:**
> @bheremans: My /etc/lirc/hardware.conf is identical to yours.

I now have lirc_ite8709 listed by lsmod, ASWELL as lirc_dev. And still can't modprobe lirc_it87

you are not supposed to load lirc_ite8709. It actually can disallow further loading of it_87 because of releasing the IOs acquired in init phase does not always work well in this module.

So my suggestion is:
remove the lirc_ite8709 from the kernel 
**sudo rm /lib/modules/2.6.32.3-core2/misc/lirc_ite8709**
(or you can ban the module in /etc/modprobe.d/blacklist  because it will keep loading, it's pnp module), then reboot your computer. 

Do this straight after the reboot:
**cat /proc/ioports**

look for something like this:
```

...
0310-0317 : 
...

```

now, try to insert the correct module into the kernel with 
**sudo modprobe lirc_it87**

now do **lsmod | grep lirc** and see if is the module loaded correctly.

you can check the **cat /proc/ioports** as well, you should end with something like this:

```
0310-0317 : lirc_it87
```

let me know if this helps.

---

### Post by tjodSK on 2010-01-20
> **evil-noxx said:**
> I've just removed everything related to lirc i had on my system, downloaded, compiled (with the different driver source) and installed lirc
I've also copied lircd.conf to the right place.
However, when i rebooted the module wasn't loaded. So i modprobed it and lsmod | grep lirc showed output similar to yours.
But when i try irw i get this:

noxx@linux-c6x1:~> sudo irw
connect: Connection refused

mode2 -d /dev/lirc0 does show some output...
do i still have to configure every key from the remote control? or is it suposed to work right away?

Edit: xev gives no output either...
Edit2: Don't know if it matters but i'm running opensuse, not ubuntu

it souldn't matter whether you run ubuntu or opensuse. Just be sure you've removed all lirc stuff from your package manager (if you installed any lirc packages). 

If the mode2 does output pulses and spaces, it means you've set up the driver and the hardware works. 

You now need to set up configuration for the hardware (hardware.conf) and the remote (lircd.conf). Feel free to use my lircd.conf you can find around post #40, but i include my most recent config.. The main difference is the key names assigned to individual buttons. In the newer config (below) the names does correspond with so-called standard, the MCE remote. If you use this config as your lircd.conf, you'll be then able to generate the third needed file, the .lircrc with tool provided by mythbuntu team (mythbuntu-lircr-generator)

Can you please verify if you have the module loaded (lsmod | grep lirc) and the lircd daemon running (ps aux | grep lircd). The connection refused message does indicate that the daemon is not running or accepting connections for any reason. 

You can run the daemon from the command line (lircd -n) - it will not daemonize the process so you can review the messages. The lircd must be running prior to irw, while mode2 does NOT.

let me know if this helps.

---

### Post by tjodSK on 2010-01-20
I'm including the remote config compatible with mythbuntu-lircrc-generator:

```
#
# this bogus config file was butchered by hand by tjod 
# Mon Jan 11 01:30:00 2010
#
#Should work with HP dv3 remote

begin remote

  name   hp-dv3
  flags CONST_LENGTH|RAW_CODES
  eps            30
  aeps          100

  ptrail           0
  repeat     0     0
# frequency confirmed to work with the SA3250
  gap 51199
 
      begin raw_codes

     name power 
      620     1174      137      760      137      760
      137      760      137      760      137      760
      620      691      137     1174      137      760
      137

    name videos
      620     1174      206      691      206      691
      206      691      206      691      206      691
      620      691      206     1105      620
##

    name replay
      206      691      206      691      206      691
      206      691      206      691      206      691
      206   

    name play
      620     1174      206      691      206      691
      620      691      206     1105      620      691
      206      691      206     1105      206   

    name dvd
      620     1174      206      691      206      691
      206      691      620     1174      206      691
      620     1174      206      691      206
##

    name rewind
      620     1174      206      691      206      691
      206      691      206      691      620     1174
      620     1174      620   

    name stop
      620     1174      206      691      206      691
      206      691      206      691      620      691
      206     1105      206      691      620 

    name forward
      620     1174      206      691      206      691
      206      691      206      691      620     1174
      620     1174      206      691      206
##
    
    name back
      620     1174      206      691      206      691
      206      691      206      691      620      691
      206     1105      620      691      206

    name up
      620     1174      206      691      206      691
      206      691      206      691      620      691
      206      691      206      691      206     1105
      206     

    name skip
      620     1174      206      691      206      691
      206      691      206      691      620      691
      206     1105      620     1174      206
##


    name left
      620     1174      206      691      206      691
      206      691      620     1174      206      691
      206      691      206      691      206      691
      206  

    name enter
      620     1174      206      691      206      691  
      206      691      620     1174      206      691
      206      691      620     1174      206   

    name right
      620     1174      206      691      206      691
      206      691      620     1174      206      691
      206      691      206      691      620
##

    name clear
      620     1174      206      691      206      691
      206      691      620     1174      206      691
      206      691      620      691      137
    name down
      620     1174      206      691      206      691
      206      691      206      691      620      691
      206      691      137      760      137      760
      206
    name guide 
      620     1174      206      691      206      691
      206      691      206      691      206      691
      620      691      206      691      206      691
      206
##

    name voldown
      620     1174      206      691      206      691
      206      691      206      691      620     1174
      206      691      206      691      620 

    name mute
      620     1174      206      691      206      691
      206      691      206      691      206      691
      620      691      206      691      206     1105
      206 

    name volup
      620     1174      206      691      206      691
      206      691      206      691      620     1174
      206      691      206      691      206      691
      206

end raw_codes

end remote
#
```

i can confirm bheremans issue, the remote is kinda "touchy", but i can live with that for now.

---

### Post by evil-noxx on 2010-01-20
turns out lirc wasn't running. Uninstalling the old lirc with the package manager probably caused /etc/init.d/lirc to disapear (I think i'll need help setting that up later).
After loading the driver and starting the lircd -n, irw no longer gave a connection refused error. It actually gave no output whatsoever.

This was the output from lircd:
noxx@linux-c6x1:~> sudo /usr/local/sbin/lircd -n
lircd: lircd(default) ready, using /var/run/lirc/lircd
lircd: accepted new client on /var/run/lirc/lircd
lircd: could not get file information for /dev/lirc
lircd: default_init(): No such file or directory
lircd: WARNING: Failed to initialize hardware
lircd: removed client

Everything except for the first line showd up immediately after running irw...

I also have a few, possibly irrelevant, questions:
- Does IRda have anything to do with the remote working properly?
- What's the .lircd file for?
- What's irw supposed to output?

Thank you for your help and patience


Edit:
after reading those errors a bit more carefully i decided to try to create a symbolic link to lirc0 called lirc. Good news is it worked.
here's some stuff irw gave:

0000000000000010 00 down hp-dv3
0000000000000010 01 down hp-dv3
000000000000000f 00 clear hp-dv3
0000000000000011 00 guide hp-dv3
0000000000000008 00 forward hp-dv3
0000000000000014 00 volup hp-dv3
0000000000000014 01 volup hp-dv3
0000000000000014 02 volup hp-dv3
0000000000000014 03 volup hp-dv3

Bad news is the remote's still not controling the laptop in any way :(

---

### Post by tjodSK on 2010-01-21
if the irw works, you are almost there!

The .lircrc file is supposed to map remote events to appropriate actions. Grab mythbuntu-lircrc-generator, this tool should generate the lircrc files for totem, vlc, mplayer, elisa, ...
[B]
EDIT[/B]


may i ask you a question.. what lircd.conf are you using?

---

### Post by technic93 on 2010-01-21
Maybe there is a difference between Dell Studio 15 and HP Pavilion dv3500.
I can't get your driver working, because module don't want to load:(
I follow all instructions but I get this: 
FATAL: Error inserting lirc_it87 (/lib/modules/2.6.32-020632-generic/misc/lirc_it87.ko): No such device or address

UPDATE:
Ok i changed this in lirc_it87.h
/* it87 Ports: */
#define it87_ADRPORT          0x4e
#define it87_DATAPORT         0x4f

And module loaded There is some progress!

---

### Post by evil-noxx on 2010-01-21
I'm using the lircd.conf and hardware.conf posted previously on this thread...
I'm having trouble finding mythbuntu-lircrc-generator (both binary and source code). Everywhere i look the say to use apt-get install... Since I'm using opensuse .deb's aren't very useful.
I was thinking of making my own lircrc, as it doesn't seem too hard

---

### Post by jackallen0714 on 2010-01-23
> **technic93 said:**
> Maybe there is a difference between Dell Studio 15 and HP Pavilion dv3500.
I can't get your driver working, because module don't want to load:(
I follow all instructions but I get this: 
FATAL: Error inserting lirc_it87 (/lib/modules/2.6.32-020632-generic/misc/lirc_it87.ko): No such device or address

UPDATE:
Ok i changed this in lirc_it87.h
/* it87 Ports: */
#define it87_ADRPORT          0x4e
#define it87_DATAPORT         0x4f

And module loaded There is some progress!

How to get this port address? I'm using Lenovo Y530, which used ITE8708. I also can't  get the driver working following the change in HP laptop. :(

---

### Post by technic93 on 2010-01-23
It was in lirc_it85.h file somewhere in this topic. The module loads successfully  but irw says nothing:( So the problem is not solved for me

UPDATE:
Get it working on Dell Studio 1535 laptop!! Thank you.

---

### Post by LubindaMaim on 2010-01-23
more importantly have developers been notified of this so with lucid it works out the box?

---

### Post by LinusNichtTorvalds on 2010-01-24
> **technic93 said:**
> It was in lirc_it85.h file somewhere in this topic. The module loads successfully  but irw says nothing:( So the problem is not solved for me

UPDATE:
Get it working on Dell Studio 1535 laptop!! Thank you.

How do you managed to get it work? I don't understand the way you compiled the driver for lirc... :( I'm also using a Dell Studio 1535 with Ubuntu Karmic.

> **tjodSK said:**
> sure, you do. This "driver" is in very "early" stage of development and has been hacked mostly by me and bheremans. This is not *standalone* kernel driver, you need to install "lirc" (lirc.org).

So, i'm adding a little how-to.

1, grab latest lirc from lirc.org (tested with 0.8.6)
2, download attached hacked drivers from post #39.
3, untar lirc installation and OVERWRITE original lirc it87.c and .h driver with provided hacked version (drivers are located in drivers/lirc_it87)
4, ./configure, you should select it87 (not ite8709) driver in configuration dialog
5, make && sudo make install
6, grab the lirc.conf from post #40 save it as /etc/lirc/lircd.conf
7, reboot
8, now, run sudo irw. You should get output indicating the remote is working.


let me know if this works...

Is this How-To still correct? Or do I have to change something in the driver files? If yes, WHAT?

---

### Post by technic93 on 2010-01-24
That howto is for HP laptop
For Dell Studio 1535 I changed (just a little) drivers, you can get them from attachment. Also you can find lircd.conf and lirrc for Totem there.

P.S. Sorry for bad English

---

### Post by evil-noxx on 2010-01-25
So, I finally got my hands on mythbuntu-lircrc-generator. It generated configurations for a bunch of programs (including totem and vlc). 
However that didn't help at all. I think it might even have broken my totem as it suddenly started crashing everytime i try to play a file with it.

Any ideias on what might be going wrong with the remote configurations??

---

### Post by sn3rd on 2010-01-25
I used technic93's driver and was able to modprobe, but still not getting the correct output from
```

cat /proc/ioports

```

Am I not installing lirc properly?

Would someone be willing to detail cleaning up and re-installing lirc for us?

---

### Post by evil-noxx on 2010-01-25
> **sn3rd said:**
> I used technic93's driver and was able to modprobe, but still not getting the correct output from
```

cat /proc/ioports

```Am I not installing lirc properly?

Would someone be willing to detail cleaning up and re-installing lirc for us?

Here are some not very detailed instructions...

Open up synaptic package manager (if your on ubuntu) and search for "lirc".
Remove everything related to lirc... In my case was "lirc","lirc-kmp-default","pulseaudio-module-lirc" and probably others
Then download the lirc source code. You can use cvs to do that...
Also download the lirc_it87 driver source code and overwrite the one that came with lirc's source
Then, assuming all dependecies have been taken care of, open up a terminal, change to lirc's source directory, run ./autogen.sh, then run ./setup.sh.
During the set up make sure to choose the correct driver
After that, run make, sudo make install

Now you should be able to load the driver like so:
sudo modprobe lirc_it87

if there were no errors then the driver should be working... However in my case that doesn't mean i can control the laptop with the remote as lirc still needs to be properly configured. Look through the thread for the lircd.conf and hardware.conf files if you don't allready have them.

Hope this helps, as confusings as it may be...

---

### Post by technic93 on 2010-01-26
There is also the difference in /proc/ioports but it works for me.

---

### Post by LinusNichtTorvalds on 2010-01-26
> **technic93 said:**
> That howto is for HP laptop
For Dell Studio 1535 I changed (just a little) drivers, you can get them from attachment. Also you can find lircd.conf and lirrc for Totem there.

P.S. Sorry for bad English

What do I do wrong? I can't compile the driver...

```

linus@dell-laptop:~/Desktop/lirc-0.8.6$ ./setup.sh 
dialog not found!
linus@dell-laptop:~/Desktop/lirc-0.8.6$ ./configure 
dialog not found!
Please read the documentation!!!
linus@dell-laptop:~/Desktop/lirc-0.8.6$ make
make: *** Keine Targets angegeben und keine »make«-Steuerdatei gefunden.  Schluss.

```

---

### Post by 816_8055 on 2010-01-26
> **LinusNichtTorvalds said:**
> What do I do wrong? I can't compile the driver...

```

linus@dell-laptop:~/Desktop/lirc-0.8.6$ ./setup.sh 
dialog not found!
linus@dell-laptop:~/Desktop/lirc-0.8.6$ ./configure 
dialog not found!
Please read the documentation!!!
linus@dell-laptop:~/Desktop/lirc-0.8.6$ make
make: *** Keine Targets angegeben und keine »make«-Steuerdatei gefunden.  Schluss.

```

```

sudo apt-get install dialog

```

---

### Post by LinusNichtTorvalds on 2010-01-26
Okay, works fine. I've compiled and installed LIRC correctly. 

Module is loaded:
```

linus@dell-laptop:~$ lsmod | grep -i lirc
lirc_it87              18336  0 
lirc_dev               10868  1 lirc_it87

```**Which hardware.conf do I have to use?**

My lircd.conf:
```

# Please make this file available to others
# by sending it to <[EMAIL="lirc@bartelmus.de"]lirc@bartelmus.de[/EMAIL]>
#
# this config file was automatically generated
# using lirc-0.8.6(default) on Sun Jan 24 15:46:41 2010
#
# contributed by 
#
# brand:                       file.conf
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  file.conf
  bits            8
  flags RC6|NO_HEAD_REP|CONST_LENGTH
  eps            30
  aeps          100

  header       2470   840
  one           406   417
  zero          406   417
  pre_data_bits   29
  pre_data       0x37FE354
  gap          77824
  min_repeat      4
  toggle_bit_mask 0x8000
  rc6_mask    0x100000000

      begin codes
          key_up                   0xA7
          key_down                 0xA6
          key_ok                   0xA3
          key_left                 0xA5
          key_right                0xA4
          key_playpause            0xD3
          key_stop                 0xCE
          key_next                 0xDF
          key_previous             0xDE
          key_back                 0xD0
          key_forward              0xD1
          key_volumeup             0xEF
          key_volumedown           0xEE
          key_mute                 0xF2
          key_media                0x63
          key_power                0xF3
          key_player               0x64
          key_info                 0xF0
          key_enter                0x5B
      end codes

end remote

```Mode2 says:
```
linus@dell-laptop:~$ sudo mode2 -d /dev/lirc0
space 34
pulse 46
space 45010
pulse 46
space 42962
pulse 70
space 40890
pulse 2414
space 898
pulse 366
space 434
pulse 390
space 426
pulse 398
space 818
pulse 286
space 834
pulse 1046
space 882
pulse 398
space 426
pulse 270
space 426
[...]

```Dmesg:
```

linus@dell-laptop:~$ dmesg | grep -i lirc
[  149.094526] lirc_dev: IR Remote Control driver registered, major 61 
[  149.095742] lirc_dev: lirc_register_driver: sample_rate: 0
[  149.095815] lirc_it87: found it8712.
[  149.095838] lirc_it87: set default irq 0x4
[  149.095878] lirc_it87: I/O port 0x0300, IRQ 4.
[  149.095921] lirc_it87: Installed.

```

```

linus@dell-laptop:~$ cat /proc/ioports | grep -i lirc
0300-0307 : lirc_it87

```

---

### Post by LinusNichtTorvalds on 2010-01-26
lircd-module is loaded, but **sudo irw** shows nothing. :([B]

Which [/B]hardware.conf/ lircd.conf **do I have to use?**

---

### Post by technic93 on 2010-01-26
In hardware.conf
Set device to /dev/lirc0
and modules to lirc_it87
Something like this... Also check if lirc is really running.

---

### Post by LinusNichtTorvalds on 2010-01-27
**/etc/lirc/hardware.conf**
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="ITE8709 CIR port"
REMOTE_MODULES="lirc_dev lirc_it87"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

```


**/etc/lirc/lircd.conf**
```

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.6(default) on Sun Jan 24 15:46:41 2010
#
# contributed by 
#
# brand:                       file.conf
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  file.conf
  bits            8
  flags RC6|NO_HEAD_REP|CONST_LENGTH
  eps            30
  aeps          100

  header       2470   840
  one           406   417
  zero          406   417
  pre_data_bits   29
  pre_data       0x37FE354
  gap          77824
  min_repeat      4
  toggle_bit_mask 0x8000
  rc6_mask    0x100000000

      begin codes
          key_up                   0xA7
          key_down                 0xA6
          key_ok                   0xA3
          key_left                 0xA5
          key_right                0xA4
          key_playpause            0xD3
          key_stop                 0xCE
          key_next                 0xDF
          key_previous             0xDE
          key_back                 0xD0
          key_forward              0xD1
          key_volumeup             0xEF
          key_volumedown           0xEE
          key_mute                 0xF2
          key_media                0x63
          key_power                0xF3
          key_player               0x64
          key_info                 0xF0
          key_enter                0x5B
      end codes

end remote

```

Lircd is running, but I have to start it manually after booting with "sudo lircd". How can I make lircd starting automatically after booting?
```
linus@dell-laptop:/etc/lirc# ps -A | grep -i lirc
 5663 ?        00:00:00 lircd
```

---

### Post by technic93 on 2010-01-27
I solve this problem by apt-get install lirc, after manually compiling kernel module. But I don`t know if it is correct.

---

### Post by kazuo_teramoto on 2010-01-31
Thanks tjodSK and bheremans. The driver and lirc.conf are working for me, I'm using a dv3500 with Arch Linux.

I'm getting repeat problems like bheremans, setting "repeat" in lircrc dont do anything.

Trying with a another remote control, a LG 6710V00090N, I dont get the repeat problem, pressing a key only give me one event in irw and pressing multiple times give me the correct incremented output.

I cannot get the LG control to work with the lirc.conf found in the lirc site, but I need to create one with irrecord using raw codes, like the HP built-in control.

So this answer the tjodSK question if the incrementing of second field of irw works with raw_code, looks like it get incremented too.

EDIT:
I found a possible workaround, changing gap to 100000 in lircd.conf give me a, IMHO, better behavior. With this value of gap I get only one event at the release of a button, but repeats dont happen when holding the button down.

---

### Post by jackallen0714 on 2010-02-07
It seems my laptop Y530 differs from HP or Dell in hardware design, maybe some differences in selecting ports. Anyone know how to find out these ports address? 

/* it87 Ports: */
#define it87_ADRPORT 0x4e
#define it87_DATAPORT 0x4f

---

### Post by jackallen0714 on 2010-02-08
No one cares...sigh

---

### Post by markitoxs on 2010-02-08
> **jackallen0714 said:**
> No one cares...sigh

of course we care, me personally, I cant remember the answer, but if you see at the posting times you will see that you need to be patient.

---

### Post by jackallen0714 on 2010-02-12
:o Help needed !!!

---

### Post by sn3rd on 2010-02-15
Using Dell Studio 1537.

I'm now at a point where the driver loads, I get the correct entries in /proc/ioports, mode2 gives me output, xmode2 gives me output, irw gives me output.

So I assume that it's working. Also, the increments work correctly; instead of having a repeated 00 field, if I hold down a button I get an increasing field:

```

000000037fe354f2 00 key_mute file.conf
000000037fe354f2 01 key_mute file.conf
000000037fe354f2 02 key_mute file.conf
000000037fe354f2 03 key_mute file.conf
000000037fe354f2 04 key_mute file.conf
000000037fe354f2 05 key_mute file.conf
000000037fe354f2 06 key_mute file.conf
000000037fe354f2 07 key_mute file.conf
000000037fe354f2 08 key_mute file.conf
000000037fe354f2 09 key_mute file.conf
000000037fe354f2 0a key_mute file.conf

```

So now how do I get this to do something useful?

I installed and ran mythbuntu-lirc-generator but I'm not quite sure how to use it. It created a bunch of files; not sure what to do with them?

---

### Post by bheremans on 2010-02-15
> **kazuo_teramoto said:**
> 
I found a possible workaround, changing gap to 100000 in lircd.conf give me a, IMHO, better behavior. With this value of gap I get only one event at the release of a button, but repeats dont happen when holding the button down.

Thanks this solution works fine for me to. No repeats anymore

---

### Post by bheremans on 2010-02-15
> **jackallen0714 said:**
> It seems my laptop Y530 differs from HP or Dell in hardware design, maybe some differences in selecting ports. Anyone know how to find out these ports address? 

/* it87 Ports: */
#define it87_ADRPORT 0x4e
#define it87_DATAPORT 0x4f

Sorry, I have no idea ..

---

### Post by bheremans on 2010-02-15
> **sn3rd said:**
> Using Dell Studio 1537.

I'm now at a point where the driver loads, I get the correct entries in /proc/ioports, mode2 gives me output, xmode2 gives me output, irw gives me output.

So I assume that it's working. Also, the increments work correctly; instead of having a repeated 00 field, if I hold down a button I get an increasing field:

```

000000037fe354f2 00 key_mute file.conf
000000037fe354f2 01 key_mute file.conf
000000037fe354f2 02 key_mute file.conf
000000037fe354f2 03 key_mute file.conf
000000037fe354f2 04 key_mute file.conf
000000037fe354f2 05 key_mute file.conf
000000037fe354f2 06 key_mute file.conf
000000037fe354f2 07 key_mute file.conf
000000037fe354f2 08 key_mute file.conf
000000037fe354f2 09 key_mute file.conf
000000037fe354f2 0a key_mute file.conf

```

So now how do I get this to do something useful?

I installed and ran mythbuntu-lirc-generator but I'm not quite sure how to use it. It created a bunch of files; not sure what to do with them?

best is to check the documentation of the application you will use. For now I'm only using the remote with xbmc. In xbmx you have to add the keys in a file Lircmap.xml 

example of my file : /usr/share/xbmc/system/Lircmap.xml 

```


<!-- This file contains the mapping of LIRC keys to XBMC keys used in Keymap.xml  -->
<!--                                                                              -->
<!-- How to add remotes                                                           -->
<!-- <remote device="name_Lirc_calls_the_remote">                                 -->
<!--                                                                              -->
<!-- For the commands the layout following layout is used                         -->
<!-- <XBMC_COMMAND>LircButtonName</XBMC_COMMAND>                                  -->
<!--                                                                              -->
<!-- For a list of XBMC_COMMAND's check out the <remote> sections of keymap.xml   -->

<lircmap>
	<remote device="hp-dv3">
		<power>power</power>
		<volumeplus>key_volumeup</volumeplus>
		<volumeminus>key_volumedown</volumeminus>
		<mute>key_mute</mute>
		<info>key_info</info>
		<pause>key_play</pause>
		<stop>key_stop</stop>
		<forward>key_fastforward</forward>
		<reverse>key_rewind</reverse>
		<left>key_left</left>
		<right>key_right</right>
		<up>key_up</up>
		<down>key_down</down>
		<select>key_ok</select>
		<back>key_exit</back>
		<menu>key_home</menu>
		<pageplus>key_prev</pageplus>
		<pageminus>key_next</pageminus>
	</remote>
</lircmap>



```

---

### Post by Haser on 2010-02-16
> **sn3rd said:**
> Using Dell Studio 1537.

I'm now at a point where the driver loads, I get the correct entries in /proc/ioports, mode2 gives me output, xmode2 gives me output, irw gives me output.

So I assume that it's working. Also, the increments work correctly; instead of having a repeated 00 field, if I hold down a button I get an increasing field:

```

000000037fe354f2 00 key_mute file.conf
000000037fe354f2 01 key_mute file.conf
000000037fe354f2 02 key_mute file.conf
000000037fe354f2 03 key_mute file.conf
000000037fe354f2 04 key_mute file.conf
000000037fe354f2 05 key_mute file.conf
000000037fe354f2 06 key_mute file.conf
000000037fe354f2 07 key_mute file.conf
000000037fe354f2 08 key_mute file.conf
000000037fe354f2 09 key_mute file.conf
000000037fe354f2 0a key_mute file.conf

```

So now how do I get this to do something useful?

I installed and ran mythbuntu-lirc-generator but I'm not quite sure how to use it. It created a bunch of files; not sure what to do with them?

Hi, 
sn3rd, how did you run irw?

---

### Post by sn3rd on 2010-02-19
I'm using irxevent, and it's working great!

I did as suggested by everyone else:

1) Remove lirc
2) compile and install the driver (as posted earlier as a zip file)
3)
```

cat /proc/ioports | grep 

```
Result:
```

0300-0307 : lirc_it87

```

4)
```

sudo irw

```
then press buttons on your remote. You should see some feedback.

I then proceeded to use mythbuntu-lirc-generator to generate some skeleton configs, but I've started using irxevent in order to get the remote to work system-wide.

---

### Post by evaarties on 2010-02-21
> **sn3rd said:**
> I'm using irxevent, and it's working great!

I did as suggested by everyone else:

1) Remove lirc
2) compile and install the driver (as posted earlier as a zip file)
3)
```

cat /proc/ioports | grep 

```
Result:
```

0300-0307 : lirc_it87

```

4)
```

sudo irw

```
then press buttons on your remote. You should see some feedback.

I then proceeded to use mythbuntu-lirc-generator to generate some skeleton configs, but I've started using irxevent in order to get the remote to work system-wide.

Is there a possibility that support for the Dell Studio 15/17 ir will be available in Ubuntu 10.04?

---

### Post by technic93 on 2010-02-24
> **evaarties said:**
> Is there a possibility that support for the Dell Studio 15/17 ir will be available in Ubuntu 10.04?

How about writing message to lirc developers?

---

### Post by evaarties on 2010-02-24
> **technic93 said:**
> How about writing message to lirc developers?

I added an update to the thread I started on sourceforge with the latest post in this thread: 

[http://sourceforge.net/projects/lirc/forums/forum/16772/topic/3407688](http://sourceforge.net/projects/lirc/forums/forum/16772/topic/3407688)

---

### Post by fresneda on 2010-04-19
Just out of curiosity, has anyone managed to get hdmi audio to work?

---

### Post by markitoxs on 2010-04-19
> **fresneda said:**
> Just out of curiosity, has anyone managed to get hdmi audio to work?

I am running HDMI audio since like 9.04. Still works on Lucid Lynx beta.

---

### Post by fresneda on 2010-04-19
Interesting. Is it (hdmi audio) related to the video or to the audio device? My audio device is  82801I (IDT 92HD71B7X), and at least with kernel 2.6.32 I don't get any hdmi devices listed with aplay.
I apologize for not actually running ubuntu, but could you tell me what is your kernel version, and what is the proper device to configure?
thanks

---

### Post by markitoxs on 2010-04-19
> **fresneda said:**
> Interesting. Is it (hdmi audio) related to the video or to the audio device? My audio device is  82801I (IDT 92HD71B7X), and at least with kernel 2.6.32 I don't get any hdmi devices listed with aplay.
I apologize for not actually running ubuntu, but could you tell me what is your kernel version, and what is the proper device to configure?
thanks

It is an interesting thing you ask there, because I believe that without the nvidia driver no HDMI output works, I will need to try that one day...

the way I got it working was to edit /etc/modprobe.d/alsa-base.conf


```
#To get hdmi
options snd-hda-intel model=hp-dv5 enable_msi=1

#To get internal mic working
#add
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
#options snd-hda-intel model=dell-m4-1 
```

Once done and rebooted, go to System > Preferences > Sound
And under the Hardware tab, select as profile: Digital Stereo (IEC958 ) Output + Analog Stereo Input


However now that I check I notice that Lucid Lynx has removed those lines in alsa-base.conf and I still have hdmi sound. My hardware profile is now Analog Stereo Duplex. Interesting...

Im running kernel 2.6.32-20-generic #30-Ubuntu SMP 

and aplay -l returns:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I remember that before updating to the beta, under aplay =l I could see the HDMI device.


Hope it helps... 

p.s. Can you use the volume up/down multimedia keys without any issues?

---

### Post by fresneda on 2010-04-19
Thank you for your reply. Just to be clear, I don't have any digital audio playback issues, and to get the mic working, I only had to add the line 
```
options snd-hda-intel model=hp-dv5
```
in  alsa-base.conf. What I want to do is to plug into my lcd tv via the hdmi connection to watch movies,etc. Unfortunately, I don't get any audio, and the reason for this is, I believe, the absence of any hdmi audio device. I've noticed you too don't have any listed hdmi devices. Can you get any audio through the hdmi connection?
My multimedia volume keys are working, but not as smoothly as in windows. They are too sensitive: a slight press of the button and the volume goes all the way up or down... To get them working I just had to configure global keyboard shortcuts in kde (4.4.2). It recognizes the volume key input as "Volume Up"  and "Volume Down".
Here is the output of aplay -l:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by fresneda on 2010-07-11
Update: I managed to get audio output from the hdmi connection (the laptop is connected to a lcd tv) using nvidia driver 195.36.24.
cheers

---

### Post by jackallen0714 on 2010-07-31
I followed the steps tjodSK given
unfortunately 


sudo modprobe
lirc_it87FATAL: Error inserting lirc_it87 (/lib/modules/2.6.32-24-generic/kernel/ubuntu/lirc/lirc_it87/lirc_it87.ko): No such device or address

 dmesg | grep lirc
[ 5042.652814] lirc_dev: lirc_register_driver: sample_rate: 0
[ 5042.653455] lirc_it87: no IT8752/8512 found, exiting..

I also changed  lirc_it87.h

#define it87_ADRPORT      	0x2e
#define it87_DATAPORT     	0x2f

still no luck 
anyone can help ?

---

### Post by tjodSK on 2010-07-31
sure. do you have dv3550?

---

### Post by jackallen0714 on 2010-07-31
> **tjodSK said:**
> sure. do you have dv3550?

No, but I have a Lenovo ideapad Y530, which also have a ITE8708 chip

---

### Post by jackallen0714 on 2010-08-05
Finally the driver seems working on Y530, but not sure
Changes can be found in attachment. 

dmesg | grep lirc

[   23.313930] lirc_dev: IR Remote Control driver registered, major 61 
[   23.323568] lirc_dev: lirc_register_driver: sample_rate: 0
[   23.323948] lirc_it87: set default io 0x300
[   23.323974] lirc_it87: set default irq 0x4
[   23.324016] lirc_it87: I/O port 0x0300, IRQ 4.
[   23.324088] lirc_it87: Installed.

cat /proc/ioports

0000-001f : dma1
0020-0021 : pic1
0040-0043 : timer0
0050-0053 : timer1
0060-0060 : keyboard
0064-0064 : keyboard
0070-0077 : rtc0
0080-008f : dma page reg
00a0-00a1 : pic2
00c0-00df : dma2
00f0-00ff : fpu
0240-0259 : pnp 00:02
025c-025c : pnp 00:01
025d-025d : pnp 00:01
0300-0307 : lirc_it87
03c0-03df : vga+
0400-047f : pnp 00:0a
  0400-0403 : ACPI PM1a_EVT_BLK
  0404-0405 : ACPI PM1a_CNT_BLK
  0408-040b : ACPI PM_TMR
  0410-0415 : ACPI CPU throttle
  0420-042f : ACPI GPE0_BLK
  0450-0450 : ACPI PM2_CNT_BLK
04d0-04d1 : pnp 00:0a
0500-053f : pnp 00:0a
0cf8-0cff : PCI conf1
9000-9fff : PCI Bus 0000:04
a000-afff : PCI Bus 0000:03
b000-bfff : PCI Bus 0000:02
c000-cfff : PCI Bus 0000:01
  c000-c07f : 0000:01:00.0
d000-d01f : 0000:00:1f.2
  d000-d01f : ahci
d020-d03f : 0000:00:1d.2
  d020-d03f : uhci_hcd
d040-d05f : 0000:00:1d.1
  d040-d05f : uhci_hcd
d060-d07f : 0000:00:1d.0
  d060-d07f : uhci_hcd
d080-d09f : 0000:00:1a.2
  d080-d09f : uhci_hcd
d0a0-d0bf : 0000:00:1a.1
  d0a0-d0bf : uhci_hcd
d0c0-d0df : 0000:00:1a.0
  d0c0-d0df : uhci_hcd
d0e0-d0e3 : 0000:00:1f.2
  d0e0-d0e3 : ahci
d0f0-d0f7 : 0000:00:1f.2
  d0f0-d0f7 : ahci
d100-d103 : 0000:00:1f.2
  d100-d103 : ahci
d110-d117 : 0000:00:1f.2
  d110-d117 : ahci

Get some output in xmode2 but no matter which botton I press, the output image seems identical.
irw get nothing, irrecord often cause system halting

---

### Post by jackallen0714 on 2010-08-05
modprobe with debug=1

dmesg | grep lirc

[19409.444735] lirc_it87: iir: 0x4 fifo: 0x20
[19409.444739] lirc_it87: data=00
[19409.444744] lirc_it87: data=00
[19409.444748] lirc_it87: data=00
[19409.444752] lirc_it87: data=00
[19409.444756] lirc_it87: data=00
[19409.444760] lirc_it87: data=00
[19409.444765] lirc_it87: data=00
[19409.444769] lirc_it87: data=00
[19409.444773] lirc_it87: data=00
[19409.444777] lirc_it87: data=00
[19409.444781] lirc_it87: data=00
[19409.444785] lirc_it87: data=00
[19409.444789] lirc_it87: data=00
[19409.444793] lirc_it87: data=00
[19409.444798] lirc_it87: data=00
[19409.444802] lirc_it87: data=00
[19409.444806] lirc_it87: data=00
[19409.444810] lirc_it87: data=00
[19409.444814] lirc_it87: data=00
[19409.444818] lirc_it87: data=00
[19409.444822] lirc_it87: data=00
[19409.444827] lirc_it87: data=00
[19409.444831] lirc_it87: data=00
[19409.444835] lirc_it87: data=00
[19409.444839] lirc_it87: data=00
[19409.444843] lirc_it87: data=00
[19409.444847] lirc_it87: data=00
[19409.444851] lirc_it87: data=00
[19409.444855] lirc_it87: data=00
[19409.444860] lirc_it87: data=00
[19409.444864] lirc_it87: data=00
[19409.444868] lirc_it87: data=00
[19409.445064] lirc_it87:  TIMEOUT

Any idea ?

---

### Post by jackallen0714 on 2010-08-05
I changed the battery of the remote control and 

see what xmode2 got

---

### Post by jackallen0714 on 2010-08-05
irrecord

Press RETURN now to start recording.
................................................................................
Found const length: 75776
Please keep on pressing buttons like described above.
................................................................................
RC-6 remote control found.
No header data.
No repeat code found.
Signals are biphase encoded.
Signal length is 41
Checking for toggle bit mask.
Please press an arbitrary button repeatedly as fast as possible.
Make sure you keep pressing the SAME button and that you DON'T HOLD
the button down!.
If you can't see any dots appear, then wait a bit between button presses.

Press RETURN to continue.

No toggle bit mask found.
But I know for sure that RC6 has a toggle bit!

What happened ?

---

### Post by paulatz on 2010-12-02
I'm sorry for necroing this thread, but I want to share some news on the front of the remote controller. I've been in contact with the incredibly kind and helpful Juan Jesús García de Soria Lucena during last weekend to get our hardware supported in the mainstream kernel. As a result Ubuntu 11.04 (and any distro with a 2.6.38 kernel) will support our device natively.

You can follow the discussion in the [mailing list archive]("http://sourceforge.net/mailarchive/forum.php?thread_name=AANLkTim2V%2BRics9cn4DGEOYTnQNQTocug2kVzs4r-GyU%40mail.gmail.com&forum_name=lirc-list"). For the moment, if you have ubuntu 10.4 or older you can still use the hacked driver from this discussion.

However, if you have ubuntu 10.10 the driver is broken, i.e. it does not work well with the kernel. If you need, I have a pre-build package of the developement kernel that have the new driver integrated and that I can share. If you want to download please contact me directly and I will put it online. You can write to user paulax on the domain email.it, don't make it look like spam ;)

---

### Post by markitoxs on 2010-12-02
Those are fantastic news! Thank you both for your work!

I would be interested in those deb packages to test them.

---

### Post by klew2 on 2011-05-03
@paulatz: do you know if it is included in ubuntu 11.04? Which driver I should choose during lirc installation? I've tried "ITE8709 CIR port" but I don't see anything comming in irw. And I also tried "ITE IT8704/05/12/18/20 CIR port" with the same results. Additionally the second driver hangs my linux completly when I try to rmmod it.

---

