---
title: "Battery monitoring erratic with Breezy"
date: 2005-10-30
forum: Hardware &amp; Laptops
---

### Post by abovett on 2005-10-30
Hi.

I have a rebadged TwinHead E12B notebook which I've been using OK with Hoary. I upgraded to Breezy and the ACPI is not reading the battery correctly. What happens is that with a fully charged battery the battery status indicator will suddenly drop to almost zero and I will get a warning that my battery is almost flat. Then it will go back up again.

Initially I did an upgrade install but I've since done a clean install and it behaves the same. I've searched the forums and found people reporting problems with not being able to read the status at all, but haven't found anyone with my particular problem.

Looking at /proc/acpi/battery/BAT0/state using:
```
watch -n 1 cat /proc/acpi/battery/BAT0/stat
```
shows that the remaining capacity value is mostly decrementing normally but occasionally a spurious value of 192 mWh appears. It's always 192, and I guess that if the battery monitor catches one of these values as it reads the number it thinks the battery is flat.

In case it was the laptop not Breezy, I tried reinstalling Hoary. The problem goes away. Switch back to Breezy - it comes back.

I wondered if it was a problem with the DSDT (though I don't understand much about them) so I read the wiki page at [https://wiki.ubuntu.com/ACPIBattery]("https://wiki.ubuntu.com/ACPIBattery") and followed it as best I could. The DSDT for the E12B notebook (from  [http://acpi.sourceforge.net/dsdt/index.php]("http://acpi.sourceforge.net/dsdt/index.php"))  appears to already be compiled (it's a .aml file) so I didn't assemble it - just put it in /etc/mkinitramfs/ and reconfigured the kernel package with dpkg-reconfigure, but it didn't make any difference.

So:

1. Anyone else seen this problem?
2. Anyone know what causes this?
3. Was what I did with my DSDT correct?
4. How can I tell if my DSDT is being used. Should dmesg show something?

Update:

I just tried watching the capacity value in /proc/acpi/battery/BAT0/stat whilst charging (rather than discharging). In this case a different spurious value appears: 128 rather than 192. Both of these are pretty round numbers in binary - 10000000 and 11000000 - which seems more than a coincidence, though I don't know what it could mean.

I'm thinking I maybe ought to file a bug report on this, but I'd appreciate any feedback from other people with similar problems.

Andy B

---

### Post by abovett on 2005-11-07
I've had a look at Bugzilla and there appear to be a number of people reporting this or a similar problem. There are several bugs which appear to be duplicates - I added my comments to bug 14050 which appears to be the most active and relevant thread.

Andy B

---

### Post by majed on 2005-11-08
I had this in gnome, but not XFCE..

---

