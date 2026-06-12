---
title: "NIC and WNIC detected but do not work"
date: 2016-09-18
forum: Hardware
---

### Post by richk77 on 2016-09-18
I have a Lenovo T440p laptop.  The model is Ubuntu certified.  It's a couple of years old.

I've been running Ubuntu on it since it was new, and recently installed a new HDD, and now I cannot use Ubuntu on it.  There's always been an issue with the install of 14.04 - it just crashes while loading - but in the past I've been able to install 12.04LTS and then upgrade.  When I do this now the WNIC and NIC are not active.  It's bizarre, because it has worked before, and I even used the same 12.04 ISO I downloaded many months ago.  The only differences I can think of are a move from an SSD to a spinning disk, and using Rufus to burn the ISO to a USB stick, but I cannot see how either of these things could affect it.

I've run the LSPCI command and both the NIC and WNIC are listed, but nether works.  The laptop sees no wireless networks and reports the cable state as 'disconnected'.  I certainly know the cable works, because I'm using a different laptop connected to it right now.

I'm only a casual user of Ubuntu, so don't really know where to go from here.  Can anyone suggest the next steps I should take.  Is there a command I can use to force Ubuntu to re-inventory the hardware and install drivers?

---

### Post by TheFu on 2016-09-18
**sudo lshw -C network** - will show the devices AND drivers being used.
**cat /etc/network/interfaces**  - will show the wired connection settings

Please post using code tags.

---

### Post by richk77 on 2016-09-20
I'll get that data, but first, can you please tell me what 'code tags' are?  I don't know - sorry.

---

### Post by TheFu on 2016-09-20
> **richk77 said:**
> I'll get that data, but first, can you please tell me what 'code tags' are?  I don't know - sorry.

[https://ubuntuforums.org/showthread.php?p=12776168#post12776168](https://ubuntuforums.org/showthread.php?p=12776168#post12776168)

---

### Post by richk77 on 2016-09-21
I'm at a total loss now to understand what's happened.  After trying 12.04 and 14.04, Debian, Mint and SUSE - experiencing problems every time with crashing installs or missing NICs, I abandoned hope and installed Windows.  This went on without complaint, and once I had installed the Lenovo drivers for the NIC and WNIC it worked fine.  To try what you suggested I pulled the HDD and put in an un-partitioned SSD.  I wrote the 12.04 ISO from my NAS to the same USB stick I used before and tried again.  This time, NIC and WNIC appeared immediately and both worked.  I installed 12.04 and then upgraded to 14.04.  I'm totally lost.

---

### Post by TheFu on 2016-09-21
At this point, if you don't have a critical reason to run 14.04, switching to 16.04 would be highly recommended to get to a newer LTS release.

12.04 should be deleted. It isn't safe to run a 12.04 desktop anymore because most of the GUI programs haven't been patched in years, even for security issues. Only Canonical maintained packages get the full 5 yrs of support - 3rd party support is limited to whatever that 3rd party decides which might be completely great or terrible.

BTW, newer isn't always an "upgrade", at least not for me. ;)

---

