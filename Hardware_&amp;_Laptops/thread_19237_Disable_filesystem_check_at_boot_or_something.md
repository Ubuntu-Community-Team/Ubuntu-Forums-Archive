---
title: "Disable filesystem check at boot or something?"
date: 2005-03-11
forum: Hardware &amp; Laptops
---

### Post by fackamato on 2005-03-11
... or something. I'd rather not, but I kind of have to. I have two harddrives, one is a P-ATA one, the other is a S-ATA one. When I boot the modules for my southbridge which controls the S-ATA ports isn't loaded in the beginning I guess, so the kernel doesn't find my harddrive, or something. So it begins an e2fsck check, but the HDD uses reiserfs, which it doens't understand so I get prompted with "press control+d for normal startup or enter root password for maintenance".

Any idea on how to solve this?

dmesg @ [http://www.tehjunkyard.net/dmesg.txt](http://www.tehjunkyard.net/dmesg.txt)
messages @ [http://www.tehjunkyard.net/messages.txt](http://www.tehjunkyard.net/messages.txt)

edit:

lsmod
[size=1]```
Module                  Size  Used by
nls_cp437               5824  1 
isofs                  37372  1 
vmnet                  31568  0 
vmmon                  50496  0 
proc_intf               4324  0 
cpufreq_powersave       1856  0 
cpufreq_userspace       6240  0 
cpufreq_ondemand        6888  0 
freq_table              4384  0 
thermal                13608  0 
fan                     4612  0 
button                  6704  0 
processor              23368  1 thermal
ac                      4900  0 
battery                10212  0 
ipv6                  266400  14 
nfs                   216420  3 
lockd                  67016  2 nfs
sunrpc                153188  6 nfs,lockd
snd_ens1371            25088  6 
snd_rawmidi            25536  1 snd_ens1371
snd_seq_device          8844  1 snd_rawmidi
snd_ac97_codec         77344  1 snd_ens1371
snd_pcm_oss            54884  0 
snd_mixer_oss          20576  3 snd_pcm_oss
snd_pcm                99520  4 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              26404  2 snd_pcm
snd                    58468  14 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         10180  1 snd_pcm
gameport                4992  1 snd_ens1371
tuner                  22500  0 
saa7134               105576  0 
video_buf              22404  1 saa7134
v4l2_common             5920  1 saa7134
v4l1_compat            14660  1 saa7134
soundcore              10592  4 snd,saa7134
ir_common               5060  1 saa7134
videodev               10240  1 saa7134
joydev                 10144  0 
tsdev                   7904  0 
e1000                  89716  0 
ata_piix                9508  4 
libata                 51364  1 ata_piix
ehci_hcd               34148  0 
usbhid                 33184  0 
uhci_hcd               34640  0 
usbcore               123064  4 ehci_hcd,usbhid,uhci_hcd
shpchp                102468  0 
pci_hotplug            35068  1 shpchp
intel_agp              22876  0 
intel_mch_agp          10768  1 
agpgart                35308  3 intel_agp,intel_mch_agp
floppy                 61460  0 
pcspkr                  3788  0 
rtc                    13032  0 
nls_iso8859_1           4160  1 
ntfs                  113136  1 
md                     49264  0 
dm_mod                 63264  1 
capability              4872  0 
commoncap               8192  1 capability
loop                   17224  2 
nvidia               3471964  12 
w83781d                35688  0 
eeprom                  7704  0 
i2c_sensor              3712  2 w83781d,eeprom
i2c_isa                 2176  0 
i2c_i801                8780  0 
i2c_core               23136  7 tuner,saa7134,w83781d,eeprom,i2c_sensor,i2c_isa,i2c_i801
parport_pc             38532  1 
lp                     11972  0 
parport                38472  2 parport_pc,lp
evdev                   9760  0 
ide_cd                 43108  0 
cdrom                  41792  1 ide_cd
mousedev               11932  1 
psmouse                22408  0 
sd_mod                 18464  5 
scsi_mod              131200  2 libata,sd_mod
reiserfs              272560  1 
ext2                   69672  0 
ext3                  141512  4 
jbd                    65464  1 ext3
mbcache                 8676  2 ext2,ext3
ide_generic             1536  0 
ide_disk               21536  4 
piix                   11140  1 
ide_core              133500  4 ide_cd,ide_generic,ide_disk,piix
unix                   29392  730 
fbcon                  38976  0 
crc32                   4384  1 fbcon
font                    8384  1 fbcon
bitblit                 5856  1 fbcon
vesafb                  7012  0 
cfbcopyarea             4192  1 vesafb
cfbimgblt               3136  1 vesafb
cfbfillrect             3840  1 vesafb

```[/size]

intel ich5 southbridge ;O

---

### Post by bored2k on 2005-03-11
You sure youre shutting down you computer correctly?

Just today I had power problems and my Box got shutdown wrongfuly maybe twice, and after this I got like in 5 restarts "filesystem check" or something (took only about 10seconds though).


edit > I did not see the new edit, but It still doesnt change my question.

---

### Post by fackamato on 2005-03-11
[QUOTE=bored2k]You sure youre shutting down you computer correctly?

Just today I had power problems and my Box got shutdown wrongfuly maybe twice, and after this I got like in 5 restarts "filesystem check" or something (took only about 10seconds though).


edit > I did not see the new edit, but It still doesnt change my question.[/QUOTE]

It has nothing to do with that. e2fsk doesn't even find a harddrive to check, since they're not available. There's no sda, sda1-4 in /dev at that time. So there's nothing to check, but it expect it to be something, but there's not. After I press control+d, and the normal startup procedure is continuing, I get the sda devices and mount correctly mounts everything etc. I need the sda devices to exist before the filesystem checker starts or something... And yes, I shut down/reboot my computer correctly :). Too much important information to lose here...

Thanks for the quick reply btw.

---

### Post by bored2k on 2005-03-11
[QUOTE=fackamato]It has nothing to do with that. e2fsk doesn't even find a harddrive to check, since they're not available. There's no sda, sda1-4 in /dev at that time. So there's nothing to check, but it expect it to be something, but there's not. After I press control+d, and the normal startup procedure is continuing, I get the sda devices and mount correctly mounts everything etc. I need the sda devices to exist before the filesystem checker starts or something... And yes, I shut down/reboot my computer correctly :). Too much important information to lose here...

Thanks for the quick reply btw.[/QUOTE]
 2.30am ... I think  my Jedi powers are degrading by minute .

Sorry for not reading correctly!

---

### Post by fackamato on 2005-03-11
[QUOTE=bored2k]2.30am ... I think  my Jedi powers are degrading by minute .

Sorry for not reading correctly![/QUOTE]

:D

---

### Post by flyfishin on 2005-03-12
I've got ext3 partitions and I get the same error message.  I press Control-D and it boots up just fine. I'd also like to know how to fix this issue.

---

### Post by fackamato on 2005-03-12
[QUOTE=flyfishin]I've got ext3 partitions and I get the same error message.  I press Control-D and it boots up just fine. I'd also like to know how to fix this issue.[/QUOTE]


 :neutral: 

I've dist-upgraded to hoary, and now using the kernel 2.6.10-4-686-smp, still got this issue. :/

---

### Post by flyfishin on 2005-03-12
Mine is now fixed.  I cheated and reinstalled Hoary Preview and formatted the /usr/local partition that was giving me trouble.  I used to run FC3 on this laptop and the original ext3 partition was created with the FC3 install.  I didn't want to lose information on the partition so I didn't format it on my original install.  For some reason Hoary didn't like that ext3 partition during boot but I could use it once the system was up.  I couldn't run e2fsck on it at all.  The reinstall and reformatting it fixed things.

---

### Post by dhmlife on 2007-12-12
I'm running 7.10 on my HP Pavilion dv9000 with NVidia graphics card. I got the restricted NVidia driver to work and have been using my system and had replaced Vista totally with Ubuntu. Now the 30 Mount disk check stops me from booting. hangs at 70-80%. I can't boot to a shell or command line other than GRUB command line. How can i disable this check at boot time and get back to my ubuntu desktop? HEEELLPP!  :)




Danny

---

