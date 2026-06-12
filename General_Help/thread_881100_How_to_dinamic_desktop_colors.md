---
title: "How to: dinamic desktop colors"
date: 2008-08-05
forum: General Help
---

### Post by Diabolis on 2008-08-05
I just found this perl script. Its very simple, but you can modify it using different gnome keys. Just think about all the possibilities.

If you use only maximized windows,  you won't see a thing.

It does look good if you use transparent gnome panels or transparent terminals or anything transparent that will show the desktop.

**Instructions: **

Copy the following to a text file and save it as "changeDesktopColor.pl"
[PHP]#!/usr/bin/perl

#Color the background based on system load

# The results from the script will only be visible if you have some portion of the desktop background displaying the primary background color.
#If you have a graphic that covers the whole desktop, then you will not see anything.
#
# This script will change the background color every 15 seconds based on the system load.
# reddish - the system is very active
# yellow - an active process has been running at least 5 minutes
# white - an active process has been running at least 15 minutes
# if no processes are raising the system load, the colors will cycle from green to blue to black.

# Hacking Ubuntu
# Author: Neal Krawetz
# Web site: http://www.wiley.com/WileyCDA/WileyTitle/productCd-047010872X.html

# Keys
my $Primary_Color = "/desktop/gnome/background/primary_color";
#my $Secondary_Color = "/desktop/gnome/background/secondary_color";
#my $Background = "/desktop/gnome/background/picture_filename $File";

my $Load; # system load
my $R, $G, $B; #Red, Green, Blue colors

while (1) {
	$Load=`uptime`; #get the current load
	# format is "time duration, users, load average: 0.00, 0.00, 0.00"
	# remove everything except the first load value
	$Load =~ s/.*: //;
	# load values: 1 minute, 5 minute, 15 minute averages
	# these are colored: 1=Red, 5=Green, 15=Blue
	($R,$G,$B) = split(', ',$Load);

	# scale up to the range 0-255, but cap it at 255
	$R = $R * 255; if ($R > 255) { $R = 255; }
	$G = $G * 255; if ($G > 255) { $G = 255; }
	$B = $B * 255; if ($B > 255) { $B = 255; }
	# convert to hex
	$Load = sprintf "%02x%02x%02x",$R,$G,$B;

	# set the color
	system("gconftool-2 -t str --set $Primary_Color '#$Load'");
	sleep 15; # Update 4 times per minute
}
done
[/PHP]

Make the file executable:
```
chmod +x changeDesktopColor.pl
```

Add it to your sessions
**system / preferences / sessions**

Thats it.

---

### Post by Diabolis on 2008-08-10
Pretty much the same script with two modifications:

- sets a horizontal gradient
- uses the opposite color for the secondary color in the gradient

[PHP]#!/usr/bin/perl

# Command
	my $Command = "gconftool-2 -t str --set";

# Keys
	my $Primary_Color = "/desktop/gnome/background/primary_color";
	my $Secondary_Color = "/desktop/gnome/background/secondary_color";
	# Possible values are "horizontal-gradient", "vertical-gradient", and "solid".
	my $Shading_Type = "/desktop/gnome/background/color_shading_type";

# Set color background with gradient
	system("$Command $Shading_Type horizontal-gradient");

my $Load; # system load
my $R, $G, $B; #Red, Green, Blue colors

while (1) {
	$Load=`uptime`; #get the current load
	# format is "time duration, users, load average: 0.00, 0.00, 0.00"
	# remove everything except the first load value
	$Load =~ s/.*: //;
	# load values: 1 minute, 5 minute, 15 minute averages
	# these are colored: 1=Red, 5=Green, 15=Blue
	($R,$G,$B) = split(', ',$Load);

	# scale up to the range 0-255, but cap it at 255
	$R = $R * 255; if ($R > 255) { $R = 255; }
	$G = $G * 255; if ($G > 255) { $G = 255; }
	$B = $B * 255; if ($B > 255) { $B = 255; }
	# convert to hex
	$Load = sprintf "%02x%02x%02x",$R,$G,$B;
	#print "primary: " $Load;

	# set the colors
	system("$Command $Primary_Color '#$Load'");
	$Load = sprintf "%02x%02x%02x",255-$R,255-$G,255-$B;
	system("$Command $Secondary_Color '#$Load'");

	sleep 10; # Update 6 times per minute
}
done[/PHP]

---

