---
title: "Acer 5102WLMi wireless WEP no-go so far"
date: 2006-09-04
forum: Hardware &amp; Laptops
---

### Post by Mike'sHardLinux on 2006-09-04
A search of these forums turned up 2 threads where a user named cruiseraddict says they are successfully using Ubuntu on this laptop, but they didn't say if they were using encrypted wifi. It's hard to believe someone who uses Linux would use an un-encrypted wireless connection, but I know many actually do this from my experience on the Fedora forums.

I am able to have a great connection if I turn off encryption, but if I enable it, it doesn't work. Some googling turned up a russian website that claims this laptop uses an Atheros SL-5354mp chip.

I am using Ubuntu i386. When I install Ubuntu, the proper restricted modules are installed as far as I can tell.

Initially, I simply used System --> Administration --> Networking to configure ath0, but it takes a long time, and then encrypted wifi still doesn't work. Like I said, turning off encryption works fine.

I really don't know exactly what else to try. Here's some random information in case any of it might be of use:

**lspci**
```
0000:06:02.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)
```

**uname -r**
```
2.6.15-26.386
```
[B]
ifconfig[/B] shows that for RX packets there are 16846 errors, and for TX packets there are 9 errors.

I found what seems to be a script (wl.install.madwifi.sl5354mp.wrap) on madwifi.net that says it is for the sl5354mp. I modified the script to match the settings of my lan, but after it is done, I still have no network connection. It doesn't give any errors. Truthfully, I'm not even sure what this script is really supposed to do. I see it configures my wifi card, but then it also seems like it's trying to set it up as a router or something.

Has anyone had any success with encrypted(WEP) wifi on this laptop, or similar?

Oh, almost forgot, I absolutely refuse to use an un-encrypted wifi connection. (In reality, WEP is really the bare minimum of encryption, since it is relatively easy to break.)

I feel like I'm all over the place. I've tried some things that I don't even really know what they are doing. Any help or suggestions are appreciated.
Thanks

---

### Post by Haegin on 2006-09-22
Any update on this as I'm looking to buy this laptop. Also how is the support for the rest of it?

---

### Post by Bossieman on 2006-09-22
I am very interested in this computer. Shouldnt you use the 686 core instead of the 386? 386 doesnt support dual core.

---

