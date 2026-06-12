---
title: "Realtek ALC883 Sound Card not working"
date: 2011-04-19
forum: Hardware
---

### Post by vikrang on 2011-04-19
I am not able to get any sound when I try the Live CD of Ubuntu or any Linux distro for that matter...My Desktop speakers work only with WIN ..... Is there any driver which has to be downloaded ?
 
Pl assist !

---

### Post by TBABill on 2011-04-19
[http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt) > ALC882/883/885/888/889
======================
  3stack-dig	3-jack with SPDIF I/O
  6stack-dig	6-jack digital with SPDIF I/O
  arima		Arima W820Di1
  targa		Targa T8, MSI-1049 T8
  asus-a7j	ASUS A7J
  asus-a7m	ASUS A7M
  macpro	MacPro support
  mb5		Macbook 5,1
  macmini3	Macmini 3,1
  mba21		Macbook Air 2,1
  mbp3		Macbook Pro rev3
  imac24	iMac 24'' with jack detection
  imac91	iMac 9,1
  w2jc		ASUS W2JC
  3stack-2ch-dig	3-jack with SPDIF I/O (ALC883)
  alc883-6stack-dig	6-jack digital with SPDIF I/O (ALC883)
  3stack-6ch    3-jack 6-channel
  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
  6stack-dig-demo  6-jack digital for Intel demo board
  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
  acer-aspire	Acer Aspire 9810
  acer-aspire-4930g Acer Aspire 4930G
  acer-aspire-6530g Acer Aspire 6530G
  acer-aspire-7730g Acer Aspire 7730G
  acer-aspire-8930g Acer Aspire 8930G
  medion	Medion Laptops
  targa-dig	Targa/MSI
  targa-2ch-dig	Targa/MSI with 2-channel
  targa-8ch-dig Targa/MSI with 8-channel (MSI GX620)
  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
  lenovo-101e	Lenovo 101E
  lenovo-nb0763	Lenovo NB0763
  lenovo-ms7195-dig Lenovo MS7195
  lenovo-sky	Lenovo Sky
  haier-w66	Haier W66
  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)
  6stack-dell	Dell machines with 6stack (Inspiron 530)
  mitac		Mitac 8252D
  clevo-m540r	Clevo M540R (6ch + digital)
  clevo-m720	Clevo M720 laptop series
  fujitsu-pi2515 Fujitsu AMILO Pi2515
  fujitsu-xa3530 Fujitsu AMILO XA3530
  3stack-6ch-intel Intel DG33* boards
  intel-alc889a	Intel IbexPeak with ALC889A
  intel-x58	Intel DX58 with ALC889
  asus-p5q	ASUS P5Q-EM boards
  mb31		MacBook 3,1
  sony-vaio-tt  Sony VAIO TT
  auto		auto-config reading BIOS (default)

 
Without knowing anything about your machine, this will be very generic. The info above that I quoted is from that link. It is a list of different options for your ALC883 chipset. What you can do is find something in that list closest to your machine and try the following:
 
1. Open /etc/modprobe.d/alsa-base.conf by doing ```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
 
2. Add this line to the end of the list and place # in front of the current last line of that file (so it will be ignored) ```
options snd-hda-intel model=xxxxxx
```
 
3. I used "xxxxxx" because that is what you will replace in that line with each attempt from the quoted info above. For example, if you had an Acer you could start your first try with "options snd-hda-intel model=acer" and try different ones until you get the one that works.
 
4. Each time you try one, save the file and restart. If it works, great, if not, move to the next closest. Try them all even if your brand is different than the one listed. 
 
Good luck!

---

### Post by vikrang on 2011-04-20
OMG !!! That involves quite some work!
 
Actually the Realtek ALC883 came onboard with GIGABYTE Mother Board -- Intel Dual Core 2.5 Mhz ..(Socket 775 I -guess not sure)
 
Can I eliminate the branded ones listed above since mine is an assembled PC?

---

### Post by TBABill on 2011-04-20
It's not terribly difficult, but yes it takes some time for sure. You could eliminate whatever you want, but you could also find that one that is =dell, for example, may work for yours even though it is not branded. There is also the "auto" option at the end of the list and it's pretty much just trial and error. Sorry I can't give more specific info, but each machine is different and the possibilities are any on that list.

---

### Post by lidex on 2011-04-21
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by vikrang on 2011-04-21
Thanks ...I am still sort of struggling with this driver...lidex I will also post the result of the command u have given...Meanwhile if the results below would be of any help in sorting out the problem , pl do let me know
 
[FONT=Courier New][FONT=Verdana][SIZE=1]**lspci -v | grep -i audio**[/SIZE][/FONT]
 
[SIZE=1][FONT=Courier New]00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)[/FONT][/SIZE]
 
 
[/FONT] 
**cat /dev/sndstat**
 
Installed drivers: 
Type 10: ALSA emulation
 
Card config: 
HDA Intel at 0xe1280000 irq 16
 
Audio devices: NOT ENABLED IN CONFIG
 
Synth devices: NOT ENABLED IN CONFIG
 
Midi devices: NOT ENABLED IN CONFIG
 
Timers:
31: system timer
 
Mixers: NOT ENABLED IN CONFIG
 
**tail /var/log/messages**
 
Apr 21 08:58:42 localhost kernel: [ 2241.532203] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
Apr 21 08:59:15 localhost kernel: [ 2275.264712] HDA Intel 0000:00:1b.0: PCI INT A disabled
Apr 21 08:59:16 localhost kernel: [ 2275.433817] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 21 08:59:16 localhost kernel: [ 2275.501917] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input11
Apr 21 09:00:07 localhost kernel: [ 2327.028708] HDA Intel 0000:00:1b.0: PCI INT A disabled
Apr 21 09:00:36 localhost kernel: [ 2355.797634] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 21 09:00:36 localhost kernel: [ 2355.860200] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input12
Apr 21 09:02:04 localhost kernel: [ 2444.269148] HDA Intel 0000:00:1b.0: PCI INT A disabled
Apr 21 09:02:48 localhost kernel: [ 2487.500728] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 21 09:02:48 localhost kernel: [ 2487.564200] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input1
 
[FONT=Courier New][/FONT]

---

### Post by mastablasta on 2011-04-21
the card seems to be recognise, but i am not sure why it is disabled. alsda info script should say more on what is happening.
 
not sure if you know but to run commands you can copy & paste them into the terminal.

---

### Post by vikrang on 2011-04-21
Lidex , Here you go , this is the output I got

root@ubuntu:~# wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
--14:50:02--  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
           => `alsa-info.sh'
