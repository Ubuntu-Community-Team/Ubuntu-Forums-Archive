---
title: "Sound Device Not Working"
date: 2004-11-13
forum: Hardware &amp; Laptops
---

### Post by Crisp on 2004-11-13
Hi

I recently installed Ubuntu, and everything has gone great.  The only thing I havn't got working yet is my sound.  Now, I'm playing a CD with CD Player to test this out, and I have the Volume Control open.  The four tabs are as follows:

RealTek ALC650 rev 3 [OSS Mixer]
CMedia PCI [OSS Mixer]
NVidia nForce2 [Alsa Mixer]
C-Media PCI CMI8738 [Alsa Mixer]

I tried all the obvious things like unmuting and putting the sliders up to full volume etc, but it did nothing.  It seems like it must be a driver issue then.  I have no problems which sound device I use, as long as I get sound, and interestingly the sound worked fine on the LiveCD.  Hopefully it wont be too hard to work out.

I realise I've given limited information here, so if you need any extra just ask and I'll provide.  Hopefully someone can help me sort this out.

-Crisp

---

### Post by Crisp on 2004-11-14
[QUOTE=Crisp]Hi

I recently installed Ubuntu, and everything has gone great.  The only thing I havn't got working yet is my sound.  Now, I'm playing a CD with CD Player to test this out, and I have the Volume Control open.  The four tabs are as follows:

RealTek ALC650 rev 3 [OSS Mixer]
CMedia PCI [OSS Mixer]
NVidia nForce2 [Alsa Mixer]
C-Media PCI CMI8738 [Alsa Mixer]

I tried all the obvious things like unmuting and putting the sliders up to full volume etc, but it did nothing.  It seems like it must be a driver issue then.  I have no problems which sound device I use, as long as I get sound, and interestingly the sound worked fine on the LiveCD.  Hopefully it wont be too hard to work out.

I realise I've given limited information here, so if you need any extra just ask and I'll provide.  Hopefully someone can help me sort this out.

-Crisp[/QUOTE]
 Anyone?  Just a push in the right direction...

---

### Post by Crisp on 2004-11-14
crisp@benson:~ $ lspci
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
0000:00:05.0 Multimedia audio controller: nVidia Corporation nForce MultiMedia audio [Via VT82C686B] (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:0c.0 PCI bridge: nVidia Corporation nForce2 PCI Bridge (rev a3)
0000:00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
0000:01:06.0 Communication controller: Intel Corp. 536EP Data Fax Modem
0000:01:07.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
0000:01:09.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:02:01.0 Ethernet controller: 3Com Corporation 3C920B-EMB Integrated Fast Ethernet Controller [Tornado] (rev 40)
0000:03:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)

---

### Post by Juergen on 2004-11-15
I have no real help to offer, but maybe the info for this driver on the alsa-hompage helps: [http://makeashortlink.de/?yovuruwe](http://makeashortlink.de/?yovuruwe)

---

### Post by louisamaus on 2004-11-20
My CM8738 now works !!!  Yeaaahhhhhh  \\:D/ 

A Tip from Rodney, thanks:

you need to type " su " minus the quotes, hit enter
then your password
then I would type " alsaconf " hit enter
after it has found your soundcard type " alsamixer " hit enter
set your levels using the m key to un-mute and the up/down arrows for volume levels
once your happy type " alsactl store " hit enter
this will save your settings

---

### Post by gitano1 on 2004-11-22
Louisamaus, I have a Soundblaster Awe64 soundcard which is also not responding. Do your instructions above work for that card. 
Also since I am totally new to this system a few more specifics: 
Where do you type in the "su" and password? Are they typed in a command screen?

---

### Post by bob k on 2004-11-22
[QUOTE=gitano1]Louisamaus, I have a Soundblaster Awe64 soundcard which is also not responding. Do your instructions above work for that card. 
Also since I am totally new to this system a few more specifics: 
Where do you type in the "su" and password? Are they typed in a command screen?[/QUOTE]
 You have to open a terminal window. if it is not your task bar just right click anywhere on the background and select open terminal and that will give you the command line interface.

---

### Post by gitano1 on 2004-11-22
Thanks, Bob. I will give it a shot.

---

### Post by gitano1 on 2004-11-22
New problem. This is the first time I opened a terminal window. I typed in "su" was asked for a password. I typed the only password I have used. The cursor did not move. After a brief pause I was denied entry. Is there something I am missing. My understanding from the information in the install program was that there was only one profile initially installed in the system, and that the password for that profile would work for administrative functions. Is there some form of administrative default password that I am missing?

---

### Post by duff on 2004-11-22
[QUOTE=gitano1]New problem. This is the first time I opened a terminal window. I typed in "su" was asked for a password. I typed the only password I have used. The cursor did not move. After a brief pause I was denied entry. Is there something I am missing. My understanding from the information in the install program was that there was only one profile initially installed in the system, and that the password for that profile would work for administrative functions. Is there some form of administrative default password that I am missing?[/QUOTE]

If I need to perform multiple commands as root, I usually just "sudo sh".  But if you want to actually set the root password, I beleive "sudo passwd" should let you set it.

---

### Post by gitano1 on 2004-11-26
All right, I got the root password set up. Thank you for that help, but I am getting no where when I try to get sound. I used the "alsaconf" and got  back no such command. 
when I ran Alsamixer I got this message: 
alsamixer: function snd_ctl_open failed for default: no such file or directory.

I saw alsamixer in the boot-up listing, so I know it is in there somewhere. Any help on getting this thing resolved would be greatly appreciated. So far this is the only thing I can't get to work on this system. #-o

---

### Post by gitano1 on 2004-11-28
The problem continues. I watched the boot up sequence carefully and this time I saw the Alsamixer installed. There was a note that followed, No sound card found. Any tips on how to get Ubuntu to recognize my sound card on boot?

---

### Post by ruwach on 2004-12-08
its been a while since your post so you may have already gotten this thing figgured out. but if not, try this.
open a root terminal
after providing the password,
 type in modprobe snd_emu10k1
then modprobe soundcore
 
let us know !

---

### Post by gitano1 on 2004-12-08
I gave it a shot and got a panel full of error messages.

---

### Post by SoS on 2004-12-09
[QUOTE=gitano1]There was a note that followed, No sound card found. Any tips on how to get Ubuntu to recognize my sound card on boot?[/QUOTE]
alsactl : load_state  : 1134 : No soundcard found
I have the same problem too, can't get the sound working if Ubuntu thinks that I don't even have a soundcard :neutral:

---

### Post by gitano1 on 2004-12-11
Apparently there is a newer version of Alsa available which does recognize a larger range of soundcards. However you have to install the entire kernel to get it to work properly. I am in the process of learning how to do that. Being a newby to Linux is definitely a strange feeling. I am pretty cocky around my Windows machines. This is humbling.  ](*,)

