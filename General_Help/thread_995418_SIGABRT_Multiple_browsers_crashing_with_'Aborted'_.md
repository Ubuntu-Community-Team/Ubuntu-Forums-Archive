---
title: "SIGABRT Multiple browsers crashing with 'Aborted' since upgrade!"
date: 2008-11-27
forum: General Help
---

### Post by jubalj on 2008-11-27
Hi there,

I am having a very frustrating issue since upgrade to Intrepid.. I am finding that multiple browsers are crashing when I try to access certain websites (?ajax heavy) - the main website that I can consistenly (within 30-60s) crash the browser on is facebook.com. Sometimes it crashes as the page is loading, sometimes I can browse face book for few minutes before it crashes..

Initally I noticed it in firefox, I thought it may be a flash issue - but it still crashes in safe mode with a new profile created - without flash. Eventually I gave up on firefox and installed opera - which also to my suprise crashes (but slightly less frequently on facebook). now I have installed epihpany, konqueror, seamonkey to my surprise all of them crash.

What is worse is that I eventually installed safari, internet explorer and firefox under wine.. but the ALL also crash, randomly.. but reasonably consistently (withint 2-3minutes of use, when trying to load a page like facebook, or sometimes twitter/gmail - making me suspicious that its AJAX related?)

It seems to be an underlying problem with something on my system.. I've tried to play with pulse audio to see if this might be the issue? But otherwise i'm at my wits end.. and would appreciate any help.. 

here is the debug output from firefox (filed a bug here [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/286205](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/286205) but no response)

Program received signal SIGABRT, Aborted.
[Switching to Thread 0xa9866b90 (LWP 3423)]
0xb80d4430 in __kernel_vsyscall ()
(gdb) where
#0  0xb80d4430 in __kernel_vsyscall ()
#1  0xb7e2a880 in raise () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7e2c248 in abort () from /lib/tls/i686/cmov/libc.so.6
#3  0xab7340c5 in talloc_strdup () from /usr/lib/libtalloc.so.1
#4  0xab830d59 in talloc_sub_basic () from /lib/libnss_wins.so.2
#5  0xab770281 in ?? () from /lib/libnss_wins.so.2
#6  0xab7713f2 in lp_lockdir () from /lib/libnss_wins.so.2
#7  0xab82aa75 in lock_path () from /lib/libnss_wins.so.2
#8  0xab7c9767 in receive_unexpected () from /lib/libnss_wins.so.2
#9  0xab7cc375 in receive_nmb_packet () from /lib/libnss_wins.so.2
#10 0xab7cee4d in name_query () from /lib/libnss_wins.so.2
#11 0xab76c555 in _nss_wins_gethostbyname_r () from /lib/libnss_wins.so.2
#12 0xab76c853 in _nss_wins_gethostbyname2_r () from /lib/libnss_wins.so.2
#13 0xb7ec4666 in ?? () from /lib/tls/i686/cmov/libc.so.6
#14 0xb7ec6039 in getaddrinfo () from /lib/tls/i686/cmov/libc.so.6
#15 0xb7d356b9 in PR_GetAddrInfoByName () from /usr/lib/libnspr4.so.0d
#16 0xb7316818 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#17 0xb7d431e1 in ?? () from /usr/lib/libnspr4.so.0d
#18 0xb808c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#19 0xb7ee07ee in clone () from /lib/tls/i686/cmov/libc.so.6

(gdb) thread apply all bt

