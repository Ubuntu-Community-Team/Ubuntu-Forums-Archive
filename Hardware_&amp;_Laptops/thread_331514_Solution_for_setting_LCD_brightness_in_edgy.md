---
title: "Solution for setting LCD brightness in edgy"
date: 2007-01-04
forum: Hardware &amp; Laptops
---

### Post by Mr. Sinister on 2007-01-04
I've seen lots of posts about problems setting the lcd brightness under edgy, so I thought I'd share my solution. I have a dell e1705 notebook. Brightness is controlled by the file:

/proc/acpi/video/VID/LCD/brightness
```
levels:  12 60 12 24 36 48 60 72 84 100
current: 84
```
I wrote a script that reads the current value and adjusts it up or down in steps of 12. The only problem is, after switching to or from AC power, the file doesn't update, so it adjusts from the previous value. I then set up key shortcuts (Win+Up & Win+Down) to run the script. I tried setting Fn+Up and Fn+Down to do it, but they're apparently not accessible.
```


#!/usr/bin/perl -w
#===============================================================================
#   adjustBrightness.pl
#===============================================================================
my $file = "/proc/acpi/video/VID/LCD/brightness";

unless (scalar(@ARGV) == 1 and ($ARGV[0] eq "up" or $ARGV[0] eq "down"))
{
  die("You must specify 'up' or 'down'.\n");
}
my $direction = shift();

my $setting = "";
my @levels = ();
open(B, $file) or die("Error opening '$file': $!\n");
while (<B>)
{
  if (m#^current: (\d+)$#)
  {
    $setting = $1;
  }
}
close(B);
chomp($setting);

if ($direction eq "up")
{
  $setting+=12;
}
elsif ($direction eq "down")
{
  $setting-=12;
}
exit(0) if ($setting < 12 or $setting > 84);
open(B, ">$file") or die("Error opening '$file': $!\n");
print(B "$setting\n");
close(B);

```

You should be able to modify this setup for your own needs, if your brightness isn't exactly the same.

---

