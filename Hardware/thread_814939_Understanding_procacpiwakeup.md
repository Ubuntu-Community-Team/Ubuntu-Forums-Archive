---
title: "Understanding /proc/acpi/wakeup"
date: 2008-06-01
forum: Hardware
---

### Post by NZJon on 2008-06-01
Hi,

I'm running Ubuntu 8.04 on an AMD (x86_64) platform, have have been able to get suspend working, which is really great. 

However, I've been trying to get my machine to wake up after a suspend, without having to use the computer's power button. From reading [http://www.uluga.ubuntuforums.org/showpost.php?p=4466270&postcount=4](http://www.uluga.ubuntuforums.org/showpost.php?p=4466270&postcount=4) I know I need to set up my /proc/acpi/wakeup correctly, but I don't understand exactly what I am doing.

I would like to enable WOL (ethernet "Wake On Lan"), PS2 keyboard and mouse and USB device to wake up the machine after a suspend. The contents of my /proc/acpi/wakeup are:

```
jon@black:/etc/acpi$ cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
HUB0	  S5	 disabled  pci:0000:00:06.0
XVR0	  S5	 disabled  pci:0000:00:0f.0
XVR1	  S5	 disabled  pci:0000:00:0e.0
XVR2	  S5	 disabled  pci:0000:00:0d.0
XVR3	  S5	 disabled  pci:0000:00:0c.0
XVR4	  S5	 disabled  pci:0000:00:0b.0
XVR5	  S5	 disabled  pci:0000:00:0a.0
UAR1	  S5	 disabled  pnp:00:07
PS2M	  S4	 disabled  pnp:00:09
USB0	  S4	 disabled  pci:0000:00:02.0
USB2	  S4	 disabled  pci:0000:00:02.1
AZAD	  S5	 disabled  pci:0000:00:06.1
MMAC	  S5	 disabled  pci:0000:00:08.0
MAC1	  S5	 disabled  pci:0000:00:09.0
```

Obviously I can do the following to enable USB:

```
root#black> echo UCH1 > /proc/acpi/wakeup
```

and this works. But, what are the other devices? Is there a way to work out what, for example, XVR2 actually is? How do you go from the device "code" and the "system node" to knowing exactly what is what? What would be the difference between the USB0 an USB2 devices? And, finally, what would I "activate" in order to enable the ethernet WOL to wake up the machine after a suspend?

Many thanks for any help you can give.

Cheers,

   Jon



(And, just in case anyone asks, yes, I have enabled WOL by using ethtool.)
```

jon@black:/etc/acpi$ sudo ethtool eth0:
Settings for eth0::
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	**Supports Wake-on: g**
	Wake-on: g
	Link detected: yes
```

---

### Post by sdennie on 2008-06-01
Wow, that's really interesting.  I wasn't even aware of that file but, it seems really interesting.  Those look like things that are exported via ACPI and probably very machine dependent.  Probably the only way you could figure out what each device is would be to: 1) Enable stuff and figure out what it does by trial and error.  2) Decompile the DSDT and see if you can understand the code (quite hard to do actually) 3) Ask google really, really nicely to tell you what each device is.

Regardless, I'll look into that file a bit more.  I'm really surprised that it can be written to.

---

### Post by sdennie on 2008-06-01
I looked at this a bit more and, you might be able to do an "lspci" and correlate the pci device number of your ethernet card to the device numbers displayed in /proc/acpi/wakeup and enable it.  No way to try this out though.

---

### Post by NZJon on 2008-06-02
Hi vor,

Bingo! That's what I needed to know:
```
lspci
```

The output from that matched the "System Nodes" reported in /proc/acpi/wakeup, and so I can correctly enable the devices I wanted to be able to wakeup from a suspend.

Many thanks,

  Jon

---

### Post by sdennie on 2008-06-02
Glad that helped.  Now I'm wondering how many people I've told, "Your laptop won't resume on lid open because your BIOS doesn't support it", when in reality, a simple echo to /proc/acpi/wakeup might do the job...  Neat file.

---

### Post by NZJon on 2008-06-02
Yep, it certainly is good when you make a discovery like this!

I thought I had everything fixed, but it looks as though a suspend-and-wakeup cycle only works once for me. If I suspend the machine after it has already been suspended-and-woken-up, it fails to wake up. Sigh. I think I saw something like this in the forums a while ago, so I shall have to search out that solution now...

Hey, think how many people you can make happy by saying you've found a (potential) fix for their resume-on-lid problems!!

Cheers,

   Jon

---

### Post by sdennie on 2008-06-02
How does it fail to resume?  If it fails with a completely white screen and you are using nvidia, it probably isn't completely failing.  Blindly type in your password to the white screen and the machine will come back up.

---

### Post by NZJon on 2008-06-03
Hi vor,

Thanks for your reply. When I say it fails to resume, what I mean is that once I have suspended the machine for the second time, it will no longer respond to any of:

- WOL packets
- PS2 mouse/keyboard
- USB device
- power button

I have to use the reset button (which I think physically breaks the power circuit, whereas the power button sends a signal to the motherboard...?) to restart the machine.

I shall keep searching... and thanks for your help,

   Jon

---

### Post by sdennie on 2008-06-03
Unfortunately, suspend/resume failures are very laptop/motherboard specific.  About all I can do is point you at the things that may hold a fix for you: /etc/default/acpi-support (which may not be useful in Hardy anymore) and all the stuff in /usr/lib/pm-utils.

---

### Post by vashwood on 2008-06-03
So you were able to see your system nodes for your NIC?  It doesn't seem to match up for me.  I will post the outputs when I get home today.

I also remember seeing a solution about fixing WOL if it has been woken up a 2nd time.  I'll try to search for it too.

---

### Post by vashwood on 2008-06-03
This is my output.  Any ideas?

```
ryan@ubuntu:~$ cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
PCI0	  S4	 disabled  no-bus:pci0000:00
PCI1	  S4	 disabled  pci:0000:00:01.0
PCI2	  S4	 disabled  pci:0000:00:1e.0
USB0	  S4	 disabled  pci:0000:00:1f.2
USB1	  S4	 disabled  pci:0000:00:1f.4
AC97	  S4	 disabled  
ryan@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] (rev 11)
02:09.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)

```

---

### Post by NZJon on 2008-06-03
Hi there vashwood,

I'd agree, it looks like your ADMtek NIC does not have a corresponding entry in /proc/acpi/wakeup. Is it a seperate card, or is it a built-in NIC? If its a seperate card, then maybe you have to use a WOL lead to connect the card to the motherboard (as shown at the top of this page: [http://www.andrewmallett.net/tech/networks/wake_on_lan.htm](http://www.andrewmallett.net/tech/networks/wake_on_lan.htm) -- ignore the rest of it, only the pictures are of interest). If it's a built-in NIC, then I can only guess that you might need to set up the BIOS to enable the NIC to wakeup the machine.

Other than those suggestions, there's not much more I can say. I only found out about the lspci command a few days ago, and the /proc/acpi/wakeup a few days before that!

Hope that helps,

  Jon

---

### Post by vashwood on 2008-06-03
Thanks.  It's a separate PCI card and I have a cable that directly hooks it up to the Motherboard.  I'm just not sure if I should be enabling anything in /proc/acpi/wakeup

---

### Post by vashwood on 2008-06-06
I got it to work!!!  I guess I just needed to try it.  I just enabled one of the PCI devices and it seems like it enables them all.  And now I can wake up from suspend s3.  

One last question.  How do I get it to run that command on boot?  I was thinking of adding this to one of the init scripts but I'm not sure which one.

```
 grep 'PCI0.*enabled' < /proc/acpi/wakeup >/dev/null || \
    echo PCI0  > /proc/acpi/wakeup
```

---

### Post by sdennie on 2008-06-06
You may only have to add it to /etc/rc.local.  If that only works over a single suspend/resume cycle then you'd probably also have to create a script with that command in /etc/pm/sleep.d

---

### Post by i speak in math on 2008-06-06
> **NZJon said:**
> Yep, it certainly is good when you make a discovery like this!

I thought I had everything fixed, but it looks as though a suspend-and-wakeup cycle only works once for me. If I suspend the machine after it has already been suspended-and-woken-up, it fails to wake up. Sigh. I think I saw something like this in the forums a while ago, so I shall have to search out that solution now...

Hey, think how many people you can make happy by saying you've found a (potential) fix for their resume-on-lid problems!!

Cheers,

   Jon

sounds like the same problem i have. I can suspend and resume okay once (system is a little unstable) but the second time i try to resume, i get a locked up system (no caps lock toggle). 
```
Device	S-state	  Status   Sysfs node
SLPB	  S4	*enabled   
P32	  S4	 disabled  pci:0000:00:1e.0
EXP1	  S4	 disabled  pci:0000:00:1c.0
EXP2	  S4	 disabled  
EXP3	  S4	 disabled  
EXP4	  S4	 disabled  
EXP5	  S4	 disabled  
EXP6	  S4	 disabled  
```

Apparently, there is supposed to be a LID device???

---

### Post by himikeb on 2008-06-16
I found that the trick to resume on your events working after the 1st time is to add them to the Suspend script.
Read up on the pm-utils package in hardy...
I created a custom-script in /etc/pm/sleep.d, which I named 15enablewol
> #!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
        hibernate|suspend)
                ethtool -s eth0 wol g
                ;;
        thaw|resume)
                ;;
        *)
                ;;
esac

exit 

Now, every time time machine executes all the sleep scripts, it also sets the WOL properly.
(Be sure to chmod +x that script)
Good Luck!

---