Thread 29 (Thread 0xa7862b90 (LWP 3427)):
#0  0xb80d4430 in __kernel_vsyscall ()
#1  0xb7ed8c01 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xab832a79 in sys_select_intr () from /lib/libnss_wins.so.2
#3  0xab7cc1df in receive_packet () from /lib/libnss_wins.so.2
#4  0xab7cc340 in receive_nmb_packet () from /lib/libnss_wins.so.2
#5  0xab7cee4d in name_query () from /lib/libnss_wins.so.2
#6  0xab76c555 in _nss_wins_gethostbyname_r () from /lib/libnss_wins.so.2
#7  0xab76c853 in _nss_wins_gethostbyname2_r () from /lib/libnss_wins.so.2
#8  0xb7ec4666 in ?? () from /lib/tls/i686/cmov/libc.so.6
#9  0xb7ec6039 in getaddrinfo () from /lib/tls/i686/cmov/libc.so.6
#10 0xb7d356b9 in PR_GetAddrInfoByName () from /usr/lib/libnspr4.so.0d
#11 0xb7316818 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#12 0xb7d431e1 in ?? () from /usr/lib/libnspr4.so.0d
#13 0xb808c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#14 0xb7ee07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 28 (Thread 0xa8063b90 (LWP 3426)):
#0  0xb80d4430 in __kernel_vsyscall ()
#1  0xb7ed8c01 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xab832a79 in sys_select_intr () from /lib/libnss_wins.so.2
#3  0xab7cc1df in receive_packet () from /lib/libnss_wins.so.2
---Type <return> to continue, or q <return> to quit---
#4  0xab7cc340 in receive_nmb_packet () from /lib/libnss_wins.so.2
#5  0xab7cee4d in name_query () from /lib/libnss_wins.so.2
#6  0xab76c555 in _nss_wins_gethostbyname_r () from /lib/libnss_wins.so.2
#7  0xab76c853 in _nss_wins_gethostbyname2_r () from /lib/libnss_wins.so.2
#8  0xb7ec4666 in ?? () from /lib/tls/i686/cmov/libc.so.6
#9  0xb7ec6039 in getaddrinfo () from /lib/tls/i686/cmov/libc.so.6
#10 0xb7d356b9 in PR_GetAddrInfoByName () from /usr/lib/libnspr4.so.0d
#11 0xb7316818 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#12 0xb7d431e1 in ?? () from /usr/lib/libnspr4.so.0d
#13 0xb808c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#14 0xb7ee07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 27 (Thread 0xa8864b90 (LWP 3425)):
#0  0xb80d4430 in __kernel_vsyscall ()
#1  0xb7ed8c01 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xab832a79 in sys_select_intr () from /lib/libnss_wins.so.2
#3  0xab7cc1df in receive_packet () from /lib/libnss_wins.so.2
#4  0xab7cc340 in receive_nmb_packet () from /lib/libnss_wins.so.2
#5  0xab7cee4d in name_query () from /lib/libnss_wins.so.2
#6  0xab76c555 in _nss_wins_gethostbyname_r () from /lib/libnss_wins.so.2
#7  0xab76c853 in _nss_wins_gethostbyname2_r () from /lib/libnss_wins.so.2
#8  0xb7ec4666 in ?? () from /lib/tls/i686/cmov/libc.so.6
#9  0xb7ec6039 in getaddrinfo () from /lib/tls/i686/cmov/libc.so.6
---Type <return> to continue, or q <return> to quit---
#10 0xb7d356b9 in PR_GetAddrInfoByName () from /usr/lib/libnspr4.so.0d
#11 0xb7316818 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#12 0xb7d431e1 in ?? () from /usr/lib/libnspr4.so.0d
#13 0xb808c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#14 0xb7ee07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 26 (Thread 0xa9065b90 (LWP 3424)):
#0  0xb80d4430 in __kernel_vsyscall ()
#1  0xb7e8afb6 in gettimeofday () from /lib/tls/i686/cmov/libc.so.6
#2  0xab8188d6 in GetTimeOfDay () from /lib/libnss_wins.so.2
#3  0xab7cedb2 in name_query () from /lib/libnss_wins.so.2
#4  0xab76c555 in _nss_wins_gethostbyname_r () from /lib/libnss_wins.so.2
#5  0xab76c853 in _nss_wins_gethostbyname2_r () from /lib/libnss_wins.so.2
#6  0xb7ec4666 in ?? () from /lib/tls/i686/cmov/libc.so.6
#7  0xb7ec6039 in getaddrinfo () from /lib/tls/i686/cmov/libc.so.6
#8  0xb7d356b9 in PR_GetAddrInfoByName () from /usr/lib/libnspr4.so.0d
#9  0xb7316818 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#10 0xb7d431e1 in ?? () from /usr/lib/libnspr4.so.0d
#11 0xb808c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#12 0xb7ee07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 25 (Thread 0xa9866b90 (LWP 3423)):
#0  0xb80d4430 in __kernel_vsyscall ()
---Type <return> to continue, or q <return> to quit---
#1  0xb7e2a880 in raise () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7e2c248 in abort () from /lib/tls/i686/cmov/libc.so.6
#3  0xab7340c5 in talloc_strdup () from /usr/lib/libtalloc.so.1
#4  0xab830d59 in talloc_sub_basic () from /lib/libnss_wins.so.2
#5  0xab770281 in ?? () from /lib/libnss_wins.so.2
#6  0xab7713f2 in lp_lockdir () from /lib/libnss_wins.so.2
#7  0xab82aa75 in lock_path () from /lib/libnss_wins.so.2
#8  0xab7c9767 in receive_unexpected () from /lib/libnss_wins.so.2
#9  0xab7cc375 in receive_nmb_packet () from /lib/libnss_wins.so.2
#10 0xab7cee4d in name_query () from /lib/libnss_wins.so.2
#11 0xab76c555 in _nss_wins_gethostbyname_r () from /lib/libnss_wins.so.2
#12 0xab76c853 in _nss_wins_gethostbyname2_r () from /lib/libnss_wins.so.2
#13 0xb7ec4666 in ?? () from /lib/tls/i686/cmov/libc.so.6
#14 0xb7ec6039 in getaddrinfo () from /lib/tls/i686/cmov/libc.so.6
#15 0xb7d356b9 in PR_GetAddrInfoByName () from /usr/lib/libnspr4.so.0d
#16 0xb7316818 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#17 0xb7d431e1 in ?? () from /usr/lib/libnspr4.so.0d
#18 0xb808c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#19 0xb7ee07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 24 (Thread 0xaa067b90 (LWP 3421)):
#0  0xb80d4430 in __kernel_vsyscall ()
#1  0xb7ed8c01 in select () from /lib/tls/i686/cmov/libc.so.6
---Type <return> to continue, or q <return> to quit---
#2  0xab832a79 in sys_select_intr () from /lib/libnss_wins.so.2
#3  0xab7cc1df in receive_packet () from /lib/libnss_wins.so.2
#4  0xab7cc340 in receive_nmb_packet () from /lib/libnss_wins.so.2
#5  0xab7cee4d in name_query () from /lib/libnss_wins.so.2
#6  0xab76c555 in _nss_wins_gethostbyname_r () from /lib/libnss_wins.so.2
#7  0xab76c853 in _nss_wins_gethostbyname2_r () from /lib/libnss_wins.so.2
#8  0xb7ec4666 in ?? () from /lib/tls/i686/cmov/libc.so.6
#9  0xb7ec6039 in getaddrinfo () from /lib/tls/i686/cmov/libc.so.6
#10 0xb7d356b9 in PR_GetAddrInfoByName () from /usr/lib/libnspr4.so.0d
#11 0xb7316818 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#12 0xb7d431e1 in ?? () from /usr/lib/libnspr4.so.0d
#13 0xb808c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#14 0xb7ee07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 23 (Thread 0xad0ffb90 (LWP 3420)):
#0  0xb80d4430 in __kernel_vsyscall ()
#1  0xb7ed8c01 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xab832a79 in sys_select_intr () from /lib/libnss_wins.so.2
#3  0xab7cc1df in receive_packet () from /lib/libnss_wins.so.2
#4  0xab7cc340 in receive_nmb_packet () from /lib/libnss_wins.so.2
#5  0xab7cee4d in name_query () from /lib/libnss_wins.so.2
#6  0xab76c555 in _nss_wins_gethostbyname_r () from /lib/libnss_wins.so.2
#7  0xab76c853 in _nss_wins_gethostbyname2_r () from /lib/libnss_wins.so.2
---Type <return> to continue, or q <return> to quit---
#8  0xb7ec4666 in ?? () from /lib/tls/i686/cmov/libc.so.6
#9  0xb7ec6039 in getaddrinfo () from /lib/tls/i686/cmov/libc.so.6
#10 0xb7d356b9 in PR_GetAddrInfoByName () from /usr/lib/libnspr4.so.0d
#11 0xb7316818 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#12 0xb7d431e1 in ?? () from /usr/lib/libnspr4.so.0d
#13 0xb808c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#14 0xb7ee07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 22 (Thread 0xaa8fdb90 (LWP 3418)):
#0  0xb80d4430 in __kernel_vsyscall ()
#1  0xb7ed5f77 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb5c89bce in ?? () from /usr/lib/libasound.so.2
#3  0xb5c89d84 in snd_pcm_wait () from /usr/lib/libasound.so.2
#4  0xb04cbae3 in ?? () from /usr/lib/adobe-flashplugin/libflashplayer.so
#5  0xb808c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#6  0xb7ee07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 21 (Thread 0xab0feb90 (LWP 3417)):
#0  0xb80d4430 in __kernel_vsyscall ()
#1  0xb7ed5f77 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xab471532 in ?? () from /usr/lib/libpulse.so.0
#3  0xab463509 in pa_mainloop_poll () from /usr/lib/libpulse.so.0
#4  0xab464cd3 in pa_mainloop_iterate () from /usr/lib/libpulse.so.0
---Type <return> to continue, or q <return> to quit---
#5  0xab464da4 in pa_mainloop_run () from /usr/lib/libpulse.so.0
#6  0xab4712e3 in ?? () from /usr/lib/libpulse.so.0
#7  0xab4928e2 in ?? () from /usr/lib/libpulse.so.0
#8  0xb808c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#9  0xb7ee07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 20 (Thread 0xb1306b90 (LWP 3416)):
#0  0xb80d4430 in __kernel_vsyscall ()
#1  0xb7ed8c01 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xab832a79 in sys_select_intr () from /lib/libnss_wins.so.2
#3  0xab7cc1df in receive_packet () from /lib/libnss_wins.so.2
#4  0xab7cc340 in receive_nmb_packet () from /lib/libnss_wins.so.2
#5  0xab7cee4d in name_query () from /lib/libnss_wins.so.2
#6  0xab76c555 in _nss_wins_gethostbyname_r () from /lib/libnss_wins.so.2
#7  0xab76c853 in _nss_wins_gethostbyname2_r () from /lib/libnss_wins.so.2
#8  0xb7ec4666 in ?? () from /lib/tls/i686/cmov/libc.so.6
#9  0xb7ec6039 in getaddrinfo () from /lib/tls/i686/cmov/libc.so.6
#10 0xb7d356b9 in PR_GetAddrInfoByName () from /usr/lib/libnspr4.so.0d
#11 0xb7316818 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#12 0xb7d431e1 in ?? () from /usr/lib/libnspr4.so.0d
#13 0xb808c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#14 0xb7ee07ee in clone () from /lib/tls/i686/cmov/libc.so.6

