---
title: "External DVD drive works with laptop flawlessly, keeps giving me IO errors on tower."
date: 2019-10-22
forum: Hardware
---

### Post by thecarl2 on 2019-10-22
Hello. I've been getting answers from these forums for years but this is the first time I've actually had an issue I can't find the solution to on my own, so time to make my first post.

I have a DVD drive I've been using to make backups of my DVDs. It works perfectly with my laptop.
When I plug it into my tower (running Ubuntu 18.04.3 LTS (GNU/Linux 4.15.0-65-generic x86_64 Server) it keeps giving me IO errors.
It reads about 11Mb (plus or minus a few Kb) before this happens.

It reads normal CDs and unencrypted DVDs without an issue.
Only encrypted DVDs cause a problem.

I've installed and verified that libdvdcss2 and libdvdread4 are installed, and it does read the first ~11Mb correctly.

So after going through the troubleshooting guides and looking at some other issues people have had like this, I'm kinda lost as to what to do next.

Looking at the output of dmesg I get a lot of messages like this:[INDENT][101483.960894] print_req_error: I/O error, dev sr0, sector 14807812
[101484.432737] sr 0:0:1:0: [sr0] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[101484.432740] sr 0:0:1:0: [sr0] tag#0 Sense Key : Illegal Request [current] 
[101484.432743] sr 0:0:1:0: [sr0] tag#0 Add. Sense: Read of scrambled sector without authentication
[101484.432748] sr 0:0:1:0: [sr0] tag#0 CDB: Read(10) 28 00 00 38 7d 01 00 00 01 00
[/INDENT]

I do get an error like this on my laptop too, so I'm not sure if that's a hint.
Also I tried a few internal DVD drives and they have the exact same issue, so I don't think its a power supply issue.

So I'm wondering what I should do next to get more information as to what could be wrong.

---

