---
title: "Anyone have a Soundcard That Works with SPDIF output?"
date: 2008-04-02
forum: Hardware &amp; Laptops
---

### Post by thebigbluecan on 2008-04-02
Ive been searching for a sound card that works under Ubuntu with SPDIF output for a week now. If you have one that works could you please post it...and the process you had to go through to get it to work...if any.  

 Thanks 




                                                                  ~TED       :guitar:

---

### Post by warp99 on 2008-04-02
I have an on-board card that works fine with the spdif output. If you want the output enabled you have to specify it. You also have to have your IEC958 level in alsamixer turned all the way up.

You can easily send the output to spdif by using xine (Totem) and settings the channel out to AC3 pass-through. Hope this helps.

Edit:

Specs on card:

```
:~$ lspci -v |grep audio
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

```

---

### Post by thebigbluecan on 2008-04-02
Thanks.... Im looking for a PCI card though ](*,) Because I dont want to get a whole new mobo. But thanks for the info... it might come in handy :)

---

