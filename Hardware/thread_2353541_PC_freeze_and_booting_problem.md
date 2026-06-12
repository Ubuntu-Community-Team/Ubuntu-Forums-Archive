---
title: "PC freeze and booting problem"
date: 2017-02-22
forum: Hardware
---

### Post by Atitudes on 2017-02-22
Hi all,

This is not an usual thread as I'm not having a "specific" hardware issue but I'm coming here as a last resort asking for your kind attention because this forum (and the search function :-\") has been my problem solver for so many years, I would really appreciate some benevolent help here. 

I love my computer but I'm more than aware it's getting pretty old, it was a nice  purchase years ago but still, this issue has happened for years and I  think it's time to figure out what has been happening before I even  consider doing an upgrade or... a funeral :-({|=. 

Sometimes it just doesn't boot, no matter how many reboots I perform,  the screen doesn't turn on and it just stays with the led  blinking in a "I'm not even ON" position. In the past I was sure my HDD  was running while this was happening but nowadays, since I loaded the SO to an SSD (kept my /home  in the HDD) I really can't tell if something is eventually "booting".

Some years ago it really stopped working and I started to unplug the  components one by one until I found out it was the wireless board's  fault which I eventually replaced and all went fine for some months but  then, it started again.

Usually the solution comes with a slight "kick in the box" and a reboot  and everything works fine again (it's working pretty fine now for example). Sometimes I give the graphic card a tap  or clean my memory sticks and it's all good but I really can't tell  from where this issue may come from.

This usually happens when I boot the computer but on some occasions, it  freezes while it's already booted and working fine, just like ten  minutes ago :mad:
My question is: [U]Is there a way I could find out what piece of hardware is faulty and causing this issue? 
[/U]
This is because I was thinking to perform a small hardware upgrade to  rejuvenate this awesome computer that has made my days for years and  years! But I'm afraid the issue could still persist in some way and  that's why I'm coming here to seek for assistance.

Just for the record, I'm not an expert neither with hardware nor with ubuntu but I'm also not a complete fool either :tongue:  I rely on this community for seven years now and I couldn't be more  happier with all the excellent support I have seen regarding many  different topics and I only have one thing to say:
"Help me please, your are my only hope" !!!

Not sure if this helps but here's some of the commands I've learned over the years: (the death star plans)
```
atitudes@Desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Juniper XT [Radeon HD 5770]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Juniper HDMI Audio [Radeon HD 5700 Series]
02:00.0 Ethernet controller: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
03:00.0 SATA controller: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
03:00.1 IDE interface: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
04:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
05:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
atitudes@Desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 006 Device 002: ID 1532:001c Razer USA, Ltd RZ01-0036 Optical Gaming Mouse [Abyssus]
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Or perhaps the attachment may be of more use...

Thank you very much in advance, any help is much appreciated!

---

### Post by DuckHook on 2017-02-23
Old HW hound here.

[LIST]
[*]Firstly, you have my admiration for respecting old hardware.
[*]
[*]Secondly,> …a slight "kick in the box"…and everything works fine again…just put a big smile on my face.
[*]
[*]Thirdly, your system specs are not at all underpowered or obsolete. This is a box worth putting some elbow grease into.
[/LIST]
Here are some of the methods I use when assessing old boxes with intermittent, irregular and inconsistent misbehaviour:

[LIST=1]
[*]Is it the PSU? A bad PSU with unsteady power output will cause crazy behaviour that feels completely random.
[*]It could be the MOBO. I've dealt with a couple of MOBOs that had tiny hairline cracks. Very hard to detect. In your case, this would be a prime suspect since your problems don't seem to be confined to one specific subsystem.
[*]Are all fans working? Is unit intermittently overheating? What does lm-sensors report?
[*]What do logs say, especially syslog and kern.log?
[*]You don't mention if all of these problems are occurring on one OS that you've had running from day one. If so, then the problem could be OS related. But if you've changed OSes a number of times with fresh installs, then the cause is unlikely to be a corrupt installation. You still may wish to run your box using a LiveUSB stick for a few days. Does this make the problems stop? All info is useful.
[/LIST]
I don't know how far you want to get mired in detective work. Diagnosing these sorts of problems often take on the character of crime scene investigations, which isn't everyone's cup of tea. Your question:> Is there a way I could find out what piece of hardware is faulty and causing this issue?…is very pertinent. And the usual way to solving that one is conceptually simple, but procedurally both a grind and resource-dependent: you substitute each component one-by-one until you isolate the trouble-maker.

This is possible for a pack rat like me who collects all sorts of bits and pieces and has them spread out across three big basement tables. But most users don't have replacement parts just laying around, or their sig-others are understandably not as patient with the permanent mess as Mrs DuckHook is. In any case, this slow grinding process of replacing a component at a time may not be readily available to you. In that case, you will have to decide if the expense of buying and trying components this way is worth it. For most users, it rarely is. You are better off retiring the poor thing and buying a new machine.

I know. It feels like you are abandoning a loved one. It also feels like a such a colossal waste. But new computers are so cheap these days that it is often just not worth it trying to nursemaid an ailing one, unless, of course, you are a stubborn old fool like me who just likes to triumph over a mystery.

---

### Post by Atitudes on 2017-02-23
Hi @DuckHook!

Thank you so much for taking the time to reply and for all your suggestions. It took me some tough labor and hard cash to set up and build this machine at that time which has served me well (despite this issue) for all these years. 

Unfortunately, we may have a problem because you got it right
> you are a stubborn old fool like me who just likes to triumph over a mystery.
indeed... and that's why I came here seeking for assistance in the event a solution may be found.

I did store some old parts but they are from another era and cannot help in this case. That was another funny story; I kept an old AMD desktop working despite having more than 50% of its MOBO capacitors budged and they never leaked or blown :D. They are stored at my parents' house and Mrs Atitudes throw me huge apprehensive eyes each time I visit them and tell her the stories she already knows about it... I managed to keep some HDD and memory sticks hidden in our house though.

Alright, let's get to business:
 
[LIST=1]
[*] > Is it the PSU? A bad PSU         with unsteady power output will cause crazy     behaviour that feels     completely     random.
Well, sorry but that's another funny     story.     When I built this computer I chose a NOX case which had the         particularity to have the PSU slot at the     bottom instead of the     usual top one. This     was about 10 years ago and despite the guy at     the     store didn't feel comfortable with this, he did his best. When I         returned months latter, the store had a huge     display of NOX cases     and he told me he loved     my built and made a similar one with the     same     case... About 7 months ago I had my computer dusted and cleaned         at another store and also asked them to     perform a check up. They     told me everything     was working fine, including the PSU (there were     no     freezes or failed boots that day...), but he did told me         something funny: I had the PSU mounted     upside down all these years     since the fan     should be facing down, not up...      [IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABYAAAAQCAMAAAAlM38UAAAAOVBMVEUAAABFRUVUUk9/fn/ nQD/tAD/zgD/6gD//ROhoaH//pPHxsf//8f2/9f// v////8A/sAAAD///8FrjPgAAAAEXRSTlP/////////////////////ACWtmWIAAACYSURBVHicRdBZEsQgCARQlEREjHr/007jNv2VelIdlMZN8Oxv mOrpaR9cBiYs4ikJyxWVmgtWQhMy2nwx2DoYkmHO4fqBStzHN0Yn8OH38ONy1U6PBiJsrsPK7N9PU737G5U46Db9rQ2wdqNVRfjhxgGEYbVWyymGVSAiLVDzaK yIM34Q7GHmau9wX92lhQfUG97 vD4wcmiwv3pXLaOwAAAABJRU5ErkJggg==[/IMG] [IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABkAAAAPCAMAAAAmuJTXAAAALVBMVEUAAABFRUXKIgL nQD/tAD/zgD/6gD//RO9v7X//pP//8f// v8A/sAAAD///8sSPs8AAAADXRSTlP///////////////8APegihgAAAHVJREFUeJx1kFEOgDAIQ lwINP7n1c2nYLG97XspaQpFWd/QGe8aHXC/9bM6nBUynpn/F9VRCojGzQjErlUvAZTuajomdkATYWmYURjwSwI12By083TAPprajCM1I1ots7dPOQpGoKz6epkbPDabXH4u1va gBHqwqmUerTOAAAAABJRU5ErkJggg==[/IMG]         
Anyway, I might buy a new one to give it a try     since it can be     used in the event I build     another machine but my feeling is that     it's     working fine. If you don't mind, I prefer to get back to this         solution later, in the event nothing strange     is detected with the     other parts/solutions. 
[*] > It could be the MOBO.         I've dealt with a couple of MOBOs that had     tiny hairline cracks.     Very hard to detect.     In your case, this would be a prime suspect     since     your problems don't seem to be confined to one specific         subsystem.
They did dismount     everything during the     check up since I also     swapped the cooler. I will have a more     thorough     inspection during the weekend and give an update. Do you     think     I should unscrew it to see if there is something near the         screws? Or it's just a very bad idea? 
[*] > Are all fans working? Is         unit intermittently overheating? What does     lm-sensors     report?
Here I have     my doubts because around 2014     (since 14.04)     the fans have been working harder than before (just     coincidence,     nothing to do with the OS, almost sure). I used to keep     the     CPU about 30ºC in the past. At first I thought the CPU cooling         paste wasn't doing its job and that's why I     swapped the cooler. I     also had another fan     that came with the NOX case but couldn't fit     due     to the former cooler size. Since I replaced it, it got a lot         better and the fans only became more audible     when I push for it a     little more. I do     notice some intermittent boosts time to time even     when     it's idle. I now have two fans, one at the front and one in the         back (on the correct position this time). It     used to reach about     50-75ºC on the CPU     depending on the usage but it seems a lot better     nowadays.     Here's my sensors output (just the browser         opened):
```
atitudes@Desktop:~$         sensors
radeon-pci-0100
Adapter:     PCI adapter
temp1:                +54.0°C  (crit = +120.0°C, hyst =         +90.0°C)

coretemp-isa-0000
Adapter:     ISA     adapter
Core 0:           +32.0°C  (high =     +80.0°C, crit =     +100.0°C)
Core 1:           +30.0°C      (high = +80.0°C, crit =         +100.0°C)

atk0110-acpi-0
Adapter:     ACPI     interface
Vcore Voltage:          +1.08 V  (min     =  +0.85 V,     max =  +1.60 V)
 +3.3 Voltage:              +3.38 V  (min =  +2.97 V, max =  +3.63         V)
 +5 Voltage:            +5.07 V  (min     =  +4.50 V,     max =  +5.50 V)
 +12 Voltage:              +12.09 V  (min = +10.20 V, max = +13.80 V)
CPU         FAN Speed:      998 RPM  (min     =  600 RPM,     max = 7200 RPM)
CHASSIS     FAN Speed: 1117 RPM  (min = 1200     RPM,     max = 7200 RPM)
POWER FAN Speed:   1140 RPM  (min         =  600 RPM, max = 7200 RPM)
CPU     Temperature:        +32.0°C  (high =     +60.0°C, crit = +95.0°C)
MB     Temperature:         +35.0°C  (high = +45.0°C, crit =         +95.0°C)


``` 
[*] > What do logs say, especially syslog and         kern.log?

Sorry here, I've been trying to post the information but it keeps failing saying "a security token is missing" and I cannot post. I have the kern.log saved in a file but cannot attached due to size limit and since it's getting late I will update tomorrow. That's what happens when dealing with a noob ):P. Please advise. 
[*] > You don't mention if all of these problems are         occurring on one OS that you've had running     from day one. If so,     then the problem could     be OS related. But if you've changed OSes a     number     of times with fresh installs, then the cause is unlikely to     be     a corrupt installation. You still may wish to run your box using         a LiveUSB stick for a few days. Does this     make the problems stop?     All info is     useful.
The problems started around 2012, I     didn't     make any hardware changes that could impact the problem. OS         history is simple, started with XP then side     booted windows 7 and     ubuntu 9.04 and in 2010     (when graphic card drivers became     "available")     I am proud to say I am a MS free house since     then.     I always stood with LTS versions with clean installs. I did         broke the system with *"knowledgable     experiments" *once     or twice since I     got the SSD just because I kept my /home in the HDD     (so     happy when i found out I could do this!!). The main issue is to         be unable to boot at all, I can hear the     fans working and also the     HDD for a bit but     the screen just doesn't turn on so I just try and     reboot     once or twice which usually solves it and in some occasions I         have to open the case and just "cuddle"     the graphic card     and memory sticks and this     usually works. Only about thrice a year     the     system completly hangs while already booted. 
[/LIST]
 

Over the years I've been so happy with my set up and OS(s) and despite this issue being really annoying and frustrating sometimes, it does not affect my daily use besides make me hangry sometimes... I really really want to find out what could be the cause since for a cheap upgrade (and please tell me if I'm mistaken here) I could acquire a new CPU and perhaps some better memory sticks which would fit me for some more years... Even if I could only keep the graphic card, car reader and dvd it would already be a huge benefit.

Anyway, hope we can > triumph over a mystery.

Thank you very much in advance and sorry for being so long!

Cheers!

---

### Post by DuckHook on 2017-02-23
> **Atitudes said:**
> …Do you think I should unscrew it to see if there is something near the screws? Or it's just a very bad idea?I wouldn't go so far as to say it's a bad idea, but I doubt that it's necessary. Your lm-sensor temps look very cool, so no point decoupling your CPU yet again.> It used to reach about 50-75ºC on the CPU…This is a little hot but not remotely into danger territory. And…> Here's my sensors output…Everything looks more than good. Keep in mind that 37°C is body temperature, so some of those temps are enviable.> I've been trying to post the information but it keeps failing…cannot attached due to size limit…Many people post large files using pastebin. Accounts are free.> The problems started around 2012You've been living with this behaviour for ***5 years***?! :shock: I don't even know how to respond to that.

No… actually, I do: if I were you, I would consider it time to retire this old box and get something new. If it helps, think of it as a retirement and not an abandonment.> …I've been so happy with my set up and OS(s)…I really really want to find out what could be the cause since for a cheap upgrade (and please tell me if I'm mistaken here) I could acquire a new CPU and perhaps some better memory sticks which would fit me for some more years... Even if I could only keep the graphic card, car reader and dvd it would already be a huge benefit.Perhaps this might help:

I keep a couple of old fossils around for the sake of nostalgia too. But they aren't my main production box and I don't need to rely on them. Instead, they serve as torrent servers and as a backup of my backup. I also have an old one laying around as a fallback desktop machine that I can fire up should my main box melt down. In other words, they are all in non-critical roles. As much as I sometimes remember those old dogs fondly, the sheer power and dependability of my new hardware has made life less stressful and more enjoyable.

This frees you up so that you can still tinker with the thing; you just won't be depending on it.

---

### Post by Atitudes on 2017-02-25
Inspected the thing, everything seems OK and working fine; no cracks no "bad spots" at all. 
I may blame the graphic card for this as she also heats up a little sometimes, but the only symptom I witnessed is like a tiny glitch while extending screen trough HDMI  It make like a quarter of second rewind every 5 to 10 minutes time to time.

I think I managed to use that paste bin you mentioned, here's the kern.log I saved:
[Here]("http://pastebin.com/AgFvbdBn")

Really hope it worked, let me know if I did wrong!

If it happens again I will save the logs hoping it will be helpful
> You've been living with this behaviour for ***5 years***?! :shock: I don't even know how to respond to that.

True, and you don't need ;) but i happens like 4/5 times a year, the rest of the time it works more than fine! I am to blame but like for an old car, sometimes the source of a damage is very hard to detect and may arise from unusual places :-k [URL="http://pastebin.com/AgFvbdBn"]

[/URL]I'll keep this old fossil around  in case of any event :p, I have a back up laptop to hod the shots =;.

Really hope the info helps!
Thank you,

---

### Post by DuckHook on 2017-02-26
I quickly parsed through your kern.log file with grep looking for keywords like "alert", "fatal", "warning", etc&#8212;btw, that's the way to "read" these long arcane files&#8212;but found nothing. I wasn't expecting to either. Logs are uninformative unless they are the product of the crash event. In the case of hard crashes of your sort, they usually show nothing anyways, since the crash destroys the log service along with everything else. It's just another step in the diagnostic process.

I don't recall you mentioning before that the crashes were that infrequent. I thought they were occurring like once a day. I still don't think I could live with once every two months though. Worse, in many ways, because that's just enough time between crashes to lull you into a false sense of hope/security to get careless about saving your work. However, you are best placed to decide if retiring the beast is a good idea for you or not.

Don't know what more to tell you. Immediate or frequent crashes are usually the product of something that can be identified, whether HW or SW. But infrequent crashes like yours&#8230;? Dunno. Is the power dependable where you live? Is it brownouts? Is it voodoo?

The next time it crashes is the time to look through your logs. If anything looks suspicious, feel free to post on these forums again asking for help.

Until then, Good Luck and Happy Ubuntuing!

---

### Post by Atitudes on 2017-03-01
I cannot thank you enough for your patience and kind help, and I'm sorry I haven't mentioned earlier that these issues are not frequent at all (I thought I did but seems to be only in my own head..).

It kinds of remind me of a former car I had with a very small "leak" in the radiator system and I say "leak" because in years and years I never found what the problem was. Tried a bit of everything, switched pumps, radiator, cooler liquid recipient, some hoses...put the all system under pressure and nothing. My mechanic assured me it had nothing to do with the engine and the only plausible solution we had was to wait for it to get worst in order to effectively detect the source of the problem. Well, its kind of what I've been doing with this issue, at first I tried everything to my knowledge and got some help too but we also never found the source... Therefore, I've been waiting and waiting for it to get worse but it doesn't... By the way, I sold that car years ago with the same problem and it still runs pretty fine nowadays (I gave an heads up to the new owner of course).

> Don't know what more to tell you. Immediate or frequent crashes are  usually the product of something that can be identified, whether HW or  SW. But infrequent crashes like yours…? Dunno. Is the power dependable  where you live? Is it brownouts? Is it voodoo?

I'll have to gather it is voodoo... It couldn't have been power dependence since this baby always ran with an UPS (former lessons learned...) and it's very stable where I've been living these last years. These last days I did took time to switch for a new PU, it's still something I can use in the event I retire this machine. Can't be ram (also bought some a year ago and nothing changed), also cannot be HDD as I upgraded with an SSD thus, i think it's either something with the MOBO or the GPU. When I have some spare time (and $) I will upgrade my MOBO + case and keep the same GPU. I guess it's a good way to find the culprit don't you? 

I was hoping there was an easier way to find out without relying in pure luck but I guess it's not worth the time (which I don't have much and I'm sure you have loads of better things to do also :) ).

Once again, thank you very much for your excellent advices and patience to deal with me, and I guess if this happens again, I will record the logs anyway because who knows it can still have some clue here or there. 

One last thing, what is the best way to retrieve the log info? Just get it from the sys and kern files in /var/log or is there some better and more common way to most users (but me...) like running a dmesg command?

---

### Post by DuckHook on 2017-03-01
> **Atitudes said:**
> …what is the best way to retrieve the log info?Your question is harder than you think. Logs are spread out all over the place these days. They used to be all under /var/log. Output those and you're done. These days, it's more complicated:

[LIST=1]
[*]Under /var/log/ the usual suspects are syslog and kern.log.
[*]dmesg gives you some (not all) system events since last startup.
[*]journalctl is the new systemd feature that is absurdly powerful and just as absurdly new and arcane. See its man pages for usage. I'm not going to pretend to know it except in a very rudimentary way, but I have been getting significant info with is using:```
journalctl -b
```Add the -k option if you want to constrain output to just kernel events, but in that case, may as well simply run dmesg.
[/LIST]
If using Unity, there is gnome log viewer bundled as part of default install. But I like using plain grep because it has so much filtering prowess. Pipe output to a file and you have a nice tidy summary of interesting events.

---

### Post by Atitudes on 2017-03-02
Acknowledged.

Thank you very much, I will get back in the event it happens again (which may take some time to happen) hoping some relevant information can be filtered out. Until then, let's see if this new PU makes any difference...

Cheers and happy Unbutuing!

---

