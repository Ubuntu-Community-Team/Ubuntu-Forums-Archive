---
title: "Edgy and a TV Tuner"
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by Mets on 2007-02-03
Hey guys,

I'm new to Ubuntu and Linux, and I'm looking for some help on installing my tv tuner in Edgy.  I have an AverTV Cardbus tuner (PCMCIA) that I'd like to get up and runnining.  I really don't know a lot about the hardware installing process.  Thankfully, Edgy detected everything I had during setup so I didn't have to go through lots of headaches.  

I sort of have Wine working too, so I guess if nobody knows I can try to just use the windows drivers and see if that will work.  I'm kind of skeptical of that because I don't even think it's possible.  Plus, wine doesn't recognize any exe files (i.e. I have to go to shell and manually type "wine program.exe" to run anything), plus there is never any sound in anything I run under it.  So I'd prefer to not go that route.  Thanks a lot for your help.

---

### Post by david_2001 on 2007-02-03
Is that an analog or a digital tv tuner?  If it's analog then it may have been detected already.  Try the following in a terminal:
```
ls /dev/video*
```
If /dev/video and /dev/video0 exist then you're in business.  According to the avermedia website, the digital tuner version is also supported and there's a link to the installation instructions.  Note that the Windows drivers will not work!

---

### Post by Mets on 2007-02-03
thanks david

It is analog, and /dev/video and /dev/video0 are both present!

However, it doesn't look like it's working.  The power light on the device is off, and TVTime says there is no signal.

I haven't tried MythTV since that seems totally over the top for my purposes.

Oh, and if anybody could help this noob me get this going before tomorrow so I can see the Super Bowl, I'd be super appreciative. :D

Thanks again.

---

