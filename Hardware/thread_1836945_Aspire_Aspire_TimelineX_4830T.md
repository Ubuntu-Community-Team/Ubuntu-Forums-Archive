---
title: "Aspire Aspire TimelineX 4830T"
date: 2011-08-31
forum: Hardware
---

### Post by davidY on 2011-08-31
Hey anybody own this model? This is not the GT with a nvidia graphics card. My current status:

[LIST]
[*]Wireless (out of box)
[*]Suspend (out of box)
[*]Audio (kernel 3 + manual fix)
[*]Graphics (kernel 3 + edgers xorg)
[*]Brightness (acpi option in boot)
[*]Battery life - around 5 hours
[*]CPU Scaling (out of box)
[*]External monitor setup - manual editing
[/LIST]

Note: I upgraded to the xorg edgers kernel version and froze it at 3.0.0-8 because everything is working. Maybe some bugs are fixed in later versions.

Audio Out: 
Upgrade to kernel 3 to receive the patch for audio. Headphone jack sense not working. I manually disable the speakers with hda-verb /dev/snd/hwC0D0 0x1f SET_PIN_WIDGET_CONTROL 0
See: [http://kernel.org/pub/linux/kernel/people/tiwai/misc/hda-verb/]("http://kernel.org/pub/linux/kernel/people/tiwai/misc/hda-verb/")

Audio In:
Microphone does not work unless you use hda analyzer and set Node[0x23] PIN Val[0] and Val[1] to different values (i like 2,3)
See: [http://www.alsa-project.org/main/index.php/HDA_Analyzer]("http://www.alsa-project.org/main/index.php/HDA_Analyzer")

Graphics:
Use xorg edgers, which contains a kernel 3.0 upgrade. Install kernel, new xorg, and forced a stuck package to upgrade. This makes graphics pretty snappy (I can now use blur in compiz)
See: [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu)

Brightness:
Not sure, this might have worked out of box. If not try adding acpi_osi=Linux to your boot options (edit in file /etc/default/grub the line containing GRUB_CMDLINE_LINUX, then run sudo update-grub)

Battery Life:
With powertop I noticed that lots of interrupts were being generated from the card reader. Disable the card reader: sudo rmmod rts_pstor.

CPU Scaling:
See: [http://code.google.com/p/i7z/]("http://code.google.com/p/i7z/")

External Monitor:
I have a large monitor that should be the only one on when it is plugged in. I ended up setting both my ~/.config/monitors.xml and also /etc/gnome-settings-daemon/xrandr/monitors.xml to:
```
<monitors version="1">
  <configuration>
      <clone>no</clone>
      <output name="LVDS1">
          <vendor>INL</vendor>
          <product>0x0017</product>
          <serial>0x00000000</serial>
      </output>
      <output name="VGA1">
      </output>
      <output name="HDMI1">
          <vendor>VSC</vendor>
          <product>0xe226</product>
          <serial>0x01010101</serial>
          <width>1920</width>
          <height>1080</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="DP1">
      </output>
  </configuration>
</monitors>
```
The best way is to have both monitors on with the gnome-monitor-properties tool, and save the configuration. Then go in and delete everything except for [vendor, product, serial] for the monitor you want to keep off.

Hope this helps, I'll try to keep this thread updated if anyone finds something cool/mistakes.

**Useful Links**
[How to decrease power usage]("http://ubuntuforums.org/showpost.php?p=11267558&postcount=4")

---

### Post by ptg21 on 2011-09-12
Thanks for the information!  

Have just acquired a 4830TG and this is exactly the kind of information I was looking for.

---

### Post by .... on 2011-09-12
You folks should add your experience and useful info to the linlap wiki: [http://www.linlap.com/wiki/acer](http://www.linlap.com/wiki/acer)

---

### Post by ptg21 on 2011-09-19
I also had great improvements in battery life when making the following changes:

1. setting the graphics to integrated in the BIOS settings
2. installing jupiter applet (this is on Ubuntu 11.04) from webupd8.org - don't forget to make a donation!
3. using the latest kernel from xorg-edgers, as mentioned above (sound works with the latest kernel out of the box)
4. setting 

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux i915.i915_enable_rc6=1"

in /etc/default/grub (and then updating with sudo update-grub) [the first option enables hardware control of backlight, the second implements a workaround for Intel graphics as described [here]("http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1")]

The latter brought the power consumption down from around 14W to 9W with all devices turned off, screen at lowest brightness setting, as reported by powertop.

I don't know if it's a good idea to put 11.04/kernel 3.0.0-11 specific info on the linlap page, but I'll update it if required...

---

### Post by jim.hitch on 2011-09-29
Hey

Really pleased to have found this page, thanks for all the work and posting.

You forgot to mention that the touchpad is now properly working. 

My only gripe at the moment is that after adding the xorg edgers ppa I upgraded the packages it suggested and now desktop effects crashes and has to be disabled (though perhaps that's more related to kernal 3), anyway, it's fine for the moment, the above fixes are far more valuable to me than candy.

Sorry, another edit. I tried the headphone jack and it seems that headphone jack sense is now working (3.0.0-12) though the volume on the headphones is stuck on the lowest bar.

btw, the machine is now super quick, it's made a massive difference here.


Jim

---

### Post by davidY on 2011-09-30
> **jim.hitch said:**
> Hey
My only gripe at the moment is that after adding the xorg edgers ppa I upgraded the packages it suggested and now desktop effects crashes and has to be disabled (though perhaps that's more related to kernal 3), anyway, it's fine for the moment, the above fixes are far more valuable to me than candy.

Jim - you are using the T not the GT right (the one with the intel graphics card)? For me the desktop effects seem to all work. I haven't upgraded since everything was working.
Well once 11.10 comes out hopefully everything will just work out of the box :)

---

### Post by gustokonyan on 2011-09-30
Hi, thank you for this. This is what i am looking for!

But i have problems trying your solution on the graphics part. I clicked the link you gave but there are lots of folders and files. I dont know which is the correct thing to download/install. Can anyone guide me please? thanks..

My laptop is a Acer 4830TG on Ubuntu 11.04 64-bit

---

### Post by ptg21 on 2011-10-06
As I recall, all you need to do is 
> 
sudo add-apt-repository ppa:[COLON]xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade

and the appropriate packages should be installed

Agh- does anyone know how to avoid : x coming out as a 'mad' emoticon

---

### Post by gustokonyan on 2011-10-06
> **ptg21 said:**
> As I recall, all you need to do is 

and the appropriate packages should be installed

Agh- does anyone know how to avoid : x coming out as a 'mad' emoticon

i am trying this now. thanks!

---

### Post by gustokonyan on 2011-10-06
> **gustokonyan said:**
> i am trying this now. thanks!

hmm, after doing this, my screen displays squary particles whenever I open / close windows (with compiz Glide1 animation)

How do i revert / uninstall the changes i just made?


thank you!

---

### Post by jim.hitch on 2011-10-07
> **davidY said:**
> Jim - you are using the T not the GT right (the one with the intel graphics card)? For me the desktop effects seem to all work. I haven't upgraded since everything was working.
Well once 11.10 comes out hopefully everything will just work out of the box :)

Yes, I'm using the T not the GT. I don't know what it might be, but I can do without the candy for a couple of weeks... as you say, when 11.10 comes out it'll hopefully be fixed.

Maybe it's that I'm still using KDE 4.6.2?

Anyway, having the microphone and the brightness working is worth its weight in gold.

Jim

---

### Post by ptg21 on 2011-10-07
> **gustokonyan said:**
> hmm, after doing this, my screen displays squary particles whenever I open / close windows (with compiz Glide1 animation)

How do i revert / uninstall the changes i just made?


thank you!
According the edgers [page]("https://launchpad.net/~xorg-edgers/+archive/ppa")
> 
To revert to official packages, you can install the ppa-purge package and run "sudo ppa-purge xorg-edgers".


---

### Post by gustokonyan on 2011-10-07
> **ptg21 said:**
> According the edgers [page]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
Thank you

---

### Post by jim.hitch on 2011-11-02
> **davidY said:**
> 

Audio In:
Microphone does not work unless you use hda analyzer and set Node[0x23] PIN Val[0] and Val[1] to different values (i like 2,3)
See: [http://www.alsa-project.org/main/index.php/HDA_Analyzer]("http://www.alsa-project.org/main/index.php/HDA_Analyzer")



Hi, This all worked great when I built 11.04, but now have upgraded to 11.10 and this isn't working. 

If I set the values above to 2,3 for e.g., they revert back to default after I've tried to use Skype. Even when I used Skype test call just after changing the values that recording from the mic is very poor.

Any ideas?

Jim

---

### Post by davidY on 2011-11-05
Jim - try turning off microphone auto-volume setting in skype, it might try to change the volume of the mic by editing the values.

You must run hdanalyze again to see the current values, there is no refresh button, and switching to the tab does not actually refresh the values.

---

### Post by EmeraldOverlord on 2011-11-06
I have the same laptop and I have the same problem... my mic wont work in chatroulette.

---

### Post by jim.hitch on 2011-11-07
> **davidY said:**
> Jim - try turning off microphone auto-volume setting in skype, it might try to change the volume of the mic by editing the values.

You must run hdanalyze again to see the current values, there is no refresh button, and switching to the tab does not actually refresh the values.

Thanks for the response, unfortunately no joy. It seems to be exactly the same as before: I can just about hear myself, but it's very broken up and barely audible.

Jim

---

### Post by FredHampton on 2012-05-21
Real basic question relating to 4830t:

What are the key sequences to access bios settings?

<Alt Gp>F10 has at times produced an Acer logo screen
from which F2 produced several options for booting 7
but not the usual bios menu such as boot order.

---

