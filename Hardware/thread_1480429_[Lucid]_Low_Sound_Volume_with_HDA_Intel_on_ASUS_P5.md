---
title: "[Lucid] Low Sound Volume with HDA Intel on ASUS P5GC-MX/1333 Board"
date: 2010-05-11
forum: Hardware
---

### Post by deepclutch on 2010-05-11
Hi ,
My PC's Motherboard is ASUS P5GC-MX/1333 with onboard ALC662 ICH7 HDA  Sound card.

From the past few releases of Ubuntu(including 9.10,9.04 etc IIRC) ,Very Low Volume Output is the Issue.

some infos:
```
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at dddf8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
``````
root@linbox:~# cat /proc/asound/card0/codec#0 |grep Codec
Codec: Realtek ALC662 rev1

``````
root@linbox:~# dmesg | grep HDA 
[    9.307535] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    9.307613] HDA Intel 0000:00:1b.0: irq 27 for MSI/MSI-X
[    9.307639] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.433544] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[ 7186.331355] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 7186.350034] PM: freeze of drv:HDA Intel dev:0000:00:1b.0 complete after 121.406 msecs
[ 7186.811625] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[ 7186.841698] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 7186.841705] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 7186.841744] HDA Intel 0000:00:1b.0: irq 27 for MSI/MSI-X
[ 7186.981033] PM: restore of drv:HDA Intel dev:0000:00:1b.0 complete after 139.353 msecs
```--
I already tried adding below line to /etc/modprobe.d/alsa-base.conf

```
options snd-hda-intel model=auto
```Still ,there is no improvement in default sound output.
the /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz shows below options for snd-hda-intel module.
```
ALC662/663/272
==============
  3stack-dig    3-stack (2-channel) with SPDIF
  3stack-6ch     3-stack (6-channel)
  3stack-6ch-dig 3-stack (6-channel) with SPDIF
  6stack-dig     6-stack with SPDIF
  lenovo-101e     Lenovo laptop
  eeepc-p701    ASUS Eeepc P701
  eeepc-ep20    ASUS Eeepc EP20
  ecs        ECS/Foxconn mobo
  m51va        ASUS M51VA
  g71v        ASUS G71V
  h13        ASUS H13
  g50v        ASUS G50V
  asus-mode1    ASUS
  asus-mode2    ASUS
  asus-mode3    ASUS
  asus-mode4    ASUS
  asus-mode5    ASUS
  asus-mode6    ASUS
  dell        Dell with ALC272
  dell-zm1    Dell ZM1 with ALC272
  samsung-nc10    Samsung NC10 mini notebook
  auto        auto-config reading BIOS (default
```^As regarding **asus-mode1**...etc How do I figure Out which option will work with p5gc-mx/1333 board.

There is no ~/.asoundrc ...etc files in the system.

Help needed

Thanks.

---

### Post by lidex on 2010-05-13
You simply have to try them and see. I know that mode-3 works for asus ALC663. Also use gnome-alsamixer and enable everything in 'Edit>Sound Card Properties'. Go back to the soundcard tab and look for an external amplifier switch and toggle settings there.

Alsamixer is also helpful. ```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

Do this for me please. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by deepclutch on 2010-05-13
Thanks @lidex.
First ,alsa-info.sh output-Here is the O/p uploaded :

[http://pastebin.com/K9HGt6VM](http://pastebin.com/K9HGt6VM)



 I've tried few solutions recommended.
includes a python script from alsa-project called "hda-analyzer" which allows audio_out be increased.I tried that  ,still the volume is felt a little less.

I've ~/.asoundrc with below lines:
```
pcm.hda-intel {
    type hw
    card 0
}
       
ctl.hda-intel {
   type hw
   card 0
}

```I've tried quiet a fix.but ,without knowing the correct  module parameter for P5GC-MX/1333 's ALC662 HDA ,what to do?
I tried few module parameters for snd-hda-intel and last try was "options snd-hda-intel model=3stack-6ch" for which below warnings!:
```
WARNING: /etc/modprobe.d/alsa-base.conf line 45: ignoring bad line starting with 'options-snd-hda-intel' 
WARNING: /etc/modprobe.d/alsa-base.conf line 45: ignoring bad line starting with 'options-snd-hda-intel' 
WARNING: /etc/modprobe.d/alsa-base.conf line 45: ignoring bad line starting with 'options-snd-hda-intel' 
WARNING: /etc/modprobe.d/alsa-base.conf line 45: ignoring bad line starting with 'options-snd-hda-intel'
```^is compalining about the line in /etc/modprobe.d/alsa-base.conf 's 
line (retrived from /var/log/boot.log) 


I've below lines in /etc/modprobe.d/alsa-base.conf :
```
#HDA ICH7 ALC662
# ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-hda-intel

