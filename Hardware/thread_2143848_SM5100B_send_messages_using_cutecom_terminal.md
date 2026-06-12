---
title: "SM5100B send messages using cutecom terminal"
date: 2013-05-10
forum: Hardware
---

### Post by dali1985 on 2013-05-10
I would like to describe you what I did until now and what problem I have. My project is to connect the SM5100B GSM with a Raspberry Pi which runs Raspbian (similar version to debian) and to send message in my mobile. I did the first, the connection with the Raspberry pi. I have the cutecom as hyperterminal<because is the only GUI terminal in Linux> which I opened it, I connected the device /dev/ttyAMA0 and finally I clicked in the 'open device button'.
I have the following message:
+SIND: 4

I would like to send a message in my mobile. I wrote the following Inputs and I had the following results:
at
OK
at+cmgf=1
OK
at+cmgs="my number"
OK
>Hello
>Hello

But when I type or press ctrl-z it doesnt do anything. I have a spanish keyboard. What is the problem here? Is the problem the keyboard? Is the Cutecom's problem? Do I have to write any code?

---

