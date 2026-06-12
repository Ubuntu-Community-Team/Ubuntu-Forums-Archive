---
title: "ATi HD 3450 and TV Out problems"
date: 2015-12-05
forum: Hardware
---

### Post by janeku2 on 2015-12-05
Hello,
After a long time I decided to make connection to my old CRT TV Samsung with S-video cable in order to play movies on TV screen instead on my monitor using my ATI Radeon HD 3450 (RV620 LE) card.
Under Windows TV out support worked great but under Ubuntu (14.04.3)  looks like this is not working.
I have 3 cables (2 with S-video input/output and one S-video to AV output) and all of them work good. I tried all of them to eliminate possibility some of them are broken but no luck with all.
I still can;t get TV-Out signal on my TV.
Under Settings -> Displays I have Unknown display and as it could be seen by screen shot I can;t change almost anything.
In terminal with 
lspci -nn | grep VGA
I get information

[   13.191451] [drm] Connector 0:
[   13.191453] [drm]   VGA-1
[   13.191455] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   13.191456] [drm]   Encoders:
[   13.191457] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[   13.191458] [drm] Connector 1:
[   13.191459] [drm]   DIN-1
[   13.191459] [drm]   Encoders:
[   13.191460] [drm]     TV1: INTERNAL_KLDSCP_DAC2
[   13.191461] [drm] Connector 2:
[   13.191462] [drm]   DVI-I-1
[   13.191463] [drm]   HPD1
[   13.191464] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7

Seems like it is OK with card but why there is no output to my TV ?

Any one to suggest where to read solution to this problem or have similar problem. Looks like in older versions of Ubuntu it was solved with ATI drivers but now when these drivers are implemented in Ubuntu there is no much options to do with your graphic card.

Stay well and I hope soon with your help I'll be watching movies on my old CRT TV :)

---

