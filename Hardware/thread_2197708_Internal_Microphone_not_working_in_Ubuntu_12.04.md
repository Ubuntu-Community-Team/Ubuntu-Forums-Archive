---
title: "Internal Microphone not working in Ubuntu 12.04"
date: 2014-01-05
forum: Hardware
---

### Post by venkatana2 on 2014-01-05
I have compaq presario Notebook CQ 40. After upgrading to Ubuntu 12.04 from from Ubuntu 10.04, the internal mic is not working.  I am able to playback songs from file, therefore, the speakers are working.  Recording from an external mic is also ok.  Sound is unmuted in Puseaudio volume control and in Alsamixer the volume is kept at high. I need help and advise to get my mic working.  The output of Alsa-info script is given:
  	 	 	 	   venkat@venkat-laptop:~$ bash Desktop/alsa-info.sh --stdout  
 upload=true&script=true&cardinfo= 
 !!################################  
 !!ALSA Information Script v 0.4.62  
 !!################################  
 

 !!Script ran on: Sun Jan  5 07:05:13 UTC 2014  
 

 

 !!Linux Distribution  
 !!------------------  
 

 Ubuntu 12.04.3 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 12.04.3 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu precise (12.04.3 LTS)"  
 

 

 !!DMI Information  
 !!---------------  
 

 Manufacturer:      Hewlett-Packard  
 Product Name:      Compaq Presario CQ40 Notebook PC  
 Product Version:   F.24  
 Firmware Version:  F.24  
 

 

 !!Kernel Information  
 !!------------------  
 

 Kernel release:    3.2.0-58-generic  
 Operating System:  GNU/Linux  
 Architecture:      i686  
 Processor:         i686  
 SMP Enabled:       Yes  
 

 

 !!ALSA Version  
 !!------------  
 

 Driver version:     1.0.24  
 Library version:    1.0.25  
 Utilities version:  1.0.25  
 

 

 !!Loaded ALSA modules  
 !!-------------------  
 

 snd_hda_intel  
 

 

 !!Sound Servers on this system  
 !!----------------------------  
 

 Pulseaudio:  
       Installed - Yes (/usr/bin/pulseaudio)  
       Running - Yes  
 

 ESound Daemon:  
       Installed - Yes (/usr/bin/esd)  
       Running - No  
 

 

 !!Soundcards recognised by ALSA  
 !!-----------------------------  
 

  0 [Intel          ]: HDA-Intel - HDA Intel  
                       HDA Intel at 0x9c500000 irq 49  
 

 

 !!PCI Soundcards installed in the system  
 !!-------------------------------------- 
 

 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)  
 

 

 !!Advanced information - PCI Vendor/Device/Subsystem ID's  
 !!------------------------------------------------------- 
 

 00:1b.0 0403: 8086:293e (rev 03)  
 	Subsystem: 103c:3607  
 

 

 !!Modprobe options (Sound related)  
 !!--------------------------------  
 

 snd-atiixp-modem: index=-2  
 snd-intel8x0m: index=-2  
 snd-via82xx-modem: index=-2  
 snd-usb-audio: index=-2  
 snd-usb-caiaq: index=-2  
 snd-usb-ua101: index=-2  
 snd-usb-us122l: index=-2  
 snd-usb-usx2y: index=-2  
 snd-cmipci: mpu_port=0x330 fm_port=0x388  
 snd-pcsp: index=-2  
 snd-usb-audio: index=-2  
 

 

 !!Loaded sound module options  
 !!---------------------------  
 

 !!Module: snd_hda_intel  
 	align_buffer_size : Y  
 	bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1 
 	beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0  
 	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y  
 	enable_msi : -1  
 	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null) 
 	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1 
 	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null) 
 	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null) 
 	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0  
 	power_save : 0  
 	power_save_controller : Y  
 	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1 
 	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0  
 	single_cmd : N  
 	snoop : Y  
 

 

 !!HDA-Intel Codec information  
 !!---------------------------  
 --startcollapse--  
 

 Codec: IDT 92HD71B7X  
 Address: 0  
 AFG Function Id: 0x1 (unsol 1)  
 Vendor Id: 0x111d76b2  
 Subsystem Id: 0x103c3607  
 Revision Id: 0x100302  
 No Modem Function Group found  
 Default PCM:  
     rates [0x7e0]: 44100 48000 88200 96000 176400 192000  
     bits [0xe]: 16 20 24  
     formats [0x1]: PCM  
 Default Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1  
 Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1  
 GPIO: io=8, o=0, i=0, unsolicited=1, wake=1  
   IO[0]: enable=1, dir=1, wake=0, sticky=0, data=1, unsol=0  
   IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0  
   IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0  
   IO[3]: enable=1, dir=1, wake=0, sticky=0, data=1, unsol=0  
   IO[4]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0  
   IO[5]: enable=1, dir=1, wake=0, sticky=0, data=1, unsol=0  
   IO[6]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0  
   IO[7]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0  
 Power-Map: 0x00  
 Analog Loopback: 0x00  
 Node 0x0a [Pin Complex] wcaps 0x400181: Stereo  
   Control: name="Front Headphone Jack", index=0, device=0  
   Pincap 0x0000001c: OUT HP Detect  
   Pin Default 0x0221201f: [Jack] HP Out at Ext Front  
     Conn = 1/8, Color = Grey  
     DefAssociation = 0x1, Sequence = 0xf  
   Pin-ctls: 0xc0: OUT HP  
   Unsolicited: tag=01, enabled=1  
   Connection: 3  
      0x10 0x11* 0x17  
 Node 0x0b [Pin Complex] wcaps 0x400081: Stereo  
   Control: name="Mic Jack Mode", index=0, device=0  
     ControlAmp: chs=0, dir=In, idx=0, ofs=0  
   Control: name="Mic Jack", index=0, device=0  
   Pincap 0x00001724: IN Detect  
     Vref caps: HIZ 50 GRD 80  
   Pin Default 0x02a12020: [Jack] Mic at Ext Front  
     Conn = 1/8, Color = Grey  
     DefAssociation = 0x2, Sequence = 0x0  
   Pin-ctls: 0x24: IN VREF_80  
   Unsolicited: tag=02, enabled=1  
 Node 0x0c [Pin Complex] wcaps 0x400081: Stereo  
   Pincap 0x00001724: IN Detect  
     Vref caps: HIZ 50 GRD 80  
   Pin Default 0x95a79330: [Fixed] Mic at Int Top  
     Conn = Analog, Color = Pink  
     DefAssociation = 0x3, Sequence = 0x0  
     Misc = NO_PRESENCE  
   Pin-ctls: 0x24: IN VREF_80  
   Unsolicited: tag=00, enabled=0  
 Node 0x0d [Pin Complex] wcaps 0x400181: Stereo  
   Pincap 0x00000014: OUT Detect  
   Pin Default 0x90170010: [Fixed] Speaker at Int N/A  
     Conn = Analog, Color = Unknown  
     DefAssociation = 0x1, Sequence = 0x0  
   Pin-ctls: 0x00:  
   Unsolicited: tag=00, enabled=0  
   Connection: 3  
      0x10* 0x11 0x17  
 Node 0x0e [Pin Complex] wcaps 0x400081: Stereo  
   Pincap 0x00001724: IN Detect  
     Vref caps: HIZ 50 GRD 80  
   Pin Default 0x40f000f0: [N/A] Other at Ext N/A  
     Conn = Unknown, Color = Unknown  
     DefAssociation = 0xf, Sequence = 0x0  
   Pin-ctls: 0x00: VREF_HIZ  
   Unsolicited: tag=00, enabled=0  
 Node 0x0f [Pin Complex] wcaps 0x400181: Stereo  
   Pincap 0x00000014: OUT Detect  
   Pin Default 0x40f000f2: [N/A] Other at Ext N/A  
     Conn = Unknown, Color = Unknown  
     DefAssociation = 0xf, Sequence = 0x2  
   Pin-ctls: 0x00:  
   Unsolicited: tag=00, enabled=0  
   Connection: 3  
      0x10* 0x11 0x17  
 Node 0x10 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L  
   Control: name="Speaker Playback Volume", index=0, device=0  
     ControlAmp: chs=3, dir=Out, idx=0, ofs=63  
   Control: name="Speaker Playback Switch", index=0, device=0  
     ControlAmp: chs=3, dir=Out, idx=0, ofs=0  
   Device: name="STAC92xx Analog", type="Audio", device=0  
   Amp-Out caps: N/A  
   Amp-Out vals:  [0x73 0x73]  
   Converter: stream=8, channel=0  
   Power: setting=D0, actual=D0  
   Delay: 13 samples  
 Node 0x11 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L  
   Control: name="Headphone Playback Volume", index=0, device=0  
     ControlAmp: chs=3, dir=Out, idx=0, ofs=63  
   Control: name="Headphone Playback Switch", index=0, device=0  
     ControlAmp: chs=3, dir=Out, idx=0, ofs=0  
   Amp-Out caps: N/A  
   Amp-Out vals:  [0x73 0x73]  
   Converter: stream=8, channel=0  
   Power: setting=D0, actual=D0  
   Delay: 13 samples  
 Node 0x12 [Audio Input] wcaps 0x1d0541: Stereo  
   Device: name="STAC92xx Analog", type="Audio", device=0  
   Converter: stream=4, channel=0  
   SDI-Select: 0  
   Power: setting=D3, actual=D3  
   Delay: 13 samples  
   Connection: 1  
      0x1c  
   Processing caps: benign=0, ncoeff=0  
 Node 0x13 [Audio Input] wcaps 0x1d0541: Stereo  
   Converter: stream=0, channel=0  
   SDI-Select: 0  
   Power: setting=D0, actual=D0  
   Delay: 13 samples  
   Connection: 1  
      0x1d  
   Processing caps: benign=0, ncoeff=0  
 Node 0x14 [Pin Complex] wcaps 0x400100: Mono  
   Pincap 0x00000010: OUT  
   Pin Default 0x40f000f3: [N/A] Other at Ext N/A  
     Conn = Unknown, Color = Unknown  
     DefAssociation = 0xf, Sequence = 0x3  
   Pin-ctls: 0x00:  
   Connection: 1  
      0x16  
 Node 0x15 [Audio Selector] wcaps 0x300101: Stereo  
   Connection: 3  
      0x10* 0x11 0x17  
 Node 0x16 [Audio Mixer] wcaps 0x200100: Mono  
   Connection: 1  
      0x15  
 Node 0x17 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In  
   Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1  
   Amp-In vals:  [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97]  
   Connection: 5  
      0x10 0x11 0x27 0x1a 0x1b  
 Node 0x18 [Pin Complex] wcaps 0x40000d: Stereo Amp-Out  
   Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0  
   Amp-Out vals:  [0x00 0x00]  
   Pincap 0x00000020: IN  
   Pin Default 0x40f000f4: [N/A] Other at Ext N/A  
     Conn = Unknown, Color = Unknown  
     DefAssociation = 0xf, Sequence = 0x4  
   Pin-ctls: 0x00:  
 Node 0x19 [Pin Complex] wcaps 0x40000d: Stereo Amp-Out  
   Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0  
   Amp-Out vals:  [0x00 0x00]  
   Pincap 0x00000020: IN  
   Pin Default 0x40f000f5: [N/A] Other at Ext N/A  
     Conn = Unknown, Color = Unknown  
     DefAssociation = 0xf, Sequence = 0x5  
   Pin-ctls: 0x00:  
 Node 0x1a [Audio Selector] wcaps 0x30010d: Stereo Amp-Out  
   Control: name="Mux Capture Volume", index=0, device=0  
     ControlAmp: chs=3, dir=Out, idx=0, ofs=0  
   Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0  
   Amp-Out vals:  [0x03 0x03]  
   Connection: 3  
      0x0b 0x0c* 0x0e  
 Node 0x1b [Audio Selector] wcaps 0x30010d: Stereo Amp-Out  
   Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0  
   Amp-Out vals:  [0x00 0x00]  
   Connection: 3  
      0x0b* 0x0c 0x0e  
 Node 0x1c [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L  
   Control: name="Capture Volume", index=0, device=0  
     ControlAmp: chs=3, dir=Out, idx=0, ofs=0  
   Control: name="Capture Switch", index=0, device=0  
     ControlAmp: chs=3, dir=Out, idx=0, ofs=0  
   Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1  
   Amp-Out vals:  [0x0f 0x0f]  
   Connection: 4  
      0x1a* 0x17 0x18 0x19  
 Node 0x1d [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L  
   Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1  
   Amp-Out vals:  [0x80 0x80]  
   Connection: 4  
      0x1b* 0x17 0x18 0x19  
 Node 0x1e [Pin Complex] wcaps 0x400301: Stereo Digital  
   Pincap 0x00000010: OUT  
   Pin Default 0x014411a0: [Jack] SPDIF Out at Ext Rear  
     Conn = RCA, Color = Black  
     DefAssociation = 0xa, Sequence = 0x0  
     Misc = NO_PRESENCE  
   Pin-ctls: 0x40: OUT  
   Connection: 1  
      0x24  
 Node 0x1f [Pin Complex] wcaps 0x400701: Stereo Digital  
   Pincap 0x00010010: OUT EAPD  
   EAPD 0x0:  
   Pin Default 0x40f000f6: [N/A] Other at Ext N/A  
     Conn = Unknown, Color = Unknown  
     DefAssociation = 0xf, Sequence = 0x6  
   Pin-ctls: 0x00:  
   Power: setting=D0, actual=D0  
   Connection: 2  
      0x24* 0x25  
 Node 0x20 [Pin Complex] wcaps 0x400301: Stereo Digital  
   Pincap 0x00000010: OUT  
   Pin Default 0x40f000f7: [N/A] Other at Ext N/A  
     Conn = Unknown, Color = Unknown  
     DefAssociation = 0xf, Sequence = 0x7  
   Pin-ctls: 0x00:  
   Connection: 1  
      0x25  
 Node 0x21 [Audio Output] wcaps 0x40211: Stereo Digital  
   Control: name="IEC958 Playback Con Mask", index=0, device=0  
   Control: name="IEC958 Playback Pro Mask", index=0, device=0  
   Control: name="IEC958 Playback Default", index=0, device=0  
   Control: name="IEC958 Playback Switch", index=0, device=0  
   Control: name="IEC958 Default PCM Playback Switch", index=0, device=0  
   Device: name="STAC92xx Digital", type="SPDIF", device=1  
   Converter: stream=8, channel=0  
   Digital:  
   Digital category: 0x0  
   PCM:  
     rates [0x7e0]: 44100 48000 88200 96000 176400 192000  
     bits [0xe]: 16 20 24  
     formats [0x5]: PCM AC3  
   Delay: 4 samples  
 Node 0x22 [Audio Output] wcaps 0x40211: Stereo Digital  
   Converter: stream=8, channel=0  
   Digital:  
   Digital category: 0x0  
   PCM:  
     rates [0x7e0]: 44100 48000 88200 96000 176400 192000  
     bits [0xe]: 16 20 24  
     formats [0x5]: PCM AC3  
   Delay: 4 samples  
 Node 0x23 [Vendor Defined Widget] wcaps 0xf00000: Mono  
 Node 0x24 [Audio Selector] wcaps 0x300101: Stereo  
   Connection: 3  
      0x21* 0x1c 0x1d  
 Node 0x25 [Audio Selector] wcaps 0x300101: Stereo  
   Connection: 3  
      0x22* 0x1c 0x1d  
 Node 0x26 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out  
   Control: name="Beep Playback Switch", index=0, device=0  
     ControlAmp: chs=1, dir=Out, idx=0, ofs=0  
   Control: name="Beep Playback Volume", index=0, device=0  
     ControlAmp: chs=1, dir=Out, idx=0, ofs=0  
   Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=1  
   Amp-Out vals:  [0x00]  
 Node 0x27 [Pin Complex] wcaps 0x400000: Mono  
   Pincap 0x00000020: IN  
   Pin Default 0x40f000f0: [N/A] Other at Ext N/A  
     Conn = Unknown, Color = Unknown  
     DefAssociation = 0xf, Sequence = 0x0  
   Pin-ctls: 0x00:  
 Node 0x28 [Volume Knob Widget] wcaps 0x600000: Mono  
   Volume-Knob: delta=1, steps=127, direct=1, val=127  
   Connection: 2  
      0x10 0x11  
 Codec: LSI ID 1040  
 Address: 1  
 MFG Function Id: 0x2 (unsol 1)  
 Vendor Id: 0x11c11040  
 Subsystem Id: 0x103c137e  
 Revision Id: 0x100200  
 Modem Function Group: 0x1  
 Codec: Intel Cantiga HDMI  
 Address: 2  
 AFG Function Id: 0x1 (unsol 0)  
 Vendor Id: 0x80862802  
 Subsystem Id: 0x80860101  
 Revision Id: 0x100000  
 No Modem Function Group found  
 Default PCM:  
     rates [0x0]:  
     bits [0x0]:  
     formats [0x0]:  
 Default Amp-In caps: N/A  
 Default Amp-Out caps: N/A  
 GPIO: io=0, o=0, i=0, unsolicited=0, wake=0  
 Node 0x02 [Audio Output] wcaps 0x6211: 8-Channels Digital  
   Converter: stream=0, channel=0  
   Digital: Enabled  
   Digital category: 0x0  
   PCM:  
     rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000  
     bits [0x1e]: 16 20 24 32  
     formats [0x5]: PCM AC3  
 Node 0x03 [Pin Complex] wcaps 0x40739d: 8-Channels Digital Amp-Out CP  
   Control: name="HDMI/DP,pcm=3 Jack", index=0, device=0  
   Control: name="IEC958 Playback Con Mask", index=1, device=0  
   Control: name="IEC958 Playback Pro Mask", index=1, device=0  
   Control: name="IEC958 Playback Default", index=1, device=0  
   Control: name="IEC958 Playback Switch", index=1, device=0  
   Control: name="ELD", index=0, device=3  
   Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1  
   Amp-Out vals:  [0x00 0x00]  
   Pincap 0x00000094: OUT Detect HDMI  
   Pin Default 0x18560010: [Jack] Digital Out at Int HDMI  
     Conn = Digital, Color = Unknown  
     DefAssociation = 0x1, Sequence = 0x0  
   Pin-ctls: 0x40: OUT  
   Unsolicited: tag=01, enabled=1  
   Connection: 1  
      0x02  
 --endcollapse--  
 

 

 !!ALSA Device nodes  
 !!-----------------  
 

 crw-rw---T+ 1 root audio 116,  9 Jan  5 11:36 /dev/snd/controlC0  
 crw-rw---T+ 1 root audio 116,  8 Jan  5 11:36 /dev/snd/hwC0D0  
 crw-rw---T+ 1 root audio 116,  7 Jan  5 11:36 /dev/snd/hwC0D1  
 crw-rw---T+ 1 root audio 116,  6 Jan  5 11:36 /dev/snd/hwC0D2  
 crw-rw---T+ 1 root audio 116,  5 Jan  5 12:11 /dev/snd/pcmC0D0c  
 crw-rw---T+ 1 root audio 116,  4 Jan  5 12:30 /dev/snd/pcmC0D0p  
 crw-rw---T+ 1 root audio 116,  3 Jan  5 11:36 /dev/snd/pcmC0D1p  
 crw-rw---T+ 1 root audio 116,  2 Jan  5 11:36 /dev/snd/pcmC0D3p  
 crw-rw---T+ 1 root audio 116,  1 Jan  5 11:36 /dev/snd/seq  
 crw-rw---T+ 1 root audio 116, 33 Jan  5 11:36 /dev/snd/timer  
 

 /dev/snd/by-path:  
 total 0  
 drwxr-xr-x 2 root root  60 Jan  5 11:36 .  
 drwxr-xr-x 3 root root 260 Jan  5 11:36 ..  
 lrwxrwxrwx 1 root root  12 Jan  5 11:36 pci-0000:00:1b.0 -> ../controlC0  
 

 

 !!Aplay/Arecord output  
 !!--------------------  
 

 APLAY  
 

 **** List of PLAYBACK Hardware Devices ****  
 card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]  
   Subdevices: 0/1  
   Subdevice #0: subdevice #0  
 card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]  
   Subdevices: 1/1  
   Subdevice #0: subdevice #0  
 card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]  
   Subdevices: 1/1  
   Subdevice #0: subdevice #0  
 

 ARECORD  
 

 **** List of CAPTURE Hardware Devices ****  
 card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]  
   Subdevices: 1/1  
   Subdevice #0: subdevice #0  
 

 !!Amixer output  
 !!-------------  
 

 !!-------Mixer controls for card 0 [Intel]  
 

 Card hw:0 'Intel'/'HDA Intel at 0x9c500000 irq 49'  
   Mixer name	: 'Intel Cantiga HDMI'  
   Components	: 'HDA:111d76b2,103c3607,00100302 HDA:11c11040,103c137e,00100200 HDA:80862802,80860101,00100000'  
   Controls      : 29  
   Simple ctrls  : 14  
 Simple mixer control 'Master',0  
   Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum  
   Playback channels: Mono  
   Limits: Playback 0 - 64  
   Mono: Playback 52 [81%] [-9.00dB] [on]  
 Simple mixer control 'Headphone',0  
   Capabilities: pvolume pswitch penum  
   Playback channels: Front Left - Front Right  
   Limits: Playback 0 - 64  
   Mono:  
   Front Left: Playback 64 [100%] [0.00dB] [on]  
   Front Right: Playback 64 [100%] [0.00dB] [on]  
 Simple mixer control 'Speaker',0  
   Capabilities: pvolume pswitch penum  
   Playback channels: Front Left - Front Right  
   Limits: Playback 0 - 64  
   Mono:  
   Front Left: Playback 64 [100%] [0.00dB] [on]  
   Front Right: Playback 64 [100%] [0.00dB] [on]  
 Simple mixer control 'Bass Speaker',0  
   Capabilities: pswitch pswitch-joined penum  
   Playback channels: Mono  
   Mono: Playback [on]  
 Simple mixer control 'PCM',0  
   Capabilities: pvolume penum  
   Playback channels: Front Left - Front Right  
   Limits: Playback 0 - 255  
   Mono:  
   Front Left: Playback 254 [100%] [0.20dB]  
   Front Right: Playback 254 [100%] [0.20dB]  
 Simple mixer control 'Mic Jack Mode',0  
   Capabilities: enum  
   Items: 'Mic In' 'Line In'  
   Item0: 'Mic In'  
 Simple mixer control 'IEC958',0  
   Capabilities: pswitch pswitch-joined penum  
   Playback channels: Mono  
   Mono: Playback [off]  
 Simple mixer control 'IEC958 Default PCM',0  
   Capabilities: pswitch pswitch-joined penum  
   Playback channels: Mono  
   Mono: Playback [on]  
 Simple mixer control 'IEC958 Playback Source',0  
   Capabilities: enum  
   Items: 'Digital Playback' 'Analog Mux 1' 'Analog Mux 2'  
   Item0: 'Digital Playback'  
 Simple mixer control 'IEC958',1  
   Capabilities: pswitch pswitch-joined penum  
   Playback channels: Mono  
   Mono: Playback [on]  
 Simple mixer control 'Beep',0  
   Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum  
   Playback channels: Mono  
   Limits: Playback 0 - 3  
   Mono: Playback 0 [0%] [-18.00dB] [on] 
 Simple mixer control 'Capture',0  
   Capabilities: cvolume cswitch penum  
   Capture channels: Front Left - Front Right  
   Limits: Capture 0 - 15  
   Front Left: Capture 15 [100%] [22.50dB] [on]  
   Front Right: Capture 15 [100%] [22.50dB] [on]  
 Simple mixer control 'Digital',0  
   Capabilities: cvolume penum  
   Capture channels: Front Left - Front Right  
   Limits: Capture 0 - 120  
   Front Left: Capture 119 [99%] [29.50dB]  
   Front Right: Capture 119 [99%] [29.50dB]  
 Simple mixer control 'Mux',0  
   Capabilities: cvolume penum  
   Capture channels: Front Left - Front Right  
   Limits: Capture 0 - 3  
   Front Left: Capture 3 [100%] [30.00dB]  
   Front Right: Capture 3 [100%] [30.00dB]  
 

 

 !!Alsactl output  
 !!--------------  
 

 --startcollapse--  
 state.Intel {  
 	control.1 {  
 		iface MIXER  
 		name 'Speaker Playback Volume'  
 		value.0 64  
 		value.1 64  
 		comment {  
 			access 'read write'  
 			type INTEGER  
 			count 2  
 			range '0 - 64'  
 			dbmin -4800  
 			dbmax 0  
 			dbvalue.0 0  
 			dbvalue.1 0  
 		}  
 	}  
 	control.2 {  
 		iface MIXER  
 		name 'Speaker Playback Switch'  
 		value.0 true  
 		value.1 true  
 		comment {  
 			access 'read write'  
 			type BOOLEAN  
 			count 2  
 		}  
 	}  
 	control.3 {  
 		iface MIXER  
 		name 'Mic Jack Mode'  
 		value 'Mic In'  
 		comment {  
 			access 'read write'  
 			type ENUMERATED  
 			count 1  
 			item.0 'Mic In'  
 			item.1 'Line In'  
 		}  
 	}  
 	control.4 {  
 		iface MIXER  
 		name 'Beep Playback Switch'  
 		value true  
 		comment {  
 			access 'read write'  
 			type BOOLEAN  
 			count 1  
 		}  
 	}  
 	control.5 {  
 		iface MIXER  
 		name 'Beep Playback Volume'  
 		value 0  
 		comment {  
 			access 'read write'  
 			type INTEGER  
 			count 1  
 			range '0 - 3'  
 			dbmin -1800  
 			dbmax 0  
 			dbvalue.0 -1800  
 		}  
 	}  
 	control.6 {  
 		iface MIXER  
 		name 'Headphone Playback Volume'  
 		value.0 64  
 		value.1 64  
 		comment {  
 			access 'read write'  
 			type INTEGER  
 			count 2  
 			range '0 - 64'  
 			dbmin -4800  
 			dbmax 0  
 			dbvalue.0 0  
 			dbvalue.1 0  
 		}  
 	}  
 	control.7 {  
 		iface MIXER  
 		name 'Headphone Playback Switch'  
 		value.0 true  
 		value.1 true  
 		comment {  
 			access 'read write'  
 			type BOOLEAN  
 			count 2  
 		}  
 	}  
 	control.8 {  
 		iface MIXER  
 		name 'Capture Volume'  
 		value.0 15  
 		value.1 15  
 		comment {  
 			access 'read write'  
 			type INTEGER  
 			count 2  
 			range '0 - 15'  
 			dbmin 0  
 			dbmax 2250  
 			dbvalue.0 2250  
 			dbvalue.1 2250  
 		}  
 	}  
 	control.9 {  
 		iface MIXER  
 		name 'Capture Switch'  
 		value.0 true  
 		value.1 true  
 		comment {  
 			access 'read write'  
 			type BOOLEAN  
 			count 2  
 		}  
 	}  
 	control.10 {  
 		iface MIXER  
 		name 'Mux Capture Volume'  
 		value.0 3  
 		value.1 3  
 		comment {  
 			access 'read write'  
 			type INTEGER  
 			count 2  
 			range '0 - 3'  
 			dbmin 0  
 			dbmax 3000  
 			dbvalue.0 3000  
 			dbvalue.1 3000  
 		}  
 	}  
 	control.11 {  
 		iface MIXER  
 		name 'Bass Speaker Playback Switch'  
 		value true  
 		comment {  
 			access 'read write'  
 			type BOOLEAN  
 			count 1  
 		}  
 	}  
 	control.12 {  
 		iface MIXER  
 		name 'IEC958 Playback Source'  
 		value 'Digital Playback'  
 		comment {  
 			access 'read write'  
 			type ENUMERATED  
 			count 1  
 			item.0 'Digital Playback'  
 			item.1 'Analog Mux 1'  
 			item.2 'Analog Mux 2'  
 		}  
 	}  
 	control.13 {  
 		iface MIXER  
 		name 'IEC958 Playback Con Mask'  
 		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000' 
 		comment {  
 			access read  
 			type IEC958  
 			count 1  
 		}  
 	}  
 	control.14 {  
 		iface MIXER  
 		name 'IEC958 Playback Pro Mask'  
 		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000' 
 		comment {  
 			access read  
 			type IEC958  
 			count 1  
 		}  
 	}  
 	control.15 {  
 		iface MIXER  
 		name 'IEC958 Playback Default'  
 		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000' 
 		comment {  
 			access 'read write'  
 			type IEC958  
 			count 1  
 		}  
 	}  
 	control.16 {  
 		iface MIXER  
 		name 'IEC958 Playback Switch'  
 		value false  
 		comment {  
 			access 'read write'  
 			type BOOLEAN  
 			count 1  
 		}  
 	}  
 	control.17 {  
 		iface MIXER  
 		name 'IEC958 Default PCM Playback Switch'  
 		value true  
 		comment {  
 			access 'read write'  
 			type BOOLEAN  
 			count 1  
 		}  
 	}  
 	control.18 {  
 		iface MIXER  
 		name 'Master Playback Volume'  
 		value 52  
 		comment {  
 			access 'read write'  
 			type INTEGER  
 			count 1  
 			range '0 - 64'  
 			dbmin -9999999  
 			dbmax 0  
 			dbvalue.0 -900  
 		}  
 	}  
 	control.19 {  
 		iface MIXER  
 		name 'Master Playback Switch'  
 		value true  
 		comment {  
 			access 'read write'  
 			type BOOLEAN  
 			count 1  
 		}  
 	}  
 	control.20 {  
 		iface CARD  
 		name 'Front Headphone Jack'  
 		value true  
 		comment {  
 			access read  
 			type BOOLEAN  
 			count 1  
 		}  
 	}  
 	control.21 {  
 		iface CARD  
 		name 'Mic Jack'  
 		value false  
 		comment {  
 			access read  
 			type BOOLEAN  
 			count 1  
 		}  
 	}  
 	control.22 {  
 		iface CARD  
 		name 'HDMI/DP,pcm=3 Jack'  
 		value false  
 		comment {  
 			access read  
 			type BOOLEAN  
 			count 1  
 		}  
 	}  
 	control.23 {  
 		iface MIXER  
 		name 'IEC958 Playback Con Mask'  
 		index 1  
 		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000' 
 		comment {  
 			access read  
 			type IEC958  
 			count 1  
 		}  
 	}  
 	control.24 {  
 		iface MIXER  
 		name 'IEC958 Playback Pro Mask'  
 		index 1  
 		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000' 
 		comment {  
 			access read  
 			type IEC958  
 			count 1  
 		}  
 	}  
 	control.25 {  
 		iface MIXER  
 		name 'IEC958 Playback Default'  
 		index 1  
 		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000' 
 		comment {  
 			access 'read write'  
 			type IEC958  
 			count 1  
 		}  
 	}  
 	control.26 {  
 		iface MIXER  
 		name 'IEC958 Playback Switch'  
 		index 1  
 		value true  
 		comment {  
 			access 'read write'  
 			type BOOLEAN  
 			count 1  
 		}  
 	}  
 	control.27 {  
 		iface PCM  
 		device 3  
 		name ELD  
 		value ''  
 		comment {  
 			access read  
 			type BYTES  
 			count 0  
 		}  
 	}  
 	control.28 {  
 		iface MIXER  
 		name 'PCM Playback Volume'  
 		value.0 254  
 		value.1 254  
 		comment {  
 			access 'read write user'  
 			type INTEGER  
 			count 2  
 			range '0 - 255'  
 			tlv '0000000100000008ffffec1400000014'  
 			dbmin -5100  
 			dbmax 0  
 			dbvalue.0 -20  
 			dbvalue.1 -20  
 		}  
 	}  
 	control.29 {  
 		iface MIXER  
 		name 'Digital Capture Volume'  
 		value.0 119  
 		value.1 119  
 		comment {  
 			access 'read write user'  
 			type INTEGER  
 			count 2  
 			range '0 - 120'  
 			tlv '0000000100000008fffff44800000032'  
 			dbmin -3000  
 			dbmax 3000  
 			dbvalue.0 2950  
 			dbvalue.1 2950  
 		}  
 	}  
 }  
 --endcollapse--  
 

 

 !!All Loaded Modules  
 !!------------------  
 

 Module  
 michael_mic  
 arc4  
 dm_crypt  
 snd_hda_codec_hdmi  
 snd_hda_codec_idt  
 hp_wmi  
 sparse_keymap  
 snd_hda_intel  
 snd_hda_codec  
 snd_hwdep  
 uvcvideo  
 videodev  
 snd_pcm  
 ip6t_LOG  
 xt_hl  
 ip6t_rt  
 nf_conntrack_ipv6  
 nf_defrag_ipv6  
 ipt_REJECT  
 ipt_LOG  
 xt_limit  
 snd_seq_midi  
 xt_tcpudp  
 snd_rawmidi  
 psmouse  
 snd_seq_midi_event  
 serio_raw  
 joydev  
 xt_addrtype  
 lib80211_crypt_tkip  
 snd_seq  
 snd_timer  
 snd_seq_device  
 xt_state  
 jmb38x_ms  
 ip6table_filter  
 wl  
 ip6_tables  
 nf_conntrack_netbios_ns  
 nf_conntrack_broadcast  
 memstick  
 nf_nat_ftp  
 nf_nat  
 nf_conntrack_ipv4  
 nf_defrag_ipv4  
 nf_conntrack_ftp  
 nf_conntrack  
 iptable_filter  
 snd  
 cfg80211  
 ip_tables  
 x_tables  
 lib80211  
 soundcore  
 snd_page_alloc  
 btusb  
 ir_lirc_codec  
 lirc_dev  
 ir_mce_kbd_decoder  
 ir_sony_decoder  
 ir_jvc_decoder  
 ir_rc6_decoder  
 ir_rc5_decoder  
 rc_rc6_mce  
 ir_nec_decoder  
 rfcomm  
 bnep  
 ene_ir  
 parport_pc  
 bluetooth  
 ppdev  
 rc_core  
 binfmt_misc  
 mac_hid  
 lp  
 parport  
 i915  
 drm_kms_helper  
 drm  
 r8169  
 sdhci_pci  
 sdhci  
 i2c_algo_bit  
 wmi  
 usbhid  
 hid  
 video  
 

 

 !!Sysfs Files  
 !!-----------  
 

 /sys/class/sound/hwC0D0/init_pin_configs: 
 0x0a 0x0221201f  
 0x0b 0x02a12020  
 0x0c 0x95a79330  
 0x0d 0x90170110  
 0x0e 0x40f000f0  
 0x0f 0x40f000f2  
 0x14 0x40f000f3  
 0x18 0x40f000f4  
 0x19 0x40f000f5  
 0x1e 0x014411a0  
 0x1f 0x40f000f6  
 0x20 0x40f000f7  
 0x27 0x40f000f0  
 

 /sys/class/sound/hwC0D0/driver_pin_configs: 
 0x0d 0x90170010  
 

 /sys/class/sound/hwC0D0/user_pin_configs: 
 

 /sys/class/sound/hwC0D0/init_verbs:  
 

 /sys/class/sound/hwC0D0/hints:  
 

 /sys/class/sound/hwC0D1/init_pin_configs: 
 

 /sys/class/sound/hwC0D1/driver_pin_configs: 
 

 /sys/class/sound/hwC0D1/user_pin_configs: 
 

 /sys/class/sound/hwC0D1/init_verbs:  
 

 /sys/class/sound/hwC0D1/hints:  
 

 /sys/class/sound/hwC0D2/init_pin_configs: 
 0x03 0x18560010  
 

 /sys/class/sound/hwC0D2/driver_pin_configs: 
 

 /sys/class/sound/hwC0D2/user_pin_configs: 
 

 /sys/class/sound/hwC0D2/init_verbs:  
 

 /sys/class/sound/hwC0D2/hints:  
 

 

 !!ALSA/HDA dmesg  
 !!--------------  
 

 [   33.094431] type=1400 audit(1388901962.175:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=961 comm="apparmor_parser"  
 [   33.109800] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D0  
 [   33.109812] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D0  
 [   33.109823] snd_hda_intel 0000:00:1b.0: PCI INT B -> GSI 22 (level, low) -> IRQ 22  
 [   33.109927] snd_hda_intel 0000:00:1b.0: irq 49 for MSI/MSI-X  
 [   33.109972] snd_hda_intel 0000:00:1b.0: setting latency timer to 64  
 [   33.125589] r8169 0000:04:00.0: eth0: link down  
 --  
 [   33.224450] input: HP WMI hotkeys as /devices/virtual/input/input12  
 [   33.257565] HDMI status: Codec=2 Pin=3 Presence_Detect=0 ELD_Valid=0  
 [   33.257861] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13 
 [   33.258059] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14  
 [   33.258239] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15  
 [   33.275289] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:  
 

 

 

 venkat@venkat-laptop:~$

---

