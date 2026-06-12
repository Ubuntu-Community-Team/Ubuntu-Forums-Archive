---
title: "razer lycosa keyboard issue on Ubuntu 10.04"
date: 2011-05-25
forum: Hardware
---

### Post by bvkmohan on 2011-05-25
hello guys :)

Have a small problem with in my ubuntu box
for some reasons the cursor and the mouse pointer are blinking randomly and are not letting me click on anything ... I have little bit of knowledge on linux, I've checked all the hardware cabling and all ... the only incompatible hardware I am using is Razer Lycosa keyboard, I figured out the problem, when I connect a normal keyboard it works fine but not with the Razer keyboard which is actually designed for gaming in windows :( when I checked the I/O ports for the Razer keyboard I found this 

bvkmohan@xen:/proc$ cat ioports | head -10
0000-001f : dma1
0020-0021 : pic1
0040-0043 : timer0
0050-0053 : timer1
0060-0060 : keyboard
0064-0064 : keyboard
0070-0071 : rtc0
0080-008f : dma page reg
00a0-00a1 : pic2
00c0-00df : dma2
bvkmohan@xen:/proc$ 
bvkmohan@xen:/proc$ 

Is this the problem ? can I reassign the ports to available I/O ports ? if so how can I do that ? ... I need this keyboard because I love it very much :P

my box : Ubuntu Lucid 32bit.

---

### Post by bvkmohan on 2011-06-07
I wish I could close this as unanswered ](*,)](*,)](*,)](*,):confused::popcorn:

---

### Post by ac14112 on 2012-02-13
I'm currently using Mint 11 (Ubuntu 11.04) and have experienced this same problem with the Razer Lycosa. 

Previously, I've experienced the issue on Mint 12 (Ubuntu 11.10).

Unplugging the keyboard and re-plugging seems to fix the issue. 

I would love to provide more info if it happens again, but I don't know what to look at to debug the issue. Dmesg had nothing weird as far as I could tell.

So far, this is the only place I could find with a description of this issue.

---

### Post by Vadi on 2012-03-23
I don't think this is a Ubuntu issue, but a keyboard one. If you read the reviews on newegg, everyone complains about it freezing up like this on you.

I've made a mistake of getting this keyboard recently.

---

