---
title: "A question on hot swapping HDDs"
date: 2012-01-15
forum: Hardware
---

### Post by Sylos on 2012-01-15
Hello all.

I've spent the last few hours pondering and googling around the issue of hot swapping HDDs and appear to be getting no closer to an answer. So Im thinking I will post here and see if anyone who has more intelligence than me can answer the question(s).

I'm building a new rig with a Gigabyte ga-z68ap-d3 MB and Im looking into the case for it. The coolermaster CM690 II Advanced has a couple of interesting features that Im not sure if I can utilize with this MB. 

First, the case an esata port on the front. Now, the MB doesnt have an esata port (not that I can see anyway) and if Im right with my knowledge i shouldnt just plug it into a normal sata port as the power flowing over them is different. Is that correct or just hearsay?

Second, the case has a dock on the top for sliding in a standard sata drive. The issue here is Im not sure if I will be able to hot swap. Reading around seems to suggest that it will be ok if ahci is enabled on the MB. Again Im not sure if this is true or just more static I have picked up from the web.

Any thoughts will be welcome.

Cheers

---

### Post by Sylos on 2012-01-16
Bumping...

---

### Post by Sylos on 2012-01-18
Another bump for the cause....

---

### Post by Grenage on 2012-01-18
> **Sylos said:**
> Hello all.

I've spent the last few hours pondering and googling around the issue of hot swapping HDDs and appear to be getting no closer to an answer. So Im thinking I will post here and see if anyone who has more intelligence than me can answer the question(s).

I'm building a new rig with a Gigabyte ga-z68ap-d3 MB and Im looking into the case for it. The coolermaster CM690 II Advanced has a couple of interesting features that Im not sure if I can utilize with this MB. 

First, the case an esata port on the front. Now, the MB doesnt have an esata port (not that I can see anyway) and if Im right with my knowledge i shouldnt just plug it into a normal sata port as the power flowing over them is different. Is that correct or just hearsay?

Second, the case has a dock on the top for sliding in a standard sata drive. The issue here is Im not sure if I will be able to hot swap. Reading around seems to suggest that it will be ok if ahci is enabled on the MB. Again Im not sure if this is true or just more static I have picked up from the web.

Any thoughts will be welcome.

Cheers

If the motherboard can handle SATA hot-swap (I think most state it in those simple terms), then you should be ok.  I frequently swap out SATA devices.

eSATA is the same as SATA - as long as it is just eSATA.  I think there's a Powered eSATA, but I've never actually seen one.

---

### Post by saneearth on 2012-01-18
If AHCI is enabled it is supposed to be ok, but erring on the side of caution I would not want to do so. I have done it with servers to rebuild an array, but I typically don't do this at home. Matter of fact when I use my middle drive bay I seem to always have that drive pre-maturely fail. Heat I think. Anyway, the short answer is you can, but personally I wouldn't unless there is a "production" reason to do so.

---

### Post by Sylos on 2012-01-18
> **Grenage said:**
> If the motherboard can handle SATA hot-swap (I think most state it in those simple terms), then you should be ok.  I frequently swap out SATA devices.

eSATA is the same as SATA - as long as it is just eSATA.  I think there's a Powered eSATA, but I've never actually seen one.

Cheers for the post.

Im using a gigabyte GA-z68AP-D3 and I cant find anything anywhere to state that it is hot swap capable - but then I cant find anything to say it cant. I was unsure as to wether AHCI would enable me to do so on any MB or only a suitably equipped one?

A friend suggested I just try it - he seems to think the worst that will happen is it will instantly blue screen if it doesnt work. I still cant help but fear damage as a result of it. Id hate to spend all this money building a rig and then hose it!

Its not a deal breaker anyway - I just wondered if I will be able to utilise the dock on the case if I get it.

Cheers

---

### Post by Grenage on 2012-01-18
> **Sylos said:**
> Im using a gigabyte GA-z68AP-D3 and I cant find anything anywhere to state that it is hot swap capable - but then I cant find anything to say it cant. I was unsure as to wether AHCI would enable me to do so on any MB or only a suitably equipped one?

It probably will, but it will be down to the chipset.  A call to the local (if there is one) Gigabyte line might yield some results.

> **Sylos said:**
> A friend suggested I just try it - he seems to think the worst that will happen is it will instantly blue screen if it doesnt work. I still cant help but fear damage as a result of it. Id hate to spend all this money building a rig and then hose it!

The old molex connectors (who actually misses them?) could allow for some nasty damage, but I've never had an issue with damage.  Please be aware that I am basing this on personal experience and a little reading over the years.[/QUOTE]

> **Sylos said:**
> Its not a deal breaker anyway - I just wondered if I will be able to utilise the dock on the case if I get it.

My money is on yes, but there's a chance it won't work.  For the record, I swap archive drives around, which I no longer write to.  I don't know how caching would affect SATA drives if they were unexpectedly removed.

---

