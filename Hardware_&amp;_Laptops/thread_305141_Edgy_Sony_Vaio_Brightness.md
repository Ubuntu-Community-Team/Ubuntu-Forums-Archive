---
title: "Edgy Sony Vaio Brightness"
date: 2006-11-22
forum: Hardware &amp; Laptops
---

### Post by fbolduc on 2006-11-22
I know this is an issue that has been discussed, but I'm bringing something new to the topic.

I have a Sony Vaio from the K series.

The first Ubuntu distribution I installed was Breezy.
Back then, the only way I could change the LCD brightness was by command lines.

```

echo 1-8 > /proc/acpi/sony/brightness
echo 1-8 > /proc/acpi/sony/brightness_default

```

But the brightness default never seemed to work and I always needed to issue the command again when I rebooted.

Next, I installed Ubuntu Dapper.
All went smooth because I was able to change the brightness from *System -> Preference -> Power Management*. And when I changed the brightness, it stayed when I rebooted.

Today, I installed Ubuntu Edgy.
The *System -> Preference -> Power Management* no longer work as in Dapper. I am back to the Breezy situation where I must type the commands to change the brightness.

What changed from Dapper to Edgy that could affect my ability to change the brightness?

Could it be related to the kernel version 386 versus 686?

Could it be related to the ATI driver?

Could it be related to some kernel module?

Do I need to fill a bug report?

If so, what do I write in the bug report?

Regards,
Francis Bolduc

---

### Post by fbolduc on 2006-11-22
UPDATE

This is a confirmed bug: [https://launchpad.net/distros/ubuntu/+source/hal/+bug/68617](https://launchpad.net/distros/ubuntu/+source/hal/+bug/68617)

As stated in the bug report, the problem comes from the change from bash to dash as the default shell.

There is a workaround, that is to go back to the old bash shell.

The bug await someone to fix it.

---

### Post by fbolduc on 2006-11-22
UPDATE

Since there is no step-by-step solution still in the bug report, I have devised one.
As stated before, the problem is that /bin/sh points to /bin/dash in Edgy and the get/set brightness scripts should be executed by bash.

Here's how to solve the problem.

1- Open a Terminal
2- Type:   sudo gedit /usr/share/hal/scripts/hal-system-lcd-get-brightness
3- Change /bin/sh for /bin/bash on the first line and save
4- Type:   sudo gedit /usr/share/hal/scripts/hal-system-lcd-set-brightness
5- Change /bin/sh for /bin/bash on the first line and save

Then all should work as it was working in Dapper.

Cheers!

---

### Post by tomranson on 2006-12-14
> **fbolduc said:**
> UPDATE

Since there is no step-by-step solution still in the bug report, I have devised one.
As stated before, the problem is that /bin/sh points to /bin/dash in Edgy and the get/set brightness scripts should be executed by bash.

Here's how to solve the problem.

1- Open a Terminal
2- Type:   sudo gedit /usr/share/hal/scripts/hal-system-lcd-get-brightness
3- Change /bin/sh for /bin/bash on the first line and save
4- Type:   sudo gedit /usr/share/hal/scripts/hal-system-lcd-set-brightness
5- Change /bin/sh for /bin/bash on the first line and save

Then all should work as it was working in Dapper.

Cheers!

I confirm that this does the trick for a Vaio VGN-TX3XP on Edgy. :)

---

### Post by IntuitiveNipple on 2007-01-21
Works for SRX41 & SRX51 too. Thanks.

---

### Post by picanteverde on 2007-01-24
i confirm that it works on sony vaio pcg-k17

---

### Post by Guy Smiley on 2007-01-24
Works for a Sony Vaio vgn-N11S (i.e. adds brightness control to power management.
Thankyou !! :-)

---

### Post by bitzer on 2007-02-23
works on my vaio vgn-c1s/h! :-D

---

### Post by frychiko on 2007-02-24
This worked for my VGN-FE32HB/W under Edgy 6.10, unfortunately doesn't work under Feisty Fawn Herd 4.

---

### Post by NikoC on 2007-02-24
> **frychiko said:**
> This worked for my VGN-FE32HB/W under Edgy 6.10, unfortunately doesn't work under Feisty Fawn Herd 4.

I know it is not the best solution but I have installed nvclock from the repos (sudo apt-get install nvclock) and added 'nvclock -S 50' to my gnome startup list. This way brightness is always set to 50% as default value. The only 'problem' is that the login screen is still at 100% since nvclock is not loaded yet then. 
Running Feisty on a sony vgn-s4hp btw.

---

### Post by mjolinr on 2007-02-25
it worked on my sony vgn-fs640/w too! thanks a bunch, this'll really help when i need battery.

---

### Post by drbongo on 2007-03-13
This also works with a Sony Vaio VGN-TX3XP - a nice simple solution! drbongo:)

---

### Post by Kateikyoushi on 2007-03-13
Seems the fix is already done but not yet uploaded.

---

### Post by gigi on 2007-03-17
For Feisty this works for me (Sony VGN-SZ3HP), here are the files where you have to change the first line

./usr/lib/hal/scripts/linux/hal-system-lcd-get-brightness-linux
./usr/lib/hal/scripts/linux/hal-system-lcd-set-brightness-linux

change first line from 
#!/bin/sh      to      #!/bin/bash

---

### Post by treesurf on 2007-03-17
Any chance that this would work on non-Sony laptops as well?

---

### Post by smackenzie on 2007-03-17
Thanks to everyone who has posted so far - it has given me a few more things to try out in my quest.

I'm running Dapper on a Sony VGN-SZ220P and I have been unable to get the brightness control to work, even after adjusting the default shell to bash as mentioned above.  When using power management, I can adjust the brightness slider but nothing happens.  When using built in function keys (for volume, brightness etc) the volume control works but when I use brightness (Fn+F5 or Fn+F6), the entire system locks up (even Ctrl+Alt+F2 doesn't take me out!). :(  I'm using the nVidia Default Driver in xorg.conf; would that make a difference?

---

### Post by yevgeniy on 2007-03-21
running ubuntu 6.10 desktop on sony vaio pcg-f490. All works fine, just the brightness.. gonna burn my eyes out by the time I fix it :). Method above didn't work :-\

---

### Post by loumbas on 2008-04-10
confirmed that works on hardy with pavilion dv2147

---