### Post by i speak in math on 2008-06-16
can anyone confirm this works? (not that I don't trust it, it's just that I am a linux noob so I and wouldn't know how to fix a destroyed computer)

---

### Post by sdennie on 2008-06-16
> **i speak in math said:**
> can anyone confirm this works? (not that I don't trust it, it's just that I am a linux noob so I and wouldn't know how to fix a destroyed computer)

It looks perfectly safe to me.

---

### Post by i speak in math on 2008-06-16
is that ethZERO or ethOH in there?

This would be my first script (except for following the ndiswrapper directions)

Is it okay to create the a blank file in the sleep.d folder and edit it in the text editor. Then chmod -x it in the terminal? And how would I do that?

---

### Post by NZJon on 2008-06-22
Hi,

That would be ethZERO ("eth0") and not ethOH ("ethO").

To change the execute permission (you want to "chmod +x" the file, not "chmod -x" as you have written) you would do:

```

sudo chmod +x /etc/pm/sleep.d/15enablewol

```

and confirm with:

```

ls -l /etc/pm/sleep.d/15enablewol

```

In the output from the ls command, you'll see something like:

```

lrwxrwxrwx 1 root root 31 2008-05-20 15:41 /etc/pm/sleep.d/15enablewol

```

the "x"s in the first bit means that the file is executable.

Hope that helps,

   Jon

---

### Post by dwang on 2008-07-17
I spent a couple of frustrating days trying to get suspend and hibernate working with wake on lan for 8.04 (hardy).

Here is what I did to accomplish this:

1. Configure your ethernet card for wake on lan:

/usr/bin/sudo /usr/sbin/ethtool -s eth1 wol g

replace eth1 with your interface

2. Modify /proc/acpi/wakeup to enable S4 state for the PCI bridge that your ethernet card is connected to:

root@desktop:# cat /proc/acpi/wakeup
Device  S-state   Status   Sysfs node
PEGP      S4     disabled
P0P2      S4     enabled   pci:0000:00:1e.0        [COLOR="Red"]<=========[/COLOR]
AC97      S4     disabled
USB0      S3     disabled  pci:0000:00:1d.0
USB1      S3     disabled  pci:0000:00:1d.1
USB2      S3     disabled  pci:0000:00:1d.2
USB3      S3     disabled  pci:0000:00:1d.3
USB7      S3     disabled  pci:0000:00:1d.7
UAR1      S4     disabled  pnp:00:06
PEX1      S4     disabled  pci:0000:00:1c.0
PEX2      S4     disabled  pci:0000:00:1c.1
PEX3      S4     disabled  pci:0000:00:1c.2
PEX4      S4     disabled  pci:0000:00:1c.3
AZAL      S4     disabled  pci:0000:00:1b.0
PWRB      S4    *enabled

grep 'P0P2.*enabled' < /proc/acpi/wakeup >/dev/null || echo P0P2  > /proc/acpi/wakeup

Mine happens to be P0P2

use the command lspci to figure this out for your machine.

example:

lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)    [COLOR="Red"]<=========[/COLOR]
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
05:02.0 Ethernet controller: Intel Corporation 82546GB Gigabit Ethernet Controller (rev 03)
05:02.1 Ethernet controller: Intel Corporation 82546GB Gigabit Ethernet Controller (rev 03)


3. Modify 50modules in /usr/lib/pm-utils/sleep.d 

Comment out the call to  "unload_network"

4. Run sudo pm-suspend or sudo pm-hibernate and test out WOL

---

### Post by mak666 on 2008-09-15
I've finally found the info I need to get my server running how I want! Hurrah!

Except - when I try to modify /proc/acpi/wakeup - I always get "permission denied"...

> more wakeup 

PCI0      S5     disabled  no-bus:pci0000:00
USB3      S3     disabled  pci:0000:00:10.0
USB4      S3     disabled  pci:0000:00:10.1
USB5      S3     disabled  pci:0000:00:10.2
USB6      S3     disabled  pci:0000:00:10.3
USB7      S3     disabled  pci:0000:00:10.4
AC97      S5     disabled  
UAR1      S5     disabled  pnp:00:08

then running either 

> echo PCI0 > /proc/acpi/wakeup

or

> sudo echo PCI0 > /proc/acpi/wakeup 

results in 

bash: wakeup: Permission denied

I've also found (from other forums) that I might need to do 

> echo "LAN0 S3 enabled" > /proc/acpi/wakeup

but that still gets "permission denied".

I suspect I simply cannot "modify" what I'm trying to modify - as that PCI0 entry of "nobus:pci0000:0" looks suspicious. 

My lspci output shows my two ethernet ports as ; 

00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)

neither of which are shown in /proc/acpi/wakeup - even though ethtool eth0 shows "pumpg" is supported and "g" is enabled (and WOL is indeed enabled in the BIOS).

Can someone help? I'm guessing it's a "dumb noob" problem, if so - easily fixed I hope!

---

### Post by sdennie on 2008-09-15
Try:

```

sudo sh -c "echo PCI0 > /proc/acpi/wakeup"

```

Anytime you do redirection like that with sudo, you'll need to to use the sudo sh -c syntax to keep the whole construct running as root.

---

### Post by mak666 on 2008-09-17
Thanks Vor, that hit the spot. 

more /proc/acpi/wakeup now shows me ; 

```
Device	S-state	  Status   Sysfs node
PCI0	  S5	 enabled   no-bus:pci0000:00
USB3	  S3	 disabled  pci:0000:00:10.0
USB4	  S3	 disabled  pci:0000:00:10.1
USB5	  S3	 disabled  pci:0000:00:10.2
USB6	  S3	 disabled  pci:0000:00:10.3
USB7	  S3	 disabled  pci:0000:00:10.4
AC97	  S5	 disabled  
UAR1	  S5	 disabled  pnp:00:08
```

However, still no joy on WOL from hibernate. It must be a hardware issue - because my understanding is that whilst "off", and with WOL enabled - the network light on the ethernet port should remain lit, and presumably the NIC should maintain it's IP address with my router - which is not being done, the IP drops off the router as soon as the PC hibernates.

I'm chasing this down with VIA in their forums - and if I get anywhere, I'll post somewhere appropriate here for others to find. 

Thanks for the help!

---

### Post by ccl4 on 2008-09-20
hello,
hibernate does not work, when my pc hibernates, nothing happens, just the display becomes dark and i can not wake it up!
please help
thanks

---

### Post by fusionisthefuture on 2008-10-03
does anyone know how to change the s-state of the /proc/acpi/wakeup entries?

---

### Post by Nameless Neko on 2008-10-04
Edit: nevermind

---

### Post by c.monty on 2008-10-21
did anybody figure out why a NIC listed with lspci is not available in /proc/acpi/wakeup?

and has anybody managed to fix this resulting in a working WOL?
if yes, what did you do?

---

### Post by wootah on 2008-12-23
Question: Why did the above folk want WOL ? What were your environments and reasons for doing so ?

thxthx :)

---

### Post by NTolerance on 2009-01-10
Got it working on my system.  Contents of /proc/acpi/wakeup prior to getting started:

```
Device	S-state	  Status   Sysfs node
RP02	  S3	 disabled  pci:0000:00:1c.1
PXS3	  S4	 disabled  pci:0000:05:00.0
LANC	  S4	 disabled 
PS2K	  S3	 disabled  pnp:00:09
PS2M	  S3	 disabled  pnp:00:0a

```

"LANC" seemed like the one, verified working by running this command:

```
sudo sh -c "echo LANC > /proc/acpi/wakeup"
```

I then made the change permanent by creating the script /etc/init.d/wakefroms3.sh with these contents:

```
#!/bin/sh
# Set /proc/acpi/wakeup to allow PCI ethernet device to wake system
# sudo sh -c "echo LANC > /proc/acpi/wakeup"
echo LANC > /proc/acpi/wakeup

```

I added the script to my system startup with this command:

```
sudo update-rc.d /etc/init.d/wakefroms3.sh defaults
```

---

### Post by SirGe on 2009-03-16
After struggling with getting WOL working for a few days, I found a solution, that works for me on Intrepid (8.10). I am running a Q6600 on A-bit IP35 PRO.

Since I am an Ubuntu noob, I had to discover a few things; maybe others will benefit or laugh :)
- getting WOL to work after shutdown was pretty easy by adding an entry to *rc.local* to do the **ethtool -s eth0 wol g** and setting _NETDOWN_ to _no_ in */etc/default/halt*; this did not do anything for WOL from S3 (suspend).
- the mechanism used by default to handle sleep/wake does not use any of the scripts in */etc/acpi*; it uses the config from */etc/pm* and scripts from */usr/lib/pm-utils*
- */proc/acpid/wakeup* is a legacy mechanism, being replaced by entries in sysfs in individual device node directories named *power/wakeup*; just **cat** the file to see if the device is enabled for waking up the system
- in my case looking at **lspci -tv** output and poking the matching name into */proc/acpi/wakeup* worked to get the box to wake up on USB mouse events, so I did not have to dive under the desk, but did NOT work for WOL
- once I figured out the real stuff was in sysfs, I found the proper entries there by doing **lspci -tv** and looking through sysfs. I did not find the nodes for my ethernet controllers in any of the nicely named directories; they were all the way at the bottom of */sys/devices/pci0000:00* tree - just look for the path defined by components of the tree location in **lspci** output.
- when I did this, I found that the PCI bridge was enabled for wakeup (by my poking at */proc/acpi/wakeup*), but the network card itself was not
- once I found the proper */sys/devices/...* directory entry, I just did **echo enabled > power/wakeup** there
- at this point I added the above with a hardcoded path to my ethernet interface to *rc.local* to make it stick. I have not found a better way to get the sysfs path, than by laboriously parsing the **lspci -tv** output, which seems lame. Based on [this blog]("http://blog.dustinkirkland.com/2009/02/ubuntu-server-suspendhibernateresume.html"), I am inferring that the support in jaunty for this may make anything I do redundant.