---Type <return> to continue, or q <return> to quit---
Thread 19 (Thread 0xac8feb90 (LWP 3414)):
#0  0xb80d4430 in __kernel_vsyscall ()
#1  0xb80903a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
  from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7d3bf9e in ?? () from /usr/lib/libnspr4.so.0d
#3  0xb7d3cdc0 in PR_WaitCondVar () from /usr/lib/libnspr4.so.0d
#4  0xb7d3ceb7 in PR_Wait () from /usr/lib/libnspr4.so.0d
#5  0xb7a63e3c in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#6  0xb7a621f8 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#7  0xb7a32b1c in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#8  0xb7a6295f in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#9  0xb7d431e1 in ?? () from /usr/lib/libnspr4.so.0d
#10 0xb808c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7ee07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 16 (Thread 0xac0fdb90 (LWP 3404)):
#0  0xb80d4430 in __kernel_vsyscall ()
#1  0xb8090075 in pthread_cond_wait@@GLIBC_2.3.2 ()
  from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7d3ce39 in PR_WaitCondVar () from /usr/lib/libnspr4.so.0d
#3  0xb7d3ceb7 in PR_Wait () from /usr/lib/libnspr4.so.0d
#4  0xb7a6141d in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#5  0xb7a621cc in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
---Type <return> to continue, or q <return> to quit---
#6  0xb7a32b1c in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#7  0xb7a6295f in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#8  0xb7d431e1 in ?? () from /usr/lib/libnspr4.so.0d
#9  0xb808c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#10 0xb7ee07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 13 (Thread 0xadcfdb90 (LWP 3401)):
#0  0xb80d4430 in __kernel_vsyscall ()
#1  0xb8090075 in pthread_cond_wait@@GLIBC_2.3.2 ()
  from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb00a16cf in ?? () from /usr/lib/adobe-flashplugin/libflashplayer.so
