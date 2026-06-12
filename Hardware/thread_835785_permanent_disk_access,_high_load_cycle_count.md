---
title: "permanent disk access, high load_cycle_count"
date: 2008-06-20
forum: Hardware
---

### Post by schmost on 2008-06-20
I'm running hardy on a Lenovo N100 laptop and since I executed a modprobe command (for a pcmcia-driver) two days ago, something is permanently accessing the hard drive (the led is blinking + I can hear clicking noises). However, the system doesn't freeze or slow down and the free space isn't getting less either. smartctl -H /dev/sda says 'passed'..
When I run
```
sudo smartctl -A /dev/sda | grep -E "(Load_Cycle_Count|ID)"
```
I get this:
```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       206837
```
The RAW_VALUE is not rising quickly (has not changed for the last 30 minutes..)

This is a new disk I am using, I bought it 3 months ago.. isn't that a too high value!? Does that mean it will stop working any time soon? How can I find out what is accessing the disk and fix it?
Any help would be appreciated!

---

### Post by Odrodzona-Sarmacja on 2008-06-21
My bet is it is gam_server, which you can find in "gksudo mousepad /etc/gamin/gaminrc" and which you can change to other polling values like
"
fsset ext2 poll 10
fsset ext3 poll 10
fsset vfat poll 10
fsset ntfs poll 10
"

---

