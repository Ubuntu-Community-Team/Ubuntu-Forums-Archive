---
title: "usb ports inop"
date: 2008-01-24
forum: Hardware &amp; Laptops
---

### Post by rocko_mtv on 2008-01-24
I have a Toshiba A105-S2716 running 7.04 Feisty.  It is very sweet!

I finally got the touchpad tap click disabled and now trying to get my USB ports to function.  It does not recognize any device plugged into the ports.  They all work in XP Pro on this dual boot setup.  What do I need to post for someone to analyze this and the terminal command to bring it up?  Thanks in advance.

Rick

---

### Post by Yellow Pasque on 2008-01-24
The first thing you want to do is make sure your BIOS is up to date.
Next, make sure nothing's physically wrong with your USB ports. Do devices work on another OS? Do devices receive power when you plug them in on Ubuntu?
The next thing I would do is an lsmod command to make sure the proper USB modules are loaded. Look for a line like the following (I'm on Arch Linux at the moment, so yours may look a little different):
> usbcore               145072  4 usbhid,ehci_hcd,ohci_hcd
Finally, try plugging some devices in and seeing if an lsusb command recognizes them.

---

### Post by rocko_mtv on 2008-01-24
BIOS updates are done thru update manager? If so, yes.

Yes, 5 volts dc at USB ports.

I have since determined that they are working as I setup my printer through System/Administration/printers.  (Duh) Not sure why I did not go there to begin with?

On a desktop running 6.1 they just popped up notifying me they(drivers) were installed and ready to use.  I went to print and everything was perfect right out of the gate.   It did not do this on the laptop even though the devices were plugged into the usb ports during install.  So  I was wrong when stating they did not work as verified now in the log below.  It just didn't set stuff up like it did on the desktop.  But desktop is a common Intel 865 P4 mboard so it should find all that by default maybe?

Running lsmod I get this:

Module                  Size  Used by
usblp                  14848  0 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
i915                   25472  2 
drm                    81044  3 i915
speedstep_centrino      9920  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  1 
freq_table              5792  3 speedstep_centrino,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
video                  16388  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
i2c_core               22656  1 i2c_ec
dock                   10268  0 
button                  8720  0 
battery                10756  0 
container               5248  0 
ac                      6020  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
ipt_REJECT              5632  2 
xt_tcpudp               4224  5 
iptable_filter          3968  1 
ip_tables              13796  1 iptable_filter
x_tables               16388  3 ipt_REJECT,xt_tcpudp,ip_tables
nls_utf8                3072  1 
ntfs                  107764  1 
ext2                   66824  1 
af_packet              23816  4 
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
ipv6                  269088  10 
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
joydev                 10816  0 
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
arc4                    2944  2 
ecb                     4480  2 
blkcipher               6784  1 ecb
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ieee80211_crypt_wep     6144  1 
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 39212  0 
ipw2200               148040  0 
tifm_7xx1               8704  0 
tifm_core              11140  1 tifm_7xx1
sdhci                  18700  0 
ieee80211              34760  1 ipw2200
ieee80211_crypt         7040  2 ieee80211_crypt_wep,ieee80211
sky2                   43528  0 
mmc_core               26756  1 sdhci
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                38920  0 
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
serio_raw               7940  0 
intel_agp              26140  1 
agpgart                35400  3 drm,intel_agp
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
evdev                  11008  4 
tsdev                   8768  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  2 ext2,ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  5 
ata_piix               15492  4 
ahci                   22020  0 
ata_generic             9092  0 
libata                125720  3 ata_piix,ahci,ata_generic
scsi_mod              142348  5 sbp2,sg,sr_mod,sd_mod,libata
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  4 usblp,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  268 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability


Thanks for your help. Please be patient as you have another newbie here to GNU/Linux.

Do you see any issues here I should address?  Bios update like you mentioned? 

I will say this laptop seems to run cooler on Ubuntu than WinXP at the exhaust side vent.  But is it because the fan is OFF (as shown in log) or just not reaching a temp to kick in?  It stays equally hot or hotter in the HD and processor area bottom side as when running in XP where same fan runs a lot.  Xsensors doesn't run properly to verify temps.  Any ideas?

My next journey (task) will be getting Ubuntu to recognize WPA PSK on WiFi.  Oh, I forgot, I  have those pesky laptop shutdown issues too :)

Again, much appreciation for your time and sharing your experience.  I truly believe I have chosen a good path with Ubuntu to start my GNU/Linux  life.  I am like a sponge right now but in a good way!

Thanks,
Rick

---

### Post by Yellow Pasque on 2008-01-24
- Glad to hear your USB is working properly.
- I'm not sure if you can update your BIOS without Windows [http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_dtlViewDL.jsp?soid=1707090&moid=1209142&rpn=PSAA0U&BV_SessionID=@@@@0641073313.1201210830@@@@&BV_EngineID=cccjadededkdkdgcgfkceghdgngdgnn.0&ct=DL&all_docs=false](http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_dtlViewDL.jsp?soid=1707090&moid=1209142&rpn=PSAA0U&BV_SessionID=@@@@0641073313.1201210830@@@@&BV_EngineID=cccjadededkdkdgcgfkceghdgngdgnn.0&ct=DL&all_docs=false)
> Xsensors doesn't run properly to verify temps. Any ideas?
Try:
```
sudo apt-get install lm-sensors
```
After you install that, run the following command and answer yes to its questions about probing the buses and inserting the necessary modules:
> sudo sensors-detect

---

### Post by rocko_mtv on 2008-01-24
After running those commands and having it probe thru all options I get the following:

"Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. "

---

### Post by Yellow Pasque on 2008-01-24
Ok. Try this:
> sudo modprobe toshiba_acpi

---

### Post by rocko_mtv on 2008-01-24
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.20-16-generic/kernel/drivers/acpi/toshiba_acpi.ko): No such device

---

### Post by Yellow Pasque on 2008-01-24
Sorry, but it looks like your laptop isn't supported by the Toshiba driver or the Omnibook/Toshiba driver :(
[http://omnibook.sourceforge.net/doku.php?id=laptops&DokuWiki=786c00eee23f59e4325a3cbcfdd66dd9](http://omnibook.sourceforge.net/doku.php?id=laptops&DokuWiki=786c00eee23f59e4325a3cbcfdd66dd9)

---

### Post by rocko_mtv on 2008-01-24
Yes, that's a bummer eh?

Wireless and touchpad are not supported either according to that chart but I have those features in all their  glory with GUI 's working on this model.  Does this mean there is a way to get it working but it will take some experimenting?

> If your model is not listed below you may try to load the module. If it have the same DMI identification strings as a supported machine it may works out of the box.

Only the /proc/omnibook/dmi and /proc/omnibook/version files are created when you load the module on an unsupported machine. 

Should I take this to mean the module mentioned above is a generic base type and it needs built out in order to get Xsensors to work on this model?

---

### Post by Yellow Pasque on 2008-01-24
"[B]If your model is not listed below..[B]"
Your model was listed and unsupported. You should take that to mean that your laptop's ACPI routines (fan control, temperature sensing) are unsupported in Linux. Your wireless and touchpad are working through other means. Write Toshiba an angry letter and tell them to open up their hardware specs.

---

### Post by rocko_mtv on 2008-01-24
Thanks for the help and advice in trying to nail this down Temüjin.  I will repost if I find a cure and the thread is still open.   

Take care,
Rick

---

