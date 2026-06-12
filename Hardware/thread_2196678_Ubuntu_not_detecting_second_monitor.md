---
title: "Ubuntu not detecting second monitor?"
date: 2013-12-30
forum: Hardware
---

### Post by TheKingOfComputers on 2013-12-30
Hello forum-goers,

I recently purchased a second monitor for my desktop (HP 2211x 21.5 inch LCD monitor) and it won't be recognized by Ubuntu. I went into System -> Preferences -> Display and clicked "Detect Displays" (or something of the like) and my second monitor wasn't picked up. I double checked the connection (unplugged, replugged) but to no avail.

I figured perhaps the DVI port didn't have a connection to the motherboard, but it seems everything is connected properly, pic related:
[IMG]http://i43.tinypic.com/de3vb.jpg[/IMG]

The white port is the DVI, and it seems to be connected properly to the circuit.

By no means do I have any clue what I'm doing (:lolflag:), so please enlighten me as to whether or not this is a correct setup, and if not how do I fix it.

Regards,
ComputerKing

---

### Post by QIII on 2013-12-30
Hello!

Could you check your machine's documentation and let us know whether the motherboard will support multiple monitors?  Besides the on-board graphics, do you have a dedicated card?

---

### Post by TheKingOfComputers on 2013-12-30
> **QIII said:**
> Hello!

Could you check your machine's documentation and let us know whether the motherboard will support multiple monitors?  Besides the on-board graphics, do you have a dedicated card?

I have a dedicated Nvidia card.

As per [http://h20566.www2.hp.com/portal/site/hpsc/template.PAGE/public/kb/docDisplay/?javax.portlet.begCacheTok=com.vignette.cachetoken&javax.portlet.endCacheTok=com.vignette.cachetoken&javax.portlet.prp_ba847bafb2a2d782fcbb0710b053ce01=wsrp-navigationalState%3DdocId%253Demr_na-c03173335-12%257CdocLocale%253D%257CcalledBy%253D&javax.portlet.tpst=ba847bafb2a2d782fcbb0710b053ce01&sp4ts.oid=5187019&ac.admitted=1388465086992.876444892.199480143](http://h20566.www2.hp.com/portal/site/hpsc/template.PAGE/public/kb/docDisplay/?javax.portlet.begCacheTok=com.vignette.cachetoken&javax.portlet.endCacheTok=com.vignette.cachetoken&javax.portlet.prp_ba847bafb2a2d782fcbb0710b053ce01=wsrp-navigationalState%3DdocId%253Demr_na-c03173335-12%257CdocLocale%253D%257CcalledBy%253D&javax.portlet.tpst=ba847bafb2a2d782fcbb0710b053ce01&sp4ts.oid=5187019&ac.admitted=1388465086992.876444892.199480143) , my motherboard supports dual monitors but only via a VGA + HDMI or DVI + HDMI combination. However, my motherboard's documentation claims a DVI + VGA combination is possible. Regardless, I cannot seem to use both VGA ports and so will attempt at DVI + VGA tomorrow, for I don't see an HDMI port on my display.

Goodnight,
ComputerKing

---

### Post by QIII on 2013-12-31
I don't know about HP with their odd proprietary configurations, but often desktop motherboards will not allow the use of dedicated and integrated cards simultaneously.

---

### Post by TheKingOfComputers on 2013-12-31
> **QIII said:**
> I don't know about HP with their odd proprietary configurations, but often desktop motherboards will not allow the use of dedicated and integrated cards simultaneously.
I believe this to be correct. My dedicated Nvidia card seems to be the only GPU in use. I don't think I would need my Intel graphics for a dual monitor setup?

---

### Post by QIII on 2013-12-31
You will need to have both monitors connected to the dedicated card, if you can configure it as described in the section about the card in the link you provided.

---

### Post by Bucky Ball on 2013-12-31
Bumblebee is designed just for this situation.

[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by TheKingOfComputers on 2013-12-31
> **QIII said:**
> You will need to have both monitors connected to the dedicated card, if you can configure it as described in the section about the card in the link you provided.

That is not possible! The only option would be to use an HDMI setup but my display has not HDMI output. 

I suppose I could fiddle around and attempt to run both my Nvidia and Intel GPUS? But that seems counterintuitive, if not impossible.

---

### Post by Bucky Ball on 2014-01-01
Did you notice my post regarding Bumblebee???

---

