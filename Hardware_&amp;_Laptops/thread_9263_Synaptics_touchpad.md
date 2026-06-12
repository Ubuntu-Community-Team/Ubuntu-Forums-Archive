---
title: "Synaptics touchpad"
date: 2004-12-26
forum: Hardware &amp; Laptops
---

### Post by muzzy on 2004-12-26
I don't know where to post it: here or in Xfree, but...
I have notebook HP nx9020 with synaptics touchpad. When I'm staring it without external usb mouse everything is ok, but when I leave usb mouse pluged in, touchpad is recognized as ps/2 mouse and xfree don't start (no core pointer). Any Ideas?

---

### Post by iltofa on 2004-12-26
Sorry no idea for your problem :(

I would just suggest to update the bios, but I don't know if it works...

I just want to add a question regarding the opposite problem (on nx9105): my touch pad works without any particular setting, but I've tried to use an external USB mouse and I don't know how to make it works.

I've tried both plug the device after boot-up and plug it before boot the laptop.

During boot-up, when hotplug is loaded, the red light of the mouse turns off....    If I plug it when laptop is already turned on, nothing happens...

any suggestion?

---

### Post by mistic on 2004-12-27
you can try adding this to your xfree-config ( /etc/X11/XF86Config-4 )

```
Section "InputDevice"
Driver "synaptics"
[INDENT]Identifier "Mouse1"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "LeftEdge" "1900"
Option "RightEdge" "5400"
Option "TopEdge" "1900"
Option "BottomEdge" "4000"
Option "FingerLow" "25"
Option "FingerHigh" "30"
Option "MaxTapTime" "180"
Option "MaxTapMove" "220"
Option "VertScrollDelta" "100"
Option "MinSpeed" "0.02"
Option "MaxSpeed" "0.18"
Option "AccelFactor" "0.0010"
Option "SHMConfig" "on"
# Option "Repeater" "/dev/ps2mouse"[/INDENT]
EndSection
```

if that aint enough, try following the whole tutorial [here](http://madpenguin.org/cms/?m=show&opt=printable&id=887) 

grtz
Mistic

PS: for the guy with the reverse problem, are your other USB-devices working well? like a memory-stick or something like that? It sounds to me like that is where the problem lies...

---

### Post by iltofa on 2004-12-27
Sorry! I really forgot to add that no USB device works on my laptop!

So I'm looking for a suggestion about USB in these forums, but I haven't found anything until now....

You're right, the problem is USB...

Thanks....  if you have suggestions about this or found a useful thread, please let me know

Ciao

---

### Post by muzzy on 2004-12-27
But usb device are ok (printer, mouse, pendrive). I have problem only during startup - i cannot plug in usb mouse before entering initlevel other than 1 (when eg. network is configuring i can plug in the mouse). Any ideas?

---

### Post by muzzy on 2005-01-05
I've found solution - xorg <img> - now everything is OK.

---

### Post by dreamminder on 2005-03-05
[SIZE=3]Just disable the usb-legacy support in BIOS. Bye baby boys.
Do not touch the original xorg.conf (Hoary). [http://www.enthea.com.ve](http://www.enthea.com.ve) [/SIZE]

---

### Post by dreamminder on 2005-03-05
I have found somre problems with the toshiba a75-s231, when disable the legasy usb support from BIOS. The problems is that the computer does not reboot property with Linux (it freeze at this process).
I enable again this legacy support
Copy this script into /etc/init.d/   ::
----------------------------Cut Here-----------------------------------------
#!/usr/bin/perl -w
use strict;

my $MOUSENAME = "PS/2 Generic Mouse";
my $LINKNAME = "TouchPad";

print "Finding TouchPad and making device link for X server...\n";

system("rmmod", "psmouse");
system("modprobe", "psmouse");

my %dev = ();
open DEVICES, "/proc/bus/input/devices" or die "cannot read device list";
while(<DEVICES>) {
    chomp;
    if(/^([A-Z]): (.*)/) {
	$dev{$1} = $2;
    } else {
	checkDevice();
	%dev = ();
	next;
    }
}
checkDevice();

sub checkDevice {
    return if !defined $dev{N} or !defined $dev{H};
    return if $dev{N} !~ $MOUSENAME;
    die "No event device found for TouchPad"
	if $dev{H} !~ /(event\d+)/;
    makeLink($1);
    exit(0);
}

sub makeLink {
    print "Mouse is at /dev/input/$_[0]\n";
    chdir "/dev/input" or die;
    unlink $LINKNAME;
    system("ln", "-s", $_[0], $LINKNAME) == 0
	or die "Could not make /dev/input/TouchPad link";
}

--------------------------------------Cut Here----------------------------------------------------

call the file with any name, I proveit  with "findmodem" name


It works fine on me!!!!!!!!!!

---

### Post by NeoEcoS on 2005-03-18
Hello, i have the same problem with my usb mouse, and usb printer on a MSI K7N2 Delta 2 with Nforce2 chipset.

If at startup both are conected, the mouse dosen't works, i have to unplug the muose, unplug printer, plug the mouse, and plug the printer.
When i do it all works.

Run it
#tail -f /var/log/messages
unplug the mouse, and plug it again i get this 
usbhid: probe of 2-1:1.0 failed with error -5

Well, if i want to work with my usb mouse i have to do it.
Note: sometimes the mouse and the printer work well, from startup.

---

