---
title: "ACER 5740 Problems"
date: 2010-08-09
forum: Hardware
---

### Post by finemann on 2010-08-09
Hi,

I bought an ACER Aspire 5740 about a month ago. The only problem I face with it is that I am not able to change the display brightness. After some googling I found out that this was a reported bug. Several solutions were also proposed.

[LIST=1]
[*]Blacklisting the acer-wmi (this fixed the error message with the acer-wmi when it starts)

[*]A blog article says to add acpi_osi="Linux" to /etc/default/grub. The author says that he has confirmed it with Arch and Ubuntu 10.04 ([http://linux4tw.wordpress.com/2010/05/10/tips-acer-5740-laptop/](http://linux4tw.wordpress.com/2010/05/10/tips-acer-5740-laptop/)) 

[*]A previous post here asks to change > GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
([http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1477947](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1477947))
[/LIST]

But none of these seems to work for me. Please help. Thanks.

PS: Don't know if this is important or not. Fedora 13 has worser issues and the screen flickers. But on suspending the system and relogging, the problem vanishes.

---

### Post by kennethadammiller on 2010-08-19
I have an Acer Aspire 5740-6025 too, and I would also like to add some things to this post.

I don't know about your Aspire 5740, but on mine, the touchpad isn't recognized as from synaptic. I'm really not too bothered by this, but I have a little bit of control freak in me, and I want to be able to scroll both horizontally and vertically and it's not working. That way. After some time, I sent this to some ubuntu mailing lists and google groups: 

I've been unable to use scroll for a long time on Ubuntu. I would really like to add this feature, but it is proving to be a much more complicated process that what I thought it should be.
I've followed instructions at [https://bugs.launchpad.net/ubuntu/+source/gsynaptics/+bug/132627](https://bugs.launchpad.net/ubuntu/+source/gsynaptics/+bug/132627) and [https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig)

I added the ability to use the vertical scroll on my touchpad, but still, having trouble. When I scroll down it works, but scrolling up gives trouble (it jumps to the very very bottom of the page). I tried to add the program TouchPad from USC, but it fails to initilize with an error report like this:

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

I went through trying to fix that, but I couldn't get it done.  I really don't know where to go.
I do think I found something significant though: the command "xinput list" gives this:


&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; MLK Wireless Keyboard& Laser Mouse          id=10    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; MLK Wireless Keyboard& Laser Mouse          id=9    [slave  keyboard (3)]
    &#8627; CNF7017                                     id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

If you look, you can see that it is NOT detecting a synaptics touchpad.


In addition to the problems with the touchpad and brightness, I'm also having some trouble with the wifi. I also sent this message out about the wifi:


Hi, I'm using Ubuntu 10.04
I'm having trouble staying connected to a wifi network as the subject of my email describes. To give you more detail, I will say that what is happening, is I will suddenly stop receiving data packages. Network Monitor does NOT detect that I am disconnected. I haven't been patient enough to see if it will reconnect on it's own, because simply going up to NM in the top bar and selected the wireless that I want again does the trick. But I don't want to continually have to deal with this problem.

Among the things that I have tried after following some of the forum posts that I have discovered with research are updating the kernel and creating a file /etc/modprobe.conf and placing the lines

alias wlan0 iwlagn
options iwlagn swcrypto50=1 swcrypto=1

inside. I also placed this short line inside the file I created under "/etc/pm/config.d/00sleep_modules": SUSPEND_MODULES="ath9k"

None of these have fixed the problem.

Dmesg | tail reports this:

[http://pastebin.com/4aSJgVMp](http://pastebin.com/4aSJgVMp)

In particular, this line has drawn my attention: [ 2134.207681] wlan0: deauthenticating from 30:46:9a:3d:b2:1a by local choice (reason=3)

I am on an Acer 5740-6025 laptop. The wifi card is supposed to be this:
04:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

Does anyone know why this is happening? or what I can do to fix this?

If anyone has any knowledge about these problems, please let us know. I've been with acer for 2.5 years now, been through 3 laptops: I think they are a really good brand. once everything starts working on them, you're game.

---

### Post by finemann on 2010-08-20
Well your problems are really serious it seems. Luckily I just have the problem with the brightness. Most people I had talked to said that it was an issue with the kernel, and that 10.10 ought to work like a charm. Anyway you could try the alpha release of 10.10 and see if the problem is solved. 10.10 would contain the new updated kernel and drivers. Best wishes

---

### Post by kennethadammiller on 2010-08-20
It's not so much that mine are any different from yours, but I was guessing that you probably weren't able to use the side scrolly thing on your touchpad either. I would also guess that you might have trouble with wifi if you stick around on a WPA long enough too.

Don't you have these problems?

Mine is an Acer 5740-6025

---

### Post by finemann on 2010-08-20
No such problems so far. The touchpad and wi-fi works smoothly. Mine is a 5740 with a Core i3 330M, 3GB RAM, 320GB HD and Integrated Intel Graphics. Yours might be a different model altogether as Acer rolls out different models with the same name.

---

### Post by kennethadammiller on 2010-08-24
Bump

---

### Post by fjskmdl on 2010-09-01
I'm having the same problem with my Acer 5740.
tried updating the GRUB_CMDLINE_LINUX_DEFAULT with several values without success.
I updated to ubuntu maverick testing today, hoping that the problem would be fixed but it remains the same.
I hope there will be a solution soon because more people seem to have the problem.

---

### Post by rlara333 on 2010-09-10
Hey guys,
I have a 5740 with the i5. I too was having issues with the brightness. I solved it by using the kernel on Mostafa Kamal's PPA [http://ppa.launchpad.net/kamalmostafa/linux-kamal-i915bri/ubuntu](http://ppa.launchpad.net/kamalmostafa/linux-kamal-i915bri/ubuntu)  . If you don't want to use that kernel "acpi_osi=" in grub worked also but Kamal's kernel also fixed the "P" button on the computer. 

Hope this helps...

---

### Post by kennethadammiller on 2010-09-19
bump bump bump bumpity 
bumpity bumpitytytyt bump 

bumpish bumping bump

---

### Post by rlara333 on 2010-12-27
Hello,  I'm just checking back to see if any of you had fixed your brightness issues.  I've had no problems since I used Kamal's PPA.

---

