---
title: "Optimizing Ubuntu 9.04 for ThinkPad SL400"
date: 2009-05-10
forum: Hardware
---

### Post by gan1708 on 2009-05-10
**Greetings,** ):P

I purchased a Lenovo-IBM ThinkPad SL400 and installed Ubuntu 9.04 (Jaunty) on it a couple of days ago.

I've been pretty happy with it's performance so far. Some stuff like the volume buttons don't work and the screen brightness controls are finicky, but overall it's handled whatever I've asked it to do.

I' pretty much a Ubuntu noob (only used 8.04 for a few weeks in the past), so I'm not really familiar with some of the more specialized applications and terminal commands.

Are there any applications or terminal commands that I can use to further optimize my ThinkPad. Possibly something like **cpu temperature/scaling monitor, fan control, battery life optimizer**...etc? The only one I've used so far is Powertop, and I have no idea what it even does. I run it and press the keys it tells me to, but that's it. :confused: (Please include full terminal commands if they're not on synaptic)

Is there anything else I can use to optimize laptop prformance? Or something I can edit to make it run even better (although I think it runs fine as it is).

I've also seem some discussions about concurrent booting. Will I benefit from it and are the any risks O_o? (CPU is Core2Duo, and I'm running ext4.)

Lastly, does anyone know how I can get the ThinkPad trackpoint scroll button to work? (the one in between the left and right mouse buttons for the red trackpoint)

Thanks in advance.
[I]
~Cheers~[/I]



Edit: There's also this pretty loud beep (sorta like a CPU beep sound, but it comes out of the speakers). I disabled Ubuntu's log off sound, but the beep remains. I don't see any error messages, so I'm wondering if something's wrong  or if it's just one of those quirks. Has anyone ever got this and is there a way to get rid of it? (it woke up my partner last night).

---

### Post by schmittzer on 2009-05-11
> **gan1708 said:**
> 
Edit: There's also this pretty loud beep (sorta like a CPU beep sound, but it comes out of the speakers). I disabled Ubuntu's log off sound, but the beep remains. I don't see any error messages, so I'm wondering if something's wrong  or if it's just one of those quirks. Has anyone ever got this and is there a way to get rid of it? (it woke up my partner last night).

You must disable the "Beep" option in the volume control. Just click the volume icon in the taskbar and then click "volume control..." button, there you should find the "beep" volume control, once you find it, click the button below it.

PS: Dunno if it says "volume control" in english, 'couse I have Ubuntu in spanish, but should be something like that.

PS2: Sorry for my english.

Hope this could help you.
Regards.

---

### Post by dan.seti on 2009-07-03
Hi, I also recently installed 9.04 on SL400

Got the brightness key and volume key to work by following this guide,
[http://www.thinkwiki.org/wiki/SL_Driver_on_Ubuntu](http://www.thinkwiki.org/wiki/SL_Driver_on_Ubuntu)

with one change, the guide tells you to copy the .ko file into /lib/modules/`uname -r`/volatile. If you do, the file keeps getting deleted after reboot.
I put the .ko file in /lib/modules/'uname -r'/misc.

(Initially, i copied the file in firmware folder, which still work, but after reading the post by Gianluca Magalotti, misc folder seems to be the best place, as it has other laptops .ko files in there.
[http://gianlucamagalotti.wordpress.com/2009/02/16/lenovo-thinkpad-sl-series-hotkeys/](http://gianlucamagalotti.wordpress.com/2009/02/16/lenovo-thinkpad-sl-series-hotkeys/))

I also found, after a recent kernel update to 2.6.28-13, need to redo the steps again in the new kernel modules folder.

Alt-F4 (Bluetooth/Wifi kill switch) still didn't work. But i am not too concerned as the main keys (brightness, volume, mute, suspend, hibernate, disk eject (alt-f9)) all working now.

Thanks to Alexandre, ThinkWiki poster, Gianluca for their work.

---

### Post by renebs on 2009-10-02
Hi,

Is anyone running with this problem when loading lenovo-sl-laptop.ko?
> insmod lenovo-sl-laptop.ko
insmod: error inserting 'lenovo-sl-laptop.ko': -1 Operation not permitted

I am using ubuntu 8.10, and have been installing the module without a problem since linux-headers-2.6.27-7 and then reinstalling after linux-headers-2.6.27-11 , and now I am using linux-headers-2.6.27-14.

---

### Post by Muhilvannan on 2009-11-19
Hi all:
      I had Ubuntu 9.04 installed in SL400. Recently upgraded to Ubuntu 9.10, but when it came up after installation, the display went blank. Have any one faced similar issue? 
Then reverted back to 9.04. Downloaded 9.10 and then tried to install it, again if i boot with the liveCD with the option 'Try Ubuntu without installing', I am able to hear the login sound but still the monitor is blank. If i try the other option 'Install Ubuntu', it again leads me to blank page. I have tried the option, 'Use safe graphical mode' too. Seems nothing is helping.

Help me pls.  [-o<

---

