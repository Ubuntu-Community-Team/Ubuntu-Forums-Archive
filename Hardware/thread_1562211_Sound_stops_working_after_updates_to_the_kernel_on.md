---
title: "Sound stops working after updates to the kernel on Dell Studio 1458 laptop"
date: 2010-08-27
forum: Hardware
---

### Post by tacrocha on 2010-08-27
After every automatic update on Ubuntu Lucid which upgrades the kernel, thus requiring a system restart, the sound stops working on my Dell Studio 1458 laptop. To solve this, after each update I have to reinstall the alsa drivers downloaded from Realtek's site following the README istructions. It's quite simple, but annoying!

1) [Download the Linux driver version 5.15rc5 from Realtek's site]("http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High Definition Audio Codecs");

2) Unpack it to a local folder and follow the README instructions;

3) Restart your computer and the sound is back.

Does anyone have a better solution to that? I really would like to avoid doing this after each kernel update.

Thanks!

---

