---
title: "XVidCap Screen Capture Closes When I Hit Record"
date: 2008-08-13
forum: General Help
---

### Post by Eviltechie on 2008-08-13
I just installed XVidCap Screen Capture, but whenever I click record, it closes.

---

### Post by anhvu2875 on 2008-11-17
**Eviltechie**
```
sudo apt-get install libavcodec-unstripped-51
```

and try again !

---

### Post by jdwinfodesign on 2008-12-02
This worked for me.

Thanks anhvu2875, for posting.

---

### Post by jakev383 on 2008-12-04
I get package unknown on that one, but I have the same problem.

---

### Post by Braedon on 2009-05-10
Hey thanks! Though, you can no longer do this through the terminal, you have to use Synaptic package manager.

---

### Post by SGC622 on 2010-11-19
I started Xvidcap in terminal as seen below, then i hit the record button to see what it was coming up with cause the program was disappearing on me. I did sudo just to see if it made a difference, i know you can run it without it but i just gave it a try.Any help on telling me whats wrong by looking at this read out would be very much appreciated.

**I tried doing the fix in the forum above by installing that lib file in synaptic but its still doing this**

> 
scott@Home:~$ sudo xvidcap
[sudo] password for scott: 
[oss @ 0xcae870]/dev/dsp: Device or resource busy
*** glibc detected *** xvidcap: double free or corruption (out): 0x0000000000c10060 ***
======= Backtrace: =========
/lib/libc.so.6(+0x775b6)[0x7f9ec65475b6]
/lib/libc.so.6(cfree+0x73)[0x7f9ec654de83]
/usr/lib/libavformat.so.52(av_open_input_stream+0x14f)[0x7f9ec7d5f2af]
/usr/lib/libavformat.so.52(av_open_input_file+0x1f0)[0x7f9ec7d5f850]
xvidcap(xvc_ffmpeg_save_frame+0x4ff)[0x425b1f]
xvidcap[0x41093c]
xvidcap(do_record_thread+0x6c)[0x416d8c]
/lib/libpthread.so.0(+0x69ca)[0x7f9ec82479ca]
/lib/libc.so.6(clone+0x6d)[0x7f9ec65b670d]
======= Memory map: ========
00400000-00436000 r-xp 00000000 08:01 17937                              /usr/bin/xvidcap
00636000-00637000 r--p 00036000 08:01 17937                              /usr/bin/xvidcap
00637000-00638000 rw-p 00037000 08:01 17937                              /usr/bin/xvidcap
00638000-0065b000 rw-p 00000000 00:00 0 
00a51000-00cc6000 rw-p 00000000 00:00 0                                  [heap]
7f9eb4000000-7f9eb4021000 rw-p 00000000 00:00 0 
7f9eb4021000-7f9eb8000000 ---p 00000000 00:00 0 
7f9eb981b000-7f9eb981c000 ---p 00000000 00:00 0 
7f9eb981c000-7f9eba01c000 rw-p 00000000 00:00 0 
7f9eba01c000-7f9eba01d000 ---p 00000000 00:00 0 
7f9eba01d000-7f9eba81d000 rw-p 00000000 00:00 0 
7f9eba81d000-7f9eba81e000 ---p 00000000 00:00 0 
7f9eba81e000-7f9ebb01e000 rw-p 00000000 00:00 0 
7f9ebb01e000-7f9ebb01f000 ---p 00000000 00:00 0 
7f9ebb01f000-7f9ebb81f000 rw-p 00000000 00:00 0 
7f9ebb81f000-7f9ebb83a000 rw-s 00000000 00:04 5505033                    /SYSV00000000 (deleted)
7f9ebb83a000-7f9ebb855000 rw-s 00000000 00:04 5472264                    /SYSV00000000 (deleted)
7f9ebb855000-7f9ebb856000 ---p 00000000 00:00 0 
7f9ebb856000-7f9ebc056000 rw-p 00000000 00:00 0 
7f9ebc056000-7f9ebc0b6000 rw-s 00000000 00:04 5439495                    /SYSV00000000 (deleted)
7f9ebc0b6000-7f9ebc805000 r--p 00000000 08:01 656356                     /usr/share/icons/hicolor/icon-theme.cache
7f9ebc805000-7f9ebc89d000 r--p 00000000 08:01 395365                     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
7f9ebc89d000-7f9ebc89f000 r-xp 00000000 08:01 2884943                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f9ebc89f000-7f9ebca9e000 ---p 00002000 08:01 2884943                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f9ebca9e000-7f9ebca9f000 r--p 00001000 08:01 2884943                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f9ebca9f000-7f9ebcaa0000 rw-p 00002000 08:01 2884943                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so                                                             
7f9ebcaa0000-7f9ebcaa1000 r--s 00000000 08:01 16707                      /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-le64.cache-3                                        
7f9ebcaa1000-7f9ebcaa2000 r--s 00000000 08:01 982                        /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le64.cache-3                                        
7f9ebcaa2000-7f9ebcaab000 r--s 00000000 08:01 3893                       /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le64.cache-3                                        
7f9ebcaab000-7f9ebcaaf000 r--s 00000000 08:01 3892                       /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le64.cache-3                                        
7f9ebcaaf000-7f9ebcab2000 r--s 00000000 08:01 3773                       /var/cache/fontconfig/f24b2111ab8703b4e963115a8cf14259-le64.cache-3                                        
7f9ebcab2000-7f9ebcab5000 r--s 00000000 08:01 3776                       /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le64.cache-3                                        
7f9ebcab5000-7f9ebcaba000 r--s 00000000 08:01 3742                       /var/cache/fontconfig/062808c12e6e608270f93bb230aed730-le64.cache-3                                        
7f9ebcaba000-7f9ebcac0000 r--s 00000000 08:01 3798                       /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le64.cache-3                                        
7f9ebcac0000-7f9ebcac9000 r--s 00000000 08:01 3775                       /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le64.cache-3                                        
7f9ebcac9000-7f9ebcad9000 r--s 00000000 08:01 704                        /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le64.cache-3                                        
7f9ebcad9000-7f9ebcae5000 r-xp 00000000 08:01 7970                       /lib/libnss_files-2.11.1.so                                                                                
7f9ebcae5000-7f9ebcce4000 ---p 0000c000 08:01 7970                       /lib/libnss_files-2.11.1.so                                                                                
7f9ebcce4000-7f9ebcce5000 r--p 0000b000 08:01 7970                       /lib/libnss_files-2.11.1.so                                                                                
7f9ebcce5000-7f9ebcce6000 rw-p 0000c000 08:01 7970                       /lib/libnss_files-2.11.1.so                                                                                
7f9ebcce6000-7f9ebccf0000 r-xp 00000000 08:01 7938                       /lib/libnss_nis-2.11.1.so                                                                                  
7f9ebccf0000-7f9ebceef000 ---p 0000a000 08:01 7938                       /lib/libnss_nis-2.11.1.so                                                                                  
7f9ebceef000-7f9ebcef0000 r--p 00009000 08:01 7938                       /lib/libnss_nis-2.11.1.so                                                                                  
7f9ebcef0000-7f9ebcef1000 rw-p 0000a000 08:01 7938                       /lib/libnss_nis-2.11.1.so                                                                                  
7f9ebcef1000-7f9ebcf08000 r-xp 00000000 08:01 7894                       /lib/libnsl-2.11.1.so
7f9ebcf08000-7f9ebd107000 ---p 00017000 08:01 7894                       /lib/libnsl-2.11.1.so
7f9ebd107000-7f9ebd108000 r--p 00016000 08:01 7894                       /lib/libnsl-2.11.1.so
7f9ebd108000-7f9ebd109000 rw-p 00017000 08:01 7894                       /lib/libnsl-2.11.1.so
7f9ebd109000-7f9ebd10b000 rw-p 00000000 00:00 0 
7f9ebd10b000-7f9ebd113000 r-xp 00000000 08:01 7937                       /lib/libnss_compat-2.11.1.so
7f9ebd113000-7f9ebd312000 ---p 00008000 08:01 7937                       /lib/libnss_compat-2.11.1.so
7f9ebd312000-7f9ebd313000 r--p 00007000 08:01 7937                       /lib/libnss_compat-2.11.1.so
7f9ebd313000-7f9ebd314000 rw-p 00008000 08:01 7937                       /lib/libnss_compat-2.11.1.so
7f9ebd314000-7f9ebd318000 r-xp 00000000 08:01 622                        /lib/libuuid.so.1.3.0
7f9ebd318000-7f9ebd517000 ---p 00004000 08:01 622                        /lib/libuuid.so.1.3.0
7f9ebd517000-7f9ebd518000 r--p 00003000 08:01 622                        /lib/libuuid.so.1.3.0
7f9ebd518000-7f9ebd519000 rw-p 00004000 08:01 622                        /lib/libuuid.so.1.3.0
7f9ebd519000-7f9ebd51e000 r-xp 00000000 08:01 3740                       /usr/lib/libXdmcp.so.6.0.0
7f9ebd51e000-7f9ebd71d000 ---p 00005000 08:01 3740                       /usr/lib/libXdmcp.so.6.0.0Aborted



---

### Post by SGC622 on 2010-11-19
Through a little more research i found another thread that had a fix it was this below
the person said it was an old linux c++ error and said "Some programs might try to free a space through delete that has already  been unallocated. That command suppresses the error by switching off  checks for this activity."
> 
scott@Home:~$ 
scott@Home:~$ export MALLOC_CHECK_=0
scott@Home:~$ xvidcap
[oss @ 0x2605710]/dev/dsp: Device or resource busy
xtoffmpeg.c add_audio_stream(): error opening input file /dev/dsp: -5


---

### Post by Glace on 2010-11-23
> **SGC622 said:**
> Through a little more research i found another thread that had a fix it was this below
the person said it was an old linux c++ error and said "Some programs might try to free a space through delete that has already  been unallocated. That command suppresses the error by switching off  checks for this activity."

Thank you very much they worked for me.

---

