---
title: "toshiba l655d laptop wireless networking freezes and requires reconnect to work again"
date: 2011-02-15
forum: Hardware
---

### Post by Colonel_Ingus on 2011-02-15
Toshiba L655D Laptop.

Ubuntu 10.10

Wireless works for a few minutes then freezes and won't work again unless I click disconnect and then reconnect to the same network. 

Any ideas?

---

### Post by Colonel_Ingus on 2011-02-18
anyone?

---

### Post by Colonel_Ingus on 2011-02-21
Every 3 minutes it freezes.. now it will come back if I wait about 2 minutes, but then freeze again in 3-5 minutes and so on.. or I can just reconnect and it works.

---

### Post by Colonel_Ingus on 2011-03-03
Can anyone tell me something to type in, to get more info, to help diagnose this issue?


Please help me.

---

### Post by Colonel_Ingus on 2011-03-03
If left, after the connection freezes, after several minutes it starts working again on its own.

---

### Post by Colonel_Ingus on 2011-03-10
Being really patient here, as you can see above..

Anyone, any help at all? Someone that's an advanced user could maybe help me diagnose this issue...

---

### Post by random417 on 2011-03-10
I'm having the same problem. It will work fine, for a while, but then it stops working. I had some problems finding the right driver, but I believe that's right now. I'm on it now, so it does work, but I work online and I can't get it to be stable enough to work, it just quits. If I get it worked out, I'll post how on here, but if anyone has any ideas, that would be great.

---

### Post by EvaRoach65 on 2011-03-10
Hi guys,I like the concept of that laptop,nice.

---

### Post by Colonel_Ingus on 2011-03-16
> **random417 said:**
> I'm having the same problem. It will work fine, for a while, but then it stops working. I had some problems finding the right driver, but I believe that's right now. I'm on it now, so it does work, but I work online and I can't get it to be stable enough to work, it just quits. If I get it worked out, I'll post how on here, but if anyone has any ideas, that would be great.

Same here, and please don't forget, we have to fix this issue. You and I man, we seem to be the only ones in it. 

If anyone else is willing to help PLEASE help

---

### Post by Colonel_Ingus on 2011-03-21
anything?

---

### Post by Colonel_Ingus on 2011-03-22
Anyone at all?

---

### Post by Colonel_Ingus on 2011-03-30
Still need help with this.

---

### Post by Colonel_Ingus on 2011-04-01
Okay I'm off work today, decided it was getting fixed no matter what.

First, the only way to even get it to work is to:
```

sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms

```...and then reboot.

Now if you're like me, you now have a wifi connection that cuts out every few minutes and requires a reconnect. 

It's just a DNS issue, using DHCP it automatically tries to use your ISP's DNS servers.
I like leaving DHCP on with my router, but every computer here has a specific IP, most routers will still allow you to do manual entry while having dhcp on, if not, turn it off.
So Edit Connections at the top right and enter:
```

ip: 192.168.1.5
mask: 255.255.255.0
gateway: 192.168.1.1
dns: 192.168.1.1 

```Just using my linksys router as the DNS server worked like a charm. It's completely stable now, never loses its connection.

---

