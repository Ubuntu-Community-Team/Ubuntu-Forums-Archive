---
title: "Samsung Samsung SCX-4200 doesn't print"
date: 2016-10-03
forum: Hardware
---

### Post by sermus1982 on 2016-10-03
Hello,
I have a relatively fresh installation of Ubuntu 16.04 LTS.
I have Samsung SCX-4220 connected to that machine.
It's correctly recognized by the OS so that the test page is perfectly printed.
However when i try to print something else it fails. Printer doesn't even start doing anything.
From the cups log i see ghostscript fails to render with a message looking like abracadabra to me:
D [03/Oct/2016:10:27:41 +0300] [Job 70] Error: /unregistered in --run--
D [03/Oct/2016:10:27:41 +0300] [Job 70] Operand stack:
D [03/Oct/2016:10:27:41 +0300] [Job 70] (/tmp/gs_5yBbqW)   --nostringval--
D [03/Oct/2016:10:27:41 +0300] [Job 70] Execution stack:
D [03/Oct/2016:10:27:41 +0300] [Job 70] %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1981   1   3   %oparray_pop   1980   1   3   %oparray_pop   1964   1   3   %oparray_pop   --nostringval--   --nostringval--   --nostringval--   2   1   1   --nostringval--   %for_pos_int_continue   --nostringval--   --nostringval--
D [03/Oct/2016:10:27:41 +0300] [Job 70] Dictionary stack:
D [03/Oct/2016:10:27:41 +0300] [Job 70] --dict:1207/1684(ro)(G)--   --dict:1/20(G)--   --dict:83/200(L)--   --dict:83/200(L)--   --dict:132/256(ro)(G)--   --dict:283/300(ro)(G)--   --dict:28/32(L)--   --dict:6/8(L)--   --dict:22/40(L)--
D [03/Oct/2016:10:27:41 +0300] [Job 70] Current allocation mode is local
D [03/Oct/2016:10:27:41 +0300] [Job 70] GPL Ghostscript 9.18: Unrecoverable error, exit code 1
I [03/Oct/2016:10:27:41 +0300] [Job 70] Rendering completed


I compared the logs test page prints with and this one. The difference is that test page has another MIME (application/vnd.cups-pdf-banner) while regular print has application/pdf. Thus the filter chain is different, but the command the chain runs ghostscript is identical in both cases.
The log is:
[ATTACH]271482[/ATTACH]

Can somebody please at least kick me the direction i could further dig this in?

---

### Post by sermus1982 on 2016-10-06
Answering myself. I solved the problem by compiling and installing GNU ghostscript 9.20. Nothing specific was required. I just installed all cups dev packages, configured ghostscript with --prefix=/usr. Then did make and make install. Voila, after restarting cups started printing.

---

