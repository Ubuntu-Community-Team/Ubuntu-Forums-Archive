---
title: "Ubuntu 6.06 on Compaq laptop, any suggestions anyone?"
date: 2006-07-02
forum: Hardware &amp; Laptops
---

### Post by ShirishAg75 on 2006-07-02
Hi all,
        I'm going to install on an Intel-based Compaq laptop. Although would be getting the actual configuration tomorrow but was thinking of brushing up stuff as to what things should I know before I try installing Ubuntu on a Compaq notebook? 
       Are there some special keys to invoke the BIOS or something like that? Any suggestions. Thnx in advance.

---

### Post by Eversmann on 2006-07-02
After dealing with some laptops and linux (mostly ubuntu) my problems are always with wifi card, video driver and pcmcia. If it's a centrino, don't think you'll have problems. If it's a laptop with an nvidia card, no problem at all ;-), besides that..... patience ;-)

---

### Post by st00ner on 2006-07-03
i had a very bad experience with my compaq laptop. I believe there was a corupt table in the BIOS that was compaqs fault that prevented the processor fan from turning on. The Wireless card had a strange interface, but the ubuntu wiki had a solution. I still havnt found a way to fix the fan through linux, i would not recomend compaq to anyone wanting to use linux. "we only support the OS that came with the product" - compaq. that would be windows... Look elsewhere, IBM's have a very good record with linux compatibility

---

### Post by edemark on 2006-07-04
I am running ubuntu 6.06 on hp-compaq nx9010. Besides of the fun issue nothing special my ati card has out of the box 3D by Xorg (though it is extrlemly slow but works)

good luck

---

### Post by ShirishAg75 on 2006-07-05
[quote=edemark]I am running ubuntu 6.06 on hp-compaq nx9010. Besides of the fun issue nothing special my ati card has out of the box 3D by Xorg (though it is extrlemly slow but works)

good luck[/quote]

 Thnx edemark, I was looking for something similar. I would be getting the details today of what the specs are. Although their requirements at the moment are normal OS operations seeing movies, hearing music, Internet & stuff like tht. Just getting familiar with the OS.

---

### Post by zgoda on 2006-07-05
I have two nx6110 machines and while 5.10 worked like a charm, the 6.06 feels sluggish (with 386 kernel) or is absolutely unusable (with 686 kernel) due to 100% CPU usage even when idle.

---

