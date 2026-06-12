---
title: "[SOLVED] update to 2.6.24-21 killed my wireless"
date: 2008-08-23
forum: General Help
---

### Post by dolo724 on 2008-08-23
Some time ago I installed Gutsy on my Dell Inspiron 6000, things just worked. I followed the update path using the Update Manager as Ubuntu presented it, and eventually used it to upgrade to Hardy. Still, I do the updates as they are presented. 

A few days ago (two or three) 2.6.24-21-generic was presented so I took it as recommended. No problems.
Yesterday 2.6.24-21-generic Updated Modules came and I installed it as well. No problems until I rebooted: eth1 (Intel PRO/Wireless 2200bg) disappeared. :(

Everything works as advertised on 2.6.24-20-generic. I'm happy using it, but I'd like to know:
1) is it a known bug
2) with a workaround?
3) How do I search for bugs if I were doing the research (of which I am ignorant, just a user I am)

Any help will be appreciated. I copied the lsmod output from both sessions, seen below.

Thanks in advance! mIke
  moderator: feel free to move this to a more appropriate forum
**2.6.24-20-generic**			
```

Module              	    Size		  Used by
michael_mic         	3456	4	 
arc4                	2944	4	 
ecb                 	4480	4	 
blkcipher           	8324	1	 ecb
ieee80211_crypt_tkip	11648	2	 
af_packet           	23812	4	 
ipv6                	267780	8	 
binfmt_misc         	12808	1	 
rfcomm              	41744	2	 
l2cap               	25728	13	 rfcomm
ppdev               	10372	0	 
speedstep_centrino  	9152	0	 
cpufreq_conservative	8712	0	 
cpufreq_userspace   	5284	0	 
cpufreq_stats       	7104	0	 
cpufreq_ondemand    	9740	1	 
freq_table          	5536	3	 speedstep_centrino,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave   	2688	0	 
sbs                 	15112	0	 
container           	5632	0	 
sbshc               	7680	1	 sbs
dock                	11280	0	 
iptable_filter      	3840	0	 
ip_tables           	14820	1	 iptable_filter
x_tables            	16132	1	 ip_tables
sbp2                	24072	0	 
parport_pc          	36260	0	 
lp                  	12324	0	 
parport             	37832	3	 ppdev,parport_pc,lp
pcmcia              	40876	0	 
joydev              	13120	0	 
hci_usb             	16540	2	 
bluetooth           	61156	7	 rfcomm,l2cap,hci_usb
snd_intel8x0        	35356	3	 
snd_ac97_codec      	101028	1	 snd_intel8x0
ac97_bus            	3072	1	 snd_ac97_codec
snd_pcm_oss         	42144	0	 
snd_mixer_oss       	17920	1	 snd_pcm_oss
snd_pcm             	78596	3	 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
dcdbas              	9504	0	 
evdev               	13056	8	 
snd_seq_dummy       	4868	0	 
fglrx               	1555468	20	 
snd_seq_oss         	35584	0	 
snd_seq_midi        	9376	0	 
snd_rawmidi         	25760	1	 snd_seq_midi
snd_seq_midi_event  	8320	2	 snd_seq_oss,snd_seq_midi
ipw2200             	146120	0	 
video               	19856	0	 
output              	4736	1	 video
sdhci               	19076	0	 
serio_raw           	7940	0	 
snd_seq             	54224	6	 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ieee80211           	35528	1	 ipw2200
ieee80211_crypt     	7040	2	 ieee80211_crypt_tkip,ieee80211
mmc_core            	51460	1	 sdhci
yenta_socket        	27276	1	 
rsrc_nonstatic      	13696	1	 yenta_socket
pcmcia_core         	40596	3	 pcmcia,yenta_socket,rsrc_nonstatic
snd_timer           	24836	2	 snd_pcm,snd_seq
snd_seq_device      	9612	5	 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button              	9232	0	 
battery             	14212	0	 
ac                  	6916	0	 
iTCO_wdt            	13092	0	 
iTCO_vendor_support 	4868	1	 iTCO_wdt
snd                 	56996	17	 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore           	8800	1	 snd
intel_agp           	25492	0	 
snd_page_alloc      	11400	2	 snd_intel8x0,snd_pcm
pcspkr              	4224	0	 
psmouse             	40336	0	 
shpchp              	34452	0	 
pci_hotplug         	30880	1	 shpchp
agpgart             	34760	2	 fglrx,intel_agp
ext3                	136712	1	 
jbd                 	48404	1	 ext3
mbcache             	9600	1	 ext3
sg                  	36880	0	 
sr_mod              	17956	0	 
cdrom               	37408	1	 sr_mod
sd_mod              	30720	3	 
pata_acpi           	8320	0	 
ahci                	28548	0	 
ata_generic         	8324	0	 
b44                 	28432	0	 
ata_piix            	19588	2	 
libata              	159344	4	pata_acpi,ahci,ata_generic,ata_piix
scsi_mod            	151436	5	 sbp2,sg,sr_mod,sd_mod,libata
ohci1394            	33584	0	 
ieee1394            	93752	2	 sbp2,ohci1394
ssb                 	34308	1	 b44
mii                 	6400	1	 b44
ehci_hcd            	37900	0	 
uhci_hcd            	27024	0	 
usbcore             	146028	4	 hci_usb,ehci_hcd,uhci_hcd
thermal             	16796	0	 
processor           	37384	2	 thermal
fan                 	5636	0	 
fbcon               	42912	0	 
tileblit            	3456	1	 fbcon
font                	9472	1	 fbcon
bitblit             	6784	1	 fbcon
softcursor          	3072	1	 bitblit
fuse                	50708	1	
```
			
