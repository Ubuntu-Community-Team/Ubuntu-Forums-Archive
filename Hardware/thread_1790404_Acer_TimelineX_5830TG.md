---
title: "Acer TimelineX 5830TG"
date: 2011-06-25
forum: Hardware
---

### Post by rojakcoder on 2011-06-25
Hi,

I've got a Acer TimelineX 5830TG. Installed 11.04 64 bit with no problem.

Posted the driver woes [here]("http://ubuntuforums.org/showthread.php?t=1543006&page=69").

However, I still have a problem with the speakers not producing any sounds. I can hear the sounds if I have an external speaker plugged in but the sounds do not come out of the built-in speakers.

Appreciate any advice.

Output of lspci is below:

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev a1)
02:00.0 Ethernet controller: Atheros Communications Device 1083 (rev c0)
03:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
04:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
05:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)

---

### Post by rojakcoder on 2011-06-27
*bump*

---

### Post by rojakcoder on 2011-07-05
Anyone with some clue?

---

### Post by pointym5 on 2011-07-09
What do you see when you run the sound preferences app in the "Hardware" and "Output" tabs?  In the output tab, do you get a choice for whether output is on the headphone jack or the speakers?

---

### Post by pull_ya on 2011-07-13
Hi
I had the same problem.
Solution here 
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/783582](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/783582)

