---
title: "Output of regionset"
date: 2008-09-25
forum: General Help
---

### Post by spibou on 2008-09-25
When I run regionset I get
```

RPC Phase: II
type: NONE
vendor resets available: 4
user controlled changes resets available: 5
drive plays discs from region(s):, mask=0xFF

```
A comment in the file dvd_udf.h says "type: 0=NONE (no drive region setting)". Does this mean that I can play DVDs from any region?

---

### Post by mc4man on 2008-09-25
> Does this mean that I can play DVDs from any region? Not really. While you may be able to play some dvd's, at some point you won't be able to. Certainly all RCE disks (region coding enhanced) will not play on a drive that doesn't have a region set.
All open sources players don't enforce region coding so in the long run it's better to set the drive **once **to the region your in (or to what the majority of your dvd's are if different.


1 = North America (USA and Canada)
2 = Europe, Middle East, South Africa and Japan
3 = Southeast Asia, Taiwan, Korea
4 = Latin America, Australia, New Zealand
5 = Former Soviet Union (Russia, Ukraine, etc.), rest of Africa, India
6 = China

---

### Post by spibou on 2008-09-25
> **mc4man said:**
> Not really. While you may be able to play some dvd's, at some point you won't be able to.
What would that point be? So far I've played plenty of region 2 DVDs with no problem at all. An exception is the "Taxi 2" one which appears in my signature. Do you think the problem with that might be related to  region?
> **mc4man said:**
> Certainly all RCE disks (region coding enhanced) will not play on a drive that doesn't have a region set.
Is there a way to find out before buying (usually from amazon.co.uk) a DVD whether it's RCE? So far I've bought several DVDs of well known movies and they have played fine.
> **mc4man said:**
> All open sources players don't enforce region coding so in the long run it's better to set the drive **once **to the region your in (or to what the majority of your dvd's are if different.
When you say "open sources players" you are referring to software, yes? I thought regions were enforced by hardware for "RPC Phase: II" players which mine is. Apart from that, if the region is **not** being enforced then why set a region?

On a practical note, occasionally I see a region 1 DVD and I can't find the title in region 2. So far I haven't bought any but I'm wondering whether I would be able to watch them without buying additional hardware.

---

### Post by mc4man on 2008-09-25
> I thought regions were enforced by hardware 
Yes and no . If you've ever tried to play a dvd on windows with power dvd or such, the *player* will require a region being set on the drive (and also a match to the disk). Hardware wise most dvd drives are very "lax" in this regard. The exception is most Matshita dvd drives which will only allow access to encrypted content when there *is* a region match.

If you had no problem fine, I can almost guarantee that there will be some titles you can't play till a region has been set.

In my case my drives are set to region 1. With open source (unlicensed) players I can play back titles from *any region* with the *very* rare exception where structure protection prevents the player from 'brute forcing' or otherwise acquiring the decryption keys. ( that it would have gotten easily with a region match) ( only 2 titles that were region 2

Edit: the reason that people flash their drives for windows use is to turn the drive into a 'rpc1' drive, which then the players will allow playback from all regions. This is not needed in linux.

---

### Post by spibou on 2008-09-25
> **mc4man said:**
> 
If you had no problem fine, I can almost guarantee that there will be some titles you can't play till a region has been set.

When I encounter such a title will I see a message or something saying there is a region problem or will the DVD just won't play and I won't know why?

---

