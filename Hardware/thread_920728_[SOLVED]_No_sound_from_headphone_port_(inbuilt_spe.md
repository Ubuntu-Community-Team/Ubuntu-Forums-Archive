---
title: "[SOLVED] No sound from headphone port (inbuilt speakers work)"
date: 2008-09-15
forum: Hardware
---

### Post by brim4brim on 2008-09-15
Hi guys,

I have a Sony Vaio laptop although I have sound from the laptop speakers and can even control it using the extra buttons for the sound, when I plug in my headphones, the sound still comes from the laptop speakers and no sound comes from the headphones.

Anyone got any ideas?  Feel free to ask me to run terminal stuff but I've no idea what to do myself.

Thanks in advance!

---

### Post by brim4brim on 2008-09-15
A couple of things I have noticed.

My optical out port isn't turned on either (no red light like it has in windows) so it looks like the headphone port is turned off.

In audio (HDA Intel (Alsa mixer)), I see a headphone volume control but it does nothing.

Anyone able to help?

---

### Post by brim4brim on 2008-09-15
Saw someone else posting this, hope it can help someone help me.
I've turned up everything in the volme control and run alsa mixer to turn up everything.

Also tried forcing a reload of Alsa with no difference, still just sound from laptop speakers and nothing from headphone jack.

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Note if I put my headphones into the mic slot I hear a spit sound like that port has power but nothing like that for the headphone port.  Not sure if its getting power or not now.  They are all together in the side of the laptop.

---

### Post by brim4brim on 2008-09-15
Ah, getting somewhere, output from dmesg is:
[ 5076.545163] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x100f0000
[ 5076.547381] hda_codec: Unknown model for ALC262, trying auto-probe from BIOS...
[ 5076.547811] hda_codec: Cannot set up configuration from BIOS.  Using base mode...

okay a bit of Googling and this a known Kernel bug it seems:
[http://bugzilla.kernel.org/show_bug.cgi?id=8769](http://bugzilla.kernel.org/show_bug.cgi?id=8769)

Comment number 2 is this:
------- Comment  #2 From David  2007-09-20 06:34:38  [reply] -------

This happens with the kernel-included alsa drivers, but not with external
alsa-drivers.


I'm going to give using external alsa-drivers a go and hope for the best.  Although I'm not entirely sure what I'm doing.  If anyone has a link to a howto, it would be appreciated.

---

### Post by eggdeng on 2008-09-15
Try editing the alsa-base file
```
gksudo /etc/modprobe.d/alsa-base
```
Add the line
```
options snd-hda-intel model=vaio
```
or - some vaio models require -
```
options snd-hda-intel model=vaio enable=1 index=0 position_fix=1

```
at the bottom of the file and [COLOR="Red"]reboot[/COLOR].

---

### Post by brim4brim on 2008-09-15
> **eggdeng said:**
> Try editing the alsa-base file
```
gksudo /etc/modprobe.d/alsa-base
```
Add the line
```
options snd-hda-intel model=vaio
```
or - some vaio models require -
```
options snd-hda-intel model=vaio enable=1 index=0 position_fix=1

```
at the bottom of the file and [COLOR="Red"]reboot[/COLOR].

Sweet, thanks a lot man, second line worked perfectly.  Just added it and selected OSS from sound properties in System Properties and everything is working.

It switches off laptop speakers on head phone plugin and switches on laptop when I plug out headphones.

---

### Post by brim4brim on 2009-05-04
Got a PM for this.  I have just updated to 9.04 of Kubuntu literally today so I'm writing up these changes for anyone that needs them.  Nothing major but copying and pasting the above won't work on 9.04 edition of Ubuntu/Kubuntu.

Open a terminal window.  Type:
```

sudo cp /etc/modprobe.d/alsa-base.conf /etc/modprobe.d/alsa-base.conf.backup

```

Now that you have a backup copy in case you make a mistake or this isn't specific to your Vaio laptop you can continue.  The command seems to have changed slightly since the last release.
On Kubuntu type:
```

sudo kate /etc/modprobe.d/alsa-base.conf

```

On Ubuntu type:
```

sudo gedit /etc/modprobe.d/alsa-base.conf

```

You'll be prompted for your password.  This gives you read/write access to the file at location /etc/modprobe.d/alsa-base.conf which is the configuration file you need to edit.

Once you have the file open, scroll to the very end of the file and append to the file:
```

#add me, comment line which separates what you have added from the rest of the file
options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=vaio enable=1 index=0 position_fix=1

```

Now reboot and your sound should work perfectly.  I don't know exactly why this fixes the problem but it basically activates a hack for Vaio models with the HDA-Intel sound card that seems to work perfectly for my model and probably for others too as the command is specified on a few forums for different models of Vaio laptops.

---

