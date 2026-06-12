---
title: "How to boot Ubuntu by pressing &quot;Quick Start&quot; button on Lenovo S12"
date: 2010-12-03
forum: Hardware
---

### Post by dydzej on 2010-12-03
Hello, 
Lenovo Quick Start OS is some distribution of linux and a got an idea. Change this OS to full linux instalation. 

There will be no Grub.
There will be two buttons. 

[LIST]
[*]One to start normal system (Win 7)
[*]One to start full linux instalation (Ubuntu)
[/LIST]
Does anyone idea how to do that?

---

### Post by drs305 on 2010-12-03
I don't know how but I do know the Grub2 developers have worked on it. There is now an option "GRUB_BUTTON_CMOS_ADDRESS" that I believe is designed to do what you want.

You can do a search of the above and may find your answer. Here is one thread where a Dell user has done it, although I don't think the specifics are provided:
[http://web.archiveorange.com/archive/v/aVxzlFxuJsNd8K6iKyGx]("http://web.archiveorange.com/archive/v/aVxzlFxuJsNd8K6iKyGx")

If you learn how to do it please report here, as I'd like to include it in my UF guides and in the 'official' community documentation.

---

### Post by dydzej on 2010-12-03
Thank you for this link. I'll try to figure it out this weekend.
If I will be succesfull I will write here the guide.

---

### Post by dydzej on 2010-12-06
I followed this link: [http://web.archiveorange.com/archive/v/aVxzlFxuJsNd8K6iKyGx](http://web.archiveorange.com/archive/v/aVxzlFxuJsNd8K6iKyGx) and i figured out this:

[LIST]
[*]QS will boot [COLOR=#000000]immediately  after pressing QSbuton, so i had to leave QS, and it jumped into normal  OS (I can't boot Linux from USB by pressing QSbutton)[/COLOR]
[*][COLOR=#000000]I gather these files:[/COLOR]
[/LIST]
```

This is start with normal button:

0000000: 0000 4014 0099 0358 0200 fc00 0040 a0ce  ..@....X.....@..
0000010: 470f 8928 449e 8964 0000 0000 40ff 6da0  G..(D..d....@.m.
0000020: 0916 00fc 20c8 c112 01c6 dc46 dc70 0000  .... ......F.p..
0000030: f835 7b56 072e 1440 9224 690e a048 96f7  .5{V...@.$i..H..
0000040: ff00 fe00 8058 0600 0003 0078 7400 3a00  .....X.....xt.:.
0000050: 0008 0000 8000 0000 0040 0000 4020 0000  .........@..@ ..
0000060: 0087 c0c0 2525 0018 c000 0000 0000 0000  ....%%..........
0000070: 0020                                     . 

This is start with QS button:

0000000: 0000 4014 0099 0358 0200 fc00 0040 a0ce  ..@....X.....@..
0000010: 470f 8928 449e 8964 0000 0000 40ff 6da0  G..(D..d....@.m.
0000020: 0916 00fc 20c8 c112 01c6 dc46 dc70 0000  .... ......F.p..
0000030: f835 7b56 072e 1440 9224 690e a048 96f7  .5{V...@.$i..H..
0000040: ff00 fe00 8058 0600 0003 0078 7400 3a00  .....X.....xt.:.
0000050: 0008 0000 8000 0000 0040 0000 4020 0000  .........@..@ ..
0000060: 0087 c0c0 c0c0 0018 c000 0000 0000 0000  ................
0000070: 0020  

```
[LIST]
[*]There is a change on 3rd bit in line 6
[/LIST]
I don't know how to gather the complete adress
0x2525 -> 0xc0c0 ... what does ti means

---

### Post by Arand on 2011-02-10
I was the one supplying the data for the XPS computer which the feature was initially tested on, the data I supplied are here: [http://grub.enbug.org/DellXPS1530CmosTestButton](http://grub.enbug.org/DellXPS1530CmosTestButton)

I only supplied the data and confirmed it working, I have little knowledge of the actual workings behind it, but if I may guess:

You see the 0x47 bit changing from 20 to 28 there.
And in your case it seems to be both the 0x65 and 0x66 places changing from 25 -> c0, so the hex change is basically 9b, or 155 in dec.
That seems to be less trivial than the 8hex change in my case, but I'm not sure if one can simply assume that bit 0 must have been changed since it is an odd change, and just use 115:1 in your case (65hex=101dec, 101+14=115).

That is however just a wild guess, and what you should do is ask the grub-help mailing list, or go to #grub on freenode.

- arand

---

### Post by Arand on 2011-02-13
I was talking to phcoder on #grub:
> 16:36 < phcoder> arand: c0 = 0x80 | 0x40 = bits 7 and 6 set. 25= 20|04|01 = bits 0, 1, 5 set. It's bytes 0x64 and 0x65 in dump. So in GRUB notation it's 114:* and 115:*. Which one of bits (*:7, *:6, !*:0,!*.1 or !*:5) and bytes (11:* or 115:*) it really is can be discovered by trial and error or by booting more time in either config
16:42 < phcoder> Not every such button has to work in this way though
16:43 < phcoder> and from the few info I see there my guess would be that this OS actually resides in flash and nothing analogous to your case can be done
16:44 < phcoder> in this case it may be possible to replace QS OS with something else but it requires more knowledge, is potentially more dangerous and has much less space for it. 
16:45 < phcoder> But I can't tell it for sure from the info I see. I'd suggest booting with HDs removed to confirm or deny this hypothesis.
16:45 < phcoder> Feel free to forward this conversation

- arand

---

### Post by dydzej on 2011-02-16
Thank you for that info.
I think, that should be right, because i don't see any other reason, why I can't boot to my flash by pressing QS.
But I think, I don't want to open my notebook until I have warranty on it. So I'll try it next year.

---

