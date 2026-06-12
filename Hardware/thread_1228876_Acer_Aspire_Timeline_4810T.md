---
title: "Acer Aspire Timeline 4810T"
date: 2009-08-01
forum: Hardware
---

### Post by crinisuilla on 2009-08-01
The other [Acer Aspire Timeline]("http://ubuntuforums.org/showthread.php?t=1165087&highlight=Aspire+Timeline") thread is getting big, so I wanted to start a slightly different one for my laptop, the Acer Aspire 4810T (specifically the AS4810T-8480).  I installed Jaunty 64bit on it and it worked out of the box!  

Specs at a glance: C2D (U3500 @ 1.40 GHz), 4Gb RAM, 320 Gb HD, 13" panel.

I upgraded to 2.6.30.3 (the latest kernel as of this writing), then to get the wired ethernet working, I did the following:
1. Downloaded the latest driver for AR813X from [Atheros's website]("http://partner.atheros.com/drivers.aspx/")
 (1.0.0.9 as of this writing)
2. Untar and change to the src directoy
3. make
4. sudo make install
5. sudo modprobe atl1e  (or restart)

For the 2.6.30.3 kernel I needed [to do this.]("http://ubuntuforums.org/showpost.php?p=7588454&postcount=19")  change kcompat.h in the src directory:

```
208,209c208,209
< #define IRQ_HANDLED
< #define IRQ_NONE
---
> #define IRQ_HANDLED 1
> #define IRQ_NONE 0
```Suspend and hibernate also worked after the kernel upgrade.  Though I found hibernate to be insanely slow.  Suspend worked well seemingly without a hitch.

Camera driver was also correctly detected.  I could run *cheese* without having to do a modprobe.

The biggest bummer right now is that the toggle button on the mouse touchpad only turns OFF the keypad.  I can fudge mousepad toggle like so by adding the following to /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi ::
```

  <device>
    ...
    ...
    <match key="info.product" contains="Synaptics TouchPad">
        <merge key="input.x11_options.SHMConfig" type="string">On</merge>
    </match>
    ...
  </device>

```Then after restarting, I can toggle the mouse with
```
synclient TouchpadOff=0 
synclient TouchpadOff=1
```

I am loving this laptop with Linux (despite a button I never had before not working).  Screen is crisp, the "chiclet" keyboard is trendy and easy for a touch typist.  The brushed aluminum is slick.  Also, Acer rather cleverly moved the CDROM eject to the top of the keyboard so I can't accidentally open it just by carrying it (which happened far too frequently with my previous laptop).  Acer also removed the panel latch (another useless feature of my previous laptop).  Combine all that with the size, cool running, and slim profile, and I'm one satisfied laptop buyer and Linux user.

---

### Post by networm on 2009-08-04
This is just wonderful. Exactly what I've been looking for. Thank you a million time.:popcorn::KS

---

### Post by crinisuilla on 2009-08-12
I've recently been interested in getting Bluetooth to work.  lsusb does not report the presence of bluetooth, but the acer-wmi module is loading.  Has anyone had success getting the internal bluetooth on an Acer Aspire Timeline working?

---

### Post by Sashin on 2009-08-15
What do you get in the way of battery life?

---

### Post by miguellocsin on 2009-08-26
[B][COLOR=Sienna][SIZE=3]Hi,
   Can anyone help my kid with her problem? Its a new acer timeline 4810T it keeps on hanging when she's researching or using the office 2007 programs. Thanks in advance.
[/SIZE][/COLOR][/B]

---

### Post by stoner_di on 2009-08-28
> **crinisuilla said:**
> The other [Acer Aspire Timeline]("http://ubuntuforums.org/showthread.php?t=1165087&highlight=Aspire+Timeline") thread is getting big, so I wanted to start a slightly different one for my laptop, the Acer Aspire 4810T (specifically the AS4810T-8480).  I installed Jaunty 64bit on it and it worked out of the box!  

Specs at a glance: C2D (U3500 @ 1.40 GHz), 4Gb RAM, 320 Gb HD, 13" panel.

I upgraded to 2.6.30.3 (the latest kernel as of this writing), then to get the wired ethernet working, I did the following:
1. Downloaded the latest driver for AR813X from [Atheros's website]("http://partner.atheros.com/drivers.aspx/")
 (1.0.0.9 as of this writing)
2. Untar and change to the src directoy
3. make
4. sudo make install
5. sudo modprobe atl1e  (or restart)

For the 2.6.30.3 kernel I needed [to do this.]("http://ubuntuforums.org/showpost.php?p=7588454&postcount=19")  change kcompat.h in the src directory:

```
208,209c208,209
< #define IRQ_HANDLED
< #define IRQ_NONE
---
> #define IRQ_HANDLED 1
> #define IRQ_NONE 0
```Suspend and hibernate also worked after the kernel upgrade.  Though I found hibernate to be insanely slow.  Suspend worked well seemingly without a hitch.

Camera driver was also correctly detected.  I could run *cheese* without having to do a modprobe.

The biggest bummer right now is that the toggle button on the mouse touchpad only turns OFF the keypad.  I can fudge mousepad toggle like so by adding the following to /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi ::
```

  <device>
    ...
    ...
    <match key="info.product" contains="Synaptics TouchPad">
        <merge key="input.x11_options.SHMConfig" type="string">On</merge>
    </match>
    ...
  </device>

```Then after restarting, I can toggle the mouse with
```
synclient TouchpadOff=0 
synclient TouchpadOff=1
```

I am loving this laptop with Linux (despite a button I never had before not working).  Screen is crisp, the "chiclet" keyboard is trendy and easy for a touch typist.  The brushed aluminum is slick.  Also, Acer rather cleverly moved the CDROM eject to the top of the keyboard so I can't accidentally open it just by carrying it (which happened far too frequently with my previous laptop).  Acer also removed the panel latch (another useless feature of my previous laptop).  Combine all that with the size, cool running, and slim profile, and I'm one satisfied laptop buyer and Linux user.

Would you published ". config" file using the kernel compilation? How do you go apparmour?

I'll be very grateful!

---

### Post by balagosa on 2009-09-15
I have a problem with my wireless connection.

I already did the correct setup for my wired Ethernet but then my wireless is not present.

Only a) localhost, and b) eth0 show up when i do ```
ifconfig
```

