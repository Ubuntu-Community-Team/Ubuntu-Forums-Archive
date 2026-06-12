---
title: "HDMI not working on HP dv7t, no matter which Ubuntu I install"
date: 2011-07-15
forum: Hardware
---

### Post by austintexican on 2011-07-15
Hi all,

I have an HP Pavilion dv7t with Windows 7 64bit (below is a list of hardware). I have created an extra primary partition on the hard drive for installing Linux. So far, every distro I've installed seems to work fine, with the exception of one very important thing: the external LCD I have plugged into the HDMI port is not being recognized, neither by the included drivers nor AMD's proprietary drivers. I've done all recommended updates, but still no joy.

Could someone please help with this? I'm really eager to get away from Windows, but I MUST have the external monitor working.

**Versions I've tried (all are the AMD64 type)****:** Ubuntu 11.04, 10.10, and 10.04. I've also tried Linux Mint 10 Gnome and Kubuntu 11. 

I *did *get some screen flicker on the external using 10.10, but when I installed the AMD drivers, it refused to boot into the GUI. I didn't even get a login screen, just a terminal screen reporting memory errors.

**Hardware:**

[LIST]
[*]External LCD: Samsung SyncMaster 2233BW (I'm actually using an HDMI to DVI cable which works fine in Windows)
[*]Notebook: HP Pavilion dv7t
[LIST]
[*]Intel Core i5-460M Dual Core Processor          (2.53 GHz, 3MB L3 Cache) with Turbo Boost up to 2.8GHz
[*]1GB ATI Mobility Radeon HD 5650 switchable      graphics [HDMI, VGA]
[*]8GB DDR3 System Memory (2 Dimm)
[*]640GB 7200RPM Hard Drive with HP ProtectSmart Hard  Drive Protection
[*]17.3" HD+ High-Definition HP LED BrightView  Widescreen Display (1600 x 900)
[*]HP TrueVision Webcam with Integrated Digital  Microphone
[*]Intel Wireless-N Card
[/LIST]
 
[/LIST]
Any help at all would be most appreciated. I'm so sick of Microsoft's bullsh*t, but I really need the video to work properly before I can migrate.

Thanks!

---

### Post by s3Pol on 2011-08-05
Hey,

I have the same problem that you describe, but in HP DV6 and same ATI card (5650)!!
Can anyone provide a solution, or help us?
Please.....

01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series] (prog-if 00 [VGA controller])
Subsystem: Hewlett-Packard Company Device 144a
Flags: bus master, fast devsel, latency 0, IRQ 46
Memory at a0000000 (64-bit, prefetchable) [size=256M]
Memory at c4400000 (64-bit, non-prefetchable) [size=128K]
I/O ports at 4000 [size=256]
Expansion ROM at c4440000 [disabled] [size=128K]
Capabilities: <access denied>
Kernel driver in use: fglrx_pci
Kernel modules: fglrx, radeon


xrandr -q
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
1366x768 60.0*+
1360x768 59.8 60.0
1024x768 60.0
800x600 60.3 56.2
640x480 59.9
VGA1 disconnected (normal left inverted right x axis y axis)
s3Pol is online now Report Post   	Edit/Delete Message

---

### Post by s3Pol on 2011-08-05
Update:

I have installed the last drivers from:
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

