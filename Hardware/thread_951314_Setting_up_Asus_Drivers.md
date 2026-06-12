---
title: "Setting up Asus Drivers"
date: 2008-10-18
forum: Hardware
---

### Post by dharmabum4732 on 2008-10-18
Hello,

I use Ubuntu 8.04, and I'd like to install some drivers for my motherboard, but I'm a bit confused as to how to go about doing so.

Asus offers drivers for my motherboard (P5E3 Premium) on their website; but after I downloaded the file and tried to read the various sets of instructions (seemingly indecipherable), I find myself left where I started.

The drivers that asus offers are audio (which already works fine), LAN (again, already works), Raid, and WiFi.

Please let me know if any other information would be helpful regarding this matter.

Thanks,
-Max

---

### Post by shwick on 2008-10-18
You don't need motherboard drivers, it should just work auto-magically :)

---

### Post by dharmabum4732 on 2008-10-18
Hi Shwick,

I wish it did work auto-magically, but the magic doesn't seem to work concerning both wireless and raid.

In order to get these working, I hoped that the Linux drivers that Asus offers would be the solution, but I haven't figured out a way to install them.

Any advice?
-Max

---

### Post by shwick on 2008-10-19
What's the motherboard model?
The first few lines of
```
sudo lshw
```
should give you the information if you don't know. It's in the line starting with product:
Also, post the output of 
```
lspci
```
and maybe i can help with the wireless.
I've never set up RAID though, never used it...someone else will probably show up for that.

---

### Post by nickolasemp on 2009-03-12
I know it's kinda late but check ...[these instructions right here]("http://ubuntuforums.org/showpost.php?p=5346272&postcount=15")

Then just disable and enable each time your networking(next to the clock icon...right click it...)

---