Have fun!

---

### Post by jnewm on 2009-03-16
I can't believe it!  Thanks to everyone on this thread, but especially SirGe.

How in the hell did you figure all that out???!!!  I had been messing with WoL (wake on lan) for like 12 hours straight... super frustrated that it would work from s5 (turned off), but not from pm-suspend (which is another story, since that didn't even work for me at first).

Anyway, I'm going to try to post my experience after a bit of sleep, in case it helps anyone too.  But the short of it is that, once I got pm-suspend working, SirGe's trick did the rest.

(However, as a relative newb, it took me a while to figure out each of the steps...  And most difficult, that besides enabling the PCI bridge, I also had to find my network card and enable it...  which was way buried at "sys/devices/pci0000:00/pci_bus/0000:00/device/0000:00:1e.0/0000:01:08.0" for me.)

Anyway, thanks again :)

PS Question for SirGe, would you mind terribly telling me exactly how you set this to rc.local, so I don't have to navigate and do it myself each time?

---

### Post by SirGe on 2009-03-16
Thanks, jnewm - I am glad it helped.

As far as *rc.local*, pretty much literally, man...

Here is what it says in my */etc/rc.local*:

```
# hack to make sure mouse/kbd wake up the box
name=`/usr/local/bin/acpiek --vendor 046d --product c517`
if [ "X$name" != "X" ]; then
    echo $name > /proc/acpi/wakeup
fi

# turn on wake on lan
/usr/sbin/ethtool -s eth0 wol g

# hack to enable wakeup for eth0
echo enabled > /sys/devices/pci0000:00/0000:00:1e.0/0000:04:00.0/power/wakeup

exit 0

```

**acpiek** is my little hack, so I did not have to hardcode the name in */proc/acpi/wakeup* to poke; if anyone wants it, I will post it - it's just a short perl script.

I suspect there may be a better place for this stuff, than rc.local, but it works...

Oh, and on an unrelated subject.. just figured out that if you enable login sound at the System/Admin/Login Window, it will break your pulseaudio and it will take you MANY hours to figure out how to fix it. So don't! :) Basically, the audio handling chain before and after login is different, so you do not want sounds playing from the pre-login context (i.e. login applet) while your session is trying to shoehorn pulseaudio into the stack. Just listen to the pretty Gnome login sound and leave it be.

---

### Post by SirGe on 2009-03-16
Umm... This is a leetle embarassing, but just a tiny bit of digging around in */sys* will show that instead of diving down into the the pci tree as directed by *lspci -tv* address guts, you can just:

```
echo enabled > /sys/class/net/eth0/device/power/wakeup
```

How very spiffy of the guys that did the work on sysfs!

And no understanding of /proc/acpi/wakeup required! ;)

Enjoy!

---

### Post by frioux on 2009-04-28
Hey guys!

I got the regular WOL working (from off) but I can't seem to get it to work with suspend.  This is what I have in my rc.local:

```

ethtool -s eth0 wol g
echo enabled > /sys/class/net/eth0/device/power/wakeup
```

and then I can do 

```
sudo wakeonlan 00:24:8c:02:e0:65
```

from my laptop to start from off.  I've tried using wakeonlan and etherwake both from the laptop to the desktop to try to resume it but nothing happens.  I clearly have the BIOS set right for WOL from off, but I'm not really sure about WOL from suspend.  Any ideas?

---

### Post by Rob_Frohne on 2009-04-29
Hi Everyone,

How does this work in Jaunty?  I try to echo enabled > wakeup and it stays blank.  I try and sudo vi wakeup and it acts like it cannot be written, saying:

"wakeup" E667: Fsync failed
WARNING: Original file may be lost or damaged
don't quit the editor until the file is successfully written!

I am trying to make wake on LAN work for a lab of Dell GX270 computers.  I can wake from hibernate and from off, but not S3 suspend.

I find that the wakeup for my network is already enabled, but the PCI bus doesn't seem to be, and I was trying to enable that wakeup file.

Where did you find the information on sysfs that was pertinent to this?

Thanks,

Rob

---

### Post by meatlover on 2009-04-30
Hey, 

I'm having some problems with suspend on my machine.  Here is a description of my problem:

