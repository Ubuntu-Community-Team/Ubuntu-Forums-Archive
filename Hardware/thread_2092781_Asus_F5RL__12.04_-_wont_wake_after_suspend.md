---
title: "Asus F5RL / 12.04 - wont wake after suspend"
date: 2012-12-08
forum: Hardware
---

### Post by Pyotrek on 2012-12-08
> **Toz said:**
> If its an ATI card, I think that AMD may have dropped support for it ([http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware)) and that's why you don't see an option to install one.

I've read in a couple of places that this is a known issue the the 600m and that setting a BIOS password is a workaround (it resets the video on resume so that you can type in a password). Might be worth a try to confirm.

Hello,

I have same issue. Can't wake after suspend.
I have an old Asus f5rl with ATI Radeon xpress 200m.

From link you provided I learned that  - These cards are supported with the legacy ATI 9-3 Catalyst release, but  you MUST use a kernel <= 2.6.28 and Xserver <= 1.5. For example, you can use Catalyst 9-3 if you're running Ubuntu 8.04 or Debian Lenny/5.0.

I don't quite understand this. Will I be able to make it work with xubuntu 12.04?

I've tried trick with setting password from BIOS. Didn't worked for me.

Any ideas how to deal with this or should I forget about suspend?

---

### Post by Toz on 2012-12-08
Post moved to its own thread. Original thread here: [http://ubuntuforums.org/showthread.php?t=1981650]("http://ubuntuforums.org/showthread.php?t=1981650").

---

### Post by Toz on 2012-12-08
Hello and welcome to the forums.

> **Pyotrek said:**
> I don't quite understand this. Will I be able to make it work with xubuntu 12.04?
Suspend? Maybe, we could have a look and try.
The ATI drivers? No, but the open source radeaon drivers are pretty good now.

> Any ideas how to deal with this or should I forget about suspend?

Lets start by having you post back some more information. Open a terminal window, type in the following commands, and post back the results:
```
cat /proc/cmdline
lsmod
```

And lets have a look at some log files. Type in the following commands and post back the links that are generated:
```
pastebinit /var/log/pm-suspend.log
pastebinit /var/log/syslog
pastebinit /var/log/Xorg..0.log
```

---

### Post by Pyotrek on 2012-12-09
Thanks for help.

Results for the commands:

cat /proc/cmdline
```
BOOT_IMAGE=/boot/vmlinuz-3.2.0-34-generic root=UUID=86d66e9a-e9d3-46dd-b10a-de8de66e9873 ro quiet splash pci=nomsi vt.handoff=7
```lsmod
```
Module                  Size  Used by
joydev                 17393  0 
arc4                   12473  2 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   174313  1 
snd_hda_intel          32765  4 
snd_hda_codec         109562  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                96684  0 
snd                    62064  18 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13027  0 
sp5100_tco             13495  0 
soundcore              14635  1 snd
rfcomm                 38139  12 
bnep                   17830  2 
parport_pc             32114  0 
btusb                  17948  2 
ath5k                 145127  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
ath                    19387  1 ath5k
bluetooth             158438  23 rfcomm,bnep,btusb
ppdev                  12849  0 
i2c_piix4              13093  0 
mac80211              436455  1 ath5k
radeon                733824  2 
video                  19068  0 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
asus_laptop            23693  0 
sparse_keymap          13658  1 asus_laptop
drm                   197599  4 radeon,ttm,drm_kms_helper
input_polldev          13648  1 asus_laptop
cfg80211              178679  3 ath5k,ath,mac80211
i2c_algo_bit           13199  1 radeon
mac_hid                13077  0 
ati_agp                13242  0 
shpchp                 32325  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
pata_atiixp            12999  0 
atl2                   28040  0 
usb_storage            39646  0 
```for ```
pastebinit /var/log/pm-suspend.log
```[http://paste.ubuntu.com/1421051/](http://paste.ubuntu.com/1421051/)

for ```
pastebinit /var/log/syslog
```[http://paste.ubuntu.com/1421052/](http://paste.ubuntu.com/1421052/)

and for ```
pastebinit /var/log/Xorg..0.log
``````
Unable to read from: /var/log/Xorg..0.log
```

---

### Post by Toz on 2012-12-09
A few things:

[LIST=1]
[*]Does the computer turn off (go into suspend mode) or does it just hang?

[*]Why are you using **pci=nomsi** in your kernel boot line? What particular problem does it address?

[*]Have you looked at your bios settings? In particular anything that might reference C6 or C9 in the CPU settings? Maybe try disabling them.
[/LIST]

Otherwise, a couple of things to try:

[LIST=1]
[*]Try unloading your wireless driver before susend:
```
sudo modprobe -r ath5k
sudo pm-suspend
```
...if it works, you can reload the wireless driver with:
```
sudo modprobe ath5k
```

[*]Can you do the following to get a more detailed log of your suspend attempt:
```
sudo bash 
mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
export PM_DEBUG=true
pm-suspend
```
When you recover the system, post back again the new pm-suspend.log file:
```
pastebinit /var/log/pm-suspend.log
```
[/LIST]

---

### Post by Pyotrek on 2012-12-11
> Does the computer turn off (go into suspend mode) or does it just hang? Yes it turn off but can't turn back again. I can hear that disk starts but the screen stays black and only hard resets works.
> Why are you using **pci=nomsi** in your kernel boot line? What particular problem does it address? I found it here [http://ubuntuforums.org/showpost.php?p=11948346&postcount=16](http://ubuntuforums.org/showpost.php?p=11948346&postcount=16)
I thought it's worth to try.
> Have you looked at your bios settings? In particular anything that might reference C6 or C9 in the CPU settings? Maybe try disabling them. I can't find CPU settings in bios.

> Try unloading your wireless driver before suspendDidn't work.
> Can you do the following to get a more detailed log of your suspend attempt

[LIST=1]
[*] ```
sudo bash 
mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
export PM_DEBUG=true
pm-suspend
```When you recover the system, post back again the new pm-suspend.log file:
```
pastebinit /var/log/pm-suspend.log
```
[/LIST]
Here's the link:
[http://paste.ubuntu.com/1426242/](http://paste.ubuntu.com/1426242/)

---

### Post by Toz on 2012-12-11
First of all, since it doesn't seem to help, remove **pci=nomsi** from your kernel command line.

I can't find anything wrong in your log files (other than it doesn't return from suspend). The next step would be to do a resume-trace debug. The instructions are [here]("https://wiki.ubuntu.com/DebuggingKernelSuspend#A.22resume-trace.22_debugging_procedure_for_finding_buggy_drivers").

Make sure you read them through before you start so you understand what needs to be done. Hopefully this will help to identify the buggy driver.

---

### Post by Pyotrek on 2012-12-14
I have removed pc=nomsi from kernel command line.
 
I am not sure what I should provide as an output of this debugging action.
In file dmesg.txt I found such entries:
[    1.001965]   Magic number: 0:391:229
[    1.001972]   hash matches /build/buildd/linux-3.2.0/drivers/base/power/main.c:541

Here's the file itself 
[http://sdrv.ms/ZrPanN](http://sdrv.ms/ZrPanN)[URL="http://sdrv.ms/ZrPanN"]
[/URL] Should I give you anything else?

---

### Post by Toz on 2012-12-14
> **Pyotrek said:**
> I have removed pc=nomsi from kernel command line.
 
I am not sure what I should provide as an output of this debugging action.
In file dmesg.txt I found such entries:
[    1.001965]   Magic number: 0:391:229
[    1.001972]   hash matches /build/buildd/linux-3.2.0/drivers/base/power/main.c:541

Here's the file itself 
[http://sdrv.ms/ZrPanN](http://sdrv.ms/ZrPanN)[URL="http://sdrv.ms/ZrPanN"]
[/URL] Should I give you anything else?

Unfortunately, nothing obvious is coming up. A couple of more suggestions:

1. Look in your bios for some settings related to sleep states. If they exist, changing them might help.
2. Try uswsusp (an alternate suspend method) to see if it works. It works for me on an older Toshiba laptop. First, install it:
```
sudo apt-get install uswsusp
```
...then:
```
sudo s2ram
```
...or if you get a message about the system not being on a whitelist:
```
sudo s2ram -f
```

---

### Post by Pyotrek on 2012-12-16
> **Toz said:**
> Unfortunately, nothing obvious is coming up. A couple of more suggestions:

1. Look in your bios for some settings related to sleep states. If they exist, changing them might help.
2. Try uswsusp (an alternate suspend method) to see if it works. It works for me on an older Toshiba laptop. First, install it:
```
sudo apt-get install uswsusp
```...then:
```
sudo s2ram
```...or if you get a message about the system not being on a whitelist:
```
sudo s2ram -f
```

ad.1 There are no settings related to sleep in my Bios.
ad.2 Didn't work. Won't wake up.

---

### Post by Toz on 2012-12-16
> **Pyotrek said:**
> ad.2 Didn't work. Won't wake up.

Then we should remove uswsusp:
```
sudo apt-get purge uswsusp
```

Can you try the following to see if they cause the system to suspend and return:
```
sudo pm-suspend --quirk-test --quirk-s3-mode
```
```
sudo pm-suspend --quirk-test --quirk-vbe-post
```

---

### Post by Pyotrek on 2012-12-16
> **Toz said:**
> Can you try the following to see if they cause the system to suspend and return:
```
sudo pm-suspend --quirk-test --quirk-s3-mode
``````
sudo pm-suspend --quirk-test --quirk-vbe-post
```
Both didn't worked. System didn't woke up. Afterwards only unplugging the AC and waiting for some time caused system to boot correctly.

I am not sure if this could help but I remember that when using win xp on this machine sometimes display was also causing some issues. It stayed blank when starting up the system.

---

### Post by Mopar1973Man on 2012-12-16
I just been down this road with a Asus M3A motherboard with S3 suspend issues. I finally got mine functional. What was dumb was I was thinking its a Linux bug or software problem. Actually my issue was my BIOS was out-of-date. After updating the BIOS to most current flash problem is gone. So you might check to be sure the BIOS is up to date. ;)

Here is the page for the BIOS
[http://support.asus.com/download.aspx?SLanguage=en&p=3&s=95&m=F5RL&os=&hashedid=zkBaBe1G3duC4MEy](http://support.asus.com/download.aspx?SLanguage=en&p=3&s=95&m=F5RL&os=&hashedid=zkBaBe1G3duC4MEy)

---

### Post by Pyotrek on 2012-12-18
> **Mopar1973Man said:**
> I just been down this road with a Asus M3A motherboard with S3 suspend issues. I finally got mine functional. What was dumb was I was thinking its a Linux bug or software problem. Actually my issue was my BIOS was out-of-date. After updating the BIOS to most current flash problem is gone. So you might check to be sure the BIOS is up to date.
I have updated the BIOS to latest one. No change. Display stays black and only hard reset helps. By the way suspend worked fine under Windows XP.

---

