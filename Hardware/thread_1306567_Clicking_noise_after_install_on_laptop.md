---
title: "Clicking noise after install on laptop"
date: 2009-10-30
forum: Hardware
---

### Post by andywizs on 2009-10-30
Hello,

Since installing Ubuntu 9.10 I get an intermittent clicking noise, possibly coming from the hard disk or "within" my laptop. it almost sounds like the click noise you sometimes hear through speakers or on a dodgy old record, yet I can turn sound completely off and still hear it.

My laptop is a Compaq Presario v6000 if that helps? I saw an older thread about a similar issue but could find no solution.

Any help appreciated!

---

### Post by rocklinks on 2009-11-02
Snap! It's very annoying! and turning the speakers off, does not fix the problem.

---

### Post by peculiar penguin on 2009-11-02
Do you have some sort of "HDA" (HD Audio) sound controller in your laptop? Karmic now turns these off/on as needed to save power when they're not being used, which can cause audible pops/clicks with some devices.

You can disable this by changing the options of the snd-hda-intel module in /etc/modprobe.de/alsa-base.cfg (set power_save to 0 and power_save_controller to N).

---

### Post by efes50cl on 2009-11-02
[quote=andywizs;8198658]Hello,

Since installing Ubuntu 9.10 I get an intermittent clicking noise

Same problem here my notebook is Lenovo 3000 V200

---

### Post by Ayuthia on 2009-11-02
> **peculiar penguin said:**
> 
You can disable this by changing the options of the snd-hda-intel module in /etc/modprobe.de/alsa-base.cfg (set power_save to 0 and power_save_controller to N).

I think that the file location is actually:
```
/etc/modprobe.d/alsa-base.conf
```

You can also just comment out the line at the end of the file so that it looks like this:
```
#options snd-hda-intel power_save=10 power_save_controller=N
```

---

### Post by efes50cl on 2009-11-02
> **Ayuthia said:**
> I think that the file location is actually:
```
/etc/modprobe.d/alsa-base.conf
```You can also just comment out the line at the end of the file so that it looks like this:
```
#options snd-hda-intel power_save=10 power_save_controller=N
```


Nope:( didnt  work 4 me clicking problem continues. I tried different O.s (Pardus). There isnt any problem ....

---

### Post by el_uno on 2009-11-06
this worked for me, i had to restart my laptop first, but now i dont hear that annoying sound anymore.


thanks!!

---

### Post by theaaronc on 2009-11-12
> **Ayuthia said:**
> I think that the file location is actually:
```
/etc/modprobe.d/alsa-base.conf
```You can also just comment out the line at the end of the file so that it looks like this:
```
#options snd-hda-intel power_save=10 power_save_controller=N
```

This resolution worked for me. I was having the issue running 9.10 on a Presario V6000.

Edit: a reboot was also required for me.

---

### Post by theLegend on 2009-11-14
Bingo! This solution worked for my HP Pavilion laptop. Now that tiny little elf who keeps tapping my keys has gone!:p

---

### Post by speedync on 2009-11-20
Excellent fix. I just commented out that last line, rebooted and no more annoying clicks. Oh yeah, Compaq C700 laptop.

---

### Post by thejoempoem on 2009-12-03
Same problem-- Compaq Presario v6000.

I had to run gedit with a sudo command, as it was 'read only' on my lappy.
Then, i did this fix
#options snd-hda-intel power_save=10 power_save_controller=N
and, following a reboot, the problem was gone.
Thx.

---

### Post by koolair on 2010-01-04
Hi, I tried:

/etc/modprobe.d/alsa-base.conf

but it responed with:  permission denied

Then I tried:

sudo /etc/modprobe.d/alsa-base.conf

I entered my password and it responded with:  command not found

Hope someone can help...

Joe

---

### Post by Stelaninja on 2010-01-27
> **koolair said:**
> Hi, I tried:

/etc/modprobe.d/alsa-base.conf

but it responed with:  permission denied

Then I tried:

sudo /etc/modprobe.d/alsa-base.conf

I entered my password and it responded with:  command not found

Hope someone can help...

Joe

It's supposed to be
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

/etc/modprobe.d/alsa-base.conf is a text file that contains
the configuration for alsa. Gedit is a text editor you can
use to edit the file.

---

### Post by tormok on 2010-02-18
Installed Ubuntu 9.10 on my Compaq Presario C700 yesterday, and got this annoying clicking sound too.

I Entered
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```in a terminal, typed my password and changed power_save from 10 to 0 at the end of the file.

That solved the problem.

Thanks :)

---

### Post by Dorrax on 2010-05-31
I think I am having the same issue. A clicking in my headphones, usually only on one side, every second or so. I can get some relief by turning down the volume on that side through ossmix, which is probably something I should mention, I use oss, because it works better for me. Also using 10.4. I tried the solution mentioned here, but I couldn't find the line you commented out, maybe because I'm using 10.4, maybe because I'm using oss, which disables alsa upon installation and may change that file.

---

### Post by Piercedbastard on 2011-01-11
I've got this problem too, I'm running 10.10 on a HP G62(something) and I can't for the love of god find out how to fix it, since the line with the powersavethingys doesn't seem to be there.

Sorry about bumping such and old thread, but this clicking/noise is driving me up the walls.

---

### Post by tanari on 2011-01-13
same problem :(

no clicking with speakers, only in headphones (sound card creative x-fi), mute doesn't help

---

### Post by Piercedbastard on 2011-01-18
The clicking in my laptop is neither in speakers nor headphones, it's more like inside the laptop somewhere. I've noticed that as long as I'm typing, watching videos or listening to music the noise disappears. So it seems like it might be something with the "spin down hard drive when possible" or something, but it didn't help turning that feature of either so I'm pretty much at a loss.

PS. sorry if me English isn't quite up to standards, it's not my first language.

---

### Post by ordealbyfire83 on 2011-12-05
Piercedbastard : It sounds like your issue might be hard disk parking. This problem seems to come and go throughout different releases. This annoyed me beyond belief and I never suspected the hard drive because mine is otherwise practically silent. You would need to run

```
sudo hdparm -B 255 /dev/sda
```

where sda is your hard drive. This turns off Advanced Power Management (it won't ever spin down) and is a quick and dirty "bandaid" fix but it should stop the clicking. (Or if you don't want to turn it off completely try using 254 instead.) Also you'd need this to run after every reboot.

If you're unsure if it actually is your hard drive, try shutting down (no suspend/hibernate), removing your drive and booting from the LiveCD and seeing if you still hear anything.

---

