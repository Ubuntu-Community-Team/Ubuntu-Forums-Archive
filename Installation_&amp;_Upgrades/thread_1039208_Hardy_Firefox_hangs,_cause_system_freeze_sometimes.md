---
title: "Hardy Firefox hangs, cause system freeze sometimes"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by mailforbiz on 2009-01-14
Hi

I've been having occasional Firefox freezes (3.0.x ) since about a month. The freezes happen especially when some scripting is involved on the page I'm visiting for example, if I have a popup chat window open doing online chat on a website, or if the page has flash animation or some such activity. In some cases, the whole system hangs up to the point that I have to do a hard reset. 


A freeze just occured and I managed to do a strace on the firefox processes. I was doing online chat with Customer Service Rep of a website. After the chat ended, both the firefox windows froze. Doing a strace on the chat window showed that it was in a select() call. I killed that window but it wouldn't go away from the gnome-panel. The other window was still frozen. strace on that showed this:

```

myprompt:~$ strace -p 6767
Process 6767 attached - interrupt to quit
futex(0xc150760, 0x80 /* FUTEX_??? */, 2) = ? ERESTARTSYS (To be restarted)
--- SIGIO (I/O possible) @ 0 (0) ---
futex(0xaf007d70, 0x81 /* FUTEX_??? */, 1) = 1
rt_sigreturn(0xc150760)                 = 240
futex(0xc150760, 0x80 /* FUTEX_??? */, 2) = ? ERESTARTSYS (To be restarted)
--- SIGIO (I/O possible) @ 0 (0) ---
futex(0xaf007d70, 0x81 /* FUTEX_??? */, 1) = 1
rt_sigreturn(0xc150760)                 = 240
futex(0xc150760, 0x80 /* FUTEX_??? */, 2) = ? ERESTARTSYS (To be restarted)
--- SIGIO (I/O possible) @ 0 (0) ---
futex(0xaf007d70, 0x81 /* FUTEX_??? */, 1) = 1
rt_sigreturn(0xc150760)                 = 240
futex(0xc150760, 0x80 /* FUTEX_??? */, 2) = ? ERESTARTSYS (To be restarted)
--- SIGIO (I/O possible) @ 0 (0) ---
futex(0xaf007d70, 0x81 /* FUTEX_??? */, 1) = 1

```

I don't know if any of this is normal. Doing killall of gnome-panel and gnome-desktop wouldn't do any good.

I have ruled out issues with my wireless card by connecting to Ethernet directly (still, its Broadcom 4312 if its any help). I don't know where else to look. I don't care about the occasional Firefox freezes but its the accompanying system freezes which have me worried.

Thanks in advance for any help!
Hardy 8.04 on Dell 1530
Firefox 3.05

---