#3  0xb01d329f in ?? () from /usr/lib/adobe-flashplugin/libflashplayer.so
#4  0xb00a1b8d in ?? () from /usr/lib/adobe-flashplugin/libflashplayer.so
#5  0xb808c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#6  0xb7ee07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 12 (Thread 0xae4feb90 (LWP 3400)):
#0  0xb80d4430 in __kernel_vsyscall ()
#1  0xb8090075 in pthread_cond_wait@@GLIBC_2.3.2 ()
  from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb00a16cf in ?? () from /usr/lib/adobe-flashplugin/libflashplayer.so
#3  0xb01d329f in ?? () from /usr/lib/adobe-flashplugin/libflashplayer.so
#4  0xb00a1b8d in ?? () from /usr/lib/adobe-flashplugin/libflashplayer.so
---Type <return> to continue, or q <return> to quit---
#5  0xb808c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#6  0xb7ee07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 11 (Thread 0xaecffb90 (LWP 3399)):
#0  0xb80d4430 in __kernel_vsyscall ()
#1  0xb8090075 in pthread_cond_wait@@GLIBC_2.3.2 ()
  from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb00a16cf in ?? () from /usr/lib/adobe-flashplugin/libflashplayer.so
#3  0xb01d329f in ?? () from /usr/lib/adobe-flashplugin/libflashplayer.so
#4  0xb00a1b8d in ?? () from /usr/lib/adobe-flashplugin/libflashplayer.so
#5  0xb808c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#6  0xb7ee07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 10 (Thread 0xb4a9cb90 (LWP 3398)):
#0  0xb80d4430 in __kernel_vsyscall ()
#1  0xb8090075 in pthread_cond_wait@@GLIBC_2.3.2 ()
  from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb00a16cf in ?? () from /usr/lib/adobe-flashplugin/libflashplayer.so
