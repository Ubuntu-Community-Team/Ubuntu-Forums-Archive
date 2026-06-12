---
title: "Lubuntu 13.10 sound card driver for Samsung RV515-A03US"
date: 2014-02-18
forum: Hardware
---

### Post by n4rps2 on 2014-02-18
Hello, All!

I'd like to install Lubuntu 13.10 on my Samsung RV515-A03US laptop, but the LiveCD didn't have a sound card driver for it. Can anyone tell me where I might find one?

Any assistance one can offer will be appreciated...

73 DE N4RPS
Rob

Of COURSE the phone company uses Unix. Would YOU trust YOUR 911 call to Bill Gates?

---

### Post by sudodus on 2014-02-18
Are you sure that the problem is lack of a driver?

Maybe you can install pulseaudio and pavucontrol, and use the ***menus of pavucontrol*** to test all combinations of settings. That way I have been able to get my cards to work, even odd cards :-)

```
sudo apt-get install pulseaudio
sudo apt-get install pavucontro
```

---

