---
title: "How to set default sound device?"
date: 2004-11-10
forum: Hardware &amp; Laptops
---

### Post by outcast on 2004-11-10
In my PC I have both AC97 and a SB Live! in PCI. However by default ubuntu uses AC97 and I don't want that. While SB Live is recognised in the Volume Control, all sounds from the applications are played by AC97. Is there any way to set the default card to be my SB? And if that is not easily possible can I entirely disable AC97 (Note: NOT from Bios, I need AC97 for windows, just for ubuntu to disable).

---

### Post by outcast on 2004-11-11
noone? :P

---

### Post by claymore on 2004-11-11
I'm not completely certain, but you could check under the Applications>System Tools>Configuration Editor.

Then head to system>gstreamer>0.8>default.  That may have the devices you need.

The other option would be to do something involving the Computer>System Configuration>Device Manager, although I haven't been able to find a way to alter or disable objects in there.

Sorry this post isn't more helpful.

---

### Post by mrv on 2004-11-13
I had the same problem. You can work around it by putting '-d hw:1' to /etc/esound/esd.conf on the default-options line. However, the gnome mixer still defaults to the first audio device, so you have to open up the whole mixer to control the other device.

Better advices would be welcome (fiddling with the /dev/dsp* files?). I read on a mailing list that at least some of the developers seem to be aware of this, and Hoary will have some kind of gnome audio manager (or something).

---

### Post by mrv on 2004-11-13
This still doesn't solve the problem of which device seems to be primary according to ALSA. I ended up renaming /lib/modules/2.6.8.1-3-k7/kernel/sound/pci/snd-bt87x.ko to another name so it can't be found, as I have no need to control TV card's mixer anyway (via ALSA).

---

### Post by arjuk1 on 2006-12-18
I found an easy solution here:
[http://www.linuxquestions.org/questions/showthread.php?t=499520](http://www.linuxquestions.org/questions/showthread.php?t=499520)

---

### Post by rockin_goliath on 2007-06-03
You could also enable the "Multimedia Systems Selector" item in the Preferences menu (go to System-Preferences-Main Menu and Check "Multimedia Systems Selector") From there you can select the default output for all sound. It may require an X restart or a system restart, I'm not sure. I hate having to use the command line; I'm an "everything should have a GUI" person. Good luck!

---

### Post by crimsun on 2007-06-03
> **outcast said:**
> In my PC I have both AC97 and a SB Live! in PCI. However by default ubuntu uses AC97 and I don't want that. While SB Live is recognised in the Volume Control, all sounds from the applications are played by AC97. Is there any way to set the default card to be my SB? And if that is not easily possible can I entirely disable AC97 (Note: NOT from Bios, I need AC97 for windows, just for ubuntu to disable).

Just blacklist snd-intel8x0.

---

### Post by kjasa on 2007-10-30
As a newby I struggled a lot to get this problem fixed. I eventually found this wiki on Alsa's site: [http://alsa.opensrc.org/index.php?title=FAQ026](http://alsa.opensrc.org/index.php?title=FAQ026)

Basically you have to create an /etc/asound.conf file with the same contents as the ~/.asoundrc file described in many articles. Of particular use is the comment half-way through the article noting that you can use names instead of card numbers which may change with every reboot. 

Step1
Open a terminal and type:
cat /proc/asound/cards

Note the names of the cards in the block brackets eg "[Live   ]"

Step2
Create a /etc/asound.conf file by typing the following
sudo gedit /etc/asound.conf

Then paste the following in the window, replace the word "Live" with the name obtained in step 1 and save the file.

# use Soundblaster Live as default device
# (from /proc/asound/cards)

pcm.!default {
    type hw
    card Live
}
ctl.!default {
    type hw
    card Live
}

Step 3
Reboot and all should work again.

---

### Post by haydent on 2008-07-13
adding the following to the end of /etc/modprobe.d/alsa-base made my usb sound default.


options snd_usb_audio index=0
options snd_intel8x0 index=1

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by haydent on 2008-07-14
found that this didnt work with debian etch though but upgrading to larry (testing) did. as it has same new MM chooser 8.04 has.

---