options snd slots=snd-hda-intel
options snd-hda-intel index=0
options-snd-hda-intel model=3stack-6ch
```Is there any documentation for what asus-mode1..2...etc is for with regards to snd-hda-intel ?

Thanks

---

### Post by TheStroj on 2010-05-13
I had this low sound too, but I managed to solve everything by using Alsamixer and some PulseAudio programs i cant remember good.

I don't know if this simple solution will work but at top right of the screen theres volume button set at 100%, just make it 200% or whatever number you want.

If nothing of stuff written in other comments will work, you can use program like VLC to increase the sound output - making the 100% to 100%+ (i do not really recommend it but i used it too and got used to it pretty fast).

---

### Post by lidex on 2010-05-13
OK, try this. First remove any/all custom entries in alsa-base.conf then use the alsa upgrade script link in my sig to upgrade to latest version.

---

### Post by deepclutch on 2010-05-14
> **lidex said:**
> OK, try this. First remove any/all custom entries in alsa-base.conf then use the alsa upgrade script link in my sig to upgrade to latest version.
Hi ,
I think latest version of ALSA(release  version) 1.0.23 - Will it came with any fix particular to HDA Audio?
[http://alsa-project.org/main/index.php/Changes_v1.0.22_v1.0.23#HDA_Codec_driver](http://alsa-project.org/main/index.php/Changes_v1.0.22_v1.0.23#HDA_Codec_driver)

I've installed using that Script in earlier Ubuntu (as well as manually installed) version.but never felt any difference.such an update will be useful for users with newest chipsets(audio).

Still ,I will compile a alsa module for the kernel when alsa-source 1.0.23 is available for sure.
--
As of Now,there is good progress:
If I turn the speaker volume to bare minimum(the knob to the extreme left) and have the pulse audio/volume controls to the maximum ,the output is still good enough.:) ,but I've a feeling that the Volume is still a li'l bit low.Will have to figure out(for that ,I started this thread)

What Worked for Me is ,using the python script provided by ALSA HDA developers: "hda-analyzer".
[http://www.alsa-project.org/main/index.php/Help_To_Debug_Intel_HDA](http://www.alsa-project.org/main/index.php/Help_To_Debug_Intel_HDA)
[http://www.alsa-project.org/main/index.php/HDA_Analyzer](http://www.alsa-project.org/main/index.php/HDA_Analyzer)

I ran it earlier itself and it unmuted front audiio_out in particular.there is a very notable difference in Volume Output.when I earlier tried ALSAMIXER,it showed full volume,but sound o/p was low.so ,hda-analyzer helped.Here is a Screenshot with the circled area showing where I unmuted and increased volume to Maximum.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=156912&stc=1&d=1273849318[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=156911&stc=1&d=1273849318[/IMG]

Thanks to All,especially @lidex for your helping hand.
But,I will mark this thread solved after trying Alsa-1.0.23 

Thanks to All

---

### Post by deepclutch on 2010-05-17
I removed,purged pulseaudio packages installed.and on next boot ,without pulseaudio ,there is a noticeably more sound output on the same volume slider!So ,Pulseaudio is playing pranks?:) 

What is the correct solution?Do I be content with installing esd(Enlightened Sound Daemon) in Ubuntu Gnome?

Is there any other Mutli-audio sound servers like Pulse without this "low volume" problem?

Thanks.

---

### Post by lidex on 2010-05-17
ESD should already be installed. Is this a premade PC and if so what is make/model?
Did you remove those entries from alsa-base.conf?
Did you upgrade alsa?

---

### Post by deepclutch on 2010-05-25
> **lidex said:**
> ESD should already be installed. Is this a premade PC and if so what is make/model?
Did you remove those entries from alsa-base.conf?
Did you upgrade alsa?
It is a assembled Computer by Me. Motherboard Asus P5GC-MX/1333 with HDA Audio(ALC662).
Yes,Alsa is upgraded to 1.0.23(from ricotz repository,no scripts!)

Currently,the sound output is almost equivalent to a similar configuration Windows PC.

I used Pulseaudio again!here's /etc/asound.conf(It is already sourced at /usr/share/alsa/pulse-alsa.conf ) 
with ALSA Dmix ,The Sound Output is slightly More.

Thanks.

---

### Post by sreejiraj on 2010-07-12
I just bought a Sony Vaio VPCEB 26 FG and installed lucid on it. 

Did a full upgrade, but the issue remains.

Downloading the analyser and resetting Pin 19 works. But it is not persistent through rebooting.

As always, I have a debian testing installation beside it and there, alsa is on version 23, which's supposed to fix the issue. But it doesn't. However, here, the change is persistent. I don't have to run the hda analyser script every time I reboot. I am using the 2.6.34 kernel on my Debian from a third party website.

Thanks.

---

### Post by sreejiraj on 2010-07-18
Just found out that the audio is present more because of the kernel I am using (2.6.34) from liquorix.net rather than any tinkering with analyser.

I also noticed that the same kernel has out of the box support for my vaio vpceb26fg audio, but not so on Sabayon (gentoo). The issue seems to be the presence of multiple audio cards? The system also has an hdmi port.

---

### Post by sreejiraj on 2010-07-18
Just found out that the audio is present more because of the kernel I am using (2.6.34) from liquorix.net rather than any tinkering with analyser.

I also noticed that the same kernel has out of the box support for my vaio vpceb26fg audio on opensuse 11.3, but not on Sabayon (gentoo). The issue seems to be the presence of multiple audio cards? The system also has an hdmi port.

---