#3  0xb01d329f in ?? () from /usr/lib/adobe-flashplugin/libflashplayer.so
#4  0xb00a1b8d in ?? () from /usr/lib/adobe-flashplugin/libflashplayer.so
#5  0xb808c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#6  0xb7ee07ee in clone () from /lib/tls/i686/cmov/libc.so.6

---Type <return> to continue, or q <return> to quit---
Thread 8 (Thread 0xb425ab90 (LWP 3371)):
#0  0xb80d4430 in __kernel_vsyscall ()
#1  0xb8090075 in pthread_cond_wait@@GLIBC_2.3.2 ()
  from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7d3ce39 in PR_WaitCondVar () from /usr/lib/libnspr4.so.0d
#3  0xb786be56 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#4  0xb786a6f2 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#5  0xb7d431e1 in ?? () from /usr/lib/libnspr4.so.0d
#6  0xb808c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0xb7ee07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 7 (Thread 0xb3a59b90 (LWP 3370)):
#0  0xb80d4430 in __kernel_vsyscall ()
#1  0xb8090075 in pthread_cond_wait@@GLIBC_2.3.2 ()
  from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7d3ce39 in PR_WaitCondVar () from /usr/lib/libnspr4.so.0d
#3  0xb786adbe in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#4  0xb786a6f2 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#5  0xb7d431e1 in ?? () from /usr/lib/libnspr4.so.0d
#6  0xb808c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0xb7ee07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0xb53beb90 (LWP 3366)):
---Type <return> to continue, or q <return> to quit---
#0  0xb80d4430 in __kernel_vsyscall ()
#1  0xb80903a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
  from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7d3bf9e in ?? () from /usr/lib/libnspr4.so.0d
