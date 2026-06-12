---
title: "Will Ubuntu work on this HP laptop?"
date: 2009-05-08
forum: Hardware
---

### Post by dan10 on 2009-05-08
I'm considering buying the [HP G70t laptop]("http://www.shopping.hp.com/webapp/shopping/computer_series.do?storeName=computer_store&category=notebooks&series_name=G70t_series&a1=See%20all&v1=series"), on which I hope to run Ubuntu. I have referred to the [buyinghardware]("https://help.ubuntu.com/community/buyinghardware") page. I will definitely choose the Intel graphics option. But I'm concerned about wireless. There are four options, and I want whatever's the cheapest option that will work with Ubuntu:

Wireless-G Card ($0.00)
Intel Next-Gen Wireless-N Mini-card ($25.00)
Wireless-G Card with Bluetooth ($25.00)
Intel Next-Gen Wireless-N Mini-card with Bluetooth ($50.00)

I asked a sales agent, via online chat, who the manufacturer of the plain vanilla Wireless-G card is. She said: "For proprietary reasons we can't divulge some of our third party partners. However, I would like to assure that every bits and pieces of HP products are made from the latest technology." She did say that it was not from Intel.

If I buy this computer with the free Wireless-G card and install Ubuntu, will Ubuntu recognize the wireless card? Or should I pay the $25 for Intel Wireless-N, to guarantee it will work? (it will definitely work, because it's Intel, right?) Is there anything else I should consider before buying it?

---

### Post by Dark_Stang on 2009-05-08
We'll need more information than that. And that HP sales rep flat out lied to you. She didn't say what was in it because she didn't know. Chances are it's a broadcom or atheros card. Broadcom cards pretty much all work, either under the broadcom drivers, under bcm43xx drivers, or with ndiswrapper. I'm not sure about Atheros cards.

You may want to check out some brick and morter stores too. A lot of these stores sell their core products (laptops and desktops) below cost and hope to make up the difference on accessories. Plus, if you go to the store you can check out device manager in windows and see exactly what hardware us inside it.

---

