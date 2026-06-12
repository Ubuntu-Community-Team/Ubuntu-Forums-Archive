---
title: "strange one - can ONLY pull wep encrypted dhcp"
date: 2005-07-09
forum: Hardware &amp; Laptops
---

### Post by endtransmission on 2005-07-09
For the life of me I cannot pull wifi dhcp address UNLESS it has a wep key.  Flippin nuts.  I've tried everything I can think of.

This is a Thinkpad T30 running the cisco aironet 802.11b chipset...  what is that, 350, 300?  Something like that.  Whatevers stock.  

I just flipped this machine from Gentoo to Ubuntu so I know the hardware works.  The airo module is loaded properly (AFAICT), but it simply will not pull an address.  WEP enabled?  no problem.  No WEP?  no IP.  

lame.

I've gutted it if the "handy" ubuntu networking scripts in an effort to troubleshoot (removing complexity) - no change tho.  Using strictly dhcpcd as thats what I'm most familiar with and what worked before.

Thanks everyone

---

### Post by jc3835 on 2005-07-11
My first thought is that it sounds like you have WEP enabled on your router, which would cause the router to reject DHCP requests from devices not sending the WEP key.
If you disable WEP in the router, it should connect, but that's not really the greatest ideas for long-term use.

JC

---

