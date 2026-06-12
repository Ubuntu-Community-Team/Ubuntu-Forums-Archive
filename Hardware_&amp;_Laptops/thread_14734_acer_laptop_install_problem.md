---
title: "acer laptop install problem"
date: 2005-02-09
forum: Hardware &amp; Laptops
---

### Post by DanielT on 2005-02-09
Hello,

i just bought a new acer laptop (travelmate 2200) and was hoping to put ubuntu on to it, but it freezes when installing, when the 'chose language' menu (first curses install menu) comes up it won't respond, no keys work, not even caps lock etc.

I should probably mention that this laptop has something weird going on where it needs a small partition (fist partition on the table) that it writes to for recovery purposes (from what i gather from the manual) so ubuntu would have to be installed to /dev/hda2 (i don't think that makes any difference but it's worth mentioning.)

the live cd won't work either, i get the following errors:

Warning: unable ti find base module!
cat: /MorphixCD/etc/ld.so.cache: No sure file or directory

Setting paths.../linuxrc: 543: /bin/cp: not found
/linuxrc: 543: test: not found
/linuxrc: 543: rm: not found
/linuxrc: 543: awk: not found
[...]
/linuxrc: 543: echo: not found
/linuxrc: 543: mkdir: not found
/linuxrc: 543: cannot create /var/run/utmp: Directory nonexistent
VRS: Cannot open root device "<NULL>" or unknown-block(9,0)
Please append a correct "root=" boot option
Kernel panic: VFS: Unable to mount root fs on unknown-block(9,0)

Spec of laptop available here:
[http://www.comet.co.uk/comet/html/cache/320_228214.html](http://www.comet.co.uk/comet/html/cache/320_228214.html)

I currently have slackware running on it, that install went fine.

I don't think it's the cd, i have tried 3 different ones (the ones i ordered from 'shipit')

thanks for any help you can give,

Daniel,

---

### Post by DanielT on 2005-02-09
Is there any other way of installing ubuntu? 

the debian installer just doesn't work, tried all sorts of boot settings,

---

### Post by Edd on 2005-05-25
I just tried to install the distro and found out that I  had the same problem when i used the installer, i found out that if you press the [Fn] and [Left shift] key at the same time youre able to use the keyboard again. Unfortunaly you have to do this every time when you reboot. But at least youre able to install the distro and use it.

---edit----
Beside that, the touchpad doesnt work for me, i'll see if i can correct this (or does some1 have an idee to correct this ;) ), but untill then i have to use a usb mouse

---

### Post by Edd on 2005-06-03
looks like i found an anwser to the problems,

when you want to install ubuntu use as boot option:
```
linux acpi=off i8042.nomux
```
When you use these options the keyboard (and after the install) and the touchpad worked for me :)

---

### Post by rraiman on 2005-07-01
I just finished installing Ubuntu on a friend's Travemate 2200.  I had the same problem with the keyboard and mouse freezing.
The problem is a bios setting.
Select 'F2' while powering up.  Look for the biso setting:
Legasy USB Support <Enabled>

Change this to <Disabled>
Save, power down. Re power up.

Then the keyboard and touchpad will work.
Crazy setting.
Now my problems are sound, not working and the internal modem.

---

### Post by grv on 2005-07-06
sucessfully installed ubuntu 4.10 on acer travelmate 4150. the live cd didn't work, but kindof worked around the install cd.

listed my steps here: [http://scrabbers.blogspot.com](http://scrabbers.blogspot.com)

---

### Post by Edd on 2005-07-07
[QUOTE=rraiman]I just finished installing Ubuntu on a friend's Travemate 2200.  I had the same problem with the keyboard and mouse freezing.
The problem is a bios setting.
Select 'F2' while powering up.  Look for the biso setting:
Legasy USB Support <Enabled>

Change this to <Disabled>
Save, power down. Re power up.

Then the keyboard and touchpad will work.
Crazy setting.
Now my problems are sound, not working and the internal modem.[/QUOTE]

Thanks for the tip on the disableling the "Legasy USB Support", works fine here. I also was able to get the sound working, i folowed the directions from here: [http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)

Also i'm able to use acpi, i'm using a custom DSDT, wich i've downloaded from: [http://acpi.sourceforge.net/dsdt/index.php](http://acpi.sourceforge.net/dsdt/index.php)

---

### Post by stimpy22 on 2006-01-04
this is odd,  i can install fine on my Travelmate 2200.  Try the bios updates posted on Acer's website

---

### Post by Edd on 2006-01-04
[QUOTE=stimpy22]this is odd,  i can install fine on my Travelmate 2200.  Try the bios updates posted on Acer's website[/QUOTE]
hmm i will thanks,

btw do you also have acpi working with that?

---

### Post by tihom on 2006-01-17
pls help. i have an acer laptop 4100 series. i tried to install ubuntu both in live and install modes but my laptop just hangs. from the beginning this is what happens

as the computer starts

[B]this is the ubuntu live cd
press f1 for help and advanced options

for the default live system, press enter
boot:_[/B]
after i press enter

[B]loading /install/vmlinuz.........................
loading /install/initrd.gz...............................

ready.
uncompressing linux...ok, booting the kernel.
_[/B]
after this there is no response. i have waited for half an hour. i tried doing expert option and the normal install CD but the result is exactly the same.

need help....have read so much..and now really want to get into action.

---

