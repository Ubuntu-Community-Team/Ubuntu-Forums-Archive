---
title: "curious what a gigabit ethernet port might let me do"
date: 2020-03-26
forum: Hardware
---

### Post by Skaperen on 2020-03-26
i'm curious what a gigabit ethernet port might let me do if i develop my own driver for it.  i'd like to be able to send out serialized raw bits at some extreme speed (like 250000000 bps).  perhaps receive them, too?

your first thought might be what card/chip am i using?  my answer is: whatever has the best potential to do some nice things when not operating in the network stack.

---

### Post by QIII on 2020-03-27
Probably give you about a gigabit of theoretical throughput if you write a perfect driver.  Probably nothing if you don't write a perfect driver.

---

