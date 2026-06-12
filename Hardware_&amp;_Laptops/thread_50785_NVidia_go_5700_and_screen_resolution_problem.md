---
title: "NVidia go 5700 and screen resolution problem"
date: 2005-07-21
forum: Hardware &amp; Laptops
---

### Post by GreatBunzinni on 2005-07-21
I'm the proud owner of a Acer Aspire 1524 and I'm running kubuntu 5.04. The default graphics display are excellent and display everything flawlessly. The problem appears when I try to run NVidia's driver which I installed via kynaptic.

My laptop's default resolution is 1280x800 and it works great with the default xorg driver. When I replace "nv" with "nvidia" in xorg.conf and reboot, the system boots in 1280x768 video mode and KDE doesn't list 1280x800 as an available screen resolution. This is the problem.

I don't get it. xorg.conf is exactly the same. The only thing that changes is the video card driver. The rest stays exactly the same. Still, the default screen resolution isn't listed when NVidia's driver is running.

So, can anyone help me? I would love to run kubuntu with video acceleration and this is stopping me from doing just that. What do I have to do to make this work?

---

### Post by GreatBunzinni on 2005-08-01
Can't anyone help a desperate newbie? It is annoying to have to boot to windows to play True Combat: Elite  :-?

---

### Post by kkass on 2005-08-01
Ok, I had a similar problem.  I will tell you what I did to fix it.  It may not solve your problem, but I hopefully it will help point you in the right direction.

When I installed the NVIDIA drivers for my card (GeForce 5650 Go) and restarted X, the resolution looked like I was running much lower than I should.  But the system still reported that I was running 1680x1050.  The one difference I did notice was in **System > KInfoCenter >> X-Server**.  The Dimensions and resolution lines had changed.  I forget the exact change on the dimensions line (though it still said 1680x1050 with a different mm value), but the resolution line changed to 125 x 125 dpi.

Before installing the NVIDIA drivers it was:
Dimensions: 1680x1050 (569 x 356 mm)
Resolution: 74 x 74 dpi

OK the fix is to edit your '/etc/X11/xorg.conf' file and add the line: "DisplaySize  569 356" to the Monitor section.  (Notice I used the measurements from the dimensions line, so try using yours).

Here is the whole section from my xorg.cof:

Section "Monitor"
        Identifier      "Generic Monitor"
        Option       "CalcAlgorithm" "CheckDesktopGeometry"
        DisplaySize  569 356
        Option          "DPMS"
        HorizSync       30-90
        VertRefresh     50-60
EndSection

I hope this helps!

---

### Post by Rincewind on 2005-08-12
[QUOTE=GreatBunzinni]Can't anyone help a desperate newbie? It is annoying to have to boot to windows to play True Combat: Elite  :-?[/QUOTE]

Hi,

I've got the same laptop, had to mess around with x.org modeline settings to get the 1280x800.  My xorg.conf attached below.

Rincewind

---