### Post by the_maassk on 2006-07-05
I have a Compaq 1.6 GHz Pentium-M with Wi-fi, PCMCIA and the works. I have had no problems at all with anything! (Have not checked the PCMCIA though, because I don't use it). Even the inbuilt Card reader & the volume control buttons works like a charm by default. No fan issues either (neither with 386 nor the 686 kernel). Only thing being that the 686 kernel is a bit slow to react to the processor speed-stepping than the 386.

My exact model number is Compaq Presario M2201TU. As far as I know, the 'TU' is specific to my region. As for the specs themselves - 1.6 Ghz Pentium-M, 1 GB DDR, 40 GB HDD, i915 graphics, 15", inbuilt Wi-fi (BCMxxxx), 1 Firewire, 3 USB 2.0, 1 PCMCIA, inbuilt 6-in-1 media card reader.

The only custom configuration I had to do was for the Wi-fi (get the required firmware and fix it).

Let me know if you need help!

---

### Post by ShirishAg75 on 2006-07-05
[quote=the_maassk]I have a Compaq 1.6 GHz Pentium-M with Wi-fi, PCMCIA and the works. I have had no problems at all with anything! (Have not checked the PCMCIA though, because I don't use it). Even the inbuilt Card reader & the volume control buttons works like a charm by default. No fan issues either (neither with 386 nor the 686 kernel). Only thing being that the 686 kernel is a bit slow to react to the processor speed-stepping than the 386.

My exact model number is Compaq Presario M2201TU. As far as I know, the 'TU' is specific to my region. As for the specs themselves - 1.6 Ghz Pentium-M, 1 GB DDR, 40 GB HDD, i915 graphics, 15", inbuilt Wi-fi (BCMxxxx), 1 Firewire, 3 USB 2.0, 1 PCMCIA, inbuilt 6-in-1 media card reader.

The only custom configuration I had to do was for the Wi-fi (get the required firmware and fix it).

Let me know if you need help![/quote]

  Fantastic maassk u're right person as u'r system is close to my friend's rig. 
I didn't get to see the real thing but did get the specs. today. It's been raining
cats & dogs here :( It's a Compaq Presario M 2253 'AP' or 'AU' don't really know.
        System specs are :-
   1.6 Ghz Pentium-M, 40 GB HDD, i915 graphics, 15"  & he's been using some GSM phone to access the Net through it. So don't know whether that means Wi-Fi or what?

   If it does mean Wi-Fi, how did u come to know tht Wi-Fi is corrupted?
             Thnx in advance.


[OT] I've added u to my buddy list.

---

### Post by the_maassk on 2006-07-05
Internet access through GSM phone definately does not mean Wi-fi. He would either be using the phone's modem through a link (serial, bluetooth etc.) to get connected ..or he would be using a GSM PCMCIA Internet access card. Of course, his GSM service would have GPRS enabled.

That said - My Wi-fi was not corrupt. Ubuntu just does not ship the required firmware microcode for the Broadcomm chipset (which is on my laptop). You need to 'extract' it from the Windoze drivers and place them in the correct place on your Ubuntu install.

Go ahead and rock the baby! I'd be glad to help :-)

---

### Post by ShirishAg75 on 2006-07-08
crossed fingers, would be doing the default install today 2 hrs. from now. Would tell u how it went :)

---

### Post by FabreNZ on 2006-07-08
> **Eversmann said:**
> my problems are always with wifi card, video driver and pcmcia

I had those problems when using DSL (on a Toshiba A100).  It wouldn't even boot unless I disabled PCMCIA.  With Ubuntu, they all simply worked.  I was expecting a lot of trouble with the wireless networking, but I just typed in the network name and selected the card as the default gateway device, and I was connected!  I'm very impressed with Ubuntu's compatibility.

---

### Post by ShirishAg75 on 2006-07-08
I tried to install but couldn't install through the GUI way. The laptop had only 256 MB RAM & don't know how to get the text install running. I'm sure it was there on one of the other options there. Would try the same on my desktop just booting up on CD. Any suggestions guys how to get the text install running? Thnx in advance.

---

### Post by LinuxVox on 2006-07-08
I'm using an olded Compaq Presario 1247 & haven't had any problem w/it at all. I loaded breeezy Badger & have now upgraded to Dapper Drake on this machine. Aside from not having display limitations (800x600) no problems at all. It picked up my wifi card, D-Link 650+ w/o any problem.

Running 30G hard drive w/160M of RAM. It's not a beauty but works good enough for me!

LinuxVox

---

### Post by ShirishAg75 on 2006-07-08
It's a brand-new laptop & hence would like to do a clean install rather than do a badger & then d/l the alternate one & then uprade to dapper. It would be much better if I can found a way to install dapper (even a text install would do). I'm sure the  Xserver will start as the virtual (Live) desktop did come up each time :)

---

### Post by gazza567 on 2006-07-09
I run a brand new v5010AU and it works well.

just had to run the special wifi script from the forum to get the wifi running. stupid broadcom hard ware. but since i found that. not a single issue.

---

### Post by the_maassk on 2006-07-10
Shirish - 256 Megs is enough for any install!

There are two version of the CD - a Live CD and an Alternate Install CD. I prefer to use the Alternate install CD. Though running the graphical install through the Live CD should also not have any problems (I installed Xubuntu through a Live CD). I think I have a copy of the Live CD ISO somewhere on my hard disk. Let me burn it and boot it. Watch for my response in a few hours.

---

### Post by ShirishAg75 on 2006-07-11
AFAIK the Xubuntu Live CD use the XF86 which is much lighter on system resources. With Ubuntu the system was hanging. Although he's going to upgrade his notebook in couple of days so will try again. Just for the experience have also downloaded & burnt the alternate install cd. So if tht doesn't work then would use the alternate method. 

 A slightly [OT] question does anybody know where the examples are situated on the cd. The ones which have the openoffice e.g. as well as stuff from ubuntu official book. I'm exploring from windows. 

Also from the cd, is there any way to make the hard disk writable & copy some screenshots as well as take those examples & stuff from the desktop to the hdd. Thnx in advance.

---

### Post by the_maassk on 2006-07-11
I have a funny feeling which says that the Live CD should be mounting your HDD partitions by itself (I may be wrong because I have not done this myself). If that is not the case; to copy data to your hard disk from the Live CD, you'd need to mount your hard disk partition using the 'mount' command with appropriate parameters (man mount for details).

Edit:
I just got my 10 CD pack I ordered from Shipit! I'm going to give away 7 of them :-)

---

### Post by timbl on 2006-07-13
I have a HP Compaq nc6220 which works well. I had to fix the following issues:

1. Random select, cut and paste. There are a number of posted solutions which indicate that the synaptics driver needs to be downgraded to the old xfree one. I tried this and it did not work for me. In the end I just removed all reference to synaptics in my xord.conf as I never use it anyway. Turns out it still works but does not have any advanced functionality - probably why it was messed up in the first place.

2. CPU always maxed and fan always running on high. I found some other posts with this problem. To fix, I added the following to my rc.local file:

echo 1 > /sys/module/processor/parameters/max_cstate

which fixed the problem. As I understand it, this is only a problem for i686 kernels.

3. Using a higher resolution display then the built in - 1280x1024 vs 1024x768. The problem is that the BIOS removes any display resolutions that are not current - i810 driver. When booting with the internal display the 1280x1024 resolution is disabled. This can be addressed with a dual head configuration, but all my 3d apps failed to run and I want to use compiz. Also I don't really want to run dual head.

In the end I created two xorg.conf files, one with a Monitor layout that only included an external CRT and one for the internal display. As long as I boot up with the external CRT, I can still switch to the internal by using fn-f4 and using xrandr to drop the resolution. I need the second xorg.conf to start X when booting up without an external display.

I am not very happy with this solution. My next step is try to update the BIOS.

4. Enable wireless activation button and light (wireless still works without but it looks nice)

 create the following file /etc/modprobe.d/ipw2200 with one line:

     options ipw2200 led=1


With these fixes everything is working well enough, but I miss my thinkpad.

---

### Post by ramasdf123 on 2006-07-13
i have a compaq v2405us and installin ubuntu was fine, they only prob was the wifi card which was BroadCom 4318. I used the wrapper thing as it said in the forum and i got it to work.

---

### Post by ShirishAg75 on 2006-07-17
Progress has been very slow from my side. Now I'm able to boot, get the installer working but can't get the right combo to get pass the partioner.

 As of things stand right now, the laptop has 40 GB drive & is divided like
  1 primary partition Fat 32 13 GB        /dev/hda1
  1 extended partition Fat 32 13 GB     /dev/hda2 - now how this?
         1st logical drive i.e. D i.e 5 GB    /dev/hda 5
          2nd logical drive i.e. E i.e. 6 GB  /dev/hda 6

   the rest of the space is unallocated. Now I was thinking of making one primary partition for / & one 1 GB space for swp.  Now for swap should I say extended partition or what? Things went so smoothly on the desktop didn't really think it through. Can somebody help?

       Would be posting the fdisk -l output as well 
        the parted (print) output  as well as screenies as to what mess I'm making. 

        Hopefully somebody would be able to guide me, thnx in advance.

---

### Post by the_maassk on 2006-07-18
Read my post on this thread about my partitioning scheme:

[http://ubuntuforums.org/showthread.php?t=212980](http://ubuntuforums.org/showthread.php?t=212980)

Hope it helps some.

---

### Post by ginapi on 2006-07-18
I have a Compaq nx6110 and I'm very happy with it. 
Breezy was working absolutely fine. 
I upgraded to Dapper the last week and till now I found a problem with acpi battery events that I'm tryng to solve.
I never used the wirelss card but I think it should work.

---

### Post by ShirishAg75 on 2006-07-19
o.k. guys, I'm a real nut-case. It took me 2 days to realize what I had done right whie installing on the desktop & I was forgetting the same while doing on the laptop, partition both / & swp at the same time . Although I've to say its a nice guide u've written. One thing though u'll have to either point out or link or give in tht guide is how to mount it as the FAT32 partition would be setup later & give write permissions to it.

   Couple of things which didn't get right are the keyboard, some of the keys respond in with different keys. For e.g. the one on top of 2  when I use shift on the laptop should show **@** but instead shows **"** & where I press **"** then **@** shows up. What could be wrong here & how that can be fixed ?

     Secondly, is there a way to do some better trackpad handling/sensitivity etc. My friend is found of creating caricatures/cartoons on the go. I know it's a bad idea to give him that much power :rolleyes: but that's GNU. Who knows one of these days if he likes it one of his cartoons/caricatures will find themselves on art.gnome.org :)


Lastly,  is there a GUI friendly something (point & click) sort of dialer for BSNL. My friend uses Huawei about which I don't have much clue at the moment, although have bought the pdf to read.  This last part I would be cross-posting in the networking/Internet section also so either here or there it would be nice.

                           Thnx guys for all your help & advice.

---

### Post by the_maassk on 2006-07-19
Thanks for the heads-up about a reference to mount the FAT32 in 'rw' mode later (I remember my Dapper mounted it 'rw' by itself though!).

On the touchpad - I remember an app called gsynaptics (should be in the repos) which will give him more control over the touchpad. Do remember to read the install instructions on it because you need to enable something in the X.Org conf file for it to work (I don't remember the name of the parameter...SHMConfig or something).

On a point-and-click dialer for BSNL - I've not played with my modem much because I'm on cable...but I feel there would be a way to create a config with the dialling rules and have a shortcut to it. Hope someone else is able to help you out on this.

Edit: On the keyboard thing - well..beats me..but you could check the keyboard mapping config.

---

### Post by kury on 2006-07-20
I can't install ubuntu on my compaq presario 1200, any suggestion please? nobody seems to have an answer...

---

### Post by the_maassk on 2006-07-20
> **kury said:**
> I can't install ubuntu on my compaq presario 1200, any suggestion please? nobody seems to have an answer...

Any specifics on the problems you are facing would enable the people out here to help you.

---

### Post by TFrog on 2006-07-26
I'm currently running Kubuntu on a Compaq R4125US laptop and am actually writing this post from it.  I use the ndiswrapper drivers for wireless for two reasons.  Those are WPA support and speed of 54Mbps.  I've heard that the fw-cutter drivers don't support 54Mbps yet nor WPA both of which I prefer.  That said I've had few problems with the laptop other than the fact that my volume up, down, and disable buttons didn't work out of the box.  Still looking for info on it.  Also have some funky things going on with the synaptics touchpad.  It will randomly switch windows or do a random copy past into various apps.  Anyone experiencing this and have any ideas would be great to hear from them.  Other than that, I actually like Kubuntu on my laptop better than Winbloze.  It actually runs cooler than in Winbloze.  At times, I don't even hear the fan running though I know it's running.  It just runs slower even under load.  No I don't have the ATI drivers loaded for 3D as I'm not a gamer.  I don't use PCMCIA so I can't vouch for that.  The memory card reader I'm not sure on either.  Otherwise, dead solid:-D

---

### Post by ioxer on 2006-07-28
I'm running Ubuntu on a Compaq ET095AV. It works very well except I think I have the fan issue. Compaq recently released (last month) a BIOS that "Improves system fan control" but it requires Windows to intsall the BIOS and I don't have Windows on my laptop anymore. :sad:

I'll have to find a way around this; I'm too lazy to re-install Windows. Does anyone know if VMWare will allow me to install the BIOS update?

---

