---
title: "Help needed with my Laptop's 82852/855 chipset"
date: 2011-03-03
forum: Hardware
---

### Post by Handssolow on 2011-03-03
I needed to add after quiet splash in Grub2 i915.modeset=1 to get a fresh Lucid to boot properly on the Toshiba M35X-S114 laptop a relative has just given me.

Moving on I've found that vlc crashes my whole system when I attempt to play a DVD video with 1024x768 but anything below, say 832x624 plays, though there is the occasional error reported in the terminal.

Any suggestions available here from someone who has solved this 855 graphics problem? Otherwise I'll have to spend a lot of time decrypting the moves described below. It seems mainly to involve using a different kernel-

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Edit:Incidentally I found that I could boot Debian 6.0 live session without any alteration to the boot line whereas a Lucid CD wouldn't boot unless I added i915.modeset=1.

---

### Post by Handssolow on 2011-03-04
I've can also watch digital TV on my laptop using a Afatech A9015 DVB-TD USB2.0 stick adaptor with Kaffeine but it has to be on 832x624. If I push up to 1024x768 the system crashes and I need to reboot. The adaptor doesn't like this either, it seems to take a few minutes to recover.

Is anyone with a 855 intel chipset able to watch a DVD in 1024x768 on their laptop?

There are two similar chipsets, 855GM and mine which is 855GME. They support a slightly different range of CPUs.

---

### Post by Handssolow on 2011-03-06
I chose Stefan Glasenhardt's approach (thanks Stefan) to resolve the issue I was having with my Toshiba laptop's 855 chipset running at 1024x768 as is described here-
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Install the updated -intel driver
sudo add-apt-repository ppa:glasen/intel-driver 
sudo apt-get update && sudo apt-get upgrade

Install the 855gm PPA and the patched kernel modules
sudo add-apt-repository ppa:glasen/855gm-fix
sudo apt-get update && sudo apt-get install dkms 855gm-fix-dkms

I've now removed i915.modeset=1 from the boot line and updated grub to make it permanent. I can play DVDs and also view TV with my DVB adaptor on 1024x768 without it crashing to a dark screen.

I'm sticking with Lucid LTS on this laptop. I've no foreseeable plans to move up to Maverick.

Edit:Currently I can use Kaffeine for DVB TV and DVD playback, Totem Movie Player and VLC for DVD playback (with the appropriate codecs/plugins) but DVD playback using gxine isn't working properly. Colour rendering or contrast isn't right and if I then switch to DVD playback using VLC that too has been similarly corrupted. I've no need to use gxine having the other working programs.

---

