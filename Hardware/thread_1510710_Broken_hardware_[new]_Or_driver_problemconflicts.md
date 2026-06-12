---
title: "Broken hardware? [new] Or driver problem/conflicts?"
date: 2010-06-15
forum: Hardware
---

### Post by Moozillaaa on 2010-06-15
Is my chipset broken, or do I have a driver / hardware conflict?

It's a new build:
[COLOR=Indigo]
[/COLOR] [COLOR=Purple]FoxConn A7DA-S mobo / ATI HD 3300 integrated vids
AMD Athlon II x3 440
Kingston 1G 667 x 4sticks[/COLOR]

It worked *PRETTY* good for 6 weeks - occasional flickering with GLSlideshow preview, and sometimes I had to refresh a webpage since fonts were still large - not reduced to proper display size.

Today, I booted up, and got an 'Out of Range' signal on the display Westinghouse 19" LCD. Display works fine in Windows. No update yesterday, that could have done this.

I can get X-server loaded in reduced resolution, and loaded the ATI proprietary driver, re-booted, and 'Out of Range' again.

I reloaded Ubuntu on a spare partition, and got the same error.

When I first assembled the board, it was a problem - the CMOS jumpers are mis-labeled, and it turns out to have been recalled. Tech support SEEMED to get me booted up OK, but now this...

HELP???

---

### Post by gordintoronto on 2010-06-16
Does the manual for the Westinghouse tell you what "out of range" means?
...
After a little Googling, it seems likely that you need to boot in safe mode and reduce the refresh rate of your graphics card.

---

### Post by jocko on 2010-06-16
> **gordintoronto said:**
> Does the manual for the Westinghouse tell you what "out of range" means?
No need to look that up in a manual. It means the graphics card is set to use a resolution and/or refresh rate that the monitor does not support.
The solution depends on why it happened. Either you added an unsupported resolution/refresh to your /etc/X11/xorg.conf or you set it in the catalyst control center.
If the problem is with xorg.conf, I think running this in a terminal (or from recovery mode) could help:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo aticonfig --initial
```It first backs up your current xorg.conf and then creates a new one.

If the problem is a setting in the catalyst control center, you need to delete its configuration file (it will be regenerated automatically):
```
sudo rm /etc/ati/amdpcsdb
```

---

### Post by Moozillaaa on 2010-06-16
> **jocko said:**
> No need to look that up in a manual. It means the graphics card is set to use a resolution and/or refresh rate that the monitor does not support.
The solution depends on why it happened. Either you added an unsupported resolution/refresh to your /etc/X11/xorg.conf or you set it in the catalyst control center.
If the problem is with xorg.conf, I think running this in a terminal (or from recovery mode) could help:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo aticonfig --initial
```It first backs up your current xorg.conf and then creates a new one.

If the problem is a setting in the catalyst control center, you need to delete its configuration file (it will be regenerated automatically):
```
sudo rm /etc/ati/amdpcsdb
```

Good explanations!

I reconfigured x to default, so there was nothing to back up. So aticonfig --initial returned
> chucknb@chucknb-desktop:~$ sudo aticonfig --initial
Data incomplete in file /etc/X11/xorg.conf
    Device section "Configured Video Device" must have a Driver line.
aticonfig: Parsing the configuration file failed.
The above error messages are reported from XFree86 and may assist you in
diagnosing the problem with your configuration input file. Try use -f option
to generate a new configuration file.
chucknb@chucknb-desktop:~$Then I removed amdpcsdb, re-booted, and it hung on 'loading hardware drivers'. I tried again, 'recovery/fix broken packages', and it finally loaded lo-res display. 

Then I added manually fglrx, and it started boot process, then the display showed NO SIGNAL for 5 seconds, and it then went to 'Low graphics mode'.

That's where it is now...

---

### Post by Moozillaaa on 2010-06-16
I got higher resolution, but I believe still that I have a broken video chip.

You cannot see the occasional horizontal flicker, or distorted graphics of the X-server as it loads - it's ugly.

But I can capture another flaw - as I click and drag the GLSlideshow dialogue window, see the lost preview window (and the flicker manifests in the preview window WORSE with mouse movement):

---

### Post by Moozillaaa on 2010-06-18
bumpin' here...

---