[https://bugs.launchpad.net/ubuntu/+bug/368873](https://bugs.launchpad.net/ubuntu/+bug/368873).

Here is a copy of my wakeup file:

```
cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
RP00	  S4	 disabled  pci:0000:00:01.0
P0P1	  S4	 disabled  pci:0000:00:1e.0
USB0	  S3	 disabled  pci:0000:00:1d.0
USB1	  S3	 disabled  pci:0000:00:1d.1
USB2	  S3	 disabled  pci:0000:00:1d.2
USBR	  S3	 disabled  
EUSB	  S3	 disabled  pci:0000:00:1d.7
USB3	  S3	 disabled  pci:0000:00:1a.0
USB4	  S3	 disabled  pci:0000:00:1a.1
USB5	  S3	 disabled  pci:0000:00:1a.2
USBE	  S3	 disabled  pci:0000:00:1a.7
HDAC	  S3	 disabled  pci:0000:00:1b.0
RP01	  S4	 disabled  pci:0000:00:1c.0
GLAN	  S3	 disabled  pci:0000:02:00.0
RP03	  S4	 disabled  pci:0000:00:1c.2
RP04	  S4	 disabled  
RP05	  S4	 disabled  
RP06	  S4	 disabled  
RP07	  S4	 disabled  
RP02	  S3	 disabled  pci:0000:00:1c.1
WLAN	  S3	 disabled  pci:0000:03:00.0
SLPB	  S4	*enabled   

```

I enabled all of the settings above and tried to suspend and it didn't work.  Also here is my lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9300M GS (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
07:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:03.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:03.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:03.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```

Please let me know if you have any ideas.

---

### Post by Rob_Frohne on 2009-05-01
Hi,

This thread is about getting wake to work from various devices like the LAN.  

It appears that you may not have enabled everything to wake your laptop up, unless you are posting the /proc/acpi/wakeup file before you made changes.  

To make changes to that file do this:

sudo su

echo USB0 > /proc/acpi/wakeup

The look at the file and you will see USB0 enabled instead of disabled as it now appears.  Now a USB mouse for example connected to USB0 should be able to wake your laptop if everything else is working right.

See this web page for some more on how to enable interfaces.

[http://www.averyjparker.com/ubuntu-linux/](http://www.averyjparker.com/ubuntu-linux/)

You may also want to look at this wiki too, though it may be a tad out of date.

[https://wiki.ubuntu.com/UnderstandingSuspend](https://wiki.ubuntu.com/UnderstandingSuspend)

Good luck!

Rob

---

### Post by Rob_Frohne on 2009-05-01
> **Rob_Frohne said:**
> Hi Everyone,

How does this work in Jaunty?  I try to echo enabled > wakeup and it stays blank.  I try and sudo vi wakeup and it acts like it cannot be written, saying:

"wakeup" E667: Fsync failed
WARNING: Original file may be lost or damaged
don't quit the editor until the file is successfully written!

I am trying to make wake on LAN work for a lab of Dell GX270 computers.  I can wake from hibernate and from off, but not S3 suspend.

I find that the wakeup for my network is already enabled, but the PCI bus doesn't seem to be, and I was trying to enable that wakeup file.

Where did you find the information on sysfs that was pertinent to this?

Thanks,

Rob

I found a solution at this link.   (See my previous post for a summary of that site.) 


[http://www.averyjparker.com/ubuntu-linux/](http://www.averyjparker.com/ubuntu-linux/)


I had to enable PCI1, which allowed wakeup to occur from S3 sleep.  Note that the /proc/acpi/wakeup file has S5 in the row for PCI1, and so I wasn't sure it would apply, but it worked fine.

I hope this helps someone else save some power.

Best regards,

Rob

---

### Post by TiredBird on 2009-05-09
My thanks to the many contributors to this thread. Although I still have not solved all of my problems, I have at least found a fix for one of them. 
```

sudo su
echo PS2K > /proc/acpi/wakeup

```
The foregoing fixed the problem of not being able to wakeup from mouse or keyboard action. (The one command took care of both.) I am adding a startup script to enable this on boot.

The problem I still have is that the GUI, (Ubuntu 8.10 i386 and Ubuntu 9.04 amd64, both running on a custom desktop with ASUS K8N motherboard and AMD64 processor), does not give me any options for suspend or hibernate. I have to initiate them from the command line.

Any suggestions regarding this?

---

### Post by TiredBird on 2009-05-10
My problems related to suspend and hibernate have been solved thanks to the posts in  [http://ubuntuforums.org/showthread.php?t=1144999]("http://ubuntuforums.org/showthread.php?t=1144999.") and this thread.

---

### Post by vamsiguturu on 2009-05-20
I have a setup with a client doing a TCP download from a server(Both are Linux Fedora Core 10).I changed the rmem_max and wmem_max from 64KBytes to 256KBytes.My purpose is to check the throughput at different TCP Window size. But unfortunately I get same at all sizes.

Let me know the place where I can configure the TCP Window size like in Iperf tool.

---

### Post by MaximCarnage on 2009-05-28
Thanks goes to all the advice given by the great people here.   :D

I finally got WOL to work and it feels good to know how to do it.   :D

........
I spoke too soon :(
WOL works only for the first 10 seconds after putting the pc to standby, after that it doesn't register the magic packet anymore :(
........
I hope the Ubuntu developers  makes Wake-On-Lan retard-proof in the next release

---

### Post by eltucaso on 2009-09-14
Hi all; I have WOL working fine for me, and I am using it over a wireless network.  The process to get it up and running is very simple, it just took a lot of research to get there.  I am a complete Ubuntu noob, I have less than 48 hours of messing around with it.  My XP got out of control and OS X on a PC is not an easy undertaking.     
 

     First of all, I would like to say that none of this is original work to myself; everything here is copied from some other knowledgeable Ubuntu guru, probably from this forum.  I have only translated their work into English and compiled it into a simple tutorial.  Now, how to get it working...
 

     My setup:  I have a home wireless LAN, my Ubuntu 9.04 machine (a Gateway Computer with a media bay and additional NIC) is acting as the server: I have an XBOX, MacBook Pro, and MacBook as the clients.  I have two wireless routers, a WRT600N v1.1 setup with DD-WRT (which using a ATFTP took a few hours of fun to get working, and is the central hub of my network, the Ubuntu server is wired to this router) and a WRT54G connecting my entertainment system (TV, BLU RAY, XBOX, etc) to the wireless network, also running off DD-WRT, and acting as a bridge.  I only use WOL to wake the server so I can backup data or download pictures and stuff to the MacBooks.  I am using a program on my MacBooks (Leopard) called WakeOnLan v.1.0, which will wake my Ubuntu 9.04 after the below listed mods, but will not put it to sleep (there is a button for that).  I have my Ubuntu machine set to sleep after 45 minutes of non-use.     
 

     Neither Suspend or Hibernate works on the Ubuntu server, thus it does not work for WOL; if I try to use hibernate I always get some "thaw" message on shutdown, then have to hard-boot it.  If I suspend I get a non-stop beeping from the CPU and no boot-up on power-up.  If you hard-boot the system then WOL does not work.  The computer must have been soft shut down to work.   Since neither hibernate or suspend work, due to my graphics card (ATI RADEON 9800 pro), which there are no ATI drivers for, only the generic ones that come stock with 9.04 don't fit the bill (the generic xorg drivers allow both hibernate and suspend to take place on my system, but to re-boot a hard shutdown is necessary).  So, the only method to avoid hibernating or suspending and a hard-boot is to disable them.  You can do that by doing the following: Press ALT-F2, type gconf-editor, in left pane browse to apps->gnome-power-manager->general. In right part of the window uncheck can_hibernate and can_suspend options
 

     With the below mods, my server now wakes with either the above listed program or from the keyboard.  I'm sure I could spend a few minutes working out how to get the mouse to wake it but am not interested in that .  So,...onto the mods...
 

     Before any mod you need to go into your BIOS and turn on WOL.  If it is not there, my understanding is that you must have a NIC that is WOL compliant and connected via a special cable to the mother board.  I have the option on my MB/BIOS so I don't know about how things work if you don't.   
 

     I also had to set up Samba on Ubuntu (not too hard) and on the Mac (easy, just Google them), and setup Ubuntu to auto-mount on boot the desired partition.  This is best done (I think) with a program called Storage Device Manager (there are several tools out there, some of them obsolete with 9.04).  SDM is not too intuitive, at least for a noob, but after installation (under add/remove programs, same as Samba) use the assistant to set it up for mounting at boot.  SDM messed up the privileges for 2 internal drives, changing the permissions to root only for mount and edit; without using FSTAB I rebooted and used SDM, and had to re-work the mount points for the Samba shares afterwards.  Now that that is done, they are visible on boot from the net.     
 

     There are several mods to be made in Ubuntu; including one to a file and one to the startup configuration.  From what I gather every time you re-boot Ubuntu certain files are not maintained for startup, so you have to add the changes you want (to use WOL) to a script to load the changes on each startup.  Correct me here somebody if I'm off a bit, but I know the startup changes have to be made, regardless.   
 

     So, in Ubuntu go to your terminal and enter the following commands:
 

 _**first**_: configure ethernet card for WOL, type in terminal:
         /usr/bin/sudo /usr/sbin/ethtool -s eth0 wol g   
             (replace eth0 with your interface, you could add other modifiers, type man ethtool to see the other WOL options)
 

 _**second**_: modify your wakeup file to wakeup from your chosen devices:
         to view what is "enabled" already, type in terminal:
             cat /proc/acpi/wakeup
 

 

 monster@monster-desktop:/$ cat /proc/acpi/wakeup 
 Device    S-state      Status   Sysfs node 
 TANA      S4     **enabled**   pci:0000:**02:01.0**  ****ethernet card
 P0P3      S4     **enabled**   pci:0000:00:**1e.0**  ****PCI
 AC97      S4     disabled   
 USB0      S3     **enabled**   pci:0000:00:**1d.0**  ****my keyboard
 USB1      S3     disabled  pci:0000:00:1d.1 
 USB2      S3     disabled  pci:0000:00:1d.2 
 USB3      S3     disabled  pci:0000:00:1d.3 
 USB7      S3     disabled  pci:0000:00:1d.7 
 UAR1      S4     disabled  pnp:00:06 
 SLPB      S4    **enabled    *****my power button, by default already enabled
 

     To decypher what needs to be enabled, you will have to cross reference two lists; the wakeup file (the above cat command) and the lspci file (just type lspci).  Your system will be different from my system, so you will have to do some analysis here.
 

 monster@monster-desktop:/$ lspci 
 00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02) 
 00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02) 
 00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge (rev 02) 
 00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02) 
 00:**1d.0** USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) 
 00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) 
 00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) 
 00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) 
 00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) 
 00:**1e.0** PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) 
 00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02) 
 00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) 
 00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) 
 00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02) 
 01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] 
 01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary) 
 **02:01.0** Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller 
 03:02.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02) 
 03:03.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04) 
 03:03.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04) 
 03:04.0 Modem: Smart Link Ltd. SmartLink SmartPCI562 56K Modem (rev 03) 
 

     With both of those files listed in your terminal, compare the first parts of the lspci line with the last parts of the wakeup file lines. You will see that all of the wakeup file items are in the lspci file, but not the other way around.  Once you have figured out what is what, you will want to ensure you have a PCI device and whatever else you want to use to boot your machine enabled.  To change what is enabled and what is not, do the following
 

 _**third**_: change the disabled to enabled, type in terminal:
         sudo sh -c "echo P0P3 > /proc/acpi/wakeup"
             do this for each item, then run cat /proc/acpi/wakeup to verify it worked
 

 _**fourth**_: you need to set you startup configuration so that it keeps these changes after each re-boot.  To do that we need to create a script: simply type in terminal:
 

     sudo vi /etc/init.d/wakefmsleep.sh  
 

     To use vi, an editor, push &#8220;a&#8221; then type the text I have below (or just right click and paste it).  When finished typing, hit ESC to quit input, then &#8220;ZZ&#8221; to save the file.
 

 Example script file, the result of the above instructions:
 

 #!/bin/sh 
 # Set /proc/acpi/wakeup to allow PCI ethernet device to wake system 
 # sudo sh -c "echo LANC > /proc/acpi/wakeup" 
 echo P0P3 > /proc/acpi/wakeup 
 echo TANA > /proc/acpi/wakeup 
 echo USB0 > /proc/acpi/wakeup 
   
     Now that the script is created, there are two commands left to finish up the startup configuration.  Type in terminal:  
 

         sudo update-rc.d wakefmsleep.sh defaults
         sudo chmod +x /etc/init.d/wakefmsleep.sh
 

 You should be finished.  If you followed, verbatim minus the exact script lines, you should be good to go.  I have made some other changes on my system, and I don't know if they affected my success or not. There were changes under the System-Administration-Authorizations section.  I changed the WOL section to all yes and added my user below.  I also got WICD, and I am pretty sure the DD-WRT on my router is enabling the wireless use of the WOL (I enabled it on there too, and added my server as a host).  I hope I did not plagiarize too much from others in the forum; I am only hoping to help others waste less time figuring this out.  Maybe somebody smart could turn this into a GUI thing and save a lot of people a lot of time...

---

### Post by Roo on 2009-11-27
I found this thread helpful in getting my Ubuntu 9.10 system configured to work with WOL.  

I blogged about it here: [http://www.lowtek.ca/roo/2009/wake-on-lan/](http://www.lowtek.ca/roo/2009/wake-on-lan/)

Hopefully my experience may help others and thanks to those that posted to this thread.

Roo

---

### Post by |V|utley on 2009-12-03
I have been trying for months to get WOL from suspend working on my Ubuntu 8.04 then 8.10 machine, but to no avail.

When I came across this thread I had high hopes, but alas nothing here seems to work.  I'm sooo close - it really seems to me that it should work, so I'm hoping that I'm missing something obvious and that the clever peeps on this forum can point it out to me!

My machine is a few years old, its running a motherboard with an integrated NIC that does support WOL.  The BIOS has been set to allow magic packets (the setting is called PME).  When the machine is shutdown (to the S1 state), it can be restarted via WOL.  When put into suspend (S3, using pm-suspend), WOL does not work, but clicking the left mouse button does work.

In other words, suspend and resume do work, it is simply that WOL to resume from suspend doesn't.  Now I know this hardware can do that, because it used to run Windows XP, and resume from suspend always worked.

I have tried all the things list in this post (and in other threads), but what I have noticed is that when ever I resume from suspend (via the mouse), the WOL flag on the NIC (set by using ethtool) has gone.  It is definitely set correctly before going into suspend.  I don't know if this is because the network module is unloaded at suspend, or it is actively being unset at suspend or....?  I have tried putting in scripts all over the place to stop the network being unloaded on suspend, but I cannot tell if it is working (except WOL doesn't work).  I do know that the NIC remains powered at suspend and shutdown however - the lights remain on at the router.

One other thing.  In setting /proc/acpi/wakeup, and /sys/.../wakeup, as outlined in this thread I used lspci to look at PCI devices to match to /proc/acpi/wakeup.  Here is what I have in /proc/acpi/wakeup:

```
Device	S-state	  Status   Sysfs node
PCI0	  S4	 enabled   no-bus:pci0000:00
PS2K	  S4	 disabled  pnp:00:05
USB1	  S4	 disabled  pci:0000:00:02.2
USB2	  S4	 disabled  pci:0000:00:02.3
MDM	  S4	 disabled
```

Here is what I get from lspci:
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO] (rev 10)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0d.0 USB Controller: NEC Corporation USB (rev 41)
00:0d.1 USB Controller: NEC Corporation USB (rev 41)
00:0d.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc R360 NJ [Radeon 9800 XT]
01:00.1 Display controller: ATI Technologies Inc RV350 NJ [Radeon 9800 XT] (Secondary)
```

I don't see any direct match between lspci and /proc/acpi/wakeup.  I assumed that I just needed to enable PCI0, as the PCI bridge, but that didn't work.  Should I be doing something to add the ethernet controller to /proc/acpi/wakup?

Sorry for the long post, but I'd really appreciate any help!

---

### Post by |V|utley on 2009-12-08
An update:

I decided to start again.  I installed Windows XP Pro in one partition, just to prove that WOL from suspend does work, and yep it definitely does.

I then installed Ubuntu 9.10 on another partition (I'd upgraded to 9.10 before).  This time, I can get WOL from suspend to work, but only once (as others have found), because the "g" flag gets dropped from the ethtool setting on each resume.

I've rechecked /proc/acpi/wakeup and /sys/class/net/eth0/device/power/wakup, and they are both disabled for PCI0 and eth0 specifically, but it still works in general, so it doesn't seem to be directly related to that.

What I did to make the wol flag stick was this:

Add the ethtool command (ethtool -s eth0 wol pg) to /etc/rc.local, to set it on boot.
Add the same ethtool command to 55NetworkManager (the resume section) under /usr/lib/pm-utils/sleep.d

The seems a bit of a hack but it works.  Its better than setting up a cron job to do the same thing!

I did try creating my own script in /usr/lib/pm-utils/sleep.d to reset the wol flag, but it didn't work.  Does any one know how those scripts work?  Do you have to tell the suspend/resume functions to run this extra script, or should you just be able to drop another script in that directory and it will run?

---

### Post by CazperII on 2010-01-12
I am also trying to wake up my desktop (asus P5B) with WOL, but for some strange reason I cannot get any PCI device enabled in /proc/acpi/wakeup.

Some output:

```

$ lspci -tv
-[0000:00]-+-00.0  Intel Corporation 82P965/G965 Memory Controller Hub
           +-01.0-[0000:01]----00.0  nVidia Corporation G73 [GeForce 7600 GS]
           +-1a.0  Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4
           +-1a.1  Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5
           +-1a.7  Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2
           +-1b.0  Intel Corporation 82801H (ICH8 Family) HD Audio Controller
           +-1c.0-[0000:04]--
           +-1c.3-[0000:03]----00.0  Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller
           +-1c.4-[0000:02]--+-00.0  JMicron Technology Corp. JMB362/JMB363 AHCI Controller
           |                 \-00.1  JMicron Technology Corp. JMB362/JMB363 AHCI Controller
           +-1d.0  Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3
           +-1d.7  Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1
           +-1e.0-[0000:05]--+-01.0  Xilinx Corporation RME Hammerfall DSP
           |                 \-02.0  D-Link System Inc DGE-528T Gigabit Ethernet Adapter
           +-1f.0  Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller
           +-1f.2  Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller
           +-1f.3  Intel Corporation 82801H (ICH8 Family) SMBus Controller
           \-1f.5  Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller

```

```

$ cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
P0P2	  S4	 disabled  pci:0000:00:01.0
P0P1	  S4	 disabled  pci:0000:00:1e.0
UAR1	  S4	 enabled   pnp:00:06
PS2K	  S4	 enabled   pnp:00:0d
EUSB	  S4	 enabled   pci:0000:00:1d.7
USBE	  S4	 enabled   pci:0000:00:1a.7
P0P4	  S4	 disabled  pci:0000:00:1c.0
P0P5	  S4	 disabled  
P0P6	  S4	 disabled  
P0P7	  S4	 disabled  pci:0000:00:1c.3
P0P8	  S4	 disabled  pci:0000:00:1c.4
P0P9	  S4	 disabled  
USB0	  S4	 enabled   pci:0000:00:1d.0
USB1	  S4	 enabled   pci:0000:00:1d.1
USB2	  S4	 disabled  pci:0000:00:1d.2
USB3	  S4	 disabled  
USB4	  S4	 disabled  pci:0000:00:1a.0
USB5	  S4	 disabled  pci:0000:00:1a.1

```

The realtek ethernet controller is POP7 (pci:0000:00:1c.3)

I have tried to enable any of the "POP" devices using the following command:

```
$ su -c "echo POP7 > /proc/acpi/wakeup"
```

PCI and PCI-EXPRESS devices are enabled in the BIOS for waking up the system. Still all the POP devices stay disabled. Other devices like USB0 do work with the same command...

Any ideas?

Edit: Maybe another clue, if I run this command (as root):

```
$ echo enabled > /sys/class/pci_bus/0000\:00/power/wakeup
```

I get the message:

```
bash: echo: write error: Invalid argument
```

---

### Post by egpetrich on 2010-02-21
To CazperII: It's hard to tell for certain, but you may be typing your command incorrectly. On my system at least, the device "P0P1" is "P-zero-P-one", not "P-Oh-P-one". Sometimes I wish that the system font still kept the slash through the numeral "0".

---

### Post by egpetrich on 2010-02-21
Hello All,

This thread has been *very* helpful. Last night, I managed to get my system to wake-on-LAN from S3 (suspend). I had all but given up on the possibility, but then a sequence of thread references led me here.

I have an Intel D845PEBT2 motherboard with integrated LAN. I had managed to get wake-on-LAN to work from S5 (shutdown); wake-on-LAN from S3 didn't work out of the box, but the PS/2 keyboard would wake the system.

My starting configuration:
```
$ sudo ethtool eth0
...blah blah...
Supports Wake-on: g
Wake-on: g
...blah blah...

$ lspci -tv
-[0000:00]-+-00.0  Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
           +-01.0-[0000:01]----00.0  nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x]
           +-1d.0  Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
           +-1d.7  Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
           +-1e.0-[0000:02]--+-06.0  Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller
           |                 \-08.0  Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller
           +-1f.0  Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
           +-1f.1  Intel Corporation 82801DB (ICH4) IDE Controller
           +-1f.3  Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
           \-1f.5  Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller

$ cat /proc/acpi/wakeup
Device  S-state   Status   Sysfs node
P0P1      S4     disabled  pci:0000:00:1e.0
UAR1      S4     disabled  pnp:00:07
USB0      S3     disabled  pci:0000:00:1d.0
USB1      S3     disabled  pci:0000:00:1d.1
USB2      S3     disabled  pci:0000:00:1d.2
USB3      S3     disabled  pci:0000:00:1d.7
AC97      S4     disabled
SLPB      S4    *enabled
```
It took me a little digging to realize that the network controller itself wasn't the thing disabled; the bridge above it was (I think that's the correct term).
So after careful consideration, I did this:
```
sudo sh -c 'echo enabled > /sys/devices/pci0000\:00/0000\:00\:1e.0/power/wakeup'
sudo sh -c 'echo P0P1 > /proc/acpi/wakeup'

```
(Note that the device name is "papa-zero-papa-one", not "papa-oscar-papa-one". It took me a bit to figure that one out.)
Now I have:
```
$ cat /proc/acpi/wakeup
Device  S-state   Status   Sysfs node
P0P1      S4     enabled   pci:0000:00:1e.0
UAR1      S4     disabled  pnp:00:07
USB0      S3     disabled  pci:0000:00:1d.0
USB1      S3     disabled  pci:0000:00:1d.1
USB2      S3     disabled  pci:0000:00:1d.2
USB3      S3     disabled  pci:0000:00:1d.7
AC97      S4     disabled
SLPB      S4    *enabled

$ cat /sys/devices/pci0000\:00/0000\:00\:1e.0/power/wakeup
enabled
```
Now I can go to S3 with "sudo powersave --suspend-to-ram" and then use wake-on-LAN to come out of it. Even better, the "enabled" state doesn't get lost along the way; I have gone through at least two suspend-resume cycles without a problem. I'm not sure if both of the above commands are necessary, or if only one did the trick. I'll probably just put both of them into /etc/rc.local and be done with it.

Thanks to everyone for doing the hard work for me. You made my weekend!

---

### Post by MartinAyla on 2010-03-07
Hi

Thanks for a very informative thread so far :)

