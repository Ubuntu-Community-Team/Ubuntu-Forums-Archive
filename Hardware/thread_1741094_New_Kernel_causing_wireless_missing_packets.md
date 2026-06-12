---
title: "New Kernel causing wireless missing packets"
date: 2011-04-27
forum: Hardware
---

### Post by sreilly on 2011-04-27
Hi,

I'm running 10.10 on a Zotac ID40 nettop box, and very fine it is too.

The other day, however, I upgraded the kernel to 2.6.35-28-generic and since then the wireless connection has become sporadic (despite showing all the bars/100% from my line-of-sight Netgear DG834, distance <10m)

Running ping show a number of packets are being dropped to both internal network machines and internet locations.
Local Wireless Access Points are also noticeable by their absence - showing two instead of the more usual ten.

I tried compiling/installing the RaLink RT2860 drivers from the Ralink site and that now, at least, showed the true(?) levels on the system tray wireless icon - wild fluctuations and random disconnects.

Re-installing kernel 2.6.35-25-generic fixes the wireless issue and the number of visible local WAPs returns to normal.

Just wanted to voice my concern that something is wrong with 2.6.35-28.

Steve

---

### Post by KegHead on 2011-04-27
Hi!

Did you install kernel via;

Sudo apt-get update

sudo apt-get install linux-image-f

Restart

KegHead

---

### Post by sreilly on 2011-04-28
Hi,

I did the usual;

# apt-get update
# apt-get dist-upgrade -y
# sync; sync; reboot

Steve

---

### Post by KegHead on 2011-04-28
Hi!

Try:

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Restart

KegHead

---

### Post by sreilly on 2011-04-28
Hi KegHead,

Not really sure what your intentions are.
I didn't have problems installing the 2.6.35-28 kernel or headers. The Zotac ID40 ran fine, except for this wireless issue.

Steve

---

### Post by KegHead on 2011-04-28
Hi!

To completely update/upgrade your machine.

Could solve your problem.

KegHead

---

### Post by sreilly on 2011-04-28
Hi,

OK I'll give it another shot tonight.

Thanks,

Steve

---

### Post by sreilly on 2011-04-29
Hi KegHead,

I am surprised to say that your suggestion worked!

... and a little concerned.

I had to also do;

sudo apt-get install linux-headers-2.6.35-28 -f

But what concerns me is that there was no indication of an install error during the initial installation of 28 or in the dpkg.log file.

Oddly, with 28 I still only see two of my neighbours WAPs, but many more with 25 (Not that I'm looking at other peoples WAPs!)

Many thanks for your help.

Steve

---

### Post by KegHead on 2011-04-29
Hi!

Always has worked for me.

KegHead

---

