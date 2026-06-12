---
title: "No network connection"
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by aaron2073 on 2009-06-03
I am trying to connect to the internet via wireless. I can not get wireless network on the task bar. 
 
Error occured
W;Failed to Fetch http;//dell-mini.archive.canonical.com/updates/pool/public/l/linux/linuz-image-2.6.24-22-
lpia_2.6.24-22.45netbook10_lpia.deb
  Could not resolve 'dell-mini.archive.canonical.com'

---

### Post by theDaveTheRave on 2009-06-03
There should be something in the <system - control centre> menu where you can add a small icon for networking connectivity.

I know that I am using network manager (part of the standard gnome install), and it creates a list of the potential wirless networks that are available.

Are you unable to connect to the network?

can you see the wirless networks? 

try
```

iwlist scan

```
to show them.

if you can't see them we will need information on you wireless card

```

lshw -C network

```
will show you what your card is, search for the card (in the product section) in the forums and you should get more specific help if there is an issue with it (or post the results here).

David

---

### Post by aaron2073 on 2009-06-03
Under iwlist scan I get
lo       Interface doesn't support scanning.
eth0    Interface doesn't support scanning.
sms    Interface doesn't support scanning.
 
When I input lshw -C network  i get
bash: lshw: command not found

---

### Post by aaron2073 on 2009-06-03
I can not connect to the internet and I can not see wireless networks. I have the connection tab, but it only shows wired network.

---

### Post by Fangman on 2009-06-03
same problem I was having on my BRAND new (less than 2 days) Mini 1210. I called Dell and their solution was to reinstall ubuntu... The tech guy said that the most recent update wasn't compatible with my wireless that comes standard. I have no clue as to why this would be! Reinstall seems to have worked, except now I cannot connect to the wireless at school using the proxy server and same password info I used yesterday successfully. (oddly same issue happened on monday straight out of the box)

---

### Post by aaron2073 on 2009-06-03
Being new to ubuntu.. how do I reinstall ubuntu.. This computer is a birthday gift to my kids, from Grandma..So I very rarely go on it...

---

### Post by Fangman on 2009-06-23
well you need an external cd drive.... I luckilly had one that I was able to borrow from a friend.

---

### Post by aaron2073 on 2009-06-23
I got it fixed, after 3 hours on phone with Dell.. The did a complete upgrade and restored wireless network driver.. It was a pain.. It all started because an upgrade started and there was not enough memory for the upgrade...Not much space on the mini's.. Need external hard drive..

---