---

### Post by mdmcginn on 2005-03-27
I have some of the same symptoms as others with no sound (only system beeps):

root@ubuntu:/home/michael # alsa
bash: alsa: command not found
root@ubuntu:/home/michael #
root@ubuntu:/home/michael # alsa-base
bash: alsa-base: command not found
root@ubuntu:/home/michael # alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
root@ubuntu:/home/michael # modprobe snd_emu10k1
(nothing happened here)
root@ubuntu:/home/michael # alsaconf
bash: alsaconf: command not found
root@ubuntu:/home/michael # modprobe snd_EMU10K1
FATAL: Module snd_EMU10K1 not found.
root@ubuntu:/home/michael #

Yet alsa etc. has been installed, including EMU10K1.conf. Sound is beautiful on Windows 98. The boot message says no sound card detected.

---

### Post by mercurus on 2005-03-28
I own a Creative SB Audigy 2 Value card which was not supported until kernel version 2.6.11. Once the emu10k1 driver was updated I was all set ... all I can suggest is to read the HOWTOs on kernel compilation under Ubuntu and give it a shot on a non-mission-critical system. I imagine there are more up to date kernel image packages available for Warty than 2.6.8.1 ... I'm not completely sure where one would obtain them.

Is there an existing kernel repository that I don't know about (nothing in universe later than 2.6.8.1), where ?
If not, drop me a message and I'll compile a vanilla 2.6.11.2 kernel with the Warty standard config file for anyone who may be in a pickle ... alternatively ... Hoary might be the go ... not sure which kernel version it uses.

Cheers
mercurus

---

### Post by mdmcginn on 2005-03-28
My Hoary uses 2.6.10-5.386. It still doesn't recognize my soundcard. This is a pretty old laptop, something like a Compaq Armada 4220. The soundcard is ES1878 (ESS).

---

### Post by mdmcginn on 2005-03-31
A discussion on [http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?act=Print;f=6;t=4226](http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?act=Print;f=6;t=4226)
recommended 
modprobe sb16 io=0x22 irq=5 dma=1 esstype=1878

but dmesg got 
ESS AudioDrive ES18XX soundcard not found or device busy

And I also tried 
modprobe snd_ess18xx enable=1 isapnp=0 port =0x220 mpu_port=0x330 dma1=1 dma2=5 irq=5 fm_port=0x388
but I got 
FATAL: Error inserting snd_es18xx (/lib/modules/2.6.10-5-386/kernel/sound/isa/snd-es18xx.ko): No such device.

I also have seen FATAL: Module sb16 not found.
Do I need to wait for a new kernel for Hoary?

---

### Post by ploum on 2005-04-09
I've the same problem on an old Compaq Pressario ( [http://ubuntuforums.org/showthread.php?t=24916](http://ubuntuforums.org/showthread.php?t=24916) )

Sound was really great in Warty.

I've tried with the Warty Kernel, without success :-( (it doesn't change anything)

So it's not a kernel issue.

---

### Post by Tiede on 2005-08-09
If you are under Warty, try wat is said in [ here ](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards)
(Basically, it amounts to loading the module snd_sbawe by yourself. It should be really easy ;)
If this still does not work, go in your BIOS, and change the Plug& Play Aware OS option to No (Don' t worry, PnP will still work)

If you are under Hoary though, I am afraid I cannot offer much help, as I am having problems with my SoundBlaster Awe64 card too :(

---

### Post by 3kravinarayan on 2006-12-01
I HAVE REad IT ALL HERE.

my mike is not working, contacts seem fine. speakers are working though.

my sound card is CM8738. 2 days ago, with windows it was fine. what is it tht i ned to do to get the mike working.

video player also is not working. says decoder and plugins are needed. which are these, and wherefrom do i get them

pl help

Regards

Ravi          waiting  for a :-D

---

### Post by Tiede on 2006-12-02
>For your microphone problem go to System -> Preferences-> Sound, and make sure the correct input device is selected. Also, double click the volume icon to make sure the right device is used.

>For the video player warnings, read the [ wiki entry about Restricted Formats](https://help.ubuntu.com/community/RestrictedFormats).

---

