---
title: "hal and xinput"
date: 2009-06-20
forum: Hardware
---

### Post by chrixxer on 2009-06-20
I'm going a little nuts here...  I have a Mini 9 that I've installed 9.04 UNR onto, and I love it, except that the touchpad drives me nuts.  I got SHMConfig working and [FONT="Courier New"]syndaemon[/FONT] for the ignore-while-typing thing, but I'd also like to kill the touchpad entirely whenever I have an external mouse plugged in.  (I spend a fair amount of time on Macs running OS X and I love that feature in its mouse support!)

I've gotten *very* close to getting this working, setting up an FDI for the hardware abstraction layer (hal) to set a script I wrote as a callout for add / remove events triggered by my external USB mouse:

[FONT="Courier New"]_/etc/hal/fdi/policy/mouse.fdi_[/FONT]

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="USB Optical Mouse">
        <append key="info.callouts.add" type="strlist">mouse_touchpad</append>
        <append key="info.callouts.remove" type="strlist">mouse_touchpad</append>
      </match>
  </device>
</deviceinfo>
```

Then I created the script itself (here it's bloated with debug logging):

[FONT="Courier New"]_/usr/lib/hal/scripts_[/FONT]

```
#!/usr/bin/perl
use warnings;
use strict;

my $action = $ENV{'HALD_ACTION'} || 'add';
my $logstring = $0 . " called with euid '" . $> . "' and HALD_ACTION '" . $action . "'";
print $logstring . "\n";
`/usr/bin/logger '$logstring'`;

my @udis = `/usr/bin/hal-find-by-capability --capability input.touchpad`;
foreach my $udi (@udis) {
	chomp $udi;
	my $cmd = "/usr/bin/hal-get-property --udi $udi --key info.product";
	my @results = `$cmd`;
	foreach my $product (@results) {
		chomp $product;
		my $xinput = "/usr/bin/xinput set-int-prop \"" . $product . "\" \"Device Enabled\" 8 ";
		my $message;
		if($action eq 'add') {
			$message = "Disabling $udi";
			$xinput .= "0";
		} else { 
			`/usr/bin/logger 'Enabling $udi'`;
			$xinput .= "1";
		}
		`/usr/bin/logger 'Disabling $udi'`;
		my $cmdoutput = `$xinput`;
		`/usr/bin/logger '$xinput result: $cmdoutput'`;
		my $lclcmd = "/usr/bin/xinput list-props \"" . $product . "\" | /bin/grep Device";
		$cmdoutput = `$lclcmd`;
		`/usr/bin/logger 'Current state of $product is: $cmdoutput'`;
	}
}
```

When I run this as root or via [FONT="Courier New"]sudo[/FONT], I get the output in [FONT="Courier New"]/var/log/messages[/FONT] I expect to see, and the touchpad goes inactive as it's supposed to:

```
Jun 20 15:39:01 galileo chris: /usr/lib/hal/scripts/mouse_touchpad called with euid 0 and HALD_ACTION add
Jun 20 15:39:01 galileo chris: Disabling /org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input
Jun 20 15:39:01 galileo chris: /usr/bin/xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 0 result: 
Jun 20 15:39:01 galileo chris: Current state of SynPS/2 Synaptics TouchPad is: Device SynPS/2 Synaptics TouchPad: ^IDevice Enabled (109):^I^I0 ^ISynaptics Grab Event Device (282):^I^I1 

```

(Device Enabled 0, and the trackpad is unresponsive, as desired.)

If I disconnect and reconnect the mouse, the callout is obviously getting hit, and the process (the '[FONT="Courier New"]mouse_touchpad[/FONT]' script) is able to spawn other scripts (since it's getting its information about devices from running [FONT="Courier New"]hal-find-by-capability[/FONT] and [FONT="Courier New"]hal-get-property[/FONT] and logging to [FONT="Courier New"]syslog[/FONT] through [FONT="Courier New"]logger[/FONT]).  However, xinput doesn't seem to be firing off when it's being called as a hal callout by way of my Perl script; here's the logged information when it gets called as a callout:

```
Jun 20 15:44:41 galileo kernel: [25286.992163] usb 2-1: USB disconnect, address 2
Jun 20 15:44:41 galileo logger: /usr/lib/hal/scripts/mouse_touchpad called with euid 0 and HALD_ACTION remove
Jun 20 15:44:41 galileo logger: Enabling /org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input
Jun 20 15:44:41 galileo logger: Disabling /org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input
Jun 20 15:44:41 galileo logger: /usr/bin/xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 1 result: 
Jun 20 15:44:41 galileo logger: Current state of SynPS/2 Synaptics TouchPad is: 
Jun 20 15:44:41 galileo logger: /usr/lib/hal/scripts/mouse_touchpad called with euid 0 and HALD_ACTION remove
Jun 20 15:44:41 galileo logger: Enabling /org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input
Jun 20 15:44:41 galileo logger: Disabling /org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input
Jun 20 15:44:41 galileo logger: /usr/bin/xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 1 result: 
Jun 20 15:44:41 galileo logger: Current state of SynPS/2 Synaptics TouchPad is: 
Jun 20 15:44:45 galileo kernel: [25290.912118] usb 2-1: new low speed USB device using uhci_hcd and address 3
Jun 20 15:44:45 galileo kernel: [25291.131473] usb 2-1: configuration #1 chosen from 1 choice
Jun 20 15:44:45 galileo kernel: [25291.191282] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input24
Jun 20 15:44:45 galileo kernel: [25291.216551] generic-usb 0003:04D9:048E.0010: input,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:1d.0-1/input0
Jun 20 15:44:45 galileo logger: /usr/lib/hal/scripts/mouse_touchpad called with euid 0 and HALD_ACTION add
Jun 20 15:44:45 galileo logger: Disabling /org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input
Jun 20 15:44:45 galileo logger: /usr/bin/xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 0 result: 
Jun 20 15:44:45 galileo logger: Current state of SynPS/2 Synaptics TouchPad is: 
Jun 20 15:44:45 galileo logger: /usr/lib/hal/scripts/mouse_touchpad called with euid 0 and HALD_ACTION add
Jun 20 15:44:46 galileo logger: Disabling /org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input
Jun 20 15:44:46 galileo logger: /usr/bin/xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 0 result: 
Jun 20 15:44:46 galileo logger: Current state of SynPS/2 Synaptics TouchPad is: 
```

The script runs but xinput evidently isn't being run, or run properly, and so the state of the touchpad is never modified.

Help?!

Many, many thanks!
Chris

---