### Post by fxalpha on 2005-08-12
hi, got that laptop too. runnning ubuntu hoary amd64 and 386. all hardware is working in 386 including wifi, probs with wlan in 64bit, drivers are now available but they complain about wrong os when i try to install. Here's link to my xorg so you can compare. mine runs 1280x800 and is using the ubuntu nvidia packages. If you need any more files for reference let me know :)
ubuntu rox on this lappy.
just out of interest, my card reader picks and chooses when to work. if it doesn't pop the icon on desktop after insertion i get read errors/ unable to apply power to pcmcia sort of msgs in the logs and from dmesg. you guys get anything like this?
[http://www.fxalpha.co.uk/xorg.conf](http://www.fxalpha.co.uk/xorg.conf)

---

### Post by GreatBunzinni on 2005-08-12
This is very strange. My xorg.conf file is exactly the same as fxalpha and I can't get 1280x800 resolution with the NVidia drivers. Just 1280x768. The only difference is that I don't have the DRI module commented off.

Can anyone suggest a new approach to solve this problem? I've ran out of ideas with this one :S

---

### Post by Rincewind on 2005-08-12
[QUOTE=GreatBunzinni]This is very strange. My xorg.conf file is exactly the same as fxalpha and I can't get 1280x800 resolution with the NVidia drivers. Just 1280x768. The only difference is that I don't have the DRI module commented off.

Can anyone suggest a new approach to solve this problem? I've ran out of ideas with this one :S[/QUOTE]

Please try my xorg.conf attached above...

Option "IgnoreEDID" "1"

...in the monitor section is important!

---

### Post by Rincewind on 2005-08-12
[QUOTE=fxalpha]just out of interest, my card reader picks and chooses when to work. if it doesn't pop the icon on desktop after insertion i get read errors/ unable to apply power to pcmcia sort of msgs in the logs and from dmesg. you guys get anything like this?
[http://www.fxalpha.co.uk/xorg.conf](http://www.fxalpha.co.uk/xorg.conf)[/QUOTE]

Hi,

Yeah, I get the following in the log after inserting a card:

[INDENT]cs: memory probe 0xa0000000-0xa0ffffff: clean.
Probing IDE interface ide2...
hde: Memory Card Adapter, CFA DISK drive
ide2 at 0x100-0x107,0x10e on irq 3
hde: max request size: 128KiB
hde: 121856 sectors (62 MB) w/1KiB Cache, CHS=476/8/32
hde: cache flushes not supported
 /dev/ide/host2/bus0/target0/lun0:hde: status error: status=0x7f { DriveReady DeviceFault SeekComplete DataRequest CorrectedError Index Error }
hde: status error: error=0x00 { }
ide: failed opcode was: unknown
hde: drive not ready for command
ide2: reset: master: error (0x40?)
 p1
ide-cs: hde: Vcc = 3.3, Vpp = 0.0
[/INDENT]

But I can mount hde manually after that.

Rincewind

---

### Post by fxalpha on 2005-08-12
Cheers for that! Glad it's not just me. Tried mounting afterwards and like you said, it mounted ok. Strange, but it means i know now, so thankyou :)
Also i checked and i don't got the  ignore EDID in my xorg.conf
What does this line actually do? My display is fine without, but would it be a good idea to put it in?

---

### Post by Rincewind on 2005-08-12
[QUOTE=fxalpha]Cheers for that! Glad it's not just me. Tried mounting afterwards and like you said, it mounted ok. Strange, but it means i know now, so thankyou :)
Also i checked and i don't got the  ignore EDID in my xorg.conf
What does this line actually do? My display is fine without, but would it be a good idea to put it in?[/QUOTE]

EDID stands for "Extended Display Identification Data" and gives info about the capabilites of the monitor, but it doesn't work correctly with the nvidia drivers on this laptop, so 'ignore EDID' ignores it and uses the modes you specify....  I think! :)  I had to google it...  Anyway, it solved my problems. :)

Plus it solved the white screen problem - switching to another console (ctrl-alt-F1 etc) left a white screen with corruption until 'ignore EDID' was put in.

Rincewind

---

### Post by GreatBunzinni on 2005-08-13
[QUOTE=Rincewind]Please try my xorg.conf attached above...

Option "IgnoreEDID" "1"

...in the monitor section is important![/QUOTE]

I've tried and it works!! Now, I only need to fine tune the display for it to look exactly like the non-nvidia display.  The fonts are huge compared with the non-accelerated driver's display. I believe that it has something to do with the resolution. The non-nvidia resolution is 75x75dpi while the nvidia resolution is 100x100 dpi. Is this what is making it look so big? If so, how can I correct that?


Oh, and thanks for the help, Rincewind. Kudos!

---

### Post by fxalpha on 2005-08-13
rincewind, it's people like you that got me through the difficult first stages with linux. and it goes to show you learn a new and useful thing everyday. thanks. i thought i was stuck with the white screen thing. now it works as it should.
glad yours is fixed too Great Bunzinni.
al

---

### Post by kkass on 2005-08-13
GreatBunzinni, review my post from above.  That is exactly how my display looked after switching to the nvidia drivers.

[QUOTE=kkass]OK the fix is to edit your '/etc/X11/xorg.conf' file and add the line: "DisplaySize  569 356" to the Monitor section.  (Notice I used the measurements from the dimensions line, so try using yours).[/QUOTE]

---

### Post by GreatBunzinni on 2005-08-14
[QUOTE=kkass]GreatBunzinni, review my post from above.  That is exactly how my display looked after switching to the nvidia drivers.[/QUOTE]
You are absolutely right. What happened was that I had that line in my xorg.conf. Unfortunately, in the middle of those experiments, I left it commented out while believing it was active. Everything runs very smoothly and as it should run after uncommenting that line.

Thanks everyone for helping. It's thanks to people like you (rincewind, kkass) that hopeless newbies like me can make things work. Thanks for your help and thanks for your patience. Kudos!

---

