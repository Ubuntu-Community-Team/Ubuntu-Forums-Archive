---
title: "Sound card not reconized!"
date: 2009-06-22
forum: Hardware
---

### Post by netvamp on 2009-06-22
**No Sound Card Detected! &no volume controll!** 			
 			 			 		   		 		 		[FONT=Arial]Okay so i have a soundblaster x-fi xtreamgamer _mod#sb0730_ i installed a driver from alsa site  _(snd-ctxfi)_ and got sound to work finally. My issue is that my sound is at max blasting my ears off all the time. I can adjust the sound through a site like youtube from a in site players controlls but my Ubuntu master controll doesnt work. So i typed alsamixer in terminal and got this 
 alsamixer
 alsamixer: function snd_ctl_open failed for default: No such file or directory
 So i tried a few other commands to figure out some more detailed info i got from forums like thus:
 lspci -v | less
 Memory at d3200000 (32-bit, non-prefetchable) [size=512]
         [virtual] Expansion ROM at f0000000 [disabled] [size=512K]
         Capabilities: <access denied>
         Kernel driver in use: sata_sil
 
 04:04.0 Mass storage controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
         Subsystem: Super Micro Computer Inc Device 3112
         Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 27
         I/O ports at 4048 [size=8]
         I/O ports at 403c [size=4]
         I/O ports at 4040 [size=8]
         I/O ports at 4038 [size=4]
         I/O ports at 4010 [size=16]
         Memory at d3200400 (32-bit, non-prefetchable) [size=512]
         [virtual] Expansion ROM at f0080000 [disabled] [size=512K]
         Capabilities: <access denied>
         Kernel driver in use: sata_sil
 
 [U]05:01.0 Multimedia audio controller: Creative Labs SB X-Fi
         Subsystem: Creative Labs Device 0031
         Flags: bus master, medium devsel, latency 64, IRQ 16
         I/O ports at 5000 [size=32][/U]
 :
 
 and got the above
 another command:
 lspci | grep audio
 _05:01.0 Multimedia audio controller: Creative Labs SB X-Fi_
 
 but if i type:
 cat /proc/asound/cards
 --- no soundcards ---       
 and one more to help
 i typed and got:
 lsmod | grep intel
 intel_agp              34108  1 
 intel_rng              12672  0 
 agpgart                42696  2 nvidia,intel_agp
 
So i have sound but no controll i have done so many things i cant remeber to fix sound still blares. And its saying doesnt reconize soundcard so i cant use alsamixer commands or alsaconf even.
 I am a super noob with ubuntu/linux so please help me. Im using _Ubuntu 9.04 32bit_. On a custum built comp with supermicro motherboard.
 Thankyou for all your soon to come help:smile:
 
 p.s. sorry for my bad spelling and document struture im exhausted...

ive come up with a few more commands=Info that i think will help:
aplay -l
aplay: device_list:217: no soundcards found...

and:
uname -r
2.6.28-13-generic

and:
uname -a
Linux netvamp-command 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 i686 GNU/Linux

hope all this is sufficant to help.


[/FONT]

---

### Post by netvamp on 2009-06-22
Here is another command output that may be usefull:
lshw -c sound
  *-multimedia            
       description: Multimedia audio controller
       product: SB X-Fi
       vendor: Creative Labs
       physical id: 1
       bus info: pci@0000:05:01.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=oss_sbxfi latency=64 maxlatency=5 mingnt=4 module=oss_sbxfi


 Also just because im unsure if i clarified my goal and purpurse to getting my soundcard reconized is to be able to controll my volume which is at a maxed out level very loud all the time. I hoping once sound card is identified that alsamixer will config and work or whatever. and here is what i get from alsamixer at this time:
 alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory

those commands are from root. Sudo commands.
thanks.
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=7501301") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=7501301")

---

