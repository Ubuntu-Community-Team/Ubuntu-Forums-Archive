---
title: "UrbanTerror + ssh + grep + libnotify?"
date: 2008-08-31
forum: General Help
---

### Post by jesusfreak180 on 2008-08-31
Ok, sorry if this is the wrong section to post on for this.

I have just set up a new Urban Terror server.
I would like to know what is going on, like people joining, or a new game....
The server is hosted on my home network, and when it runs it shows detailed reports of what is going on.  It also outputs the same stuff into a log file.  I know that I can use grep or some other regex stuff to see what is going on
I use ssh to connect to it.
Is there any way I can either: Check the log file every *x* second, then grep the new info, sending that to libnotify?  Or do the same, but grep/regex the incoming output from the server command line output.

example log file:

```
urt@ubuntu:~/.q3a/q3ut4$ cat urtgames.log 
  0:00 ------------------------------------------------------------
  0:00 InitGame: \sv_allowdownload\0\g_matchmode\0\g_gametype\4\sv_maxclients\12\sv_floodprotect\1\g_warmup\20\capturelimit\0\sv_hostname\JP's Awsome Server\g_followstrict\1\fraglimit\10\timelimit\20\g_cahtime\60\g_swaproles\0\g_roundtime\3\g_bombexplodetime\40\g_bombdefusetime\10\g_hotpotato\2\g_waverespawns\0\g_redwave\15\g_bluewave\15\g_respawndelay\8\g_suddendeath\1\g_maxrounds\5\g_friendlyfire\1\g_allowvote\536877694\g_armbands\1\g_survivorrule\0\g_teamnameblue\Blue Peeps\g_teamnamered\Red Peeps\g_gear\0\g_deadchat\1\g_maxGameClients\12\dmflags\0\sv_dlURL\urbanterror.net\sv_maxPing\0\sv_minPing\0\sv_maxRate\0\sv_minRate\0\version\ioq3 1.35urt linux-i386 Dec 20 2007\protocol\68\mapname\ut4_eagle\sv_privateClients\0\gamename\q3ut4\g_needpass\0\g_enableDust\0\g_enableBreath\0\g_antilagvis\0\g_survivor\1\g_enablePrecip\0\g_modversion\4.1
  0:00 Warmup:
  0:24 ClientConnect: 0
  0:24 ClientUserinfo: 0 \ip\192.168.1.1:27960\challenge\-1375992965\qport\300\protocol\68\name\Josh\racered\2\raceblue\2\rate\8000\ut_timenudge\0\cg_rgb\128 128 128\funred\pirate\cg_predictitems\0\cg_physics\1\gear\FLJARUA\cl_anonymous\0\sex\male\handicap\100\color2\5\color1\4\team_headmodel\*james\team_model\james\headmodel\sarge\model\sarge\snaps\20\teamtask\0\cl_guid\95FFFF160A399BD5CA8D7E8C955EC626\weapmodes\00000110220000020002
  0:24 ClientUserinfoChanged: 0 n\Josh\t\3\r\2\tl\0\f0\\f1\\f2\\a0\255\a1\255\a2\255
  0:37 ClientUserinfo: 0 \ip\192.168.1.1:27960\name\Josh\racered\2\raceblue\2\rate\8000\ut_timenudge\0\cg_rgb\128 128 128\funred\pirate\cg_predictitems\0\cg_physics\1\gear\FLJARUA\cl_anonymous\0\sex\male\handicap\100\color2\5\color1\4\team_headmodel\*james\team_model\james\headmodel\sarge\model\sarge\snaps\20\teamtask\0\cl_guid\95FFFF160A399BD5CA8D7E8C955EC626\weapmodes\00000110220000020002
  0:37 ClientUserinfoChanged: 0 n\Josh\t\3\r\2\tl\0\f0\\f1\\f2\\a0\255\a1\255\a2\255
  0:37 ClientBegin: 0
  0:46 Kill: 0 0 10: Josh killed Josh by MOD_CHANGE_TEAM

```

---

