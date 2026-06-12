---
title: "disabling shutdown system beep in intrepid"
date: 2008-11-09
forum: General Help
---

### Post by haloedrain on 2008-11-09
Just installed 8.10, my computer now beeps at me every time I turn it off.  How do I make it stop?

---

### Post by th89 on 2008-11-09
Go to System > Preferences > Sound > Sounds (tab) > Uncheck "Play alert sounds". That should do it. That also stops the annoying beep when you backspace one too many times as well. :P

---

### Post by lovinglinux on 2008-11-09
[http://ubuntu-tutorials.com/2007/07/26/turning-off-the-system-hardware-beep-linux-tutorial/](http://ubuntu-tutorials.com/2007/07/26/turning-off-the-system-hardware-beep-linux-tutorial/)

---

### Post by haloedrain on 2008-11-10
Hmm, that box already is unchecked, and the too many backspaces beep is still disabled as well, as are other beeps in the terminal.  I saw the linked tutorial also, but if I could just disable this one without disabling system beeps entirely I'd prefer that.  It *used* to shut down without making noise....is there a configurable script somewhere?

---

### Post by tuesdaytaurus on 2008-11-10
Hi

I'm new to Ubuntu (about 4 days). I have the same problem. Is there somewhere I can download and alternative sound theme for ubuntu? I've also disabled most of the anoying alert sounds, but my pc still beeps. even though the relevant sounds are disabled. Are there some hierarchical dependency tree or something?

---

### Post by Sam on 2008-11-10
At the end of /etc/profile, add:
```
# disable system beeps
setterm -blength 0
```

---

### Post by Chunky Dunk on 2008-11-10
Also, you can try "sudo rmmod pcspkr".

If that works, then open up "/etc/modprobe.d/blacklist" and add this line: "blacklist pcspkr". It'll prevent that module from loading up when you start your computer.

The first one will disable it until you reboot, the second makes it permanent.

---

### Post by shane2peru on 2008-11-11
> **Chunky Dunk said:**
> Also, you can try "sudo rmmod pcspkr".

If that works, then open up "/etc/modprobe.d/blacklist" and add this line: "blacklist pcspkr". It'll prevent that module from loading up when you start your computer.

The first one will disable it until you reboot, the second makes it permanent.

This one worked for me.  Thanks for the info.

Shane

---

### Post by tuesdaytaurus on 2008-11-11
I Tried the one from **Sam**:
> At the end of /etc/profile, add:

Code:
# disable system beeps
setterm -blength 0

But for some reason that killed all the sound on my Dell inspirion. After undoing the change and doing a reboot, I tried the one from **Chunky dunk** and that did the trick
> Also, you can try "sudo rmmod pcspkr".

If that works, then open up "/etc/modprobe.d/blacklist" and add this line: "blacklist pcspkr". It'll prevent that module from loading up when you start your computer.

The first one will disable it until you reboot, the second makes it permanent. 

Thanks All.

---

### Post by josel777 on 2008-11-19
> **Chunky Dunk said:**
> Also, you can try "sudo rmmod pcspkr".

If that works, then open up "/etc/modprobe.d/blacklist" and add this line: "blacklist pcspkr". It'll prevent that module from loading up when you start your computer.

The first one will disable it until you reboot, the second makes it permanent.


I get the following with "sudo rmmod pcspkr": ERROR: Module pcspkr does not exist in /proc/modules. However, sudo modprobe -r pcspkr works each time I run it.

When I add "blacklist pcspkr" to "/etc/modprobe.d/blacklist" the beep doesn't go away permanently. Below are the contents of "/etc/modprobe.d/blacklist":

[COLOR="Navy"]cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# slow wireless driver
blacklist bcm43xx

# this is how you mute annoying beeps in console and shutdown
blacklist pcspkr[/COLOR]

What am I missing?

---

### Post by josel777 on 2008-11-20
Anyone?

---

### Post by pluckypigeon on 2008-12-18
.

---

### Post by DJ_Peng on 2009-01-19
> **lovinglinux said:**
> [http://ubuntu-tutorials.com/2007/07/26/turning-off-the-system-hardware-beep-linux-tutorial/](http://ubuntu-tutorials.com/2007/07/26/turning-off-the-system-hardware-beep-linux-tutorial/)
Thanks for posting that link. I had been wanting to find a way to do that. I'll try to remember to come back and click the Thank You icon once they're turned back on.

---

### Post by lovinglinux on 2009-01-20
> **DJ_Peng said:**
> Thanks for posting that link. I had been wanting to find a way to do that. I'll try to remember to come back and click the Thank You icon once they're turned back on.

You are welcome. That beeping sound can make anyone mad :D

---

### Post by le singe on 2009-01-21
I was also looking to disable the system beep at shut down, so I tried the suggestion to go into sound preferences and untick the "Play alert sound" setting.  I think I first unticked "Play alerts and sound effects," then tried leaving that checked but disabling the sub-setting "Play alert sound." 

Problem is, this now killed all of my audio and in its place gives me nothing more than a crackling sound.  

I don't see what I did wrong.

Sorry if I come across as expecting too much, or not having the patience to deal with Ubuntu/Linux (which I normally love), but it's incredibly frustrating when modifying a simple setting presented to you in the basic sound set-up can effectively nix all sound output.  I mean, there is no sound now whatsoever.... shouldn't rechecking the settings back to how they were give it back?

Little annoyances like this really hold this OS back, in my opinion.  I don't mean to just rant, but I'm sure most users here who are now happy with setups working perfectly have probably encountered frustrations like this as well and know where I'm coming from.

Any way to reset my sound settings?  Thanks in advance to anyone who can be of assistance.

---

### Post by le singe on 2009-01-22
> **le singe said:**
> I was also looking to disable the system beep at shut down, so I tried the suggestion to go into sound preferences and untick the "Play alert sound" setting.  I think I first unticked "Play alerts and sound effects," then tried leaving that checked but disabling the sub-setting "Play alert sound." 

Problem is, this now killed all of my audio and in its place gives me nothing more than a crackling sound.  

I don't see what I did wrong.

Sorry if I come across as expecting too much, or not having the patience to deal with Ubuntu/Linux (which I normally love), but it's incredibly frustrating when modifying a simple setting presented to you in the basic sound set-up can effectively nix all sound output.  I mean, there is no sound now whatsoever.... shouldn't rechecking the settings back to how they were give it back?

Little annoyances like this really hold this OS back, in my opinion.  I don't mean to just rant, but I'm sure most users here who are now happy with setups working perfectly have probably encountered frustrations like this as well and know where I'm coming from.

Any way to reset my sound settings?  Thanks in advance to anyone who can be of assistance.

Ok so I'll reply to myself as I've found a fix, and perhaps this can help someone else, too.

Apparently unchecking the settings above-mentioned muted a setting in the volume control, which makes sense... it just wasn't obvious that putting the settings back to how they were didn't unmute this....

So anyways, you just have to right-click on the speaker icon in the panel and open up Volume Control, you'll see that PCM has been muted.  Raise those bars up and voilà.

I got frustrated hastily, as I often do, but still I think it ought to be a little more obvious than that... perhaps in the sound preferences there could be a Volume Control tab or something, some kind of link between the two.  Maybe I'm being too picky.  Okay, rant over.

---

### Post by vladi11 on 2009-01-22
The solution that worked for me was this:

In your home folder create a file named .inputrc
Open it and write [COLOR="DarkOrange"]set bell-style none[/COLOR].
Save it and that annoyng beep it's gone.

Credit for this : [Ubuntu tutorials]("http://ubuntu-tutorials.com/2007/07/26/turning-off-the-system-hardware-beep-linux-tutorial/")

---

### Post by optimistique1 on 2009-02-06
Hi Guys
I am using Xubuntu 8.10 and cannot find ANY solution to stop the system beep at shutdown.  Surely I am not the only one suffering this..

I have tried - Go to System > Preferences > Sound > Sounds (tab) > Uncheck "Play alert sounds".  However, Xubuntu does not have this option :-(

I have also tried "sudo rmmod pcspkr" and then opened up "/etc/modprobe.d/blacklist" and add this line: "blacklist pcspkr".  This also does not work......

Any help would be greatly appreciated.;)

---

### Post by pluckypigeon on 2009-02-07
> **optimistique1 said:**
> Hi Guys
I am using Xubuntu 8.10 and cannot find ANY solution to stop the system beep at shutdown.  Surely I am not the only one suffering this..

I have tried - Go to System > Preferences > Sound > Sounds (tab) > Uncheck "Play alert sounds".  However, Xubuntu does not have this option :-(

I have also tried "sudo rmmod pcspkr" and then opened up "/etc/modprobe.d/blacklist" and add this line: "blacklist pcspkr".  This also does not work......

Any help would be greatly appreciated.;)

Hey, sorry for your long wait. 

In the newer versions of Linux you have to blacklist pcspkr and snd_pcsp.

Add this to your /etc/modprobe.d/blacklist (IN JAUNTY AND LATER the file is blacklist.conf)

blacklist pcspkr
blacklist snd_pcsp

Hope this solves your problem!

---

### Post by optimistique1 on 2009-05-23
I know I am probably being very stupid but I am trying to stop the system beep on shut down by following these instruction:

Removing the driver

The system speaker is controlled by a driver in the Linux kernel. This allows the pc speaker to beep at you for different reasons or at different events. If you remove the module which drives the speaker, the beeping goes away, as the machine no longer knows how to interface with that device.
This can be done manually with a command such as:

    sudo modprobe -r pcspkr

or you can set it as a persistent change by adding the module to your system driver blacklist, available at:

    /etc/modprobe.d/blacklist

simply append the line &#8220;blacklist pcspkr&#8221; for that driver to be disregarded at every boot.

If you&#8217;d like to manually re-insert the module use:

    sudo modprobe pcspkr

However, I have no idea how or where to insert the line 'blacklist pcspkr'.

When I try to insert this line into the blacklist.conf file it says I don't have the correct permissions.

Here is the content of the file if someone could tell me where to insert 'blacklist pcspkr' and HOW!!!

*********************************************************************************************************************************


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

---

### Post by benerivo on 2009-05-23
You can do it by entering this in the terminal...```
gksudo gedit /etc/modprobe.d/blacklist.conf
```then just go to the bottom of the file and add a new line that reads...```
sudo modprobe pcspkr
```then save, and restart the pc.

---

