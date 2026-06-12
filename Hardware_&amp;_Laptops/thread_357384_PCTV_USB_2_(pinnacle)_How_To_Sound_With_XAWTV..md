---
title: "PCTV USB 2 (pinnacle) How To Sound With XAWTV."
date: 2007-02-09
forum: Hardware &amp; Laptops
---

### Post by Turk on 2007-02-09
Rarely, TvTime didn't work in Dapper. I got view in XawTv but no sound, the same code for TvTime does also work in XawTv .

Install XAWTV

Install SOX

After opening XAWTV (terminal):
sox -t ossdsp -r 48000 -b -c 2 /dev/dsp1 -t ossdsp /dev/dsp

---