**2.6.24-21-generic**
			```

Module               	   Size		  Used by
ipv6                 	267780	8	
binfmt_misc          	12808	1	
rfcomm               	41744	2	
l2cap                	25728	13	 rfcomm
ppdev                	10372	0	
speedstep_centrino   	9152	0	
cpufreq_conservative 	8712	0	
cpufreq_userspace    	5284	0	
cpufreq_stats        	7104	0	
cpufreq_ondemand     	9740	1	
freq_table           	5536	3	speedstep_centrino,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave    	2688	0	
sbs                  	15112	0	
container            	5632	0	
sbshc                	7680	1	sbs
dock                 	11280	0	
iptable_filter       	3840	0	
ip_tables            	14820	1	iptable_filter
x_tables             	16132	1	ip_tables
sbp2                 	24072	0	
parport_pc           	36260	0	
lp                   	12324	0	
parport              	37832	3	ppdev,parport_pc,lp
joydev               	13120	0	
pcmcia               	40876	0	
hci_usb              	16540	2	
bluetooth            	61156	7	rfcomm,l2cap,hci_usb
snd_intel8x0         	35356	3	
snd_ac97_codec       	101028	1	snd_intel8x0
ac97_bus             	3072	1	snd_ac97_codec
evdev                	13056	8	
dcdbas               	9504	0	
snd_pcm_oss          	42144	0	
snd_mixer_oss        	17920	1	snd_pcm_oss
snd_pcm              	78596	3	snd_intel8x0,snd_ac97_codec,snd_pcm_oss
serio_raw            	7940	0	
fglrx                	1555468	20	
psmouse              	40336	0	
snd_seq_dummy        	4868	0	
snd_seq_oss          	35584	0	
snd_seq_midi         	9376	0	
snd_rawmidi          	25760	1	snd_seq_midi
ieee80211_crypt      	7040	0	
video                	19856	0	
output               	4736	1	video
sdhci                	19076	0	
snd_seq_midi_event   	8320	2	snd_seq_oss,snd_seq_midi
ieee80211_rtl        	79496	0	
ieee80211_crypt_tkip_rtl 	11648	1	ieee80211_rtl
ieee80211_crypt_wep_rtl 	6400	1	ieee80211_rtl
ieee80211_crypt_ccmp_rtl 	8064	1	ieee80211_rtl
ieee80211_crypt_rtl   	6788	4	 ieee80211_rtl,ieee80211_crypt_tkip_rtl,ieee80211_crypt_wep_rtl,ieee80211_crypt_ccmp_rtl
mmc_core             	51460	1	sdhci
yenta_socket         	27276	1	
rsrc_nonstatic       	13696	1	yenta_socket
pcmcia_core          	40596	3	pcmcia,yenta_socket,rsrc_nonstatic
snd_seq              	54224	6	snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer            	24836	2	snd_pcm,snd_seq
snd_seq_device       	9612	5	snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button               	9232	0	
battery              	14212	0	
ac                   	6916	0	
snd                  	56996	17	 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore            	8800	1	snd
iTCO_wdt             	13092	0	
iTCO_vendor_support  	4868	1	iTCO_wdt
pcspkr               	4224	0	
snd_page_alloc       	11400	2	snd_intel8x0,snd_pcm
shpchp               	34452	0	
pci_hotplug          	30880	1	shpchp
intel_agp            	25492	0	
agpgart              	34760	2	fglrx,intel_agp
ext3                 	136840	1	
jbd                  	48404	1	ext3
mbcache              	9600	1	ext3
sg                   	36880	0	
sr_mod               	17956	0	
cdrom                	37408	1	sr_mod

sd_mod               	30720	3	
pata_acpi            	8320	0	
ahci                 	28548	0	
ata_generic          	8324	0	
b44                  	28432	0	
ata_piix             	19588	2	
libata               	159344	4	pata_acpi,ahci,ata_generic,ata_piix
scsi_mod             	151436	5	sbp2,sg,sr_mod,sd_mod,libata
ohci1394             	33584	0	
ieee1394             	93752	2	sbp2,ohci1394
ssb                  	34308	1	b44
mii                  	6400	1	b44
ehci_hcd             	37900	0	
uhci_hcd             	27024	0	
usbcore              	146412	4	hci_usb,ehci_hcd,uhci_hcd
thermal              	16796	0	
processor            	37384	2	thermal
fan                  	5636	0	
fbcon                	42912	0	
tileblit             	3456	1	fbcon
font                 	9472	1	fbcon
bitblit              	6784	1	fbcon
softcursor           	3072	1	bitblit
fuse                 	50708	1
```

