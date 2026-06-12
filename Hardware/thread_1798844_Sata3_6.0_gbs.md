---
title: "Sata3 6.0 gb/s"
date: 2011-07-06
forum: Hardware
---

### Post by GonchuB on 2011-07-06
Does somebody know if Ubuntu 11.04 has support for Sata3 hard drives? I'm going to buy one and read somewhere that their Sata3 HD was not recognized by ubuntu 10.04.

---

### Post by psusi on 2011-07-06
Yes; it is just the next generation signaling rate, nothing special is required to support it.

---

### Post by lidex on 2011-07-08
> **GonchuB said:**
> Does somebody know if Ubuntu 11.04 has support for Sata3 hard drives? I'm going to buy one and read somewhere that their Sata3 HD was not recognized by ubuntu 10.04.

I think more importantly "Does your motherboard support it"?

---

### Post by Yellow Pasque on 2011-07-08
If it comes down to it, you can jumper the drive to SATA 3Gbps mode. For a mechanical hard disk, you will not notice a performance difference.

---

### Post by psusi on 2011-07-08
> **Temüjin said:**
> If it comes down to it, you can jumper the drive to SATA 3Gbps mode. For a mechanical hard disk, you will not notice a performance difference.

You don't even need a jumper; it will fall back to 3 or 1.5 gbps automatically if the other end doesn't support the higher speed.

And yea, only the highest end SSD drives are faster than 3 Gbps anyhow.

---

### Post by Yellow Pasque on 2011-07-08
> **psusi said:**
> You don't even need a jumper; it will fall back to 3 or 1.5 gbps automatically
In theory, yes, but given the mishaps with the 3Gbps -> 1.5Gbps fallback in the early days of SATA 3Gbps, I wouldn't make the assumption. ;)

---

