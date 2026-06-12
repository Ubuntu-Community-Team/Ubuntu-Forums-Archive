---
title: "USB Cable Modem Issue"
date: 2006-12-07
forum: Hardware &amp; Laptops
---

### Post by steven8 on 2006-12-07
Okay, I have mentioned this in the Absolute Beginners area, but I have some more unusual evidence now, and would like to see if we can figure this out:

1) Dapper works with my Toshiba USB cable modem ootb, by using the rndis_host driver.

2) Edgy did not work with my modem, but could see it.

and here's the kicker...

3) Feisty Fawn Herd 1 does not work with it ootb, so I did a little checking, with the little knowledge I have picked up.  Here are the steps I took:

    3a) I checked Device Manager.  It sees the modem properly,   but is using for a driver "usb".

    3b) Using Device Databsse, it hung up on Network Check.

    3c) In the terminal, I typed locate rndis_host, and got this result: /lib/modules/2.6.19-7-generic/kernel/drivers/net/rndis_host.ko

Here, I thought, all right!, I just need to figure out how to assign that driver to my device, so I navigated to that folder.  Lo and behold!. . .the file is not there!

Now, this begs a couple of questions:

1) Why has the driver been removed from the kernel.

2) Why did my search find something that was not there (ctrl-h, found no hidden anything).

3) If it is there, and my search was somehow flawed, why has Ubuntu stopped applying the correct driver to work with my device during detection?

4) Can I take the existng ko file which must (sorry, I am writing from windows by neccessity right now) be there in my Dapper set up, and transfer it into an Edgy or Feisty installation and get it to work?

Thanks for your patience in reading if you have made it this far.  Any thoughts would be much appreciated.  I love Dapper, but wouldn't mind upgrading at some point, as Ubuntu moves forward.

---

### Post by steven8 on 2006-12-08
*bump*

I have noticed that if a person mentions USB cable modems on a Linux Distro website people run for the hills. :-)

Anyone have any ideas?  If was to use Edgy or Feisty but go back to an earlier kernel, so as to have the modem work, then I may as well use Dapper, right?

---

### Post by steven8 on 2006-12-08
*bump*

---

### Post by steven8 on 2006-12-08
*bump*

---

### Post by steven8 on 2006-12-09
*bump* each time it goes to the next page. . .

---

### Post by steven8 on 2006-12-09
*bump* Any thoughts on this?

---

### Post by Biggus on 2006-12-09
> *bump* Any thoughts on this?

Perhaps you are *bump*ing excessively?

---

### Post by steven8 on 2006-12-09
I have waited until it reaches the second page or beyond each time.  Once it gets there, it may never come back.

Do you have any ideas about how to get my usb cable modem working in Edgy or Feisty the way it does in Dapper, so I can upgrade at some point?

Thanks.

---

### Post by steven8 on 2006-12-10
Okay, I went back into the Feisty Fawn disc, and found that my search WAS flawed.  The rndis_host.ko driver file is there.

Now. . .how can I make my modem use that driver?  The device manager is there, with the device database, but they do not actually let me manage my hardware.  There is no option to 'change driver'.

What do I do?

---

### Post by Biggus on 2006-12-12
> Once it gets there, it may never come back

You never know, sometimes it can find a way.

---

### Post by steven8 on 2006-12-12
It would be cool if it found it's way back to the top other than me bumping.  Does anyone know how to change a driver for a piece of hardware?  Trouble is, I don't, and I haven't been able to find a way.

---

### Post by msak007 on 2006-12-13
Well, I'll try to offer some advice but my knowledge is limited and I've never used the device.

You say that in Dapper, it used the "rndis_host" driver, but in Edgy (and Feisty) it uses the "usb" driver? What you can do is in Edgy, post the output of **lsmod** (lower case L). This will tell us what drivers / modules are currently loaded. We can look through the list for anything of relevance related to your modem. 

I checked /lib/modules/2.6.17-10-generic/kernel/drivers/usb/net, and I have the rndis_host.ko file you referred to so not sure why you wouldn't have it, especially if "locate" found it and told you where it is.

Also, if it is in fact using a different module for the device you may have to blacklist the one it's trying to load. I had to do something similar for my Linksys WMP54GS wireless card, which wanted to use the native bcm43xx module / driver. I had to blacklist it in order to be able to use ndiswrapper.

---

### Post by steven8 on 2006-12-13
I found the driver.  I don't know what I did wrong in searching.