I have a problem though.

I want to enable wake from usb device, so that I can wake XBMC (mediacenter), when suspended, with my remote.

But, when I run:
```
cat /proc/acpi/wakeup
```

The only entries I have are these:
```
Device	S-state	  Status   Sysfs node
ADP1	  S3	 disabled  
LID0	  S3	*enabled   
EC	  S3	 disabled  
OHC1	  S3	 disabled  pci:0000:00:04.0
EHC1	  S3	 disabled  pci:0000:00:04.1
OHC2	  S3	 disabled  pci:0000:00:06.0
EHC2	  S3	 disabled  pci:0000:00:06.1
GIGE	  S5	 disabled  pci:0000:00:0a.0
```

Is it possible to add entries to this list?

PS. I'm running Ubuntu Karmic on a MacBookPro5,5

I really hope someone can help :)

Thanks
Martin

---

### Post by MartinAyla on 2010-03-07
OK, so I found out that OHC1, OHC2, EHC1 and EHC2 are the USB controllers.

So I guess one of those needs enabling.

Can someone tell me how I identify which one of the 4 controllers my USB IR receiver is connected to?

I read that you should only wakeup-enable one device, otherwise it could cause conflicts.

Here is lspci:
```
htpc@htpc:~$ lspci -tv
-[0000:00]-+-00.0  nVidia Corporation MCP79 Host Bridge
           +-00.1  nVidia Corporation MCP79 Memory Controller
           +-03.0  nVidia Corporation MCP79 LPC Bridge
           +-03.1  nVidia Corporation MCP79 Memory Controller
           +-03.2  nVidia Corporation MCP79 SMBus
           +-03.3  nVidia Corporation MCP79 Memory Controller
           +-03.4  nVidia Corporation Device 0a98
           +-03.5  nVidia Corporation MCP79 Co-processor
           +-04.0  nVidia Corporation MCP79 OHCI USB 1.1 Controller
           +-04.1  nVidia Corporation MCP79 EHCI USB 2.0 Controller
           +-06.0  nVidia Corporation MCP79 OHCI USB 1.1 Controller
           +-06.1  nVidia Corporation MCP79 EHCI USB 2.0 Controller
           +-08.0  nVidia Corporation MCP79 High Definition Audio
           +-09.0-[0000:01]--
           +-0a.0  nVidia Corporation MCP79 Ethernet
           +-0b.0  nVidia Corporation MCP79 SATA Controller
           +-10.0-[0000:02]----00.0  nVidia Corporation C79 [GeForce 9400M]
           +-15.0-[0000:03]----00.0  Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller
           \-16.0-[0000:04]----00.0  Agere Systems FW643 PCI Express1394b Controller (PHY/Link)
```