#3  0xb7d3cdc0 in PR_WaitCondVar () from /usr/lib/libnspr4.so.0d
#4  0xb7a65148 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#5  0xb7a621f8 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#6  0xb7a32b1c in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#7  0xb7a6295f in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#8  0xb7d431e1 in ?? () from /usr/lib/libnspr4.so.0d
#9  0xb808c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#10 0xb7ee07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb5bbfb90 (LWP 3365)):
#0  0xb80d4430 in __kernel_vsyscall ()
#1  0xb7ed5f77 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7d3ed8c in ?? () from /usr/lib/libnspr4.so.0d
#3  0xb730ce3f in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#4  0xb730d334 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#5  0xb730d5de in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#6  0xb7a6219a in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#7  0xb7a32b1c in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#8  0xb730d057 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
---Type <return> to continue, or q <return> to quit---
#9  0xb7a621f8 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#10 0xb7a32b1c in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#11 0xb7a6295f in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#12 0xb7d431e1 in ?? () from /usr/lib/libnspr4.so.0d
#13 0xb808c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#14 0xb7ee07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7dfd6c0 (LWP 3361)):
#0  0xb80d4430 in __kernel_vsyscall ()
#1  0xb7ed8c01 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb6592e5f in ?? () from /usr/lib/libxcb.so.1
#3  0xb659356e in ?? () from /usr/lib/libxcb.so.1
#4  0xb6593afb in xcb_send_request () from /usr/lib/libxcb.so.1
#5  0xb6b96166 in _XPutXCBBuffer () from /usr/lib/libX11.so.6
#6  0xb6b96530 in ?? () from /usr/lib/libX11.so.6
#7  0xb6c47f82 in XRenderFreePicture () from /usr/lib/libXrender.so.1
#8  0xb6e9f962 in ?? () from /usr/lib/libcairo.so.2
#9  0xb6e83e6e in cairo_surface_finish () from /usr/lib/libcairo.so.2
#10 0xb6e83f18 in cairo_surface_destroy () from /usr/lib/libcairo.so.2
#11 0xb6e7b178 in cairo_pattern_destroy () from /usr/lib/libcairo.so.2
#12 0xb7a9b043 in gfxPattern::~gfxPattern ()
  from /usr/lib/xulrunner-1.9.0.4/libxul.so
#13 0xb79c6186 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
---Type <return> to continue, or q <return> to quit---
#14 0xb7419241 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#15 0xb740383d in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#16 0xb7403fbd in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#17 0xb740c8c7 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#18 0xb740cc61 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#19 0xb740cce7 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#20 0xb740cc61 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#21 0xb740cce7 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#22 0xb740cc61 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#23 0xb741bf47 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#24 0xb7422611 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#25 0xb7662d40 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#26 0xb76632fc in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#27 0xb7663d76 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#28 0xb765ea2c in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#29 0xb79a21c4 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#30 0xb799da5c in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#31 0xb799dfbd in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#32 0xb68d0036 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#33 0xb6d14c4b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#34 0xb6d2b095 in ?? () from /usr/lib/libgobject-2.0.so.0
#35 0xb6d2c62b in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#36 0xb6d2cc26 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
---Type <return> to continue, or q <return> to quit---
#37 0xb69e533e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#38 0xb68c9f73 in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
#39 0xb672c9b5 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#40 0xb672d27b in gdk_window_process_updates ()
  from /usr/lib/libgdk-x11-2.0.so.0