I am not on Linux, right now, as I'm at work.  So, when I get home in the morning, how do I 'blacklist' something?

Thanks for the support!! :-)

---

### Post by msak007 on 2006-12-13
> **steven8 said:**
> I found the driver.  I don't know what I did wrong in searching.

I am not on Linux, right now, as I'm at work.  So, when I get home in the morning, how do I 'blacklist' something?

Thanks for the support!! :-)
Work the graveyard shift eh? :) As far as blacklisting goes, I never said that was the resolution. I just said it's possible if the system is indeed loading one module and you want it to load another. Once you post the output of lsmod (with your modem plugged in), we can go from there.

---

### Post by steven8 on 2006-12-13
Yeah.  I work 9 pm to 7 am.  It's not so bad, as I only do it 4 days a week.

Okay, I won't think about the blacklist thing just yet.  I'll post the output of lsmod in the morning.  I always have the modem plugged in and turned on!!

Thanks!!

---

### Post by steven8 on 2006-12-13
Okay, this is from Feisty Fawn liveCD.  I'd assume, since edgy doesn't work with the modem, it would be the same.

lsmod:
> ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc            13320  1 
rfcomm                 43544  0 
l2cap                  27136  5 rfcomm
bluetooth              59620  4 rfcomm,l2cap
ipv6                  269600  10 
ppdev                  10628  0 
lp                     12964  0 
cpufreq_userspace       5664  0 
cpufreq_stats           7744  0 
cpufreq_powersave       2944  0 
cpufreq_ondemand        9740  0 
freq_table              6176  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8968  0 
video                  17540  0 
sbs                    16676  0 
i2c_ec                  6144  1 sbs
container               5504  0 
button                  7824  0 
battery                11396  0 
asus_acpi              17688  0 
ac                      6404  0 
af_packet              24968  0 
fuse                   49428  0 
snd_ens1371            28832  1 
snd_ac97_codec        100896  1 snd_ens1371
snd_ac97_bus            3328  1 snd_ac97_codec
snd_pcm_oss            47232  0 
snd_mixer_oss          18432  1 snd_pcm_oss
snd_mpu401              9640  0 
snd_mpu401_uart        10240  1 snd_mpu401
snd_pcm                84996  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
tsdev                   9152  0 
snd_seq_dummy           4996  0 
snd_seq_oss            36352  0 
snd_seq_midi            9984  0 
snd_rawmidi            26752  3 snd_ens1371,snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                58352  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
usblp                  16128  0 
serio_raw               8452  0 
analog                 13088  0 
gameport               17288  2 snd_ens1371,analog
floppy                 61732  0 
parport_pc             37668  1 
parport                39368  3 ppdev,lp,parport_pc
snd_timer              24964  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    58372  14 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_mpu401,snd_mpu401_uart,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                41224  0 
pcspkr                  4352  0 
soundcore               9312  1 snd
snd_page_alloc         11400  1 snd_pcm
shpchp                 40480  0 
i2c_sis630              8844  0 
sis_agp                 9860  1 
pci_hotplug            34752  1 shpchp
i2c_core               23936  2 i2c_ec,i2c_sis630
agpgart                34888  1 sis_agp
evdev                  11520  1 
squashfs               47748  1 
loop                   18440  2 
unionfs                79264  1 
nls_cp437               6912  1 
isofs                  38204  1 
ide_cd                 34336  1 
cdrom                  39072  1 ide_cd
ide_disk               17920  0 
ata_generic             8452  0 
libata                112660  1 ata_generic
scsi_mod              144908  1 libata
ehci_hcd               35080  0 
uhci_hcd               26248  0 
ohci_hcd               22788  0 
usbcore               143620  5 usblp,ehci_hcd,uhci_hcd,ohci_hcd
sis5513                15240  0 [permanent]
generic                 6532  0 [permanent]
thermal                15496  0 
processor              32712  1 thermal
fan                     5892  0 
fbcon                  44448  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3456  1 bitblit
vesafb                  9264  0 
capability              6024  0 
commoncap               8704  1 capability


---

### Post by msak007 on 2006-12-14
First things first, I haven't touched Feisty yet and being that it's still in early stages of development (Herd 1), I would recommend against using it right now unless you really need to. Let's troubleshoot the issue with a stable, released version first (such as Edgy) and if you can get it working there, attempt the same resolution in Feisty.