---

### Post by BoneyOne on 2008-08-24
I also have the same problem where after updating and rebooting eth1 disappears. I'm running on Sony Vaio PCG-6G4L. 

Is there a way to go back to the older 2.6.24-20? Or has anyone heard of an update to fix this? Found a solution to fix it?

---

### Post by dolo724 on 2008-08-24
> **BoneyOne said:**
> I also have the same problem where after updating and rebooting eth1 disappears. I'm running on Sony Vaio PCG-6G4L. 

Is there a way to go back to the older 2.6.24-20? Or has anyone heard of an update to fix this? Found a solution to fix it?

Until I get a better answer, I am hitting ESC during the GRUB process, then selecting the older kernel. It works fine in the old mode for me.

---

### Post by Nepherte on 2008-08-24
You have most likely enabled the proposed repository. You need to realize that the proposed repository is very different to other repositories, i.e. they rather offer beta, unstable packages than stable ones. It is therefore recommended you disable the hardy-proposed repository unless you have an interest in testing updates and providing feedback. The latest stable kernel update the repositories provide is -19. That being said, I suggest you take the latest kernel that works for you in the grub boot loader menu.

---

### Post by hansdown on 2008-08-24
Please go to system>administration>software sources. You will be asked for your password. Click on updates and make sure the first and second boxes are checked, and the third and fourth boxes are un-checked, as these are pre-release and unsupported updates. This will stop update notification for these, as they are for testing purposes.

---

### Post by dolo724 on 2008-08-24
Thanks to Nepherte and hansdown, I disabled the errant repositories. Frankly, I'm not ready for the bleeding edge like I thought I was. oh well.

Otherwise it works great. !  I installed StartUp-Manager to help me with selecting a new GRUB default. I'm okay with CLI issues, not an expert, and GRUB is one of those grey areas for me. 

I call this one, SOLVED.

mIke

---

### Post by hansdown on 2008-08-24
Glad you got it fixed dolo724.

---

