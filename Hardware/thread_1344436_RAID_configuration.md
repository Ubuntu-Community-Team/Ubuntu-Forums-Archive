---
title: "RAID configuration"
date: 2009-12-02
forum: Hardware
---

### Post by impreziv on 2009-12-02
I have 2 500GB hard drives that are setup in a mirrored array. I created the array using the built in RAID software from my motherboard manufacturer. My motherboard is an Asus P5K-E WiFi-AP edition. When I boot into Windows 7 the array shows up as one 500GB drive like it should have I have been using it for months without any issues. However, when I boot into Ubuntu, v9.10 if it matters, it always shows the drives as seperate. How can I get them to show up as a mirrored array like they do in Windows?

---

### Post by impreziv on 2009-12-02
> **impreziv said:**
> I have 2 500GB hard drives that are setup in a mirrored array. I created the array using the built in RAID software from my motherboard manufacturer. My motherboard is an Asus P5K-E WiFi-AP edition. When I boot into Windows 7 the array shows up as one 500GB drive like it should have I have been using it for months without any issues. However, when I boot into Ubuntu, v9.10 if it matters, it always shows the drives as seperate. How can I get them to show up as a mirrored array like they do in Windows?

Problem solved! Thank you for the PM, but you could have posted right in here lol. If anyone else winds up having a similar problem here is what fixed it:

> 
Yeah, I figured it out, basically what I did was I downloaded dmraid and gparted (which was pretty weird) because I would not be able to mount without gparted, unless you know of a command I can use.

This is what I did which I would probably have to make a file to make this happen each time I start the computer since this is only good for one login session.

1)  Open Terminal > dmraid -ay (to activate the raid)
2)  type sudo gparted and gparted opens up and shows the raid
3) Then in the Places Tab on the top, I can click on my RAID system and type root password to mount the drive. Now I have access to it!


I did this and in Places it showed my RAID and the drives separately also. I just did a quick restart and now just the RAID is there!!

---

