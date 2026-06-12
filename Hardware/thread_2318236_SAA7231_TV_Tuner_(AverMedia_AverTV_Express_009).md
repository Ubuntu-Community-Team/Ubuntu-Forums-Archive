---
title: "SAA7231 TV Tuner (AverMedia AverTV Express 009)"
date: 2016-03-24
forum: Hardware
---

### Post by neoxxx23 on 2016-03-24
Hello there!

I recently bought the TV tuner named in the title and it seems like it won't work with tvtime. It says that there is no video resource available (/dev/video0). A tried to google it but I found only some old threads mostly with less success solving this problem with cards using the chipset SAA7231.

lspci gives this output:
```
02:00.0 Multimedia controller: Philips Semiconductors SAA7231 (rev aa)
```

Is there a way to make this tuner work over GNU/Linux? If there's no better solution, is there a way to make Wine handle the device?

Thank you for your help!

---

