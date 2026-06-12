---
title: "Synaptic Touchpad  Event log"
date: 2011-04-22
forum: Hardware
---

### Post by lleming on 2011-04-22
Some how I enable it a while ago. So dmesg full of message from synaptic driver. I found that need to put xorg.conf a line
Option "SendCoreEvents" "true" in section "InputDevice".
But looks like I didnt create xorg.conf
how to revert settings back?
otherwise dmesg gives me:

[ 3335.865553] evbug.c: Event. Dev: input3, Type: 1, Code: 34, Value: 1
[ 3335.865559] evbug.c: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[ 3335.940271] evbug.c: Event. Dev: input10, Type: 3, Code: 2, Value: -1043
[ 3335.940275] evbug.c: Event. Dev: input10, Type: 0, Code: 0, Value: 0
[ 3335.969113] evbug.c: Event. Dev: input3, Type: 4, Code: 4, Value: 34
[ 3335.969121] evbug.c: Event. Dev: input3, Type: 1, Code: 34, Value: 0
[ 3335.969128] evbug.c: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[ 3336.341120] evbug.c: Event. Dev: input10, Type: 3, Code: 2, Value: -1034
[ 3336.341124] evbug.c: Event. Dev: input10, Type: 0, Code: 0, Value: 0
[ 3336.740509] evbug.c: Event. Dev: input10, Type: 3, Code: 2, Value: -1023
[ 3336.740513] evbug.c: Event. Dev: input10, Type: 0, Code: 0, Value: 0
[ 3336.783299] evbug.c: Event. Dev: input3, Type: 4, Code: 4, Value: 14
[ 3336.783307] evbug.c: Event. Dev: input3, Type: 1, Code: 14, Value: 1
[ 3336.783317] evbug.c: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[ 3336.790281] evbug.c: Event. Dev: input10, Type: 3, Code: 1, Value: -57
[ 3336.790284] evbug.c: Event. Dev: input10, Type: 3, Code: 2, Value: -1134
[ 3336.790286] evbug.c: Event. Dev: input10, Type: 0, Code: 0, Value: 0
[ 3336.840448] evbug.c: Event. Dev: input10, Type: 3, Code: 2, Value: -1008
[ 3336.840451] evbug.c: Event. Dev: input10, Type: 0, Code: 0, Value: 0
[ 3336.851592] evbug.c: Event. Dev: input3, Type: 4, Code: 4, Value: 14
[ 3336.851602] evbug.c: Event. Dev: input3, Type: 1, Code: 14, Value: 0
[ 3336.851610] evbug.c: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[ 3336.890420] evbug.c: Event. Dev: input10, Type: 3, Code: 2, Value: -1044
[ 3336.890425] evbug.c: Event. Dev: input10, Type: 0, Code: 0, Value: 0
[ 3336.962425] evbug.c: Event. Dev: input3, Type: 4, Code: 4, Value: 14
[ 3336.962433] evbug.c: Event. Dev: input3, Type: 1, Code: 14, Value: 1
[ 3336.962439] evbug.c: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[ 3337.031343] evbug.c: Event. Dev: input3, Type: 4, Code: 4, Value: 14
[ 3337.031350] evbug.c: Event. Dev: input3, Type: 1, Code: 14, Value: 0
[ 3337.031358] evbug.c: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[ 3337.089613] evbug.c: Event. Dev: input10, Type: 3, Code: 2, Value: -1017
[ 3337.089617] evbug.c: Event. Dev: input10, Type: 0, Code: 0, Value: 0
[ 3337.129018] evbug.c: Event. Dev: input3, Type: 4, Code: 4, Value: 14
[ 3337.129027] evbug.c: Event. Dev: input3, Type: 1, Code: 14, Value: 1
[ 3337.129035] evbug.c: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[ 3337.139638] evbug.c: Event. Dev: input10, Type: 3, Code: 2, Value: -1023
[ 3337.139641] evbug.c: Event. Dev: input10, Type: 0, Code: 0, Value: 0
[ 3337.190266] evbug.c: Event. Dev: input10, Type: 3, Code: 2, Value: -1014
[ 3337.190271] evbug.c: Event. Dev: input10, Type: 0, Code: 0, Value: 0
[ 3337.199447] evbug.c: Event. Dev: input3, Type: 4, Code: 4, Value: 14
[ 3337.199455] evbug.c: Event. Dev: input3, Type: 1, Code: 14, Value: 0
[ 3337.199463] evbug.c: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[ 3337.285752] evbug.c: Event. Dev: input3, Type: 4, Code: 4, Value: 14
[ 3337.285762] evbug.c: Event. Dev: input3, Type: 1, Code: 14, Value: 1
[ 3337.285769] evbug.c: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[ 3337.290210] evbug.c: Event. Dev: input10, Type: 3, Code: 2, Value: -1021
[ 3337.290213] evbug.c: Event. Dev: input10, Type: 0, Code: 0, Value: 0
[ 3337.339415] evbug.c: Event. Dev: input10, Type: 3, Code: 2, Value: -1031
[ 3337.339419] evbug.c: Event. Dev: input10, Type: 0, Code: 0, Value: 0
[ 3337.425621] evbug.c: Event. Dev: input3, Type: 4, Code: 4, Value: 14
[ 3337.425630] evbug.c: Event. Dev: input3, Type: 1, Code: 14, Value: 0
[ 3337.425639] evbug.c: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[ 3337.490013] evbug.c: Event. Dev: input10, Type: 3, Code: 0, Value: 47
[ 3337.490018] evbug.c: Event. Dev: input10, Type: 0, Code: 0, Value: 0
[ 3337.839164] evbug.c: Event. Dev: input10, Type: 3, Code: 0, Value: 39
[ 3337.839169] evbug.c: Event. Dev: input10, Type: 0, Code: 0, Value: 0
[ 3337.939715] evbug.c: Event. Dev: input10, Type: 3, Code: 2, Value: -1038
[ 3337.939718] evbug.c: Event. Dev: input10, Type: 0, Code: 0, Value: 0
[ 3338.139777] evbug.c: Event. Dev: input10, Type: 3, Code: 0, Value: 47
[ 3338.139782] evbug.c: Event. Dev: input10, Type: 3, Code: 2, Value: -1030
[ 3338.139784] evbug.c: Event. Dev: input10, Type: 0, Code: 0, Value: 0
[ 3338.162338] evbug.c: Event. Dev: input3, Type: 4, Code: 4, Value: 50
[ 3338.162345] evbug.c: Event. Dev: input3, Type: 1, Code: 50, Value: 1
[ 3338.162352] evbug.c: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[ 3338.272493] evbug.c: Event. Dev: input3, Type: 4, Code: 4, Value: 50
[ 3338.272501] evbug.c: Event. Dev: input3, Type: 1, Code: 50, Value: 0
[ 3338.272507] evbug.c: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[ 3338.274753] evbug.c: Event. Dev: input3, Type: 4, Code: 4, Value: 18
[ 3338.274761] evbug.c: Event. Dev: input3, Type: 1, Code: 18, Value: 1
[ 3338.274768] evbug.c: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[ 3338.289054] evbug.c: Event. Dev: input10, Type: 3, Code: 2, Value: -1038
[ 3338.289057] evbug.c: Event. Dev: input10, Type: 0, Code: 0, Value: 0
[ 3338.339138] evbug.c: Event. Dev: input10, Type: 3, Code: 1, Value: -69
[ 3338.339143] evbug.c: Event. Dev: input10, Type: 0, Code: 0, Value: 0
[ 3338.340087] evbug.c: Event. Dev: input3, Type: 4, Code: 4, Value: 18
[ 3338.340093] evbug.c: Event. Dev: input3, Type: 1, Code: 18, Value: 0
[ 3338.340100] evbug.c: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[ 3338.389042] evbug.c: Event. Dev: input10, Type: 3, Code: 0, Value: 39
[ 3338.389046] evbug.c: Event. Dev: input10, Type: 0, Code: 0, Value: 0
[ 3338.438874] evbug.c: Event. Dev: input10, Type: 3, Code: 2, Value: -1030
[ 3338.438877] evbug.c: Event. Dev: input10, Type: 0, Code: 0, Value: 0
[ 3338.463039] evbug.c: Event. Dev: input3, Type: 4, Code: 4, Value: 31
[ 3338.463047] evbug.c: Event. Dev: input3, Type: 1, Code: 31, Value: 1
[ 3338.463053] evbug.c: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[ 3338.489045] evbug.c: Event. Dev: input10, Type: 3, Code: 2, Value: -1020
[ 3338.489049] evbug.c: Event. Dev: input10, Type: 0, Code: 0, Value: 0
[ 3338.570119] evbug.c: Event. Dev: input3, Type: 4, Code: 4, Value: 31
[ 3338.570127] evbug.c: Event. Dev: input3, Type: 1, Code: 31, Value: 0
[ 3338.570134] evbug.c: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[ 3338.599066] evbug.c: Event. Dev: input3, Type: 4, Code: 4, Value: 34
[ 3338.599075] evbug.c: Event. Dev: input3, Type: 1, Code: 34, Value: 1
[ 3338.599084] evbug.c: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[ 3338.638763] evbug.c: Event. Dev: input10, Type: 3, Code: 2, Value: -1050
[ 3338.638767] evbug.c: Event. Dev: input10, Type: 0, Code: 0, Value: 0
[ 3338.667424] evbug.c: Event. Dev: input3, Type: 4, Code: 4, Value: 34
[ 3338.667433] evbug.c: Event. Dev: input3, Type: 1, Code: 34, Value: 0
[ 3338.667441] evbug.c: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[ 3338.688768] evbug.c: Event. Dev: input10, Type: 3, Code: 2, Value: -1011
[ 3338.688772] evbug.c: Event. Dev: input10, Type: 0, Code: 0, Value: 0
[ 3338.888732] evbug.c: Event. Dev: input10, Type: 3, Code: 2, Value: -1001
[ 3338.888736] evbug.c: Event. Dev: input10, Type: 0, Code: 0, Value: 0
[ 3338.892753] evbug.c: Event. Dev: input3, Type: 4, Code: 4, Value: 28
[ 3338.892760] evbug.c: Event. Dev: input3, Type: 1, Code: 28, Value: 1
[ 3338.892767] evbug.c: Event. Dev: input3, Type: 0, Code: 0, Value: 0

---