And here is my USB IR receiver from lsusb:
```
Bus 004 Device 003: ID 0471:0815 Philips eHome Infrared Receiver
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        16
  idVendor           0x0471 Philips
  idProduct          0x0815 eHome Infrared Receiver
  bcdDevice            0.00
  iManufacturer           1 Philips
  iProduct                2 eHome Infrared Transceiver
  iSerial                 3 PH00SD4S
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               0
Device Status:     0x0001
  Self Powered

```

---

### Post by MartinAyla on 2010-03-08
If anyone else is reading this...

I had to enable OHC1 and OHC2, *only*, for it to work.

With the USB2 controllers enabled, the machine woke from sleep by itself, right after suspending.

---

### Post by hemish on 2010-03-21
This thread helped a lot.

I finally noticed that a lspci needs the -tv option to show the info I needed to match /proc/acpi/wakeup.

For a T43 I got this:

cat /proc/acpi/wakeup 
Device	S-state	  Status   Sysfs node
LID	  S3	*enabled   
SLPB	  S3	*enabled   
UART	  S3	 disabled  pnp:00:09
EXP0	  S4	 enabled   pci:0000:00:1c.0
EXP1	  S4	 enabled   
EXP2	  S4	 enabled   pci:0000:00:1c.2
EXP3	  S4	 enabled   
PCI1	  S4	 disabled  pci:0000:00:1e.0
USB0	  S3	 disabled  pci:0000:00:1d.0
USB1	  S3	 disabled  pci:0000:00:1d.1
USB3	  S3	 disabled  pci:0000:00:1d.3
USB7	  S3	 disabled  pci:0000:00:1d.7
AC9M	  S4	 disabled  

lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
0b:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8d)
0b:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

Notice the ethernet controller here does not match anything in wakeup, but with option -tv I see the match, enable 1c.0 and all is good :)

lspci -tv
-[0000:00]-+-00.0  Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
           +-01.0-[0000:01]----00.0  ATI Technologies Inc M22 [Mobility Radeon X300]
           +-1c.0-[0000:02]----00.0  Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express
           +-1c.2-[0000:03-0a]--
           +-1d.0  Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
           +-1d.1  Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
           +-1d.2  Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
           +-1d.3  Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
           +-1d.7  Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
           +-1e.0-[0000:0b-0e]--+-00.0  Ricoh Co Ltd RL5c476 II
           |                    \-02.0  Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection
           +-1e.2  Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
           +-1f.0  Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801FBM (ICH6M) SATA Controller
           \-1f.3  Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller

---

### Post by skaramanger on 2010-03-23
Greettings,

I am trying to get my home server to wake properly from suspend/hibernate.  I can get it to power on from an issued poweroff command using a magic packet. I have pm-utils, ethtool installed.

```
Device	S-state	  Status   Sysfs node
PS2K	  S4	 disabled  pnp:00:0a
NSMB	  S4	 disabled  pci:0000:00:01.1
USB0	  S4	 disabled  pci:0000:00:02.0
USB2	  S1	 disabled  pci:0000:00:02.1

NMAC	  S5	 disabled  pci:0000:00:07.0 << I have activated this using ethtool -s eth0 wol g

P0P1	  S4	 disabled  pci:0000:00:04.0
HDAC	  S4	 disabled  pci:0000:00:05.0
BR10	  S4	 disabled  pci:0000:00:09.0
BR11	  S4	 disabled  pci:0000:00:0b.0
BR12	  S4	 disabled  pci:0000:00:0c.0
PWRB	  S4	*enabled   
```

From above what else do I need to wake up to allow the system to come up completely. I was having partial success with wakeonlan, however the fan would come on but no monitor or keyboard access and a ssh connection could not be established.

```
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)

```
My servers hardware: sudo lshw

```
myeserver
    description: Desktop Computer
    product: MS-7309
    vendor: MSI
    version: 1.0
    serial: To Be Filled By O.E.M. < just an aside any software I can use to mod here?
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
    configuration: chassis=desktop uuid=00000000-0000-0000-0000-001D92BF4A38
  *-core
       description: Motherboard
       product: MS-7309
       vendor: MSI
       physical id: 0
       version: 1.0
       serial: To be filled by O.E.M. < or here?
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: MS-7309
          physical id: 0
          version: V1.11 (04/03/2008)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 2628MHz
          capacity: 2628MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good nopl pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
     *-memory:0
          description: System Memory
          physical id: 2a
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM Synchronous 333 MHz (3.0 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM Synchronous 333 MHz (3.0 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 module=i2c_nforce2
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:1
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht bus_master cap_list
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          logical name: scsi2
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd
        *-cdrom
             description: DVD-RAM writer
             product: SPD2415P
             vendor: PHILIPS
             physical id: 0.1.0
             bus info: scsi@2:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: SP03
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:1d:92:bf:4a:38
          size: 100000000
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=xxx.xxx.xxx.xxx latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
        *-disk
             description: ATA Disk
             product: ST3320620AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.AA
             serial: 6QF45AKC
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=00030a07
           *-volume:0
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                logical name: /dev/.static/dev
                version: 1.0
                serial: 
                size: 286GiB
                capacity: 286GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                configuration: created=2010-03-18 15:21:57 filesystem=ext3 modified=2010-03-22 23:58:42 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2010-03-22 23:58:01 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 11GiB
                capacity: 11GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 11GiB
                   capabilities: nofs
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
        *-display UNCLAIMED
             description: VGA compatible controller
             product: GeForce 8500 GT
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: latency=0
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:3
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
```

The server it is running intrepid 8.10 kernel:

Linux myserver 2.6.27-17-server #1 SMP Fri Mar 12 02:48:52 UTC 2010 x86_64 GNU/Linux


```
myserver@theuser:~$ cat /etc/init.d/wakefromS3.sh
#!/bin/sh
# Use ethtool to set lan card to wake from sleep,poweroff,hibernate
ethtool -s eth0 wol g
# Set /proc/acpi/wakeup to allow PCI ethernet device to wake system
# sudo sh -c "echo NMAC > /proc/acpi/wakeup"
echo NMAC > /proc/acpi/wakeup
myserver@theuser:~$ 
```

I have a feeling I'm not too far away.  If you've read this far. Thank you.  I hope someone like yourself might have a suggestion/resolution to my problem

TIA,
skaramanger

---

### Post by skaramanger on 2010-03-24
bump anyone?

---

### Post by egpetrich on 2010-03-28
skaramanger, your e-mail is unclear about whether the NMAC entry in /proc/acpi/wakeup ends up reading "enabled" after you execute "ethtool -s eth0 wol g". If it doesn't show as "enabled", then there may be something still left to do.
I had to enable the PCI bridge above my Ethernet controller to allow the wakeup to work. Your device doesn't look like it's below a PCI bridge, but I wonder if another device needs to be enabled.
Can you post the output of the command "lspci -tv"? I'm really bad at deducing how the devices are treed, and this output is fairly helpful.

---

### Post by skaramanger on 2010-03-28
egpetrich thanks for your reply.

> **egpetrich said:**
> skaramanger, your e-mail is unclear about whether the NMAC entry in /proc/acpi/wakeup ends up reading "enabled" after you execute "ethtool -s eth0 wol g". If it doesn't show as "enabled", then there may be something still left to do.
I had to enable the PCI bridge above my Ethernet controller to allow the wakeup to work. Your device doesn't look like it's below a PCI bridge, but I wonder if another device needs to be enabled.
Can you post the output of the command "lspci -tv"? I'm really bad at deducing how the devices are treed, and this output is fairly helpful.

```
user@server:~$ lspci -tv
-[0000:00]-+-00.0  nVidia Corporation MCP61 Memory Controller
           +-01.0  nVidia Corporation MCP61 LPC Bridge
           +-01.1  nVidia Corporation MCP61 SMBus
           +-01.2  nVidia Corporation MCP61 Memory Controller
           +-02.0  nVidia Corporation MCP61 USB Controller
           +-02.1  nVidia Corporation MCP61 USB Controller
           +-04.0-[0000:01]--  See below Curious?
           +-05.0  nVidia Corporation MCP61 High Definition Audio
           +-06.0  nVidia Corporation MCP61 IDE
           +-07.0  nVidia Corporation MCP61 Ethernet
           +-08.0  nVidia Corporation MCP61 SATA Controller
           +-09.0-[0000:02]----00.0  nVidia Corporation GeForce 8500 GT
           +-0b.0-[0000:03]--
           +-0c.0-[0000:04]--
           +-18.0  Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
           +-18.1  Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
           +-18.2  Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
           \-18.3  Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
user@server:~$ 
```



