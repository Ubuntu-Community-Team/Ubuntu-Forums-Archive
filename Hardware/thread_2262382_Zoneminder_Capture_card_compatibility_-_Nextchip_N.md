---
title: "Zoneminder Capture card compatibility - Nextchip NVP1204"
date: 2015-01-24
forum: Hardware
---

### Post by tyler60 on 2015-01-24
Hi all,

I bought am 8ch capture card on eBay, not realizing it was meant for a PC based environment. The software that you have to download to use it is very user-UNfriendly and Windows based, so it doesn't suit my needs.

Unfortunately, it doesn't seem to be recognized by linux, or at the very least, zoneminder. I have another 4ch card that Zoneminder works okay with (but at only 2fps per channel) and can be accessed using /dev/video0

I know linux is seeing the 8ch card (NextChip NVP1204 ST-6816-04A) because after using lspci, it shows up on the list as:
```

Multimedia video controller: Device 1b07:1204

```

I can't imagine I am the only one who is/has tried to get this card to work, does anyone know if it will work? And if so, do I need additional Linux drivers for it? Or can it function under a different /dev/*alias* ?

Please bare in mind, I am somewhat new to linux/zoneminder, so step by step instructions or links to tutorials might be required. 

Thanks.

[edit] I should also note that I am using Ubuntu Server 14.04.1 LTS x64 [/edit]

---

