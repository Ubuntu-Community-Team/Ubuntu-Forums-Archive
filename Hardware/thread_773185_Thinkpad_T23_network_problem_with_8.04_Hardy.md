---
title: "Thinkpad T23 network problem with 8.04 Hardy"
date: 2008-04-28
forum: Hardware
---

### Post by wookieman on 2008-04-28
Hi

I have a thinkpad T23 currently running xubuntu 7.04 perfectly well but I want to upgrade to 8.04. I tried recently upgrading to 7.10 but my network wouldn't work properly so I reloaded 7.04 and waited for 8.04 to be released.

Now 8.04 is out and I really want to upgrade to it for a number of updated packages that it has but my network problems are back.

I haven't installed it, just tried running the live cd. With the built in ethernet connection I can't get on the internet, I have read elsewhere that there is a problem with the 'e100' module that it uses.

I also have a Dlink pcmcia card that uses the 'tulip' module, with this I can access some websites but not others, namely I can access the mozilla site that is bookmarked in firefox, but no other site that I've tried works. On my local network I can access one of my web servers but not the other.

:confused:

any help very very gratefully received.

I will be slow though 'cos I have to boot up normally to read any suggestions you have, then reboot with the live cd, then write down and output, then reboot normally and then type up what I just wrote down. ](*,)

---

### Post by Saabuntu on 2008-05-09
Not sure why you are using a PCMCIA card when the T23 has built in NIC.
It should work right off the batt, you may want to check your BIOS firmware and see if you should update it.  Mine was two versions behind, I think they are up to 1.20 now.


As for your question just make sure your using a reliable cable and that your DHCP is working.  Check Network Manager to see if your aquiring an IP or not, and make sure you have a DNS server set.

I just upgraded to 8.04 and now I have no sound, so dont feel like your missing out.  I wish I could go back to 7.10, everything was working then...oh well the price we pay for upgrades instead of sticking with what works...

P.S- KDE4 isnt all that either on the T23....not worth it!

---

### Post by wookieman on 2008-05-17
> **Saabuntu said:**
> Not sure why you are using a PCMCIA card when the T23 has built in NIC.

I was trying a PCMCIA card because the onboard ethernet wasn't working with 8.04, it does work with 7.04.

> **Saabuntu said:**
> It should work right off the batt, you may want to check your BIOS firmware and see if you should update it.  Mine was two versions behind, I think they are up to 1.20 now.

I was way behind, 1.11, i've upgraded to 1.16, I've read there are problems with after market batteries not working with later firmware versions.

> **Saabuntu said:**
> As for your question just make sure your using a reliable cable and that your DHCP is working.  Check Network Manager to see if your aquiring an IP or not, and make sure you have a DNS server set.

I've tried with static, dhcp and roaming enabled, doesn't make any difference. I even removed the built in ethernet daughter card when I tried the PCMCIA ethernet card but no joy.

Two things to note:

1. I can ping from the command line with either ethernet and get results, but not load any internet sites in firefox except...

2. the default bookmark of [http://en-us.www.mozilla.com/en-US/firefox/central](http://en-us.www.mozilla.com/en-US/firefox/central) works but it's the only site that does.

Help, somebody, please...

---

### Post by Nigel-NZ on 2008-05-18
Hi there,

I have a very similar (identical?) issue with an IBM T22 now running 8.04.

I recently upgraded from 6.06 to 8.04.
For background, my T22 is partioned - Ubuntu 8.04 and Windows XP.

On the first power up of the day which boots into Ubuntu.
The network facing Ethernet port is active (I can see activity from other machines on my home network using Etherape). However I do not get any alloacted IP address from DHCP. No program that requires network access will work.

The only way I have found to get around this issue is to re-boot and load Windows XP (where the network connection with IP addresses all works), and then re-booting back into Ubuntu. The network connection is all fine at this stage.

If a subsequent restart/reboot is required Ubuntu restarts and the network connections is still OK.

Hope someone can suggest an solution.

Thanks.

---

