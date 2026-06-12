---
title: "hplip 2.7.10:  stack smashing detected"
date: 2007-11-12
forum: Hardware &amp; Laptops
---

### Post by raphinou on 2007-11-12
Hi,

I have a HP Photosmart 7280, which needs the latest hplip, version 2.7.10. I compiled and installed the tarball manuallu in /usr/local/hplip-2.7.10 on a Gutsy.

When running hp-setup, I get this after I select the ppd to use:

Failed to open device
*** stack smashing detected ***: python terminated
Aborted (core dumped)

An strace gives this at the end:

sendmsg(9, {msg_name(16)={sa_family=AF_INET, sin_port=htons(161), sin_addr=inet_addr("192.168.1.12")}, msg_iov(1)=[{"00\2\1\0\4\10public.1\240!\2\4U=2\357\2\1\0\2\1\0000\023"..., 50}], msg_controllen=24, {cmsg_len=24, cmsg_level=SOL_IP, cmsg_type=, ...}, msg_flags=0}, MSG_DONTWAIT|MSG_NOSIGNAL) = 50
gettimeofday({1194866269, 990851}, NULL) = 0
gettimeofday({1194866269, 990866}, NULL) = 0
select(10, [9], NULL, NULL, {0, 999985}) = 1 (in [9], left {0, 976000})
recvmsg(9, {msg_name(16)={sa_family=AF_INET, sin_port=htons(161), sin_addr=inet_addr("192.168.1.12")}, msg_iov(1)=[{"0\202\1\270\2\1\0\4\10public.1\242\202\1\247\2\4U=2\357"..., 65536}], msg_controllen=0, msg_flags=0}, 0) = 444
close(9)                                = 0
open("/dev/tty", O_RDWR|O_NOCTTY|O_NONBLOCK) = 9
writev(9, [{"*** stack smashing detected ***:"..., 33}, {"python", 6}, {" terminated\n", 12}], 3*** stack smashing detected ***: python terminated
) = 51
rt_sigprocmask(SIG_UNBLOCK, [ABRT], NULL, 8) = 0
tgkill(29413, 29413, SIGABRT)           = 0
--- SIGABRT (Aborted) @ 0 (0) ---
+++ killed by SIGABRT (core dumped) +++
Process 29413 detached

Any idea?

Thanks

Raph

---

### Post by raphinou on 2007-11-12
Here's how I fixed it: 

I used python 2.4 in place of python 2.5:

cd /usr/bin
sudo rm python
sudo rm python-config
sudo ln -s python2.4 python
sudo ln -s python2.4-config python-config

in the source directory:
make clean
./configure --prefix=/usr/
make
sudo make install

then /usr/bin/hp-setup worked fine.

---

### Post by 11hjpphty76lkjj on 2007-11-13
You got this with python 2.5?  and python 2.4 works okay?  If you don't mind please post this in the hplip bugs section of launchpad.

[https://launchpad.net/hplip](https://launchpad.net/hplip)

Thanks!

A

---