"...
The loud speakers of my 5830TG are working thanks to the HDAAnalyzer tool : [http://www.alsa-project.org/main/index.php/HDA_Analyzer](http://www.alsa-project.org/main/index.php/HDA_Analyzer)
Once the tool is installed, the option EAPD in Node[0x1b] must be enabled.
..."

---

### Post by pointym5 on 2011-07-14
Thanks for that link. Unfortunately, it's almost impossible to understand what's going on there, and certainly none of those things that I've tried have had any effect at all.  Is there some sort of concise, organized explanation of what needs to be done to a stock 11.04 installation in order to make the audio work (on one of these TimelineX machines)?

*edit* - actually I take that back - the .deb patch mentioned at comment #76 in that bug did the trick for me. I just downloaded it and installed it (I had to install the "dkms" package too) and that basically did it. After the .deb was installed, I ran "alsa force-reload", and I also had to run "modprobe snd-hda-intel". After that, sound worked fine.

---

### Post by rojakcoder on 2011-07-23
Thanks pointym5 and pull_ya!

It works! Like pointym5 mentioned, install the deb file.

However, I tried the commands as suggested by pointym5 but that did not activate the sound right away. I had to reboot to get it to work though. No biggie, so long as it works!

Have not tried the mike yet though, will update this thread again after I've tried it!

Cheers!

---

### Post by danootz on 2011-07-31
I managed to get sound through the speakers and FN brightness controls to work but a major issue I ran in to was Unity does not function at all. The first time I loaded up it said the hardware I had could not support Unity and to go to Ubuntu Classic. By default it seems the Nvidia drivers were installed and enable, I thought there might be some conflict due to the discreet & built in gpu so I uninstalled the Nvidia drivers and proceed to run an update (general update)and it seemed to be download a lot. Thought I caught the words Unity in there. I rebooted but still don't have Unity.

Additionally, the battery state claims 4hrs life compared to Windows 7's 8+ hrs of life. I can reluctantly accept half the battery life but what's strange is the read state often fluctuates in a matter of minutes. It'll go from 4hrs to 3hrs then 2:30hrs and then back up to 3hrs.

---

### Post by odwyerda on 2011-08-08
None of the above gets the sound card to work,

no sound card is detected for me...... Dont know what to do.

---

### Post by danootz on 2011-08-09
> **odwyerda said:**
> None of the above gets the sound card to work,

no sound card is detected for me...... Dont know what to do.

I"m pretty sure the link from Pull_Ya about HDA analyzer is the one that got sound working for me but I had to do a reinstall recently and now i can't locate the instructions on using it.

I've kind of reached the point where I'll just wait until Oneiric Ocelot comes out and hopefully by then, Canonical or others will figure out the hardware. :T

---

### Post by odwyerda on 2011-08-09
Hmm, Ill reinstall and give 10.04 a shot. I deleted my windows partition by mistake..... dont ask. Either way Ill reinstall and start a new. 



Thanks

---

### Post by odwyerda on 2011-08-10
Just an update, as I described the above .deb and alsamixer fix did not work for me.

However I installed 10.04 and upgraded ( yes a very long and silly method) and sound works straight out. 

Suggestion for the brightness, use wine & gapa.exe.

---

### Post by odwyerda on 2011-08-11
* Fixed, I was being stupid...

---

### Post by danootz on 2011-08-12
> **odwyerda said:**
> * Fixed, I was being stupid...

Wow, I wonder why a move from 10.04 to 11.10 makes it function.

And what was "fixed"? Did you edit the post? I didn't see what you had before.

So you're saying the 10.04 to 11.04 move provided you with a better out of box experience than a straight up 11.04 install? Additionally, how's your battery life looking? Do you have the proprietary drivers for the gpu installed?

(Maybe I should just try the 11.10 alpha/beta since for now I have no intention for using Ubuntu as my main OS until these issues are worked out without having me have to tweak things left and right. I'm not against having to do some work, but general functions like brightness and sound need to work by default. And the battery life needs to get better. Especially when Windows 7 is providing 8+ hours. You only get 1000 charges or so from a battery. No point in using Ubuntu if it's going to drain a battery quicker and have me recharge more frequently than Windows.)

---

### Post by rojakcoder on 2011-08-27
As a report-back, I haven't got the internal mike working. But everything else is working fine.

Some of you guys seem to have some problems though. Hopefully it gets solved for you soon!

---

### Post by odwyerda on 2011-10-17
I am very sorry about this very very very late reply. 


> **danootz said:**
> Wow, I wonder why a move from 10.04 to 

11.10 makes it function.

And what was "fixed"? Did you edit the post? I didn't see what you had before.

So you're saying the 10.04 to 11.04 move provided you with a better out of box experience than a straight up 11.04 install? Additionally, how's your battery life looking? Do you have the proprietary drivers for the gpu installed?



Yes 10.04 sound and mike (as far as I can remember, but don't hold me to it, it was a while ago now). Gnome worked a treat!  Battery life did not get tested as I upgraded and hour later. I installed the non-proprietary driver no problems what so ever and it worked a charm.


> **danootz said:**
> 
(Maybe I should just try the 11.10 alpha/beta since for now I have no intention for using Ubuntu as my main OS until these issues are worked out without having me have to tweak things left and right. I'm not against having to do some work, but general functions like brightness and sound need to work by default. And the battery life needs to get better. Especially when Windows 7 is providing 8+ hours. You only get 1000 charges or so from a battery. No point in using Ubuntu if it's going to drain a battery quicker and have me recharge more frequently than Windows.)

I decided that this version of Ubuntu ( and other versions of linux) would not go on this laptop because of those reasons. I would go so far to say that currently Linux is detrimental to the laptop itself because of the battery. The Dolby sound (works) and is so much better than the barely working sound. Although I am sure that there is something that could be done about that if a concerted effort was put forward. 

Has anybody given 11.10 a try yet??? 
I may give it a go during the week but again the battery life maybe a killer, perhaps a Linux as a plugged desktop replacement and Windows 7 when on the move.

---

### Post by odwyerda on 2011-10-20
Battery life increase


[http://ubuntuforums.org/showthread.php?p=11370761#post11370761](http://ubuntuforums.org/showthread.php?p=11370761#post11370761)

---

### Post by kammu on 2011-10-23
Acer timelinex 5830tg users please reply:
Can this laptop capable of handling multiple OS properly?
How's the overall quality of this laptop?
Thanks

---

### Post by rojakcoder on 2011-10-23
kammu, yes, it can handle multiple OSes. Most systems nowadays can.

Your second question is too open-ended. All I can say is that it has served me well. Other then the mike which I've not gotten working, most software controls are working fine - screen brightness, audio level, wifi/bluetooth on/off, mute key.

It even handles plugging in of a projector seamlessly.

I'm using 11.04. Hope that helps.

---

### Post by kammu on 2011-10-25
hi,
@rojakcoder thanks for your reply..
Can u just give some detailed review containing the following points:
1.How linux works on this system?
2.How's the battery life?
3.Heat issues?
4.Any speaker issues?
5.Overall perfomance?

other users also please reply..
Thank you

---

### Post by rojakcoder on 2011-10-27
Hi,

I don't know what you are looking for in your 1st question.

The battery is holding out well. I don't use Windows often so I don't know how it does against its normal expected usage. As of now, I can still use it for two hours. (I guess? Never really timed it.)

No real heat issues. Very well in that respect.

As mentioned in this thread, the speakers will need some tweaking to get them working correctly. Only thing I haven't gotten working is the internal mike.

Overall I'm satisfied with the machine. Although I don't think I've gotten the Nvidia card driver installed. I'm not too sure as I don't know how to check for sure.

---

### Post by donoterase on 2011-10-30
I think old mate's first question was HOW WELL linux works on the system. It's a broad question as it is.

Are you only getting 2 hours of battery life? That's not normal usage, considering you can pull about 7 hours from it. On average, I get between 5-7 hours from my battery, depending on usage. I had to do some tweaking to get that kind of battery life though. Out of the box, stock standard install, I got around 2hours as well. AND it would appear that the battery drain is about the same, regardless of whether the system sits there doing nothing, or under high load and usage.


> **rojakcoder said:**
> Hi,

I don't know what you are looking for in your 1st question.

The battery is holding out well. I don't use Windows often so I don't know how it does against its normal expected usage. As of now, I can still use it for two hours. (I guess? Never really timed it.)

No real heat issues. Very well in that respect.

As mentioned in this thread, the speakers will need some tweaking to get them working correctly. Only thing I haven't gotten working is the internal mike.

Overall I'm satisfied with the machine. Although I don't think I've gotten the Nvidia card driver installed. I'm not too sure as I don't know how to check for sure.

---

### Post by rojakcoder on 2011-11-03
You managed to get about 5-7?! That's amazing!

Can you share what is it that you tweak to get that kind of battery life. I've tried to time it and I get about 3 hours with the screen turned dark for a few minutes in between.

I would love to get that kind of battery usage as well and it'll be great if you can share what is it that you do to get it.

Thanks!

> **donoterase said:**
> I think old mate's first question was HOW WELL linux works on the system. It's a broad question as it is.

Are you only getting 2 hours of battery life? That's not normal usage, considering you can pull about 7 hours from it. On average, I get between 5-7 hours from my battery, depending on usage. I had to do some tweaking to get that kind of battery life though. Out of the box, stock standard install, I got around 2hours as well. AND it would appear that the battery drain is about the same, regardless of whether the system sits there doing nothing, or under high load and usage.

---

