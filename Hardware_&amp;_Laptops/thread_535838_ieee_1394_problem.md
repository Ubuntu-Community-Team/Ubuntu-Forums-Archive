---
title: "ieee 1394 problem"
date: 2007-08-27
forum: Hardware &amp; Laptops
---

### Post by hunkybill on 2007-08-27
Hi,

I compiled kino 1.1.1 to try some digital video edits. I modified /etc/modules to include loading raw1394 at bootup. I notice that I have a device /dev/raw1394 owned by root in the group plugdev, of which my login account is a member with r/w permissions.

I have a Canon DV camera that I plug into the 1394 port on my laptop, running 7.04. I try the Edit->Preferences tab to set my AV/C setting, and nothing shows up.

When I try to capture.. I get errors about IEEE 1394 not working or no R/W permissions on /dev/raw1394.

dmesg tells me:   ieee1394: Error parsing configrom for node 0-00:1023

What can I do to get my DV camera working with 7.04 here? Looking at a lot of forum threads has suggested many things.. none of which seem too relevant here. Any tips most appreciated.

Thanks

---