---

### Post by zelhar on 2009-09-19
I have a problem shutting down this notebook. I see a message that some sort of unmount failed and I must press CTRL-ALT-Del for it to restart.

---

### Post by Arlanthir on 2009-09-21
Thanks for all the information!
I'm planning on buying a 4810T myself and I had to check if it ran Ubuntu well enough :P

After reading most of the topics about the Timeline series, I'm under the impression it will be better to wait for Karmic (or risk installing the alpha6 now), as it fixes most of the bugs. 

However, I have to ask: should I get the 32 or the 64 bits version? I reckon the 32 version doesn't recognize all the RAM, and has more problems suspending and hibernating, while the 64bits version has problems too for some people :S

---

### Post by Sashin on 2009-09-21
I haven't tried the 32 bit version, but I'm running it on the 64bit version and it seems to be running really smoothly.

---

### Post by Arlanthir on 2009-09-22
> **Sashin said:**
> I haven't tried the 32 bit version, but I'm running it on the 64bit version and it seems to be running really smoothly.

That's very good to hear, thanks :)

---

### Post by crinisuilla on 2009-12-09
I used the Software Manager to upgrade to Karmic Koala, and everything worked really well, even the upgrade to grub2.  The ethernet port is correctly detected, so I didn't need to build my own kernel module.  All of my settings were maintained, too.  The mouse kill switch still doesn't work, and I haven't tested the built-in CD/DVD ROM drive yet.  I had some issues with that before where the disk had to be already inserted either during startup or while hibernating for the OS to properly detect it.

---