and still have the same issue. :(

---

### Post by Jeff Morasco on 2011-08-05
I had a similar problem running 10.04 on an hp netbook. I also had the same problem with windows. The solution I found there was found in control panel, so in Ubuntu I opened system preferences  and played around under monitor. With the hdmi plugged in, I told the computer to  look for other monitors It found one and I could 'twin' an image to the second monitor. I am a complete linux neophyte and have no idea if this is useful to you.

---

### Post by Deltik on 2011-08-05
> **Jeff Morasco said:**
> I had a similar problem running 10.04 on an hp netbook. I also had the same problem with windows. The solution I found there was found in control panel, so in Ubuntu I opened system preferences  and played around under monitor. With the hdmi plugged in, I told the computer to  look for other monitors It found one and I could 'twin' an image to the second monitor. I am a complete linux neophyte and have no idea if this is useful to you.
In addition to this, has anyone checked the ATI Catalyst Control Center?

_Ubuntu Classic Desktop:_ System >> Preferences >> ATI Catalyst Control Center (Administrative)
_Ubuntu Desktop:_ Search in the dash for "ATI Catalyst Control Center"

---

### Post by austintexican on 2011-08-06
I don't know, guys. So far I've tried OpenSUSE/KDE, various versions of Ubuntu/Gnome/Unity, Kubuntu, and LinuxMint. In every case the poor video performance and instability has been really disappointing.

Next I'm going to try Arch, LinuxMint/Debian, and Slackware, then I'm giving up on Linux until I can build a custom desktop next year. Or until AMD gets around to finding out why so many users are having problems with the Mobility drivers.

---

### Post by Deltik on 2011-08-06
Did AMD ever respond to your request?

---

### Post by austintexican on 2011-08-06
> **Deltik said:**
> Did AMD ever respond to your request?

Actually, I've been bogged down with summer finals, so I'm embarrassed to say I didn't contact them. It seemed kind of pointless at the time because it looks like this has been a known issue since 2010. My experience in the Wintel world has been that if a company hasn't addressed a problem within 3-6 months, they've probably decided to blow it off.

However, I did have the idea of asking you (since you've been on here much longer than I have) if maybe we should get as many people as we can to contact AMD as a group. Then maybe they'll actually take the problem seriously. My last tests are on Monday, but then I'm wide open the rest of the week if you want to work on that.

---

### Post by Deltik on 2011-08-06
I like that idea.

Right now, AMD's entire website is down, so I can't find out what ways there are to contact them.

This is an important issue, and it's not right for AMD to sit idly on it and look only on their Windows side.

---

### Post by austintexican on 2011-08-06
> **Deltik said:**
> I like that idea.

Right now, AMD's entire website is down, so I can't find out what ways there are to contact them.

This is an important issue, and it's not right for AMD to sit idly on it and look only on their Windows side.

Why don't we return to this Tuesday, when I'll be on break between semesters?

In the meantime, if you will create a thread asking for details from any members that have been having issues with the latest AMD drivers, especially the Mobility HD line, I'll devote a day or two on the phone next week to talk directly to a senior member at AMD support.

Maybe they'll get on it if they see that the Ubuntu community as a whole is getting concerned.

---

### Post by stephenjbarr on 2011-08-12
Let me know how I can help on this as well. I am having the same problem. Thanks.

---

### Post by austintexican on 2011-08-12
> **stephenjbarr said:**
> Let me know how I can help on this as well. I am having the same problem. Thanks.

I'm just waiting to see if Deltik wants to move forward. I feel that I'm too new here solicit a group effort like I proposed in my last post.

---

### Post by Deltik on 2011-08-12
> **austintexican said:**
> I'm just waiting to see if Deltik wants to move forward. I feel that I'm too new here solicit a group effort like I proposed in my last post.
Hmm... I thought that I had replied. Strange...

But anyway, I am interested in your idea and would like to help get a group together to get AMD's attention.

---

### Post by austintexican on 2011-08-12
> **Deltik said:**
> Hmm... I thought that I had replied. Strange...

But anyway, I am interested in your idea and would like to help get a group together to get AMD's attention.

No worries :)

If you take a look at my previous post, I was basically suggesting that since you've been here awhile, it would be more appropriate for you to solicit the forum comnmunity for any problems they've been having installing/using the AMD Radeon (aka fglrx, aka Catalyst) drivers.

Once we have a few posts in that thread, I'll spend a day or two on the phone to try and get senior a tech support person from AMD to look into the issue.

I'm free all next week, then I'll be pretty busy with school.

---

### Post by Deltik on 2011-08-12
> **austintexican said:**
> no worries :)
  Okay. :D

> **austintexican said:**
> if you take a look at my previous post, i was basically suggesting that since you've been here awhile, it would be more appropriate for you to solicit the forum comnmunity for any problems they've been having installing/using the amd radeon (aka fglrx, aka catalyst) drivers.
Actually, I've been a ghost on Ubuntu Forums until my problems with Ubuntu 11.04. I don't really know much about this place. What am I to do?

> **austintexican said:**
> once we have a few posts in that thread, i'll spend a day or two on the phone to try and get senior a tech support person from amd to look into the issue.
Um, I'm confused now. What thread?

> **austintexican said:**
> i'm free all next week, then i'll be pretty busy with school.
Same here.

---

### Post by austintexican on 2011-08-12
> **Deltik said:**
> Okay. :D

Actually, I've been a ghost on Ubuntu Forums until my problems with Ubuntu 11.04. I don't really know much about this place. What am I to do?

Um, I'm confused now. What thread?

lol, the thread I was hoping you'd create asking for member input. =P

I suppose I could do it if you don't feel comfortable, but I'm *really *new on the board. Let me know :)

---

### Post by Deltik on 2011-08-12
Oh, really? The only category I know on this forum is
				[Ubuntu Forums]("http://ubuntuforums.org/index.php")  	> [The Ubuntu Forum Community]("http://ubuntuforums.org/forumdisplay.php?f=130")   	> [Main Support Categories]("http://ubuntuforums.org/forumdisplay.php?f=327")   	> [Hardware & Laptops]("http://ubuntuforums.org/forumdisplay.php?f=332")
.

I think that you should ask the forum.

---

### Post by trungvkvk on 2011-08-13
can I  join the topic?.
 I am a newbie so do not know what is involved to learn.
 thanks

---

### Post by Deltik on 2011-08-13
> **trungvkvk said:**
> can I  join the topic?.
 I am a newbie so do not know what is involved to learn.
 thanks
Does this issue of HDMI on ATI Mobility Radeon HD 5000 Series affect you?

---

### Post by s3Pol on 2011-09-27
With radeon driver I can use HDMI port, by puting this in xorg.conf:

Section "Device"
       Identifier  "ATI Card"
       Driver      "radeon"
       BusID       "PCI:1:0:0"
EndSection

The BusID is the result of "lspci | grep ATI".
Tonight i will test with ATI driver, i think that my problem was I not specify the card that i want use.

Sorry for my english... :)

---

