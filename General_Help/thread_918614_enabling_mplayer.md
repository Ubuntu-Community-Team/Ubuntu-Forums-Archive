---
title: "enabling mplayer"
date: 2008-09-13
forum: General Help
---

### Post by krysia on 2008-09-13
I have installed mplayer but when I try to listen to bbc radio it says playing then after a short while says stopped.help please.

---

### Post by mali2297 on 2008-09-13
Can you post a link to one of the streams that you can't listen to?

You might need to install w32codecs (or w64codecs if you're running a 64 bit system), see
[https://help.ubuntu.com/community/Medibuntu#Playing Non-Native Media Formats](https://help.ubuntu.com/community/Medibuntu#Playing Non-Native Media Formats)

---

### Post by krysia on 2008-09-13
thanks mali 2297I loaded the codecs the other day still have the same problem.it seems the trouble started when I stupidly loaded the beta 8.11
upgrade which caused all sort of trouble,so I reloaded 8.04 from a canonical
cd.and since then I have been unable to get bbc.but strangely wumb a folk music station from america will play using mplayer but only in mp3 mode,so I am know more confused.
any ideas where I am going wrong.

---

### Post by mali2297 on 2008-09-13
Try this command in the terminal (copy/paste):
```

mplayer mms://livewmstream-ws.bbc.co.uk.edgestreams.net/reflector:38968

```
Does it work? Otherwise, can you see any error message in the output?

---

### Post by AlanR8 on 2008-09-13
I assume you also installed the Firefox (?) Mplayer extension? That done it always works for me.

---

### Post by Comhra on 2008-09-13
Thanks to Mali, I can now listen to BBC World Service.  Does anyone have a command that would allow me to listen to:
BBC 3
BBC Radio nan Oilean (Scottish Gaelic-Language Service) ?

---

