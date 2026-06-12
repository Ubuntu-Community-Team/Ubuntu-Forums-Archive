---
title: "Avermedia avertv go 007 tv tuner"
date: 2007-06-01
forum: Hardware &amp; Laptops
---

### Post by gmcm1979 on 2007-06-01
i have just installed an avermedia avertv go 007 fm plus tv tuner and was trying to get it to work on linux, can anyone help i have tried mythtv but it fails to install

---

### Post by gmcm1979 on 2007-06-02
can anyone help? i have tried to install mythtv again but it is too complicated is there any other software that could play live tv and capture some video

---

### Post by chanhdat on 2008-06-17
Works, but...
1. Create file "/etc/modprobe.d/saa7434":

```
alias char-major-81 videodev
options i2c-algo-bit bit_test=1
options saa7134 card=57 tuner=54 i2c_scan=1 radio_nr=0 ir_debug=9 i2c_debug=9 alsa=1 gbuffers=2
alias char-major-81-0 saa7134
alias char-major-81-1 off
alias char-major-81-2 off
alias char-major-81-3 off
alias char-major-89 i2c-dev
alias char-major-61 lirc_dev
```
Restart PC
Result: Now we can use /dev/video0 & /dev/radio0
2. Create script:

```
#!/bin/sh
sox -c 2 -s -w -r 32000 -t ossdsp /dev/dsp1 -t ossdsp -w -r 32000 /dev/dsp &
tvtime --mixer=/dev/mixer:pcm
wait tvtime
t=`pidof sox`;
kill $t;
amixer -c 0 sset PCM 80%,80% unmute
```
Result: Now we can hear sound in TVTime! :)[B][U]
Read another way here:[/U][/B]
[http://pikupq.wordpress.com/2008/06/12/configure-avermedia-aver-tv-go-007-configuration-in-ubuntu/](http://pikupq.wordpress.com/2008/06/12/configure-avermedia-aver-tv-go-007-configuration-in-ubuntu/)

---

