---
title: "Dual channel mode memory - how to check with Linux"
date: 2020-02-28
forum: Hardware
---

### Post by meijer.o on 2020-02-28
Dear reader,

I own a Thinkpad 470 which runs Ubuntu flawlessly

It has two modules of 8GB ram. These modules are exactly the same.

Can someone tell me how to check that they are used in "dual channel mode"

Thanks in advance,

Best regards,

Meijer-o

---

### Post by Yellow Pasque on 2020-02-28
Most of the time, the system will show the info at the POST screen when the system starts, though it may be hidden behind a logo/startup screen.

You should also be able to check with:
```
sudo dmidecode -t 17
```

Look at the Bank numbers. One stick should use Bank0 and the other Bank1.

---

### Post by meijer.o on 2020-02-29
Dear Yellow Pasque,

The post message does not reveal this information.

```
$ sudo dmidecode --type 17
# dmidecode 3.2

	Form Factor: SODIMM
	Set: None
	Locator: ChannelA-DIMM0
	Bank Locator: BANK 0
	Type: DDR4
	Type Detail: Synchronous Unbuffered (Unregistered)
	Speed: 2133 MT/s
	Manufacturer: Samsung
	Serial Number: 3838591E
	Asset Tag: None
	Part Number: M471A1K43CB1-CRC    
	Rank: 1
	Configured Memory Speed: 2133 MT/s
	Configured Voltage: 1.2 V

	Size: 8192 MB
	Form Factor: SODIMM
	Set: None
	Locator: ChannelB-DIMM0
	Bank Locator: BANK 2
	Type: DDR4
	Type Detail: Synchronous Unbuffered (Unregistered)
	Speed: 2133 MT/s
	Manufacturer: Samsung
	Serial Number: 2127721E
	Asset Tag: None
	Part Number: M471A1K43CB1-CRC    
	Rank: 1
	Configured Memory Speed: 2133 MT/s
	Configured Voltage: 1.2 V
```

Does this indeed mean that the memory modules are working "dual channel" and how can I tell.

Thanks for your help,

meijer.o

---

### Post by Yellow Pasque on 2020-02-29
> The post message does not reveal this information.
Sure it does:
```
Locator: ChannelA-DIMM0
Bank Locator: BANK 0
....
Locator: ChannelB-DIMM0
Bank Locator: BANK 2
```

> Does this indeed mean that the memory modules are working "dual channel" and how can I tell.

Yes, the DIMM's are in different channels and banks.

---

### Post by him610 on 2020-02-29
> Rank: 1
A detailed discussion may be found here, [https://www.crucial.com/support/articles-faq-memory/what-is-a-memory-rank]("https://www.crucial.com/support/articles-faq-memory/what-is-a-memory-rank")
Probably not anything to be concerned about; when you are sitting at your computer the slowest system part is the operator.

---

### Post by Yellow Pasque on 2020-02-29
> **him610 said:**
> A detailed discussion may be found here, [https://www.crucial.com/support/articles-faq-memory/what-is-a-memory-rank]("https://www.crucial.com/support/articles-faq-memory/what-is-a-memory-rank")
Probably not anything to be concerned about; when you are sitting at your computer the slowest system part is the operator.

No. That is a rank. It's unrelated here since the user has matching DIMM sticks. Please don't confuse us. Life does enough of that.

---

### Post by him610 on 2020-02-29
@Yellow Pasque, sorry for having caused confusion.
> Single Channel vs. Dual Channel
Another interesting article, [https://techguided.com/single-channel-vs-dual-channel-vs-quad-channel/]("https://techguided.com/single-channel-vs-dual-channel-vs-quad-channel/")

---

### Post by meijer.o on 2020-03-01
Dear all,

Thank you for your answers, I believe Yellow Pasque is right, the two modules are in two different banks and channels which means "dual channel".

@him610
I found [https://techguided.com/single-channe...-quad-channel/](https://techguided.com/single-channe...-quad-channel/) an interesting read. Keep in mind that a gaming computer has a dedicated video card which uses dedicated memory. This laptop's video card uses the system memory (Intel integrated video). As a result, the memory bandwidth has a substantial impact on the performance of the video card.

For a confirmation, bench-marking will be needed. But I am not going to open up this laptop and benchmark it with one and two modules to differentiate the results.

Best regards,

Otto

---

### Post by him610 on 2020-03-01
> This laptop's video card uses the system memory
The amount of memory shared with the the video chip can normally be set in Bios/Euve.

---

