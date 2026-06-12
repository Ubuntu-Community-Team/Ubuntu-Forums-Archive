---
title: "acpi critical point reached 95C"
date: 2008-08-20
forum: Hardware
---

### Post by Thingymebob on 2008-08-20
Recieved this message this morning when starting up my acer aspire 5100.

This happened about 12 months ago and was solved by cleaning out the cooling system however this hasn't worked this time.

If I boot with acpi=off I can get to a recovery console and sensors tells me my cores are both around 38-42C so clearly not hot.

I'm thinking the critical point must therefore be coming from elsewhere (perhaps the GPU) so what I intend to do tonight is remove the heatsink from the GPU and re-apply some fresh thermal paste.

This i'm thinking, is clearly a hardware issue, so my question is if fresh paste on the GPU and CPU doesn't work how can Ubuntu help me identify the culprit with acpi off.

by the way with acpi=off and normal boot, boot freezes at initializing bluetooth (probably because I have no bluetooth hardware)

I may also try installing the acer-wmi (acer-acpi) packages again, although from what I understand these provide support for acer wireless (already works), bluetooth (don't have), 3G (Don't have), mail LED (happy living without) and screen brightness (already works) so I'm not sure how these will help.

---

