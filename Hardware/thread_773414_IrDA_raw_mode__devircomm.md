---
title: "IrDA raw mode ? /dev/ircomm"
date: 2008-04-28
forum: Hardware
---

### Post by mostafaberg on 2008-04-28
Hello everyone !,

I wanted to play around with Infrared a little bit, I bought a cheap Sigmatel USB IrDA device for that purpose.

"I tried sending files to my phone, receiving files, etc.." everything works perfect "ofcourse after some tweaking"

well back to my main question.

I wanted to record some IR activity, like remote control codes and be able to dump this data into a file so I can examine the codes.

I also want to be able to replay codes, send custom codes,etc..

I tried lirc, but it doesnt work with USB dongles.

I'm trying to write my own little C program that reads, writes directly to /dev/ircomm .

but of course, nothing is working, because i have no clue how IrDA works !

So anyone can help me with my issues ?

My main goal is to :
1-be able to record Ir activity "remote control codes, files being sent over IR ,etc"
2-be able to send bytes , strings whatsoever over IR
3-basically to have a little IR tool that can manipulate my IR dongle in raw mode "just send/receive bits"

I'm not sure how IR works and how to access the dongle and control it.

I'm just trying to read/write to /dev/ircomm0

correct me if i'm wrong !

---

