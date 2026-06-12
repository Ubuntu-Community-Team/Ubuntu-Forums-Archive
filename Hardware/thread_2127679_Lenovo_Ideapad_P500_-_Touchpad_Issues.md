---
title: "Lenovo Ideapad P500 - Touchpad Issues"
date: 2013-03-20
forum: Hardware
---

### Post by nars on 2013-03-20
I've recently installed Ubuntu on my [Lenovo Ideapad P500]("http://www.bestbuy.com/site/Lenovo+-+IdeaPad+15.6%22+Laptop+-+6GB+Memory+-+750GB+Hard+Drive+-+Graphite+Gray/6747387.p?id=1218792108550&skuId=6747387&ref=06&loc=01&ci_src=14110944&ci_sku=6747387&extensionType={adtype}:{network}&s_kwcid=PTC!pla!{keyword}!{matchtype}!{adwords_producttargetid}!{network}!{ifmobile:M}!{creative}#tab=specifications") and have been having some difficulties with the touchpad. My touchpad is detected sometimes and works for a few minutes after startup, but usually stops working soon after.

When it does work, running xinput -list gives me

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:400a	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:1025	id=11	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Lenovo EasyCamera                       	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
    &#8627; Ideapad extra buttons                   	id=14	[slave  keyboard (3)]
```

When it does not work I get

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:400a	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:1025	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Lenovo EasyCamera                       	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
    &#8627; Ideapad extra buttons                   	id=13	[slave  keyboard (3)]
```

Any help would be greatly appreciated, as you can see I generally use a mouse but it can be inconvenient at school and when I need to quickly access my computer. I never had any mouse issues prior to Ubuntu installation (Was running Windows 8, then Mint very briefly). Also, while I've experimented with Linux a bit over the years, I am still quite a novice and will need fairly easy to understand instructions ^_<

---

### Post by nars on 2013-03-31
:confused:

---

