---
title: "Slow internet"
date: 2011-09-20
forum: Hardware
---

### Post by yashios14 on 2011-09-20
Well I know this topic has been covered many times as I have searched through a ton of the posts to try and fix my problem but to no avail.  Have been running ubuntu 10.10 for about 2 months now and really like the performance and layout of everything.  What I DON'T like is the fact that although Im connected wirelessly to the internet with anywhere between 80%-90% signal strength, my internet still loads like 56K.  Thats if it even loads the damn page at all.  Half the time it just leaves a blank screen but the progress bar at the bottom is almost complete and it just sits there.    

I am running the Realtek 8182 wireless card and Im sure that probably has something to do with it.  I have tried downloading different drivers for it and they either didn't work at all or only showed etho but no wireless.  Anyways Im willing to provide any and all source code you need to help me figure this out. 

Please help and sorry for my frustration but this is ridiculous.
Cameron

---

### Post by Metaxa on 2011-09-20
When you connect an Ethernet cable to your machine what is the performance like?

What drivers have you tried already?

These answers will help in answering your question.


Regards,

Metaxa

---

### Post by jvance492 on 2011-09-20
When you ping out to the internet or your ISP what is your average ping time. 

pingtest.net could do this

I like the idea of trying ethernet to rule the adapter out.

Windows will not help you if this is a ISP issue.

Windows will not help you ever :)

speedtest.net make sure your ISP is not congested.

tracepath google.com

Make sure your ISP doesnt have a million HOPS before there provider.

If its not an ISP issue, check your MTU setting if you have ADSL. Reducing it to 1454 can help with some providers or 1492 with good providers.

Try changing your wireless channel, maybe you have noise on the channel. 

Make sure your routers not overloaded by a torrent client or the like. 

Plug directly to your modem and see if its better.

Try a different browser. Chromium Rocks.

Make sure your neighbors arnt congesting your link if you have open security.

---

### Post by yashios14 on 2011-09-20
Ok Im not sure what drivers I had downloaded as it was awhile back when I was messing with all this.  Got fed up so I put it away for awhile and figured I open her back up and see if I could figure anything out now.  

First off I can't connect directly to the modem.
I ran the ping test on that site and it came back with 36ms.
On the second site you listed I ran the test and it came back with 49ms ping, .69 download, .37 upload.
Im not sure exactly what you mean by tracepath google.com
Tried the 1454 and 1492 mtu settings and no change.
The connection is secure so shouldn't be any outside congestion from neighbors and im not running any sort of torrent client.
Im going to try downloading Chromium and see if that helps out.

Thanx for the suggestions and keep them coming.  Like I said I really like how this OS performs its just the internet is killing me.
Cameron

---

### Post by jvance492 on 2011-09-21
Thats a low download speed but not dialup. It should be 10 times faster than 56k. 

The direct to the modem issue could be because the modems in bridge mode, which means you have to setup the PPPOE connection on the local PC. Or maybe dhcp is disabled on the modem. 

Its ADSL im assuming

The ping time looks great, did you get any packet loss?

Try booting up to a ubuntu live CD and see if that resolves the issue.

---

### Post by diasf on 2011-09-21
1) On cable (or a different card/different network) is any better?
2) How is your dns configuration? tried changing it?

---

### Post by jvance492 on 2011-09-21
> **diasf said:**
> 1) On cable (or a different card/different network) is any better?
2) How is your dns configuration? tried changing it?

Yeah. if its a DNS issue try assigning 8.8.8.8 and 8.8.4.4 to your local work station. These are Googles public DNS servers.

---

### Post by yashios14 on 2011-09-21
> **jvance492 said:**
> Yeah. if its a DNS issue try assigning 8.8.8.8 and 8.8.4.4 to your local work station. These are Googles public DNS servers.

I can connect just fine to other wireless networks as I have gone to a buddy's house and had no problems.  As for the DNS settings I have not altered them nor do I have any idea where to go to alter them and exactly how to use your addresses listed above.  Please explain a little more indepth and Ill try it out and hope for the best.
Thanx, Cameron

---