```
user@server:~$ acpitool -w
   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. PS2K	  S4	 disabled  pnp:00:0a ps2 keyboard?
  2. NSMB	  S4	 enabled   pci:0000:00:01.1 this is the bus right?
  3. USB0	  S4	 disabled  pci:0000:00:02.0
  4. USB2	  S1	 enabled   pci:0000:00:02.1 
  5. NMAC	  S5	 enabled   pci:0000:00:07.0
  6. P0P1	  S4	 disabled  pci:0000:00:04.0 what is this? bridge?
  7. HDAC	  S4	 disabled  pci:0000:00:05.0 usb audio?
  8. BR10	  S4	 disabled  pci:0000:00:09.0 Next 3 are audio of some kind? I found that sometimes turning on 1 of them turns them all on. Sound familiar? What does that mean?
  9. BR11	  S4	 disabled  pci:0000:00:0b.0
  10. BR12	  S4	 disabled  pci:0000:00:0c.0
  11. PWRB	  S4	*enabled   
user@server:~$ 
```


As you can see from above I'm been experimenting a little. I can get it to restart from hibernate, but not suspend to memory/disk.  The power comes on but no signal to the monitor (not necessary for a server right?) and hard drive light comes on but the system doesn't restore. I've been using pm-suspend and pm-hibernate and of course acpitools. 

 I'm not in a hurry. My server is just a home network experiment (March Madness has put a temporary halt to further experimenting :D ). It's just nice to be able to have control over my system and learn something new at the same time. Sorry for all the above questions, the layout is not clear to me. 

Thanks again,

Skaramanger

P.S. After my server, I'll take a shot at my desktop.

---

### Post by egpetrich on 2010-04-15
skaramanger, can you try these commands to see what happens?
```
cat /sys/devices/pci0000\:00/power/wakeup
cat /sys/devices/pci0000\:00/0000\:00\:07.0/power/wakeup
```
I'm casting about a bit here. From what I have seen elsewhere, /sys/devices is another (perhaps deprecated?) way of looking at the devices. On my own system, I had to enable the bridge sitting above my LAN adapter in order for this to work.

One thing that I think would be good to establish is whether you can get into and out of suspend and/or hibernate at all, much less with WOL packets. Your post indicated that you have been using pm-suspend and pm-hibernate. I'm not familiar with these commands; I use "sudo powersave --suspend-to-ram", which may or may not be equivalent. My old P4 system actually uses a PS/2 keyboard, which works to wake the system from suspend.

---

### Post by -jay- on 2010-05-15
i got a question i used the following code 

sudo sh -c "echo USB0 > /proc/acpi/wakeup"

do i have to keep entering that code everytime i want to suspend/resume , i tried it once just to see if it worked well i was able to resume from usb keyboard but got a white snowy background was kinda tricky to log back into lucid

---

### Post by egpetrich on 2010-06-03
@-jay-: You may need to issue the "echo USB0 > /proc/acpi/wakeup" command only once per boot. A lot of this depends on what your system changes when it resumes. Try the command "cat /proc/acpi/wakeup" after resuming to see what the report says about USB0. If the device shows as "enabled", then I don't think that you should need to execute the command again.
If USB0 is always disabled when you boot your system, then you'll need to add the command to a startup script.

---

### Post by peteisi on 2010-06-09
I've been reading through this thread as I have the same issue.  I'm running a Dell Dimension 2400 running Jaunty 9.04.   WOL magic packet can wakeup the system if I use a generic 'sudo halt' but WOL doesn't work if I suspend or hibernate the Dell machine.   Here's my current lspci -tv output:

-[0000:00]-+-00.0  Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
           +-02.0  Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
           +-1d.0  Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
           +-1d.7  Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
           +-1e.0-[0000:01]--+-05.0  Broadcom Corporation BCM4212 v.90 56k modem
**           |                 \-09.0  Broadcom Corporation BCM4401 100Base-T**
           +-1f.0  Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
           +-1f.1  Intel Corporation 82801DB (ICH4) IDE Controller
           +-1f.3  Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
           \-1f.5  Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller

Here's my /proc/acpi/wakeup:
Device    S-state      Status   Sysfs node
VBTN      S4    *enabled   
PCI0       S3     enabled   no-bus:pci0000:00
USB0      S3     disabled  pci:0000:00:1d.0
USB1      S3     disabled  pci:0000:00:1d.1
USB2      S3     disabled  pci:0000:00:1d.2
**PCI1       S5     enabled   pci:0000:00:1e.0**
PCI2       S5     disabled  
KBD        S3     disabled  pnp:00:07

The PCI1 entry in wakeup is enabled as I enabled it using the suggestions in this thread.  I also went ahead and enabled PCI0 to see if that helped (it didn't).  The wakeup file is pretty simple so I don't really see anything else in here I could tweak.   I've tried various other suggestions like changing the /etc/init.d/halt script to set 'NETDOWN=no' but that didn't make any difference either.   Since WOL does work fine if I do a full shutdown, this seems to be a case of suspend/hibernate disabling networking on the way down.  

One thing that I am puzzled about is the fact that the PCI1 entry in the wakeup file is tagged as S5 which, as I understand this, is the full shutdown state.  Should this really be set to 'S3' to work?  If so, how do I change the state for PCI1 in the wakeup file to reflect S3?

---

### Post by -jay- on 2010-06-10
> **egpetrich said:**
> @-jay-: You may need to issue the "echo USB0 > /proc/acpi/wakeup" command only once per boot. A lot of this depends on what your system changes when it resumes. Try the command "cat /proc/acpi/wakeup" after resuming to see what the report says about USB0. If the device shows as "enabled", then I don't think that you should need to execute the command again.
If USB0 is always disabled when you boot your system, then you'll need to add the command to a startup script.

yep thats what it did , it disabled after i rebooted

& when i did resume using the method above it would lag my system

---

### Post by ssulaco on 2010-08-12
> **peteisi said:**
> 
Here's my /proc/acpi/wakeup:
Device    S-state      Status   Sysfs node
VBTN      S4    *enabled   
PCI0       S3     enabled   no-bus:pci0000:00
USB0      S3     disabled  pci:0000:00:1d.0
USB1      S3     disabled  pci:0000:00:1d.1
USB2      S3     disabled  pci:0000:00:1d.2
**PCI1       S5     enabled   pci:0000:00:1e.0**
PCI2       S5     disabled  
KBD        S3     disabled  pnp:00:07

peteisi,I have an older Dell Optiplex,I toggled the KBD
```
john@john-desktop:~$ cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
VBTN	  S4	*enabled   
PCI0	  S3	 disabled  no-bus:pci0000:00
USB0	  S3	 disabled  pci:0000:00:1d.0
USB1	  S3	 disabled  pci:0000:00:1d.1
USB2	  S3	 disabled  pci:0000:00:1d.2
PCI1	  S5	 disabled  pci:0000:00:1e.0
KBD	  S3	 enabled   pnp:00:07

```
I can now resume from standby by pressing a key on the keyboard and/or moving the mouse,rather than pressing the power button,I used "rcsdnj" method in this thread
[http://ubuntuforums.org/showthread.php?t=711747](http://ubuntuforums.org/showthread.php?t=711747)

---

### Post by comodor on 2010-09-10
Hello,

Since the mouse is too sensitive for movements I'm trying to set the wakeup only on keyboard click.
both my mouse and keyboard are connected to the PS2 (PS2M , PS2K).

root@comy-desktop:/proc/acpi# cat wakeup 
Device    S-state      Status   Sysfs node
SLPB      S4    *enabled   
P32      S4     disabled  pci:0000:00:1e.0
PS2M      S4     **disabled**  pnp:00:08
PS2K      S4    ** disabled**  pnp:00:09

When i do echo PS2K > wakeup , both of then changing to enabled.

root@comy-desktop:/proc/acpi# cat wakeup 
Device    S-state      Status   Sysfs node
SLPB      S4    *enabled   
P32      S4     disabled  pci:0000:00:1e.0
PS2M      S4     **enabled**   pnp:00:08
PS2K      S4     **enabled**   pnp:00:09

Does anyone knows a way to enable only one of the devices ?

i've tried to manually enable only the PS2K.
 echo enabled > /sys/devices/pnp0/00:09/power.

but it doesn't seem to work.

Anyone has any idea ?

---

### Post by joseph.piron on 2010-10-23
Hi all!

I have found something (I'm not sure to understand deeply but hey, let's dig..) that may help someone else so I post it.
I was trying to get this feature: wake up my htpc from s3 with my remote control and the solution is to modify /proc/acpi/wakeup and a descriptor in /sys

Here are the details:
I'm using a Microsoft IR receiver for MCE remote that appears as dev 2 of bus 2 in lsusb

root@htpc:~# lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0471:0815 Philips (or NXP) eHome Infrared Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 045e:0714 Microsoft Corp. 
Bus 001 Device 005: ID 045e:0715 Microsoft Corp. 
Bus 001 Device 004: ID 045e:0707 Microsoft Corp. Wireless Laser Mouse 8000
Bus 001 Device 003: ID 045e:070c Microsoft Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

or in lsusb -t :
root@htpc:~# lsusb -t
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 1: Dev 2, If 0, Class=vend., Driver=mceusb, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/8p, 480M
    |__ Port 4: Dev 3, If 0, Class=hub, Driver=hub/4p, 480M
        |__ Port 4: Dev 4, If 0, Class=hub, Driver=hub/3p, 12M
            |__ Port 2: Dev 5, If 0, Class=HID, Driver=usbhid, 12M
            |__ Port 3: Dev 6, If 0, Class=HID, Driver=usbhid, 12M

The first thing I don't really understand is that in /proc/acpi/wakeup
root@htpc:~# cat /proc/acpi/wakeup 
Device	S-state	  Status   Sysfs node
P0P2	  S4	*disabled  pci:0000:00:01.0
P0P1	  S4	*disabled  pci:0000:00:1e.0
PS2K	  S4	*disabled  pnp:00:0e
PS2M	  S4	*disabled  pnp:00:0f
UAR1	  S4	*disabled  pnp:00:10
MC97	  S4	*disabled  
P0P4	  S4	*disabled  pci:0000:00:1c.0
P0P5	  S4	*disabled  pci:0000:00:1c.1
P0P6	  S4	*disabled  
P0P7	  S4	*disabled  
P0P8	  S4	*disabled  
P0P9	  S4	*disabled  
USB0	  S4	*enabled   pci:0000:00:1d.0
USB1	  S4	*disabled  pci:0000:00:1d.1
USB2	  S4	*disabled  pci:0000:00:1d.2
USB3	  S4	*disabled  pci:0000:00:1d.3
EUSB	  S4	*disabled  pci:0000:00:1d.7

that's USB0 I have to enabled, why not usb 1 or 2 (bus 2 in lsusb) ?
Moreover why are all the disabled/enabled preceded with a star and S4 and not S3 mentionned ?

Nevertheless that wasn't enough to get it work. I looked in gconf-editor in apps/gnome-power-manager/general but I have no can-suspend or something similar... (I'm running on 10.10, with 10.04 I could suspend only once, afterwards the computer didn't go to suspend, just black screen then login screen)
So I looked in /sys/ and found that 'cat /sys/bus/usb/devices/2-1/power/wakeup' (notice the 2.1 as bus 2 device 2 (0,1,...) gave 'disabled' so a 
 echo enabled > /sys/bus/usb/devices/2-1/power/wakeup
and now I can wake-up with the remote when I want :)


I hope this thread will help and if someone could answer what I don't understand:
Why USB0 in /proc/acpi/wakeup ?
Why have to change in /proc and /sys ?
Is it possible to automate this to get it work even if I change the usb port the receiver is plugged in ?


 .. thanks :)

---

### Post by joseph.piron on 2010-10-27
Bump up? :)