Resolving [www.alsa-project.org](www.alsa-project.org)... 77.48.224.243
Connecting to [www.alsa-project.org|77.48.224.243|:80](www.alsa-project.org|77.48.224.243|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) [following]
--14:50:03--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)
           => `alsa-info.sh'
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to [www.alsa-project.org:80](www.alsa-project.org:80).
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]

    [    <=>                              ] 27,247        27.16K/s             

14:50:07 (27.13 KB/s) - `alsa-info.sh' saved [27247]

ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : y
Uploading information to [www.alsa-project.org](www.alsa-project.org) ...  Done!

Your ALSA information is located at [http://www.alsa-project.org/db/?f=0f26d5ed6d371cea4f2be9b92219b54dbcb60bb1](http://www.alsa-project.org/db/?f=0f26d5ed6d371cea4f2be9b92219b54dbcb60bb1)

Please inform the person helping you.

---

### Post by Yellow Pasque on 2011-04-21
You're running an old version of Ubuntu (8.04) that's about to go EOL. What version was on the LiveCD you tried?

---

### Post by lidex on 2011-04-21
I'd advise backing up your data and wiping your old install. Next install lucid or maverick and if no audio then the likely entry in alsa-base.conf:
```
options snd-hda-intel model=clevo-m540r
```

---

### Post by vikrang on 2011-04-22
[SIZE=3]FANTASTIC!!!!! [/SIZE]


[SIZE=3]Thx Lidex its working Now  [/SIZE]:guitar:


[SIZE=2]To sum up for the benefit of other users

1. I used Linux Mint 10.10 (GNOME) Live DVD-- Guess it is Maverick makeover

2. I removed pulse audio (apt-get remove pulseaudio)

3. From terminal type gconf-editor

4. Go to System --->gstreamer---->0.10--->default

5. Change audiosink value to "alsasink"

6.change musicaudiosink to "alsasink"

(Terminal as Root)

7. lsof /dev/snd/*

8.. Kill "****" (the respective PIDs)

9. rmmod snd-hda-intel <Enter>
       modprobe snd-hda-intel model=clevo-m540r 

(Luckily this model worked for my card ..Else try to substitute different models in "model=" line as suggested in ALSA matrix  [http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt) 

(  Repeat steps 7 to 11 till u get sound)

10 make sure all channels are unmuted by running "alsamixer" (press"M" to toggle and raise the volume)

11. Open ur favorite mp3 file from ur favorite music player (or use some test command of ALSA)

12. say 3 cheers to Lidex

13. Enjoy!![/SIZE] :D

[B]Note : To make the changes permanent in a HDD install please add the Options snd-hda-intel model=clevo-m540r" line to /etc/modprobe.d/alsa-base.conf as suggested by lidex.
[/B]

---

### Post by dashwani on 2012-03-02
Hi,

I am also facing problem of sound (it does not play sound). I am using Ubuntu 10.04 LTS on my dell Vostro A840. Here is the specs:

[http://www.dell.com/us/en/bpi/notebooks/laptop-vostro-a840/pd.aspx?refid=laptop-vostro-a840&s=bpi](http://www.dell.com/us/en/bpi/notebooks/laptop-vostro-a840/pd.aspx?refid=laptop-vostro-a840&s=bpi)

I tried to run alsi website commends which shows that No soundcard detected. But it was workinf well some months ago in Ubuntu 11. But now i downgraded to remove this problem but still it does not work.

From vikrang suggestion, I reached at point 6 but after that i did not understood what to do?

Please help.....missing many important skype meeting.

Deepak

---

