---
title: "Call Of Duty 2 Dedicated 1.3 server"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by simi182 on 2008-12-24
Hello.. can someone help me?  I Think im doing a mistake somewhere...but i dont know where...
Ive downloaded cod2 1.3 dedicated server... install it...  copyed the "main" file from the dvd to "main" file on ubuntu (iwd files)

Now when all was done.. ive started the server...

simi@server:/windows/test$ ./cod2_lnxded
CoD2 MP 1.3 build linux-i386 Jun 23 2006
----- FS_Startup -----
Current language: english
Current search path:
/home/simi/.callofduty2/main
/windows/test/main/iw_15.iwd (85 files)
/windows/test/main/iw_14.iwd (4038 files)
/windows/test/main/iw_13.iwd (22624 files)
/windows/test/main/iw_12.iwd (1016 files)
/windows/test/main/iw_11.iwd (1462 files)
/windows/test/main/iw_10.iwd (1936 files)
/windows/test/main/iw_09.iwd (2142 files)
/windows/test/main/iw_08.iwd (2723 files)
/windows/test/main/iw_07.iwd (3384 files)
/windows/test/main/iw_06.iwd (990 files)
/windows/test/main/iw_05.iwd (928 files)
/windows/test/main/iw_04.iwd (698 files)
/windows/test/main/iw_03.iwd (26 files)
/windows/test/main/iw_02.iwd (40 files)
/windows/test/main/iw_01.iwd (16 files)
/windows/test/main/iw_00.iwd (102 files)
/windows/test/main
/home/simi/.callofduty2/raw
/home/simi/.callofduty2/raw_shared
/home/simi/.callofduty2/devraw
/home/simi/.callofduty2/devraw_shared
/windows/test/raw
/windows/test/raw_shared
/windows/test/devraw
/windows/test/devraw_shared
/windows/test/main/localized_english_iw11.iwd (1 files)
    localized assets iwd file for english
/windows/test/main/localized_english_iw10.iwd (414 files)
    localized assets iwd file for english
/windows/test/main/localized_english_iw09.iwd (98 files)
    localized assets iwd file for english
/windows/test/main/localized_english_iw08.iwd (8 files)
    localized assets iwd file for english
/windows/test/main/localized_english_iw07.iwd (1014 files)
    localized assets iwd file for english
/windows/test/main/localized_english_iw06.iwd (3110 files)
    localized assets iwd file for english
/windows/test/main/localized_english_iw05.iwd (5310 files)
    localized assets iwd file for english
/windows/test/main/localized_english_iw04.iwd (6240 files)
    localized assets iwd file for english
/windows/test/main/localized_english_iw03.iwd (6580 files)
    localized assets iwd file for english
/windows/test/main/localized_english_iw02.iwd (6404 files)
    localized assets iwd file for english
/windows/test/main/localized_english_iw01.iwd (5510 files)
    localized assets iwd file for english
/windows/test/main/localized_english_iw00.iwd (4764 files)
    localized assets iwd file for english

File Handles:
----------------------
81663 files in iwd files
execing default_mp.cfg
couldn't exec language.cfg
couldn't exec config_mp_server.cfg
Opening IP socket: localhost:28960
Hostname: server
IP: 127.0.1.1
--- Common Initialization Complete ---
Hitch warning: 4268 msec frame time

After this line... i think i should run a map..if i have read houndreds of "how to" correctly so i write...

"map mp_leningrad"
and i get ...

map mp_leningrad
g_gametype random is not a valid gametype, defaulting to dm
------ Server Initialization ------
Server: mp_leningrad
----- FS_Startup -----
Current language: english
Current search path:
/home/simi/.callofduty2/main
/windows/test/main/iw_15.iwd (85 files)
/windows/test/main/iw_14.iwd (4038 files)
/windows/test/main/iw_13.iwd (22624 files)
/windows/test/main/iw_12.iwd (1016 files)
/windows/test/main/iw_11.iwd (1462 files)
/windows/test/main/iw_10.iwd (1936 files)
/windows/test/main/iw_09.iwd (2142 files)
/windows/test/main/iw_08.iwd (2723 files)
/windows/test/main/iw_07.iwd (3384 files)
/windows/test/main/iw_06.iwd (990 files)
/windows/test/main/iw_05.iwd (928 files)
/windows/test/main/iw_04.iwd (698 files)
/windows/test/main/iw_03.iwd (26 files)
/windows/test/main/iw_02.iwd (40 files)
/windows/test/main/iw_01.iwd (16 files)
/windows/test/main/iw_00.iwd (102 files)
/windows/test/main
/home/simi/.callofduty2/raw
/home/simi/.callofduty2/raw_shared
/home/simi/.callofduty2/devraw
/home/simi/.callofduty2/devraw_shared
/windows/test/raw
/windows/test/raw_shared
/windows/test/devraw
/windows/test/devraw_shared
/windows/test/main/localized_english_iw11.iwd (1 files)
    localized assets iwd file for english
/windows/test/main/localized_english_iw10.iwd (414 files)
    localized assets iwd file for english
/windows/test/main/localized_english_iw09.iwd (98 files)
    localized assets iwd file for english
/windows/test/main/localized_english_iw08.iwd (8 files)
    localized assets iwd file for english
/windows/test/main/localized_english_iw07.iwd (1014 files)
    localized assets iwd file for english
/windows/test/main/localized_english_iw06.iwd (3110 files)
    localized assets iwd file for english
/windows/test/main/localized_english_iw05.iwd (5310 files)
    localized assets iwd file for english
/windows/test/main/localized_english_iw04.iwd (6240 files)
    localized assets iwd file for english
/windows/test/main/localized_english_iw03.iwd (6580 files)
    localized assets iwd file for english
/windows/test/main/localized_english_iw02.iwd (6404 files)
    localized assets iwd file for english
/windows/test/main/localized_english_iw01.iwd (5510 files)
    localized assets iwd file for english
/windows/test/main/localized_english_iw00.iwd (4764 files)
    localized assets iwd file for english

File Handles:
----------------------
81663 files in iwd files
------- Game Initialization -------
gamename: Call of Duty 2
gamedate: Jun 23 2006
WARNING: Couldn't open logfile: games_mp.log
-----------------------------------
-----------------------------------
PunkBuster Server: 0 Aliases Written to pbalias.dat
PunkBuster Server: 0 Stat Records Written to pbstat.dat
PunkBuster Server: Preparing to Disable PB Server... (/home/simi/.callofduty2/pb/)
Hitch warning: 10648 msec frame time
Resolving cod2master.activision.com
cod2master.activision.com resolved to 63.146.124.40:20710
Sending heartbeat to cod2master.activision.com

here im sending and resolving heartbeat all the way...

i hope i have give you enough information for the start.. please help me with this one..coz im gonna lose my mind :) 
Thanks

---

### Post by simi182 on 2008-12-24
anyone ? :D

---

### Post by St3vegate21 on 2009-05-27
I dont think that you are doing womething wrong.. As it seems, everything works fine, so the server should be runing!! Can you give me some info about how to install the server cause I am really interested in that? :-)

---