---

### Post by frafu on 2010-10-29
> **joseph.piron said:**
> 
So I looked in /sys/ and found that 'cat /sys/bus/usb/devices/2-1/power/wakeup' (notice the 2.1 as bus 2 device 2 (0,1,...) gave 'disabled' so a 
 echo enabled > /sys/bus/usb/devices/2-1/power/wakeup
and now I can wake-up with the remote when I want :)


Thanks for the info. I also had an usb mouse that did not wake up the computer. After checking under /sys/... I saw that it was disabled; similar to what you had with your remote. 

By the way, I used the GUI application named "Device Manager" (gnome-device-manager) to get the /sys/... path of the mouse. (It might be simpler to find the right path with this application. Do not forget to enable the details-view under the View menu of the application.)

Finally, I want the echo commands only to be issued if the corresponding items are not enabled. Could anybody please confirm that the following script is correct?
```

#!/bin/bash
#
status_eusb=`cat /proc/acpi/wakeup | grep "EUSB" | awk {'print $3}'`
if [ "$status_eusb" = "*disabled" ]
then
    echo "EUSB" > /proc/acpi/wakeup
fi 
#
echo enabled > /sys/devices/pci0000\:00/0000\:00\:1a.0/usb1/1-1/1-1.4/power/wakeup
#
exit 0

```

Thanks in advance, 

Francesco.

---

### Post by cjkenworthy on 2011-07-04
Hello there.

I've been following this thread in an attempt to get Wake On Lan (WOL) working on a Dell Dimension 2300 running Ubuntu server 11.04 (Natty). But I'm having no success, please can someone help? I've given as much information as possible below.

**lspci -tv**

```

-[0000:00]-+-00.0  Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
           +-02.0  Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
           +-1d.0  Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
           +-1d.7  Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
           +-1e.0-[01]--+-04.0  Ralink corp. RT2561/RT61 802.11g PCI
           |            \-06.0  Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
           +-1f.0  Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
           +-1f.1  Intel Corporation 82801DB (ICH4) IDE Controller
           +-1f.3  Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
           \-1f.5  Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller

```

My ethernet card is WOL capable, as shown by 

**ethtool eth0**

```

	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 32
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000007 (7)
			       drv probe link
	Link detected: yes

```

The ethernet device is a Realtek 8139 as shown in

**lspci**

```

01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

**ifconfig **

```

eth0      Link encap:Ethernet  HWaddr 00:40:f4:3c:88:49  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fe3c:8849/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1403 errors:0 dropped:0 overruns:0 frame:0
          TX packets:743 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:133132 (133.1 KB)  TX bytes:160142 (160.1 KB)
          Interrupt:18 Base address:0xc000 

```

I auto-enable WOL at boot-up and power down in /etc/network/interfaces with:

```

post-up /usr/bin/activateWOL
post-down /usr/bin/activateWOL

```

That file points to the script activateWOL which contains:

```

#!/bin/bash
ethtool -s eth0 wol g

```

Based on lspci I manually "enabled" ACPI devices with:

sudo sh -c "echo HUB0 > /proc/acpi/wakeup"
sudo sh -c "echo PCI0 > /proc/acpi/wakeup"

**cat /proc/acpi/wakeup**

```

Device	S-state	  Status   Sysfs node
PCI0	  S5	*enabled   no-bus:pci0000:00
HUB0	  S5	*enabled   pci:0000:00:1e.0
USB0	  S3	*disabled  pci:0000:00:1d.0
USB1	  S3	*disabled  pci:0000:00:1d.1
USB2	  S3	*disabled  pci:0000:00:1d.2
USB3	  S3	*disabled  pci:0000:00:1d.7
MODM	  S5	*disabled  
UAR1	  S5	*disabled  pnp:00:08

```

I even went as far as "enabling" the ethernet device itself with

```

sudo sh -c "echo enabled > /sys/devices/pci0000\:00/0000\:00\:1e.0/0000\:01\:06.0/power/wakeup"
```

I also tried stopping network manager going to sleep by commenting out lines in suspend_nm() 

/usr/lib/pm-utils/sleep.d/55NetworkManager

```

#!/bin/sh
# If we are running NetworkManager, tell it we are going to sleep.
# TODO: Make NetworkManager smarter about how to handle sleep/resume
#       If we are asleep for less time than it takes for TCP to reset a
#       connection, and we are assigned the same IP on resume, we should
#       not break established connections.  Apple can do this, and it is
#       rather nifty.

. "${PM_FUNCTIONS}"

suspend_nm()
{
	# Tell NetworkManager to shut down networking
        #printf "Having NetworkManager put all interaces to sleep..."
	#dbus_send --print-reply --system                         \
	#	--dest=org.freedesktop.NetworkManager  \
	#	/org/freedesktop/NetworkManager        \
	#	org.freedesktop.NetworkManager.sleep && \
	#   echo Done. || echo Failed.
}

resume_nm()
{
	# Wake up NetworkManager and make it do a new connection
	printf "Having NetworkManager wake interfaces back up..."
        dbus_send --print-reply --system                        \
		--dest=org.freedesktop.NetworkManager \
		/org/freedesktop/NetworkManager       \
		org.freedesktop.NetworkManager.wake && \
	    echo Done. || echo Failed.
}

case "$1" in
	hibernate|suspend)
		suspend_nm
		;;
	thaw|resume)
		resume_nm
		;;
	*) exit $NA
		;;
esac

```

When I shutdown or suspend with the commands:

[B]halt
pm-suspend[/B]

The computer shuts down or suspends correctly (respectively), but when I send a magic packet (from my spare Ubuntu laptop on the same LAN) using:

**wakeonlan 00:40:f4:3c:88:49**

The Dell Ubuntu server fails to wake up. Nothing happens at all. There is no LED activity on the back of the NIC card. However, I did try installing Windows XP to test the card and WOL did work correctly (when I ticked "allow this device to bring the computer out of sleep" in device manager). I used the same wakeonlan command from my spare Ubuntu laptop. (No LEDs were on the Dell Ubuntu server NIC when it was running Windows XP)

I can ping the Dell Ubuntu server when it is on and can ssh in correctly. It just won't wake on LAN when I send a magic packet.

Any ideas? Thank you for your help.

---

### Post by klein de usa on 2011-09-16
cjkenworthy

i just got wol working on a Dell Dimension 2400, i use the information in this link and trial and error to find the right pci network card.

[http://en.community.dell.com/support-forums/desktop/f/3514/t/18189720.aspx]("http://en.community.dell.com/support-forums/desktop/f/3514/t/18189720.aspx")  


BIOS Setup
----------
Power Management
Suspend Mode: S3
AC Power ...: Off
Low Power Mode: Off

System Security
PXE BIS ....: Accept

Auto Power On: Disabled

Remote Wake Up: On (Note: If you don't have this line
in your BIOS then it won't
work. )

NIC Hardware
------------
Broadcom NetXtreme Gigabyte
Note: DO NOT USE the motherboard integrated
NIC/controll

ubuntu 11.04 fresh install
i did no changes except the bios changes stated above, not all pci nic cards will work the one i did get working is:

Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)

and in my experience when the computer is off and the lights on the nic card or nic connector on the mother board aren't lit wol won't work

---

