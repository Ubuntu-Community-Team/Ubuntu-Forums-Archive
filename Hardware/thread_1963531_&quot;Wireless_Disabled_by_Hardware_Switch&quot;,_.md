---
title: "&quot;Wireless Disabled by Hardware Switch&quot;, Thinkpad sl400, Natty"
date: 2012-04-22
forum: Hardware
---

### Post by Cocomaan on 2012-04-22
Hey folks, relative newbie here looking for some help in reactivating my wireless card.

I was previously running 10.10 when the wireless card was switched off (apparently - it was working one minute, stopped working the next). There is no windows dual boot on this machine. After it stopped working 10.10, I tried rebooting the machine, and then doing a clean install of 10.10, neither of which worked. I upgraded to Natty 11.04 today, and now it is telling me "wireless disabled by hardware switch".

I am running this on a Thinkpad SL400

Here's my iwconfig:
[INDENT]lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit: 7   RTS thr: off   Fragment thr: off
          Power Management: off[/INDENT]
Here's my rfkill list
[INDENT]1: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: yes[/INDENT]
I've looked at other threads, but I am having a pretty hard time figuring out what is going on. Can anyone help? Thanks!

---

### Post by ts3 on 2012-04-22
You've probably tried this but just in case, on general principles, I'd run "sudo rfkill unblock all".  If that does not work the first time and if you have a hardware switch (usually one of the fn buttons) toggle the switch and run "sudo rfkill unblock all" again.  

I remember coming across posts about enabling wireless through the BIOS settings but none of my laptops seem to have that option.  Might be worth a search and a try though :)

If that doesn't work either I'm out of ideas, sorry.

---

### Post by coldraven on 2012-04-22
Find the switch and switch it back on :p
[http://forums.lenovo.com/t5/SL-Series-ThinkPad-Laptops/SL400-SL300-500-tight-wireless-HW-switch/td-p/111399](http://forums.lenovo.com/t5/SL-Series-ThinkPad-Laptops/SL400-SL300-500-tight-wireless-HW-switch/td-p/111399)

---

### Post by Cocomaan on 2012-04-23
> **coldraven said:**
> Find the switch and switch it back on :p
[http://forums.lenovo.com/t5/SL-Series-ThinkPad-Laptops/SL400-SL300-500-tight-wireless-HW-switch/td-p/111399](http://forums.lenovo.com/t5/SL-Series-ThinkPad-Laptops/SL400-SL300-500-tight-wireless-HW-switch/td-p/111399)
Between this and the Fn+F5, it has turned back on! 

Thanks for the help everyone. I think it was my little brother in law, 11 years old and very curious.

---