### Post by david_2001 on 2007-02-04
Until somebody who knows about these cards comes along, it might be an idea to check that it is being detected correctly.  I don't know a great deal about laptops but if this is a cardbus card then entering lspci at a terminal prompt should get some relevant information.  If it's listed in the output from lspci then the next step will be to check that it is being correctly identified by video4linux.  According to the video4linux documents, it should be card number 46, AVerMedia Cardbus TV/Radio (E500).  The information will be in /var/log/messages.  If you want to take a browse through that file then you're looking for something similar to this, copied from my system (the MSI card is registered as video2 because I have 2 other tuners):
> Feb  3 12:15:51 darkstar kernel: [17179588.448000] saa7130/34: v4l2 driver version 0.2.14 loaded
Feb  3 12:15:51 darkstar kernel: [17179588.448000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 58
Feb  3 12:15:51 darkstar kernel: [17179588.448000] saa7133[0]: found at 0000:00:09.0, rev: 208, irq: 58, latency: 32, mmio: 0xdffff000
Feb  3 12:15:51 darkstar kernel: [17179588.448000] saa7133[0]: subsystem: 1462:6231, board: MSI TV@Anywhere plus [card=82,autodetected]
Feb  3 12:15:51 darkstar kernel: [17179588.448000] saa7133[0]: board init: gpio is 40

[Skip a few lines]

Feb  3 12:15:51 darkstar kernel: [17179588.608000] saa7133[0]: i2c eeprom 00: 62 14 31 62 10 28 ff ff ff ff ff ff ff ff ff ff
Feb  3 12:15:51 darkstar kernel: [17179588.608000] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb  3 12:15:51 darkstar kernel: [17179588.608000] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb  3 12:15:51 darkstar kernel: [17179588.608000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb  3 12:15:51 darkstar kernel: [17179588.608000] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb  3 12:15:51 darkstar kernel: [17179588.608000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb  3 12:15:51 darkstar kernel: [17179588.608000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb  3 12:15:51 darkstar kernel: [17179588.608000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb  3 12:15:51 darkstar kernel: [17179588.708000] tuner 2-004b: chip found @ 0x96 (saa7133[0])
Feb  3 12:15:51 darkstar kernel: [17179588.760000] tuner 2-004b: setting tuner address to 61
Feb  3 12:15:51 darkstar kernel: [17179588.800000] tuner 2-004b: type set to tda8290+75a
Feb  3 12:15:51 darkstar kernel: [17179588.872000] saa7133[0]: registered device video2 [v4l2]
Feb  3 12:15:51 darkstar kernel: [17179588.872000] saa7133[0]: registered device vbi2
Feb  3 12:15:51 darkstar kernel: [17179588.872000] saa7133[0]: registered device radio0

[Skip a few lines]

Feb  3 12:15:51 darkstar kernel: [17179588.888000] saa7134 ALSA driver for DMA sound loaded
Feb  3 12:15:51 darkstar kernel: [17179588.888000] saa7133[0]/alsa: saa7133[0] at 0xdffff000 irq 58 registered as card -1

---

### Post by brettg on 2007-02-04
While I'm not a guru on TV, I have been experimenting with it a bit lately, here are some things i discovered.

You need to install the tvcard drivers which are called ivtv, see here.

[https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)

A quick google on your card leads me to believe that is a hardware mpeg encoder (most newer cards are) and this means that it is not supported by tvtime, kdetv, xawtv or any of the other TV apps I tried because they don't support mpeg streams.

mplayer supports mpeg2 so you can do mplayer /dev/video0 and see if that "works"

Unfortunately, you can't change channels using mplayer, so you will probably just get black output instead of a picture.

As far as I could discover, your best choice at that stage is mythtv, which is not a simple install as it also requires you to install mysql-server. 

This is where I stopped because I suddenly realised that my DVD drive is not working on my new laptop so I have given up on TV to address more a important problem. 

I hope this helps somewhat though

---

### Post by david_2001 on 2007-02-04
Please take care.  The [IVTV]("http://ivtvdriver.org/index.php/Main_Page") drivers are only for Hauppauge PVR 150/250/350/500 and similar cards that have a hardware mpeg2 encoder.  Those of us who use other cards that don't have a hardware mpeg2 encoder rely on the [LinuxTV]("http://linuxtv.org/") drivers that come with the kernel.

---

### Post by Mets on 2007-02-04
Thanks a lot for the information.

I went through and ran lspci and found that it detects my card as follows
> 03:00.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev 11)


I then went through and did the IVTV installer, and I'm pretty sure that works.  I was able to capture a big purple-fuzzy video of nothing, however when I ran the "dmesg |grep Initialized" command, I got as output
> [17179575.340000] ieee1394: Initialized config rom entry `ip1394'
[17179609.504000] [drm] Initialized drm 1.0.1 20051102
[17179609.584000] [drm] Initialized radeon 1.25.0 20060524 on minor 0

instead of anything prefixed by ivtv.  Not sure if that matters though.

MythTV is probably too long of an install right now.  I read on their site that a saa1733 should work with TV Time, but I know mine is mpeg encode so I wonder if it is even detecting the right thing.  I ran through some other tutorial designed for saa1734 cards and I had to change some settings, so I wonder if that is just left over from that or if it really is identifying it as a saa1734 card.  Thanks again.

---

### Post by david_2001 on 2007-02-04
You've got an saa7134 card - proven by the output of lspci.  That type of card that doesn't have a hardware mpeg2 encoder so those IVTV drivers aren't going to work I'm afraid.  Did you check /var/log/messages to see whether the saa7134 driver autodetected your card correctly?  (There are some tricks to make it happen if it didn't.)

---

### Post by Mets on 2007-02-04
hmm, yeah it doesn't seem to be working :confused: 

There are a whole bunch of log files in /var/log - which one should I be checking out?

> acpid            dmesg              fsck                syslog
acpid.1.gz       dmesg.0            gdm                 syslog.0
apport.log       dmesg.1.gz         hibernate.log       syslog.1.gz
apport.log.1     dmesg.2.gz         hibernate.log.1     syslog.2.gz
apport.log.2.gz  dmesg.3.gz         installer           syslog.3.gz
aptitude         dmesg.4.gz         kern.log            syslog.4.gz
aptitude.1.gz    dpkg.log           kern.log.0          udev
auth.log         dpkg.log.1         lastlog             unattended-upgrades
auth.log.0       evms-engine.1.log  lpr.log             user.log
boot             evms-engine.2.log  mail.err            user.log.0
bootstrap.log    evms-engine.3.log  mail.info           uucp.log
btmp             evms-engine.4.log  mail.log            wtmp
btmp.1           evms-engine.5.log  mail.warn           wtmp.1
cups             evms-engine.6.log  messages            wvdialconf.log
daemon.log       evms-engine.7.log  messages.0          Xorg.0.log
daemon.log.0     evms-engine.8.log  news                Xorg.0.log.old
debug            evms-engine.log    pycentral.log
debug.0          faillog            scrollkeeper.log
dist-upgrade     fontconfig.log     scrollkeeper.log.1


Thanks a lot guys, I really appreciate the help.  SOrry if I'm a little slow with this, this is my first week on linux :D

---

### Post by david_2001 on 2007-02-04
You want the one in /var/log just called "messages".  An easier alternative would be to type the following in a terminal:
```
dmesg | less
```

---

### Post by fenian on 2007-02-05
Ivtv works on a variety of different cards here is a list...

[http://ivtvdriver.org/index.php/Supported_hardware](http://ivtvdriver.org/index.php/Supported_hardware)

---

### Post by Mets on 2007-02-05
wow sorry I didn't understand the /var/log/messages thing, that's pretty embarrassing:oops: 

Here's what I get when I take out my TV Tuner and then put it back in.
BTW I removed the IVTV stuff

> Feb  5 22:21:12 localhost kernel: [17184967.644000] pccard: card ejected from slot 0
Feb  5 22:21:46 localhost kernel: [17185001.628000] pccard: CardBus card inserted into slot 0
Feb  5 22:21:46 localhost kernel: [17185001.628000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
Feb  5 22:21:46 localhost kernel: [17185001.628000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Feb  5 22:21:46 localhost kernel: [17185001.628000] saa7133[0]: found at 0000:03:00.0, rev: 17, irq: 11, latency: 0, mmio: 0xf6000000
Feb  5 22:21:46 localhost kernel: [17185001.628000] saa7133[0]: subsystem: 1461:03e2, board: Philips Tiger reference design [card=81,insmod option]
Feb  5 22:21:46 localhost kernel: [17185001.628000] saa7133[0]: board init: gpio is 0
Feb  5 22:21:46 localhost kernel: [17185001.780000] saa7133[0]: i2c eeprom 00: 61 14 e2 03 ff ff ff ff ff ff ff ff ff ff ff ff
Feb  5 22:21:46 localhost kernel: [17185001.780000] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb  5 22:21:46 localhost kernel: [17185001.780000] saa7133[0]: i2c eeprom 20: ff d1 fb ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb  5 22:21:46 localhost kernel: [17185001.780000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb  5 22:21:46 localhost kernel: [17185001.780000] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb  5 22:21:46 localhost kernel: [17185001.780000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb  5 22:21:46 localhost kernel: [17185001.780000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb  5 22:21:46 localhost kernel: [17185001.780000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb  5 22:21:46 localhost kernel: [17185001.944000] saa7134 OSS: can't load, DMA sound handler already assigned (probably to ALSA)
Feb  5 22:21:46 localhost kernel: [17185001.964000] saa7133[0]: registered device video0 [v4l2]
Feb  5 22:21:46 localhost kernel: [17185001.964000] saa7133[0]: registered device vbi0
Feb  5 22:21:46 localhost kernel: [17185001.964000] saa7133[0]: registered device radio0
Feb  5 22:21:46 localhost kernel: [17185001.964000] saa7133[0]: frontend initialization failed
Feb  5 22:21:46 localhost kernel: [17185001.964000] saa7133[0]/alsa: saa7133[0] at 0xf6000000 irq 11 registered as card -1

---

### Post by david_2001 on 2007-02-06
Looks like you're mostly there but the card isn't being properly detected.  First thing, there's some really useful reference material [here]("http://www.linuxtv.org/v4lwiki/index.php/Saa7134_devices_(saa713x)").  Follow the link for your card and I'd also recommend following the link to the Gentoo WiKi as well.

In order to get your card properly detected, some options need to be passed to the saa7134 kernel module when it loads.  My preference is to put the options into a file in /etc/modprobe.d named after the particular module and the easiest way to create this file is to issue the following command from the console (you can also use an editor to create the file, if you want):
```
sudo sh -c 'echo "options saa7134 card=46" > /etc/modprobe.d/saa7134'
```
The options won't take effect until the saa7134 module is reloaded and the easiest way to make that happen is reboot.  If you manage to get a TV picture but don't get sound then try:
```
sudo sh -c 'echo "options saa7134 card=46 oss=1" > /etc/modprobe.d/saa7134'
```
Let us know how you got on.

---

### Post by david_2001 on 2007-02-07
> **david_2001 said:**
> Looks like you're mostly there but the card isn't being properly detected.  Yada, yada, yada
Sorry to all for all the errors in earlier versions of my last post.  I think I've got it right now but, really, where are all the pedants when you need them?

---

### Post by Mets on 2007-02-07
lol, no worries on the errors.  And thanks for the links too.

I did the above command, checked to see if the file was there which it was, and rebooted.  Ubuntu loads up, but the power light on the card is still not on.  I tried TV Time and obviously no video.  I then took the card out and put it back in to see if maybe it would detect it now, but it instead froze my computer.

I'm not sure if it means anything, but the sudo echo command returned "permission denied" whenever I tried to run it, so I had top make the file with sudo gedit.

Thanks for the help, I swear we'll get it!

---

### Post by david_2001 on 2007-02-08
Grrr!  Ok, delete the saa7134 file from /etc/modprobe.d if you haven't already because we're obviously not getting the card number correct.  One question that I didn't ask and should have done is what's the actual model name/number of your TV card?

---

### Post by Mets on 2007-02-09
It's an AverMedia AverTV WDM TvTuner and Video Capture (E501R).

 I have noticed that it says saa7133, not saa7134.  Should I just rename the file that?

Actually I just found this post - [http://ubuntuforums.org/showthread.php?t=325828](http://ubuntuforums.org/showthread.php?t=325828) - so I'll give that a go too.

---

### Post by david_2001 on 2007-02-09
> **Mets said:**
>  I have noticed that it says saa7133, not saa7134.  Should I just rename the file that?
There's no need to change the filename.  The driver module is called saa7134 and works with various saa713* chips.  For example, lspci reports my saa7134 card as:
> 00:09.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d0)

It looks as though the poster of the thread you quote knows the tuner identity number as well as the card number to feed to the saa7134 driver module.  Otherwise, the installation method described is essentially the same as mine, just going at it from a slightly different direction.  Good luck!

---

### Post by Mets on 2007-02-09
man, still nothing.  I tried his post and nothing.  I redid the modprobe method specified in this thread and nothing...

All of the commands go through correctly, but the power light never lights up on the PCI and TVTime of course doesn't work.  Is there some library or module or something that I need to download from apt-get that makes PCI things work?  I know it's not a PCI problem because my WiFi card works perfectly like Plug and Play, and my tv tuner also works perfectly on windows, detected automatically.

Is there some little thing that I'm not doing?  Some minor setting that I should have changed and didn't, before I started these methods?  Thanks a lot for your help David also, sorry I can't get it working.

---

### Post by david_2001 on 2007-02-10
Troubleshooting laptop hardware is completely outside my experience.  Anyway, the /var/log/messages output you posted earlier, i.e. 
> Feb 5 22:21:46 localhost kernel: [17185001.628000] pccard: CardBus card inserted into slot 0
Feb 5 22:21:46 localhost kernel: [17185001.628000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
Feb 5 22:21:46 localhost kernel: [17185001.628000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Feb 5 22:21:46 localhost kernel: [17185001.628000] saa7133[0]: found at 0000:03:00.0, rev: 17, irq: 11, latency: 0, mmio: 0xf6000000
Feb 5 22:21:46 localhost kernel: [17185001.628000] saa7133[0]: subsystem: 1461:03e2, board: Philips Tiger reference design [card=81,insmod option]
...
is saying that the card is being detected when it's inserted, just not as the correct card type.  It could be that it's being powered down shortly after insertion but that's something I don't know how to fix.

The AVerMedia Cardbus Plus E501R page on the LinuxTV wiki is in Russian so my comprehension is limited to what an online translation site tells me, which is that the author has the card working in Debian Unstable with kernel 2.6.17, i.e. with a Linux distribution that's similar to Edgy, but with card identity options that are different to those in the post you just tried out.  If you want to give it a try then delete the /etc/modprobe.d/saa7134 from my earlier try if you haven't already, if you've put anything saa7134-specifiic in /etc/modules then clean that out as well, remove and reinsert the TV card, and then:
```
sudo rmmod saa7134_alsa
sudo rmmod saa7134_oss  *(Just as a precaution in case it got loaded)*
sudo rmmod saa7134
sudo modprobe saa7134 card=46 tuner=12 alsa=1
```
Take a look in /var/log/messages or run dmesg and see what's reported.

---

### Post by Mets on 2007-02-10
Thanks David for looking that up.  It didn't work, but, as I'll show in a second, I think there might be something competing over the saa7134 drivers that is giving us so much trouble.

Ok, I cleaned out all of the saa7134 stuff.  I then removed the tuner and reinserted, and here is what /var/log/messages had to say:

> Feb 10 15:04:09 localhost kernel: [17239807.500000] pccard: card ejected from slot 0
Feb 10 15:04:22 localhost gconfd (root-29805): GConf server is not in use, shutting down.
Feb 10 15:04:22 localhost gconfd (root-29805): Exiting
Feb 10 15:04:25 localhost kernel: [17239823.372000] pccard: CardBus card inserted into slot 0
Feb 10 15:04:25 localhost kernel: [17239823.372000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
Feb 10 15:04:25 localhost kernel: [17239823.372000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Feb 10 15:04:25 localhost kernel: [17239823.372000] saa7133[0]: found at 0000:03:00.0, rev: 17, irq: 11, latency: 0, mmio: 0xf6000000
Feb 10 15:04:25 localhost kernel: [17239823.372000] saa7133[0]: subsystem: 1461:03e2, board: Philips Tiger reference design [card=81,insmod option]
Feb 10 15:04:25 localhost kernel: [17239823.372000] saa7133[0]: board init: gpio is 0
Feb 10 15:04:25 localhost kernel: [17239823.524000] saa7133[0]: i2c eeprom 00: 61 14 e2 03 ff ff ff ff ff ff ff ff ff ff ff ff
Feb 10 15:04:25 localhost kernel: [17239823.524000] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 10 15:04:25 localhost kernel: [17239823.524000] saa7133[0]: i2c eeprom 20: ff d1 fb ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 10 15:04:25 localhost kernel: [17239823.524000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 10 15:04:25 localhost kernel: [17239823.524000] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 10 15:04:25 localhost kernel: [17239823.524000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 10 15:04:25 localhost kernel: [17239823.524000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 10 15:04:25 localhost kernel: [17239823.524000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
**Feb 10 15:04:25 localhost kernel: [17239823.768000] saa7134 OSS: can't load, DMA sound handler already assigned (probably to ALSA)**
Feb 10 15:04:25 localhost kernel: [17239823.784000] saa7133[0]: registered device video0 [v4l2]
Feb 10 15:04:25 localhost kernel: [17239823.784000] saa7133[0]: registered device vbi0
Feb 10 15:04:25 localhost kernel: [17239823.784000] saa7133[0]: registered device radio0
**Feb 10 15:04:25 localhost kernel: [17239823.784000] saa7133[0]: frontend initialization failed**
Feb 10 15:04:25 localhost kernel: [17239823.784000] saa7133[0]/alsa: saa7133[0] at 0xf6000000 irq 11 registered as card -1
Feb 10 15:04:47 localhost kernel: [17239845.120000] saa7134 ALSA driver for DMA sound unloaded



I then typed the commands, but this is the output I got:

>  sudo rmmod saa7134_alsa       //works fine
sudo rmmod saa7134_oss
ERROR: Module saa7134_oss does not exist in /proc/modules
sudo rmmod saa7134
ERROR: Module saa7134 is in use by saa7134_dvb
sudo modprobe saa7134 card=46 tuner=12 alsa=1         //works fine I guess


I don't know why saa7134_oss isn't there, and I don't know what saa7134_dvb is or why it is competing over the module that I need.  This has to have something to do with why this isn't working, because we are doing all the right commands.  By now, it should be activated.

---

### Post by david_2001 on 2007-02-10
> I then typed the commands, but this is the output I got:

Quote:
sudo rmmod saa7134_alsa //works fine
sudo rmmod saa7134_oss
ERROR: Module saa7134_oss does not exist in /proc/modules
sudo rmmod saa7134
ERROR: Module saa7134 is in use by saa7134_dvb
sudo modprobe saa7134 card=46 tuner=12 alsa=1 //works fine I guess
I don't know why saa7134_oss isn't there, and I don't know what saa7134_dvb is or why it is competing over the module that I need. This has to have something to do with why this isn't working, because we are doing all the right commands. By now, it should be activated.
It's good that saa7134_oss isn't there.  The saa7134 driver can output sound through either alsa or oss but you don't need both and alsa is preferred.

The saa7134_dvb module is probably there because your card is not being detected properly, so it needs to be unloaded as well.  EDIT: The error about frontend not being initialised is due to the dvb module being loaded when it shouldn't be.

The new set of commands becomes:
```
sudo rmmod saa7134_alsa
sudo rmmod saa7134_oss
sudo rmmod saa7134_dvb
sudo rmmod saa7134
sudo modprobe saa7134 card=46 tuner=12 alsa=1
```
If you get an error about not being able to unload saa7134_dvb because of some other dependent module then just rmmod that module first etc.  Once we get this working then we'll make the options for the saa7134 module permanent.

---

### Post by Mets on 2007-02-10
Ok just a quick question, on sudo rmmod saa7134_oss or saa7134_dvb I get:

> sudo rmmod saa7134_oss
ERROR: Module saa7134_oss does not exist in /proc/modules
sudo rmmod saa7134_dvb
ERROR: Module saa7134_dvb does not exist in /proc/modules


Do I need to apt-get these?

---

### Post by david_2001 on 2007-02-10
The errors you've reported tell me you already have them!  (Actually, they're all part of the saa7134 driver but you don't need them to load for your particular TV card.)  Hang on, how come you're getting an error from about saa7134_dvb not being loaded now when it was last time?

---

### Post by david_2001 on 2007-02-10
I'm sort of tempted to try and cut to the chase at this point.  Why not try this:

1. Remove the TV card
2. Create a file in /etc/modprobe.d containing the options for the saa7134 driver module:
```
sudo sh -c 'echo "options saa7134 card=46 tuner=12 alsa=1" > /etc/modprobe.d/saa7134'
```
(Got it right this time!!)

3. Reinsert the TV card
4. See what dmesg reports.

---

### Post by Mets on 2007-02-10
No idea why they are reporting different errors from last time.  Here's what I got:

> Feb 10 19:39:51 localhost kernel: [17182240.196000] saa7133[0]: dsp access error
Feb 10 19:39:51 localhost last message repeated 19 times
Feb 10 19:39:51 localhost kernel: [17182240.196000] saa7133[0]/irq: looping -- clearing PE (parity error!) enable bit
Feb 10 19:39:51 localhost kernel: [17182240.196000] saa7133[0]: dsp access error
Feb 10 19:39:51 localhost last message repeated 19 times
Feb 10 19:39:51 localhost kernel: [17182240.196000] saa7133[0]/irq: looping -- clearing PE (parity error!) enable bit
Feb 10 19:39:51 localhost kernel: [17182240.200000] pccard: card ejected from slot 0
Feb 10 19:39:51 localhost kernel: [17182240.212000] saa7133[0]: dsp access error
Feb 10 19:39:51 localhost last message repeated 19 times
Feb 10 19:39:51 localhost kernel: [17182240.212000] saa7133[0]/irq: looping -- clearing PE (parity error!) enable bit
Feb 10 19:39:51 localhost kernel: [17182240.228000] saa7133[0]: dsp access error
Feb 10 19:39:51 localhost last message repeated 19 times
Feb 10 19:39:51 localhost kernel: [17182240.228000] saa7133[0]/irq: looping -- clearing PE (parity error!) enable bit
Feb 10 19:40:21 localhost kernel: [17182270.872000] pccard: CardBus card inserted into slot 0
Feb 10 19:40:21 localhost kernel: [17182270.872000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
Feb 10 19:40:21 localhost kernel: [17182270.872000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Feb 10 19:40:21 localhost kernel: [17182270.872000] saa7133[0]: found at 0000:03:00.0, rev: 17, irq: 11, latency: 0, mmio: 0xf6000000
Feb 10 19:40:21 localhost kernel: [17182270.872000] saa7133[0]: subsystem: 1461:03e2, board: Philips Tiger reference design [card=81,insmod option]
Feb 10 19:40:21 localhost kernel: [17182270.872000] saa7133[0]: board init: gpio is 0
Feb 10 19:40:22 localhost kernel: [17182271.008000] saa7133[0]: i2c eeprom 00: 61 14 e2 03 ff ff ff ff ff ff ff ff ff ff ff ff
Feb 10 19:40:22 localhost kernel: [17182271.008000] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 10 19:40:22 localhost kernel: [17182271.008000] saa7133[0]: i2c eeprom 20: ff d1 fb ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 10 19:40:22 localhost kernel: [17182271.008000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 10 19:40:22 localhost kernel: [17182271.008000] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 10 19:40:22 localhost kernel: [17182271.008000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 10 19:40:22 localhost kernel: [17182271.008000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 10 19:40:22 localhost kernel: [17182271.008000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 10 19:40:22 localhost kernel: [17182271.176000] saa7134 OSS driver for DMA sound loaded
**Feb 10 19:40:22 localhost kernel: [17182271.176000] saa7134 OSS: no saa7134 cards found**
Feb 10 19:40:22 localhost kernel: [17182271.176000] saa7133[0]: registered device video0 [v4l2]
Feb 10 19:40:22 localhost kernel: [17182271.176000] saa7133[0]: registered device vbi0
Feb 10 19:40:22 localhost kernel: [17182271.176000] saa7133[0]: registered device radio0
**Feb 10 19:40:22 localhost kernel: [17182271.176000] saa7133[0]: frontend initialization failed**
Feb 10 19:40:22 localhost kernel: [17182271.176000] saa7133[0]: registered device dsp1
Feb 10 19:40:22 localhost kernel: [17182271.176000] saa7133[0]: registered device mixer1

---

### Post by david_2001 on 2007-02-10
Was this before or after my last "cut to the chase" message?  I'm off to bed now (it's five to one o'clock in the morning here but at least I've had an amusing - and amazed - half hour reading all the posts from those that got caught out by the recent kernel upgrade!)  Anyway, whichever way you try, have a go at setting the saa7134 parameters to "card=46 tuner=12 alsa=1" and I'll pick up the thread tomorrow morning.

---

### Post by Mets on 2007-02-10
hey David thanks a lot.  This was after your cut to the chase post :(

I read on the Linux TV website that you gave me that the guy got his to work by editing his saa7134_cards.c file, recompiling, and re-installing the driver.  I downloaded the saa7134 driver (which said it was from 2004) and made the changes, but couldn't get it to compile.  There is apparently no config file, and it also says that I need the videodev + v4l2 patches from [http://bytesex.org/patches/](http://bytesex.org/patches/).  I was a little unsure of what to do with these, so I just stopped for tonight too, as I need to do some HW so I don't fail out of uni over Linux :D  Thanks again.

---

### Post by david_2001 on 2007-02-11
There shouldn't be any need to download the saa7134 driver from bytesex.org, as that driver is the saa7134 driver that's already in the kernel, just older.  If you really want to try recompiling the driver then work with the current kernel source and follow the Russian's instructions from LinuxTV.  How to recompile the kernel is, of course, a whole new thread of conversation!

Anyway, I've got a little variation on my "cut to the chase" post.  If we're going to go further in diagnosing this problem then it's what I want you to try first and then post your dmesg output (note that I've changed the card options slightly and added an extra step):

1. Remove the TV card
2. Create a file in /etc/modprobe.d containing the options for the saa7134 driver module:
```
sudo sh -c 'echo "options saa7134 card=46 alsa=1" > /etc/modprobe.d/saa7134'
```
3. Edit /etc/modules and add a line containing just
```
saa7134
```
right at the end
4. Reinsert the TV card
5. See what dmesg reports.

---

### Post by avintaquin on 2007-02-11
My friend you should write a how to on this subject.
I have the KWorld PVR-TV 7131 Tuner Card and I followed your instructions above only with the options listed for my card at [http://linuxtv.org/v4lwiki/index.php/Studio_TV_Terminator](http://linuxtv.org/v4lwiki/index.php/Studio_TV_Terminator).  I.E. "card=65 tuner=54".  I left the alsa part out.  It fixed me right up.  This was for on a pci card in a desktop not a laptop so I just rebooted (don't know if that was necessary) and had video, sound, and tuner in tvtime.   It also could be noted that I did not have a existing saa7134 file in modprobe.d.  I did not rmmod any files.  I just did as instructed in the post above.  I am a complete noob and have been banging my head for a while on this problem.  Thank you so much!  Now excuse me while I go do a little victory jig.

---

### Post by david_2001 on 2007-02-11
Happy viewing :).

---

### Post by Mets on 2007-02-11
Glad to hear it worked.  David I think you are taking on one of the biggest problems with Ubuntu :D  Thanks for all of your effors.

Here's my output from the latest try (didn't work)

> Feb 11 19:03:40 localhost kernel: [17266469.880000] pccard: card ejected from slot 0
Feb 11 19:04:29 localhost gconfd (root-10693): starting (version 2.16.0), pid 10693 user 'root'
Feb 11 19:04:30 localhost gconfd (root-10693): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb 11 19:04:30 localhost gconfd (root-10693): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Feb 11 19:04:30 localhost gconfd (root-10693): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb 11 19:04:30 localhost gconfd (root-10693): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Feb 11 19:04:30 localhost gconfd (root-10693): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Feb 11 19:05:00 localhost gconfd (root-10693): GConf server is not in use, shutting down.
Feb 11 19:05:00 localhost gconfd (root-10693): Exiting
Feb 11 19:05:10 localhost kernel: [17266559.196000] pccard: CardBus card inserted into slot 0
Feb 11 19:05:10 localhost kernel: [17266559.196000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
Feb 11 19:05:10 localhost kernel: [17266559.196000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Feb 11 19:05:10 localhost kernel: [17266559.196000] saa7133[0]: found at 0000:03:00.0, rev: 17, irq: 11, latency: 0, mmio: 0xf6000000
Feb 11 19:05:10 localhost kernel: [17266559.196000] saa7133[0]: subsystem: 1461:03e2, board: Philips Tiger reference design [card=81,insmod option]
Feb 11 19:05:10 localhost kernel: [17266559.196000] saa7133[0]: board init: gpio is 0
Feb 11 19:05:10 localhost kernel: [17266559.336000] saa7133[0]: i2c eeprom 00: 61 14 e2 03 ff ff ff ff ff ff ff ff ff ff ff ff
Feb 11 19:05:10 localhost kernel: [17266559.336000] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 11 19:05:10 localhost kernel: [17266559.336000] saa7133[0]: i2c eeprom 20: ff d1 fb ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 11 19:05:10 localhost kernel: [17266559.336000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 11 19:05:10 localhost kernel: [17266559.336000] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 11 19:05:10 localhost kernel: [17266559.336000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 11 19:05:10 localhost kernel: [17266559.336000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 11 19:05:10 localhost kernel: [17266559.336000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 11 19:05:10 localhost kernel: [17266559.592000] saa7134 OSS: can't load, DMA sound handler already assigned (probably to ALSA)
Feb 11 19:05:10 localhost kernel: [17266559.604000] saa7133[0]: registered device video0 [v4l2]
Feb 11 19:05:10 localhost kernel: [17266559.604000] saa7133[0]: registered device vbi0
Feb 11 19:05:10 localhost kernel: [17266559.604000] saa7133[0]: registered device radio0
Feb 11 19:05:10 localhost kernel: [17266559.604000] saa7133[0]: frontend initialization failed
Feb 11 19:05:10 localhost kernel: [17266559.604000] saa7133[0]/alsa: saa7133[0] at 0xf6000000 irq 11 registered as card -1


It appears to me that only the frontend initialization is failing.  Everything else seems to load.

Also, in the past I've seen messages like
localhost gconfd (root-12196): GConf server is not in use, shutting down.
Could this have something to do with it?

---

### Post by david_2001 on 2007-02-12
Man, I just want to keep going now until this thread gets 1,000 views ;-)!  Actually, installing a TV card isn't difficult **provided** that the card is supported by the LinuxTV drivers.  I mean, I've got 3 TV cards installed, an MSI TV@nywhere Plus and two KWorld DVB-T 100s, and they all Just Work(tm) without any tinkering.  (I did my learning a couple of years ago with a dvb-t card that did need some setting-up, a TwinhanDTV Mini Ter.  Presently, it's back in it's box and down in the garage because support for it is broken in the 2.6.17 kernel.)

Anyway, the appearance of "insmod option" in your latest dmesg output:
> Feb 11 19:05:10 localhost kernel: [17266559.196000] saa7133[0]: subsystem: 1461:03e2, board: Philips Tiger reference design [card=81,insmod option]
 is telling me is that you're successfully passing a card type to the driver, just the wrong one :roll:.  Try doing whatever you did again but change "card=81" to "card=46".

EDIT: Actually, you were exactly where you are now 6 days ago.

EDIT Again:  If you really don't know how you're getting what you're getting, then please post the output of
```
ls -al /etc/modprobe.d
```
and your complete /etc/modules file.  Oh, and if you have a file called "saa7134" in /etc/modprobe.d, post the contents of that file as well.

---

### Post by Mets on 2007-02-12
Well, we're well over 1,000 now

I actually just realized something.  I have never, ever, given it the command card=81.  Yet every time I insert the card, it says that line that you quoted.  That tells me one of two things is happening.  1) the system is detecting my card as actually being card=81 and all this time we have been trying to get it to work with card=46, or 2) all of the things we have tried are being overridden somewhere by something that is forcing it to load the s aa7134 drivers with option card=81, and this it never works.

I tried repeating some commands to card=81.  I set /etc/modprobe.d/options to force load saa7134 with card=81, I redid somethings you sugested with card=81, and I get no results.

I tried the force load technique with card=46 and also got no results :)

Just to see what would happen, I unloaded all saa7134 modules and opened up tvtime.  For the first time, TVTime gave me a new message.  It said that it was unable to locate /dev/video0.  It's never said that before.  I'm guessing that at the very least it is detecting the card and loading it up to some degree.

For now I've removed all of the prior changes that we've made, and am posting my info:

> ls -al /etc/modprobe.d
total 96
drwxr-xr-x   3 root root 4096 2007-02-12 23:10 .
drwxr-xr-x 125 root root 8192 2007-02-12 23:12 ..
-rw-r--r--   1 root root 4360 2006-05-05 11:47 aliases
-rw-r--r--   1 root root 1690 2006-08-29 23:50 alsa-base
drwxr-xr-x   2 root root 4096 2007-01-30 03:05 arch
lrwxrwxrwx   1 root root    9 2007-01-30 03:05 arch-aliases -> arch/i386
-rw-r--r--   1 root root  741 2006-05-05 11:47 blacklist
-rw-r--r--   1 root root  628 2006-05-05 11:47 blacklist-framebuffer
-rw-r--r--   1 root root  156 2006-04-06 03:14 blacklist-modem
lrwxrwxrwx   1 root root   41 2007-01-30 03:07 blacklist-oss -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r--   1 root root  567 2006-07-04 22:01 blacklist-pata
-rw-r--r--   1 root root   38 2006-04-06 03:12 blacklist-scanner
-rw-r--r--   1 root root  838 2006-05-05 11:47 blacklist-watchdog
-rw-r--r--   1 root root  484 2006-03-20 00:53 bluez
-rw-r--r--   1 root root   53 2006-06-19 06:52 ibm_acpi.modprobe
-rw-r--r--   1 root root  205 2006-07-10 10:09 ipw3945
-rw-r--r--   1 root root  299 2006-05-05 11:47 isapnp
-rw-r--r--   1 root root  234 2007-01-09 03:51 lrm-video
-rw-r--r--   1 root root   29 2006-01-03 04:53 nvidia-kernel-nkc
-rw-r--r--   1 root root  197 2007-02-12 23:09 options
-rw-r--r--   1 root root  197 2007-02-12 23:02 options~
-rw-r--r--   1 root root   31 2007-02-12 23:10 saa7134
-rw-r--r--   1 root root   31 2007-02-12 23:10 saa7134~
-rw-r--r--   1 root root   41 2006-06-19 06:52 toshiba_acpi.modprobe


/etc/modules
> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
sbp2
sr_mod
fuse
saa7134


saa7134 file
> options saa7134 card=46 tuner=1 alsa=1


/etc/modprobe.d/options file
> # Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2
options saa7134 card=46


Thanks a lot again for taking the time to help

---

### Post by david_2001 on 2007-02-13
This one could run and run!  The "insmod option" in the following from the last dmesg output you posted, i.e.
> Feb 11 19:05:10 localhost kernel: [17266559.196000] saa7133[0]: subsystem: 1461:03e2, board: Philips Tiger reference design [card=81,**insmod option**]
definitely means that the saa7134 driver is using supplied parameters and is not autodetecting the card.  If it were autodetecting the card then the output would look more like the line for my saa7134 card
> [17179587.756000] saa7133[0]: subsystem: 1462:6231, board: MSI TV@Anywhere plus [card=82,**autodetected**]
What to do next:
[LIST=1]
[*]Forget about cards numbered 81.
[*]Edit /etc/modprobe.d/options and delete the whole "options saa7134 card=46" line.  It's just duplicating the contents of the saa7134 file.
[*]Correct the typo in /etc/modprobe.d/saa7134, which should read "options saa7134 card=46 tuner=**12** alsa=1".
[*]Browse every other file in /etc/modprobe.d looking for one that contains a line beginning with "options saa7134".  If you find one, edit the file and delete the line.
[*]Do not change /etc/modules.  It's fine.
[*]Check to see whether you have a file called /etc/modules.conf.  If you have, rename it to something like /etc/modules.conf.is.not.used.in.ubuntu, or just /etc/modules.conf.bak for simplicity, and take a peek inside the file out of curiousity ;-).  Don't delete the file if it is there, however, just in case something breaks after it's been disabled.  If the card options are being set elsewhere then that's outside my range, I'm afraid.
[*]Go back through steps 1 to 6 and very carefully check everything that you've done.  I work in Quality Assurance in real life and really don't want to spend my spare time closely reviewing the results of other people's work :biggrin:.
[*]All complete?  Sure?  Ok, restart your computer with the TV card installed.  Don't even think of playing around removing/reinstalling the card before restarting.
[*]See what dmesg tells you this time.
[/LIST]

---

### Post by Mets on 2007-02-14
Thanks a lot again david.  I removed every refrence to it I could find.  The tuner = 1 was me just trying different  values actually.  There was no modules.conf file.

I found in /etc/modprobe.d/alsa-base the following lines:

> # Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0


I commented it out, so that it is now

> # Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
#install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb #saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0


not that it mattered of course...

/var/log/messages
> Feb 14 00:38:14 localhost kernel: [17179597.300000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
Feb 14 00:38:14 localhost kernel: [17179597.300000] cs: IO port probe 0xd000-0xefff: clean.
Feb 14 00:38:14 localhost kernel: [17179597.300000] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
Feb 14 00:38:14 localhost kernel: [17179597.300000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x51ffffff
Feb 14 00:38:14 localhost kernel: [17179597.940000] pccard: CardBus card inserted into slot 0
Feb 14 00:38:14 localhost kernel: [17179598.016000] cs: IO port probe 0x100-0x3af: clean.
Feb 14 00:38:14 localhost kernel: [17179598.020000] cs: IO port probe 0x3e0-0x4ff: clean.
Feb 14 00:38:14 localhost kernel: [17179598.020000] cs: IO port probe 0x820-0x8ff: clean.
Feb 14 00:38:14 localhost kernel: [17179598.020000] cs: IO port probe 0xc00-0xcf7: clean.
Feb 14 00:38:14 localhost kernel: [17179598.020000] cs: IO port probe 0xa00-0xaff: clean.
Feb 14 00:38:14 localhost kernel: [17179598.100000] Linux video capture interface: v1.00
Feb 14 00:38:14 localhost kernel: [17179598.260000] saa7130/34: v4l2 driver version 0.2.14 loaded
Feb 14 00:38:14 localhost kernel: [17179598.260000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
Feb 14 00:38:14 localhost kernel: [17179598.260000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Feb 14 00:38:14 localhost kernel: [17179598.260000] saa7133[0]: found at 0000:03:00.0, rev: 17, irq: 11, latency: 0, mmio: 0xf6000000
Feb 14 00:38:14 localhost kernel: [17179598.260000] saa7133[0]: subsystem: 1461:03e2, board: Philips Tiger reference design [card=81,insmod option]
Feb 14 00:38:14 localhost kernel: [17179598.260000] saa7133[0]: board init: gpio is 0
Feb 14 00:38:14 localhost kernel: [17179598.396000] saa7133[0]: i2c eeprom 00: 61 14 e2 03 ff ff ff ff ff ff ff ff ff ff ff ff
Feb 14 00:38:14 localhost kernel: [17179598.396000] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 14 00:38:14 localhost kernel: [17179598.396000] saa7133[0]: i2c eeprom 20: ff d1 fb ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 14 00:38:14 localhost kernel: [17179598.396000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 14 00:38:14 localhost kernel: [17179598.396000] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 14 00:38:14 localhost kernel: [17179598.396000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 14 00:38:14 localhost kernel: [17179598.396000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 14 00:38:14 localhost kernel: [17179598.396000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 14 00:38:14 localhost kernel: [17179598.472000] NET: Registered protocol family 17
Feb 14 00:38:14 localhost kernel: [17179598.472000] saa7133[0]: registered device video0 [v4l2]
Feb 14 00:38:14 localhost kernel: [17179598.472000] saa7133[0]: registered device vbi0
Feb 14 00:38:14 localhost kernel: [17179598.472000] saa7133[0]: registered device radio0
Feb 14 00:38:14 localhost kernel: [17179598.684000] lp: driver loaded but no devices found


I guess we have to get it to autodetect somehow?  When I open tvtime, it is sensing that /dev/video0 is installed, it just can't pull any signal from it, and I'm guessing that is because the power light on the card is not on.

---

### Post by david_2001 on 2007-02-14
Just to be certain, I've paid a visit to [COLOR="SandyBrown"][www.bttv-gallery.de]("http://www.bttv-gallery.de/")[/COLOR] and checked that your card works with the saa7134 driver and indeed it does.  I also used the information there to confirm that you actually do have an Avermedia AverTV Cardbus Plus E501R by comparing the eeprom dumps.

If you're in the USA - my guess based on your reference to the Super Bowl at the start of this thread - then you may want to confirm that it has "E501R (For NTSC)" printed on the back.  If it doesn't then we're wasting our time because the PAL/SECAM version of the card will not work in the USA.

Anyway, the first thing you need need to do is edit alsa-base and put it back as it was.  That line has to be enabled (it doesn't begin with "options saa7134" so it won't affect the card type used by the driver).

Now, I realise that you've probably tried this but if you install the saa7134 driver using the rmmod/insmod method, as discussed before, then it will absolutely not, without any shadow of a doubt, be detected as a type 81:
```
sudo rmmod saa7134_alsa
sudo rmmod saa7134_dvb
sudo rmmod saa7134
sudo modprobe saa7134 card=46 alsa=1
```
I don't want to know whether tvtime works yet but only what you get from dmesg after executing the above commands in order.

PS. Don't worry too much about the light on the card not coming on.  I downloaded the user manual, product image etc. and it doesn't have a light :roll:.

---

### Post by Mets on 2007-02-14
Alright I reverted the file you mentioned.  I am indeed in the US, and the card is the E501R model.  My card does have a very small light on the top that illuminates blue when it is in use back when I used to use it on Windows before I switched to Ubuntu.  It's almost impossible to see from the pictures of the card I've seen online, unless you know where to look.  Here's the latest output, and thanks again.

/var/log/messages
> Feb 14 19:12:32 localhost kernel: [17246468.440000] saa7134 ALSA driver for DMA sound unloaded
Feb 14 19:13:14 localhost kernel: [17246510.640000] saa7130/34: v4l2 driver version 0.2.14 loaded
Feb 14 19:13:14 localhost kernel: [17246510.640000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:13:14 localhost kernel: [17246510.640000] saa7133[0]: found at 0000:03:00.0, rev: 17, irq: 11, latency: 64, mmio: 0xf6000000
Feb 14 19:13:14 localhost kernel: [17246510.640000] saa7133[0]: subsystem: 1461:03e2, board: Philips Tiger reference design [card=81,insmod option]
Feb 14 19:13:14 localhost kernel: [17246510.640000] saa7133[0]: board init: gpio is 0
Feb 14 19:13:14 localhost kernel: [17246510.776000] saa7133[0]: i2c eeprom 00: 61 14 e2 03 ff ff ff ff ff ff ff ff ff ff ff ff
Feb 14 19:13:14 localhost kernel: [17246510.776000] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 14 19:13:14 localhost kernel: [17246510.776000] saa7133[0]: i2c eeprom 20: ff d1 fb ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 14 19:13:14 localhost kernel: [17246510.776000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 14 19:13:14 localhost kernel: [17246510.776000] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 14 19:13:14 localhost kernel: [17246510.776000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 14 19:13:14 localhost kernel: [17246510.776000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 14 19:13:14 localhost kernel: [17246510.776000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 14 19:13:14 localhost kernel: [17246510.784000] saa7133[0]: registered device video0 [v4l2]
Feb 14 19:13:14 localhost kernel: [17246510.788000] saa7133[0]: registered device vbi0
Feb 14 19:13:14 localhost kernel: [17246510.788000] saa7133[0]: registered device radio0
Feb 14 19:13:14 localhost kernel: [17246510.876000] saa7134 ALSA driver for DMA sound loaded
Feb 14 19:13:14 localhost kernel: [17246510.876000] saa7133[0]/alsa: saa7133[0] at 0xf6000000 irq 11 registered as card -1

//I don't think the next two lines are from the tuner, but they seemed interesting so I included them
Feb 14 19:16:02 localhost gconfd (root-12329): starting (version 2.16.0), pid 12329 user 'root'
Feb 14 19:16:02 localhost gconfd (root-12329): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb 14 19:16:02 localhost gconfd (root-12329): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Feb 14 19:16:02 localhost gconfd (root-12329): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb 14 19:16:02 localhost gconfd (root-12329): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Feb 14 19:16:02 localhost gconfd (root-12329): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4

---

### Post by niko7865 on 2007-02-15
> **brettg said:**
> While I'm not a guru on TV, I have been experimenting with it a bit lately, here are some things i discovered.

You need to install the tvcard drivers which are called ivtv, see here.

[https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)

A quick google on your card leads me to believe that is a hardware mpeg encoder (most newer cards are) and this means that it is not supported by tvtime, kdetv, xawtv or any of the other TV apps I tried because they don't support mpeg streams.

mplayer supports mpeg2 so you can do mplayer /dev/video0 and see if that "works"

Unfortunately, you can't change channels using mplayer, so you will probably just get black output instead of a picture.

As far as I could discover, your best choice at that stage is mythtv, which is not a simple install as it also requires you to install mysql-server. 

This is where I stopped because I suddenly realised that my DVD drive is not working on my new laptop so I have given up on TV to address more a important problem. 

I hope this helps somewhat though

xawtv works fine with my tuner, which outputs an mpeg stream (Hauppage 150)

---

### Post by david_2001 on 2007-02-15
> **Mets said:**
> Alright I reverted the file you mentioned.  I am indeed in the US, and the card is the E501R model.  My card does have a very small light on the top that illuminates blue when it is in use back when I used to use it on Windows before I switched to Ubuntu.  It's almost impossible to see from the pictures of the card I've seen online, unless you know where to look.  Here's the latest output, and thanks again.

It's not going to be anything to do with GConf and those gconf-related messages you quoted look normal to my inexpert eye.  Type "man gconftool" at a console prompt or do an Internet search for GConf to find out more about what it does.

I'll believe you about the blue light.  Anyway, that wrong insmod option is still there and I have no way of determining why it's appearing despite a completely different card number being passed to the saa7134 module.

Just out of curiousity, though it shouldn't make any difference if you're using rmmod/modprobe, try this at a console prompt (it will search all files in /etc and any subdirectories for the quoted string):
```
sudo grep -r "card=81" /etc/*
```
and this:
```
sudo grep -r "saa7134" /etc/*
```
and this:
```
sudo grep -r "alias char-major-81" /etc/*
```
Also, can you just confirm that you are doing all this while logged in as a user that has privileges to "Administer the system".

EDIT: I added a screenshot to give you something to aim for!

If anybody watching this thread has a constructive suggestion then please feel free to contribute!

---

### Post by Mets on 2007-02-15
I see you have all of the bells and whistles going.  I won't even tell you about how configuring wine went for me :)

I only have two users on my  computer, mine, and root, and I use mine.  I use sudo to do everything.  I'm thinking I do.

Anyway I think we got it.  Check this out:

> sudo grep -r "card=81" /etc/*
grep: /etc/alternatives/irssi: No such file or directory
grep: /etc/alternatives/irssi.1.gz: No such file or directory
sudo grep -r/etc/modprobe.conf:options saa7134 card=81 tuner=54 oss=1
/etc/modprobe.conf~:options saa7134 card=81 tuner=54 oss=1


so I opened up /etc/modprobe.conf and I see, drum roll please
> options saa7134 card=81 tuner=54 oss=1

alias char-major-89 i2c-dev
alias char-major-81 bttv
options bttv card=78 tuner=2 radio=1



I then finished the commands
sudo grep -r "saa7134" /etc/*
grep: /etc/alternatives/irssi: No such file or directory
grep: /etc/alternatives/irssi.1.gz: No such file or directory
/etc/modprobe.conf:options saa7134 card=81 tuner=54 oss=1
/etc/modprobe.conf~:options saa7134 card=81 tuner=54 oss=1
/etc/modprobe.d/alsa-base:# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
/etc/modprobe.d/alsa-base:install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }
/etc/modprobe.d/saa7134:options saa7134 card=46 tuner=12 alsa=1
/etc/modprobe.d/options~:options saa7134 card=46
/etc/modprobe.d/saa7134~:options saa7134 card=46 tuner=1 alsa=1
/etc/modprobe.d/alsa-base~:# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
/etc/modprobe.d/alsa-base~:install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }
/etc/modules:saa7134

 sudo grep -r "alias char-major-81" /etc/*
grep: /etc/alternatives/irssi: No such file or directory
grep: /etc/alternatives/irssi.1.gz: No such file or directory
/etc/modprobe.conf:alias char-major-81 bttv
/etc/modprobe.conf~:alias char-major-81 bttv
/etc/modprobe.d/aliases:alias char-major-81-* videodev
[/QUOTE]

Even I knew that there had to be a problem with what was there.  So I commented out the saa7134 and bttv lines, and added in the option that you have been telling me for the past week, card=46, tuner=12, alsa=1.  I then ejected the card, put it back in, froze the computer (I forgot you told me not to do that), restarted, watched my little blue light come on, loaded up TVTime, and there it was...television.  I have been so deprived.  Granted, the sound doesn't work and the video is really fuzzy, but the fact that it is there is amazing.  I feel like the guy who just got off the boat after years at sea and finally gets the chance to kiss the ground.  I can't thank you enough David.  I would have bailed on this post after the second day.  I guess you're true to your quote &#8211; never give up, never surrender.

---

### Post by Mets on 2007-02-15
screen shot

EDIT : Ok well I guess the TV picture doesn't actually show up in a screen shot, but anyway, it's fuzzy and there's no sound, but the fact that there is video is just amazing.

---

### Post by david_2001 on 2007-02-15
Well, there we are (I hope)!  The /etc/modprobe.conf file should not be there - Ubuntu does not use it - and the file you have is doing all sorts of weird things.  Either rename it to /etc/modprobe.conf.bak or delete it completely and then restart your laptop (and you really must do a restart before doing any further tinkering).

PS.  I paid for CrossOver Office, it makes Wine much easier to use.

---

### Post by david_2001 on 2007-02-15
> **Mets said:**
> screen shot

EDIT : Ok well I guess the TV picture doesn't actually show up in a screen shot, but anyway, it's fuzzy and there's no sound, but the fact that there is video is just amazing.[LIST=1]
[*]Try a better aerial, changing the aerial position and retuning before messing with the audio settings!
[*]Pressing the "s" key in tvtime takes a screenshot and saves it in $HOME.
[*]Full-screen screenshots with a video application running require the X Composite Extension.
[/LIST]
EDIT: Just as a small hint of the fine-tuning to come, if your laptop has sound and it works in Ubuntu and it uses alsa then you are now the proud possessor of two alsa sound devices, the laptop's and the TV card's.  If you find that you no longer have system sound effects (at login etc.) then it will be because the TV card has become set as the default sound device.
EDIT Again: Well done!

---

### Post by Mets on 2007-02-15
Roger than on the screen shot.  I actually just went to channel management in TVTime and changed the frequency from whatever it was at to "Standard NTSC Cable" and it works fine, as good as my tuner displays.  Still no audio though.  Should I change it to oss=1 instead of alsa=1?

I deleted the file too.

EDIT
Yeah I'm not totally sure about sound on my laptop.  I open op the volume control, and I already have three different devicse installed, not including the tuner.  There is an Intel 82801DB device, SigmaTel (my audio card), and ALSA.  System sound continue to works fine, but tuner sound does not.  Video pretty much as good as it is going to get I imagine.  My roommate, who is an Ubuntu user, suggested I try some new video card drivers to make the picture better, but I'm not that daring at the moment.

---

### Post by david_2001 on 2007-02-16
The problem is that your TV card doesn't have an audio pass-through cable that can be connected to a sound card and the answer is in the [COLOR="SandyBrown"][Gentoo wiki]("http://gentoo-wiki.com/HARDWARE_saa7134")[/COLOR].  (I've tried the suggested method and can confirm that it works here.)

First, you need to find out what hardware assignments alsa is giving the sound devices in your laptop.  I would do this by entering the following at a console:
```
sudo alsactl names
```
If you don't have alsactl then
```
sudo apt-get install alsa-utils
```

The "sudo alsactl names" command will create a file called /etc/asound.names.  Browse the file and find the hardware assignment for your TV card.  Here's mine so that you can compare.  The important part is highlighted (all the nice formatting of the original gets thrown away by the forum software here!):
> ctl {
	alsactl1 {
		name hw:0
		comment 'Physical Device - HDA VIA VT82xx at 0xd7efc000 irq 58'
	}
	alsactl2 {
		name **hw:1**
		comment 'Physical Device - saa7133[0] at 0xdffff000 irq 50'
	}
}
Now visit the Gentoo wiki and scroll down to "Tvtime And Sound".  The part you want is the command line under "If you don't want bother with sox and OSS emulation, a better way to start tvtime with DMA sound would be:", customised to your particular setup.  When I tried it I had to enter the correct video and vbi devices for my system to make it work, as follows:
```
tvtime -d /dev/**video2** -b /dev/**vbi2** | arecord -D **hw:1**,0 -r 32000 -c 2 -f S16_LE | aplay -
```
Substitute the alsa hardware assignment you found above for **hw:1**.  You may be able to get away without specifying the video and vbi devices, which should be **/dev/video0** and **/dev/vbi0** for your card (or the symbolic links /dev/video and /dev/vbi) if it won't work without them.

---

### Post by Mets on 2007-02-17
awesome, sound works now too, thanks!  I changed it to /dev/video0 and /dev/vib0, and ran the tvtime command, and it detects the sound.  I doesn't seem to work if I add the command to the menu or make a launcher though, so I guess I'll just run tvtime from the terminal?  I'm assuming that's what you do.  There is one little sound issue left though.  The video and sound are out of sync.  The audio is about 1 second behind the video.  Is there any setting I can change to bring them back into sync?  Thanks again for all of your help with this.

---

### Post by david_2001 on 2007-02-17
I've got a PCI card with audio pass-through cable, so I only use the DMA sound option you are using when recording video.

Regarding the a/v sync problems, browse to the LinuxTV [COLOR="SandyBrown"][saa7134-alsa]("http://linuxtv.org/v4lwiki/index.php/Saa7134-alsa")[/COLOR] page and take a look at the alternative sound options under "ALSA audio with other applications".

Perhaps the easiest way to launch tvtime will be to create a script containing the relevant commands.  Here's an example using sox rather than arecord/aplay that works here with good a/v sync.  Change **/dev/video2**, **/dev/vbi2** and **hw:1** as necessary for your saa7134 card:
```

#!/bin/bash
tvtime -d **/dev/video2** -b **/dev/vbi2** &
sox -r 32000 -w -t alsa **hw:1**,0 -t alsa pcm.default

```
Either make the script file executable ("chmod +x <filename.sh>") or run it with "sh".  Note that the script is not clever and will leave sox running after closing tvtime.

---

### Post by Mets on 2007-02-18
awesome works great thanks.  I'll just run the script in the terminal.  I tried $finish and $exit but that didn't work, but it's no big deal.  The only thing I have to ask - does running this audio take up disk space?  It shows the output buffer in terms of megabytes, and I fee like it is maybe, at least temporarily, saving the audio to disk.  Maybe I'm just overreacting.  Thanks a million for all the help David, I can't believe we got it working.  Take care!

---

### Post by david_2001 on 2007-02-19
Persistence pays off ;-)!  And sox is essentially piping the sound from one alsa source (the TV card) to another (the sound card), so I wouldn't worry about temporary files.  In any event, Ubuntu cleans out the /tmp directory at boot time.

---

### Post by bianconiglio on 2007-12-01
Thanks david_2001! A bit off-topic. Anyway... your advice (about piping alsa into sox) works on Gutsy Gibbon, with an e-tech TVPI03 tvcard in the Netherlands. See my post on: 

[http://ubuntuforums.org/showpost.php?p=3875151&postcount=13](http://ubuntuforums.org/showpost.php?p=3875151&postcount=13)

Bye bye!

---

### Post by ecanizal on 2008-05-22
> **david_2001 said:**
> I've got a PCI card with audio pass-through cable, so I only use the DMA sound option you are using when recording video.

Regarding the a/v sync problems, browse to the LinuxTV [COLOR="SandyBrown"][saa7134-alsa]("http://linuxtv.org/v4lwiki/index.php/Saa7134-alsa")[/COLOR] page and take a look at the alternative sound options under "ALSA audio with other applications".

Perhaps the easiest way to launch tvtime will be to create a script containing the relevant commands.  Here's an example using sox rather than arecord/aplay that works here with good a/v sync.  Change **/dev/video2**, **/dev/vbi2** and **hw:1** as necessary for your saa7134 card:
```

#!/bin/bash
tvtime -d **/dev/video2** -b **/dev/vbi2** &
sox -r 32000 -w -t alsa **hw:1**,0 -t alsa pcm.default

```
Either make the script file executable ("chmod +x <filename.sh>") or run it with "sh".  Note that the script is not clever and will leave sox running after closing tvtime.

I suggest...

#/bin/bash
tvtime &
arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | sox -q -c 2 -r 32000 -w -t wav - -t alsa hw:0,0 &
pid=$(pidof tvtime)
while [ -n "$pid" ]; do
   pid=$(pidof tvtime)
done
pid=$(pidof sox)
kill -9 "$pid" 

This works better for me, because I don't have to be worried about sox whenever I exit tvtime. I had problems with every other application that uses my sound card just after using tvtime piped with sox , because sox won't die until handy killed :D

---

