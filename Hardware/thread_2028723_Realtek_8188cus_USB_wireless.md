---
title: "Realtek 8188cus USB wireless"
date: 2012-07-18
forum: Hardware
---

### Post by searchfgold6789 on 2012-07-18
Hi,
I recently got a cheap USB wireless dongle off of amazon, and it uses the 8188cus chipset. All It does is try to connect, time out, and ask for the password again, which I'm sure is correct. 
This was with the original kernel module for that chipset. I also tried downloading and installing drivers from the Realtek website; no luck. (that involved "blacklisting" the original kernelodule).
When I look at the list of kernel modules that are loaded, I see that 9192cu is there. What am I doing wrong? 
 - searchfgold6789

---

### Post by ahallubuntu on 2012-07-18
What version of Ubuntu are you using?  I have the same dongle and have used it successfully in Ubuntu 10.04, 10.10, and 11.04 - but only after building the driver from Realtek.  In 12.04 LTS (booting the live CD only), I noticed the dongle worked perfectly without doing anything - it would connect via WPA2 to my wireless network easily.

I remember having a problem in 11.10 (live CD) similar to what you describe - could be you using 11.10?  There was a built-in kernel driver but it would not connect.  So, you might have to blacklist the existing module in that case.  Yes, it's 8192CU (not 9192CU - look again) that's being used.  You will need to blacklist that kernel module, make/build the Realtek module and use that instead.

---

### Post by searchfgold6789 on 2012-07-18
This is 12.04. Apparently I have everything set up correctly, because I only have the Realtek module loaded.

---

### Post by kurt18947 on 2012-07-18
I have the Edimax EW-7811Un.  The driver included in 12.04 does what you are saying.  I downloaded the driver from Realtek, extracted it, opened a terminal and navigated to the extracted folder.  One of the entries in the folder should be install.sh.  I just use the following command:

```
sudo bash install.sh
```I should note that the file must be extracted into an account with sudo privileges.  Here's RealTek's web address:

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false)

I didn't have to blacklist the 'built-in' driver in 12.04.  I did have to blacklist the built-in driver in Mint Maya which is based on 12.04.  Why?  I have no idea.  I'm quite pleased with the tiny Edimax though, excellent signal strength for such a tiny adapter.

---

### Post by ahallubuntu on 2012-07-18
> **kurt18947 said:**
> I'm quite pleased with the tiny Edimax though, excellent signal strength for such a tiny adapter.

Same here (I think it's probably the same adapter, just rebranded).  I originally bought one on a lark off eBay for about $5 - how good could it really be?  But I get solid connections using them for media center boxes and they never drop connection.  They are only 150Mbps though, for anyone who really needs a fast data stream.

---

### Post by searchfgold6789 on 2012-07-18
Well, this one was a buck-fifty. :D I wasn't really expecting much in the way of speed, but I at least wanted a connection. (I suppose my endeavors in buying this computer accessory is a reflection of my love life.)

I have attempted removing "8921cu" from /etc/modules and removing the file /etc/modprobe.d/blacklist-rtl8192cu.conf" and rebooting, to no avail. It seems that neither of the drivers are working.

---

### Post by ahallubuntu on 2012-07-18
You WANT the 8192cu module included in /etc/modules - otherwise, the Realtek module you built won't be loaded.

Put the line

```
8192cu
```

back in the /etc/modules file.  This assumes you have already downloaded and built the Realtek module correctly from a terminal.

Then, create the file

/etc/modprobe.d/blacklist.conf

and put the line

```
blacklist 8192cu
```

in that file so the kernel module won't be loaded - your module will be instead.   Do all of this with "sudo" if you don't have permissions.

Then reboot and try it.

---

### Post by searchfgold6789 on 2012-07-18
That's what I tried doing; I undid it because of the poster who said it works put of the box in Precise. I will try again now from scratch.

---

### Post by searchfgold6789 on 2012-07-18
Just making sure.... The line "8192cu" should actually read "rtl8192cu", correct?

---

### Post by searchfgold6789 on 2012-07-18
I blacklisted "rtl8192cu" and put "8192cu" in /etc/modules. Still same behavior.

---

### Post by ahallubuntu on 2012-07-18
Start over.

Remove the blacklist file and anything you added to the /etc/modules file.

Reboot.

What module name do you see listed when you do an "lsmod" in a terminal window?

If you see

8192cu

put that exact name in the blacklists file.

Then add it to /etc/modules .

Reboot.

Do you see it in lsmod now?

Don't use "rtl8192cu" unless that's the exact module name you see in lsmod.

It did work for me using the latest 12.04 LTS 64 bit live CD when I tried it recently.  Sometimes kernel updates break things, though.  I haven't tried it with an actual installation of 12.04 LTS, just the live CD.

---

### Post by kurt18947 on 2012-07-19
Here is what I have in Mint 13 where I did have to blacklist the included module.  This is the machine that has the functional edimax ew-7811un.

lsmod

```

Module                  Size  Used by
btusb                  17912  0 
8192cu                502147  0 
parport_pc             32114  0 
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  11 btusb,bnep,rfcomm
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_analog    75395  1 
snd_hda_intel          32765  2 
snd_hda_codec         109562  2 snd_hda_codec_analog,snd_hda_intel
thinkpad_acpi          73942  0 
snd_seq_midi           13132  0 
pcmcia                 39791  0 
joydev                 17393  0 
snd_hwdep              13276  1 snd_hda_codec
arc4                   12473  2 
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_rawmidi            25424  1 snd_seq_midi
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_seq_midi_event     14475  1 snd_seq_midi
iwl3945                73111  0 
iwl_legacy             71134  1 iwl3945
mac80211              436455  2 iwl3945,iwl_legacy
psmouse                87140  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
i915                  414568  3 
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
serio_raw              13027  0 
wmi                    18744  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              28931  2 snd_pcm,snd_seq
cfg80211              178679  3 iwl3945,iwl_legacy,mac80211
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
snd                    62064  14 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,thinkpad_acpi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_seq_device,snd_timer
soundcore              14635  1 snd
video                  19068  1 i915
mac_hid                13077  0 
nvram                  14029  1 thinkpad_acpi
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
e1000e                140005  0 

```blacklist.conf

# disable onboard wifi
blacklist iwl3954
blacklist iwl_legacy
blacklist rtl8192cu
blacklist mac80211
blacklist cfg80211

most of the entries are an effort to disable the integral Intel wireless adapter.  The one that was necessary for the edimax to work was rtl8192cu.  This looks like a "YMMV" situation, unfortunately.

---

### Post by searchfgold6789 on 2012-07-19
I did as you suggested, ahallubuntu, with kirk18947's blacklists. The same thing is still happening. Only 8192cu is loaded at boot now, according to lsmod. The correct modules have been blacklisted. 

Perhaps it is the wireless settings. I am only in the next room over from the router, but I have no idea if some settings are more optimal than others for this chip. The security is WPA2 Personal.

---

### Post by searchfgold6789 on 2012-07-19
I switched the security mode to WPA and, thank heavens, it's working!!

---

### Post by kurt18947 on 2012-07-19
> **searchfgold6789 said:**
> I switched the security mode to WPA and, thank heavens, it's working!!

Good job!  If this is a notebook and you connect to other secured wifi networks like a school, you might want to check the function there as well.  You don't want to find yourself *needing* to be able to connect to a wireless network and can't.

---

