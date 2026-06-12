---
title: "Modem issues Acer 5570z"
date: 2008-03-14
forum: Hardware &amp; Laptops
---

### Post by edingc on 2008-03-14
Hello everyone-

My Ubuntu install on my Acer 5570z laptop is great - only problem is I cannot get my dial-up modem to work. I have broadband while I'm at college but this summer I will only have access to dial-up and I would definitely not like to have to boot back into XP to access the internet.

I have managed to get my wireless working with ndiswrapper but this is just frustrating me. I've downloaded scanModem and gotten the right copy of slmodemd but I'm getting some errors. The modem is integrated into the audio chipset on the 5570z.

I've moved slmodemd into /usr/sbin/ and it's the only copy in there like it should be. However, when I try to type this in:

```
sudo slmodemd -c USA --alsa hw:0,6
```

I get this error:

```
error: mixer setup: Off-hook switch not found for card hw:0
error: alsa setup: cannot open playback device 'hw:0,6': No such file or directory
error: cannot setup device `hw:0,6'
```

Different combinations of numbers at the end of the command yields the same errors.

Any ideas? If nothing works I'll send a copy into the guys that created scanModem.

Thanks so much.

-Cody

---

