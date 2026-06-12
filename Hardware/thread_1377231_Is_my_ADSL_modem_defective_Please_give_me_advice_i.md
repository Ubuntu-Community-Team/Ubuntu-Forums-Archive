---
title: "Is my ADSL modem defective? Please give me advice if you know what my problem is!"
date: 2010-01-10
forum: Hardware
---

### Post by s3a on 2010-01-10
This is a hardware problem not related to any OS. I tried two different routers, two different Ethernet wires, two different phone cables and all that is left to change is my ADSL modem but unlike all the previous stuff, I only have one ADSL modem. Here is why it is not obvious to me that the problem is the modem if it is; whenever I switched another thing or changed a setting in the router or power off the modem and router at night, my internet not only works but it works fast for a solid ~48 hours! Please someone, tell me what to do because I don't want to buy another modem if that's not the issue given that it's expensive. This issue is really aggravating me and my mom because the internet is slower than dial-up if it works at all!

Any input would be GREATLY appreciated!
Thanks in advance!

---

### Post by HermanAB on 2010-01-10
Your ISP may have changed to a newer version of ADSL and your modem doesn't handle the new bugs in the old protocol too well.  Your phone wire may be wet and your modem doesn't handle a bad signal too well.  So the problem may go away if you buy a new modem or it may not.  You won't know till you have gone and bought another one. Fortunately they don't cost too much.

BTW, you may be able to get your ISP to tweak the signal on their side.  They can change things in the DSLAM and observe the error rate, then adjust it for the lowest error rate.  So it may be a good idea to call your ISP tech support.

---

### Post by cascade9 on 2010-01-10
You could check to see if your router has newer firmware, that may fix it (its fixed a similar issue I was having with my router).

---

### Post by s3a on 2010-01-10
@HermanAB: I had a month (if not more) of stable internet usage with this ISP. You said modems are cheap...can you show me a good deal please? (because I've only found expensive ones)

@cascade9: I'll try doing that since it's do-able but I doubt it's the problem because I tried with two different routers not to mention that on this router when I had problems I did 192.168.0.1 and it reached the router's configuration menu without a problem while the actual internet did not work at all.

---

### Post by s3a on 2010-01-10
@cascade9: I checked and I already have the newest firmware.

---

### Post by Knowle on 2010-01-10
So you have slow speed issues but it works ok for around 48hours after you reboot the modem/router? Who's your ISP? What's the name of the modem and what kind of router do you have? Few random things..

Connect your modem directly to your computer. Do you still have problems? 
Try clearing your cache and cookies.
Shutdown your computer then power-cycle the modem(unplug it 5/10seconds).
After the dsl light is in sync start your computer up, try browsing and run a speed test, your ISP should have an official one on their site. It should match closely to whatever speed tier you have with them. It's possible you could have line problems and you'd need tech support to look at your dsl line profile so they can check current speeds, check noise level, try locking/unlocking sync port on modem, locking/unlock sync at dslam or remote dslam depending on your distance from the central office.

It could always be something silly like noise level being too high, virus/spyware on the PC, p2p program running in the background, someone leeching off your wifi, ect.

---

### Post by s3a on 2010-01-10
Does this exact product do what I want?: [http://www.trendnet.com/langen/products/proddetail.asp?prod=100_TDM-C400&cat=51](http://www.trendnet.com/langen/products/proddetail.asp?prod=100_TDM-C400&cat=51) (just asking for confirmation)

Also, how do I connect to my ADSL internet directly from my modem without using a router?

P.S.
ISP = VIF, Wireless Router = D-Link DI-524, Wired Router = D-Link DI-604, ADSL Modem = TP-Link TD8610. I feel that this is all pointless though and that I should just get the new modem already.

---

### Post by tgalati4 on 2010-01-11
dsl routers do wear out.  The chips get hot and warp leading to errors and slow performance.  The error-correction built into dsl can mask the aging effects, but eventually they die.  If you run your computer directly from the dsl modem, be sure to activate your firewall in both windows and linux.

Do check your cabling and have the phone company check the signal levels at their end.

man iptables

---

### Post by s3a on 2010-01-11
Does the "dying process" include functioning for 1-2 days until introducing the next issue?

---

### Post by cascade9 on 2010-01-11
> **s3a said:**
> Does the "dying process" include functioning for 1-2 days until introducing the next issue?

Nope. Well, I've used a dodgy ADSL modem and it was just slow, slow, slow no matter what you did.

If you dont have a filter...that might be an idea as well. While I dont think that noise is causing your issue, it might be, and if its noise-related, you could change modems till your blue in the face and it wont fix the problem (but with some modems you might find it is better or worse..some of them deal with noise better than others)  

> **s3a said:**
> Does this exact product do what I want?: [http://www.trendnet.com/langen/products/proddetail.asp?prod=100_TDM-C400&cat=51](http://www.trendnet.com/langen/products/proddetail.asp?prod=100_TDM-C400&cat=51) (just asking for confirmation)

Also, how do I connect to my ADSL internet directly from my modem without using a router?


Yep, that is an ADSL modem. 

Just hook the ethernet cable from the network port  on your computer to the ethernet port on the modem. Pretty easy. You might need to restart your computer and modem for that to work. 

BTW, you shouldn't need a firewall on linux...and even if you have a firewalled router, I would always run a software firewall with win. 

 Pure guess- your ISP is giving you a new IP every 48hrs, and your router isnt updating.

---

### Post by s3a on 2010-01-29
Ok so I bought a new modem and still the same problem :'(! I called my ISP and after a long talk, they made my phone line company come to fix the issue and this guy came and "fixed" it and then left. I should of stopped him before he left because I knew it subconsciously that all he did was check if the PPP light was green on my modem and the internet DOES work half of the time but right before it ceases to work, it slows down gradually then stops.

I purposely downloaded a torrent file last night to test the internet and I've noticed that under heavy internet load my internet ceases to work for a long while after that. I don't know at all if this relates to my issue in any way but I am desperate so I'm trying everything. I called my ISP again to say that the issue wasn't resolved and they told me if my phone line company has to come again and it's my fault, that I would have to pay.

So I asked what I could do to confirm if it's my fault and they gave me D-Link's phone number to see if my router is "configuring itself" like the guy said. I will call tonight but I am sooooo confident that it's not my fault but I can't find the exact source of the problem and this is really annoying especially when I need the internet for homework help! (Thankfully I can use the internet at school still) I was just hoping if someone could please help me further.

---

### Post by markbuntu on 2010-01-29
DSL modems have a diagnostic page that you should look at. It will tell you the signal levels and dropped packets etc. It is also possible that the modem keeps dropping you out of the internet. That used to happen to me sometimes and I would have to tell the modem to enable internet again even though the light was lit. 

Some ISPs have also imposed limits on downloads and will shut you off for a while if you exceed them. You should also ask them if they are doing maintenance in your area, that can screw things up intermittently.

I wish I had found this sooner, I have an old DSL modem I could have sent you. I recently switched to FIOS which is just way faster/better and cheaper than my old DSL service.

My sister had a similar problem to yours that went on for a year until she threatened to get another ISP. Finally one of the many techs that came found a filter on the phone line in the box on the outside of the house. It was put there by the cable company, go figure.

---