#41 0xb799e8f5 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#42 0xb7661766 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#43 0xb7661777 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#44 0xb7661777 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#45 0xb76619dd in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#46 0xb76610c0 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#47 0xb766308d in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#48 0xb7661954 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#49 0xb76b9297 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#50 0xb76bd933 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#51 0xb76af802 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#52 0xb76ac1ef in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#53 0xb748f098 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#54 0xb748fb41 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#55 0xb75c331c in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#56 0xb75c4646 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#57 0xb7a6e085 in NS_InvokeByIndex_P ()
  from /usr/lib/xulrunner-1.9.0.4/libxul.so
---Type <return> to continue, or q <return> to quit---
#58 0xb72da9a3 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#59 0xb72e1e53 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#60 0xb7daac65 in js_Invoke () from /usr/lib/xulrunner-1.9.0.4/libmozjs.so
#61 0xb7daafb4 in ?? () from /usr/lib/xulrunner-1.9.0.4/libmozjs.so
#62 0xb7dab0b9 in ?? () from /usr/lib/xulrunner-1.9.0.4/libmozjs.so
#63 0xb7db2664 in ?? () from /usr/lib/xulrunner-1.9.0.4/libmozjs.so
#64 0xb7d9e635 in ?? () from /usr/lib/xulrunner-1.9.0.4/libmozjs.so
#65 0xb7daacb4 in js_Invoke () from /usr/lib/xulrunner-1.9.0.4/libmozjs.so
#66 0xb7d9999f in ?? () from /usr/lib/xulrunner-1.9.0.4/libmozjs.so
#67 0xb7d9eaeb in ?? () from /usr/lib/xulrunner-1.9.0.4/libmozjs.so
#68 0xb7daacb4 in js_Invoke () from /usr/lib/xulrunner-1.9.0.4/libmozjs.so
#69 0xb7d9999f in ?? () from /usr/lib/xulrunner-1.9.0.4/libmozjs.so
#70 0xb7d9eaeb in ?? () from /usr/lib/xulrunner-1.9.0.4/libmozjs.so
#71 0xb7daacb4 in js_Invoke () from /usr/lib/xulrunner-1.9.0.4/libmozjs.so
#72 0xb7d9999f in ?? () from /usr/lib/xulrunner-1.9.0.4/libmozjs.so
#73 0xb7d9eaeb in ?? () from /usr/lib/xulrunner-1.9.0.4/libmozjs.so
#74 0xb7daacb4 in js_Invoke () from /usr/lib/xulrunner-1.9.0.4/libmozjs.so
#75 0xb72d7b21 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#76 0xb72d343d in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#77 0xb7a6eb90 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#78 0xb75898c1 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#79 0xb7589e0f in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#80 0xb75a0819 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
---Type <return> to continue, or q <return> to quit---
#81 0xb75a0915 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#82 0xb75a0d22 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#83 0xb75a0f45 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#84 0xb75485d8 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#85 0xb7536637 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#86 0xb7549f5c in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#87 0xb754ff77 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#88 0xb7a621f8 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#89 0xb7a32b1c in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#90 0xb79b5e58 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#91 0xb784b610 in ?? () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#92 0xb72af658 in XRE_main () from /usr/lib/xulrunner-1.9.0.4/libxul.so
#93 0x080491ab in ?? ()
#94 0xb7e15685 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#95 0x08048d11 in ?? ()
#0  0xb80d4430 in __kernel_vsyscall ()

---

### Post by ender1598 on 2008-11-29
I noticed something similar too.  I've used Opera and Firefox both and it seems like with heavy loading they just drop out.  Simpler sites don't cause problems but very busy sites like boingboing.net or wowinsider.com can cause both of my browsers to just dissapear.  I've also noticed that in general it seems to take a lot longer to connect to web pages.  This does not occur on other computers in the house.  It's strange but if I'm going to a new site there's very little network activity for maybe 10 seconds and then suddenly it'll start loading.  It's hard to describe but it might be related to the same problem.

---

### Post by jbcola on 2008-12-13
Same for me, but only on my 4core 64bit PC, not on a 32bit laptop installation of ubuntu.

---

### Post by jbcola on 2008-12-13
Hey, i think it was linked to this bug:

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/282287](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/282287)

---