Regarding the output, I don't see the "rndis_host" module loaded at all so that could be a problem. But on the otherhand, I don't see any other modules loaded for it (that I can tell) that would conflict with the one you want. It seems as if it's not even detecting / loading it. I've read in other forums that people have tried several distributions and had problems with everything but Dapper. What I would propose you do is this: boot into an Edgy Live CD if you don't have it installed and run the following command
```
lsusb
``` (once again with a lower case L). You already said that the device manager / system information showed the device, this will confirm that the modem is even detected as a USB device. If you see it in the list, then run the following command:
```
sudo modprobe rndis_host
```If it does load the module, then your device should theoretically work as it did before. Try that and let me know if it works. If it does work, then the permanent resolution (getting it to load automatically) should be simple and you can file a bug report.

---

### Post by steven8 on 2006-12-16
I'm at work, so I don't have anythign to cut and paste.  I put in my Edgy liveCD.  lsusb finds my toshiba device.  sudo modprobe rndis_host seems to do nothing.  Just goes back to a command prompt.  Could this be because it's just off the CD?  I could do a dual boot with edgy and try it from the installed version.  Do you think this would make a difference?

---

### Post by msak007 on 2006-12-16
You're on the right track. modprobe really won't give you any output - all it does is insert a module to get your hardware working. In this case, no output is actually better because the only output it typically gives is errors if it can't be done :). You can follow these steps without installing (I think), so try the following with the Live CD:

1. Boot into the Live CD
2. With your modem plugged in, type the command I suggested before
```
sudo modprobe rndis_host
```
This will insert the module you need to get your modem working.
3. Type
```
dmesg | tail | grep rndis
```
This will show us only the relevant output to see if the module was properly inserted. Post the output of that command.
4. Once you've verified that the module was inserted, the device should theoretically be "installed" and work. At this point I'm not sure how you would normally use it, as I don't connect to a USB modem. Do what you normally did in Dapper and see if it works then. Sorry I can't be more help on actually using it.

---

### Post by steven8 on 2006-12-16
That is good news.  I will try your next suggestions and post the output tomorrow night.  In Dapper, I had to do nothing.  the modem worked ootb.  What I am going to do is install Edgy and then give it a go.  We'll see what comes of it.

You have already helped me a bunch, and I appreciate it very mich.  Thanks, fellow Buckeye!!

---

### Post by msak007 on 2006-12-16
Sounds good. If what I've suggested does indeed fix the problem, then you can just add the module to /etc/modules so that it loads at startup. You can also file a bug report for Edgy, and possibly even Feisty to see if it can get fixed before it's released.

EDIT: I forgot 1 step in my last post, so once you've modprobed the module and can verify it loaded using the dmesg output, run
```
sudo depmod -a
```
Then try using it.

---

### Post by steven8 on 2006-12-16
Will do!  I will print out these directions and give it a go.  I'll let you know and thanks so much!!

---

### Post by steven8 on 2006-12-21
Okay, I finally got a chance to install Edgy, and followed your directions.  the module loaded judt fine according to the readout, but the modem didn't start working.  So, I went to see if I could just add the module to the modules file, but it wouldn't let.  Said I wasn't the owner.  How do I make myself the owner of this file so i can edit it?

---

### Post by msak007 on 2006-12-21
If the modem didn't work after loading the module, then unfortunately I'm out of ideas and have no other advice to give you. Putting the module at startup won't make it work, as that only loads it startup and automates what you've done manually (the modprobe part). If you want to try it anyway, just add the module to /etc/modules:
```
sudo nano /etc/modules
```Add the module you want, save the file, and restart. Once you do, an lsmod should show the module loaded. Try it and see if that does anything for you. If not, then I'm sorry but maybe it's just a bug and the device doesn't work with Edgy. What was it you had to do in Dapper to get it "working"?

---

### Post by steven8 on 2006-12-22
I didn't have to do anything to make it work in Dapper.  It just worked.  That the was the first driving factor in my sticking with Ubuntu.

Thanks for the info on how to do the modules file.  I very much appreciate all of your help.  I'll let you know if it makes a difference.

---

### Post by TransitMan on 2006-12-22
You need to open your file browser as a Super User (i.e. sudo konqueror, enter password), go to where the file you need to move is, and make a copy and place it in the /etc/modules folder.
Close out of what-ever file browser you are using and restart the system to see if your cable modem is seen and working in Edgy.

Best advice I can give, since I am routed through a router.

---

### Post by steven8 on 2006-12-22
Okay, I need to open the browser with the sudo command to become owner of the file.  Thanks!

---

