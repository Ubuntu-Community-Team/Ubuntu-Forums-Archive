---
title: "USB Webcam on Ubuntu 18.04"
date: 2020-04-30
forum: Hardware
---

### Post by ChrisOfBristol on 2020-04-30
A friend (who I recommended Linux to) intends to buy a USB webcam to use  on her desktop. I have used Linux exclusively for a decade - except for  giving up on getting a scanner to work, which has made me a little  cautious about hardware. I would like to be sure that if she buys a USB  webcam it will work for her. I have found a thread on this subject, but  it was from 2009 (and is closed), I imagine things have moved on since  then! Is she likely to have problems unless I find a list of approved  devices, or does it all work out-of-the-box now?

---

### Post by CelticWarrior on 2020-04-30
> **ChrisOfBristol said:**
> Is she likely to have problems unless I find a list of approved devices, or does it all work out-of-the-box now?

Neither...

Most generic ("plug'n'play") USB webcams work.
Most integrated laptop webcams also work.
Many that need proprietary drivers/software don't work.

---

### Post by anthonyl2019 on 2020-05-01
I only came on this forum because I have another question about webcams - which I'll ask here anyway as it may be of general help to the OP.

I run an oldish HP Elitebook 8440p and was unable to determine from within Linux what the inbuilt webcam was and/or what drivers were required, despite running lsusb and lspci.  It was listed when I booted into Windows - HP Webcam [2 MP Fixed].

Following the links from [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam) I found the webcam in: [http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/)
However having gone through all that trouble I installed Cheese (via Discover) and the webcam works so I'll go along with the other post that suggests any generic webcam probably will work.

However, and the reason I came looking in the first place, I can't find how to see the Webcam's details under (k)Ubuntu 18.04 LTS.  Where is it?

---

### Post by ChrisOfBristol on 2020-05-01
OK, how might she distinguish (on ebay for example) between a Plug 'n' Play webcam and one which needs proprietary drivers or software?

---

### Post by CelticWarrior on 2020-05-01
> **ChrisOfBristol said:**
> OK, how might she distinguish (on ebay for example) between a Plug 'n' Play webcam and one which needs proprietary drivers or software?

Yes, sort of...
Most of the "plug'n'play" ones usually mention it because it's a selling point.

---

### Post by ChrisOfBristol on 2020-05-01
Ah! I've learnt something, I always assumed that P&P just meant that you could plug and unplug it when computer was on, or that it was just an advertising slogan - duh!. I'll let her know, thanks!

---

### Post by andrew.46 on 2020-05-01
> **ChrisOfBristol said:**
>  Is she likely to have problems unless I find a list of approved  devices, or does it all work out-of-the-box now?

As other have pointed out most *mainstream* webcams will give no trouble under Linux. A specific recommendation is the Logitech HD Pro Webcam C920  that I use myself. A bigger issue these days is getting hold of one at all, the lock-down in most countries has lead to a rush on these devices and while supply has dwindled prices have skyrocketed :(.

---

### Post by ChrisOfBristol on 2020-05-01
A specific recommendation is obviously ideal, thanks. However since she isn't intending to make YouTube videos or anything similar, just wishing to join her friends* on Zoom during the lockdown, I think £100 would be more than she would wish to pay. I imagine she will be looking for something functional under £20. I saw a webcam on Freecycle a year or so ago, but couldn't see any circumstances in which I might possibly have a use for one...

(*Me included unless the advice I've been give on here is bad, in which case I might become an ex-friend.)

---

### Post by mörgæs on 2020-05-02
If you post the name of the camera she considers to buy there is a chance that someone here can give a judgement.

---

### Post by mörgæs on 2020-05-02
> **anthonyl2019 said:**
> 
I can't find how to see the Webcam's details under (k)Ubuntu 18.04 LTS.  Where is it?

This might help both posters: The command **lsusb** gives an output like
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. RTS5138 Card Reader Controller
Bus 002 Device 002: ID [COLOR=#ff0000]05ca:181d[/COLOR] Ricoh Co., Ltd Laptop_Integrated_Webcam_FHD
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0cf3:3005 Qualcomm Atheros Communications AR3011 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

which shows that my camera has the ID printed in red. Googling your ID number (possibly in quotes) should send you in the right direction.

---

### Post by ChrisOfBristol on 2020-05-02
She is looking at an Andoer USB2 webcam. A couple of customers have posted in the Q&A that works/should work on Linux. It doesn't mention Plug'n'Play though.

[https://www.amazon.co.uk/Andoer-Megapixel-Mikrofon-Desktop-Computer-Blue/dp/B00NGDV4BW](https://www.amazon.co.uk/Andoer-Megapixel-Mikrofon-Desktop-Computer-Blue/dp/B00NGDV4BW)
[URL="http://andoer+usb2+webcamhttps://www.amazon.co.uk/Megapixel-Mikrofon-Desktop-Computer-schwarz-Blue/dp/B00NGDV4BW/ref=sr_1_fkmr1_1?dchild=1&keywords=andoer%2Busb2%2Bwebcam&qid=1588408600&sr=8-1-fkmr1&th=1"]

[/URL]

---

### Post by CelticWarrior on 2020-05-02
Please check the Q&A from customers.

---

### Post by ChrisOfBristol on 2020-05-02
Eh?

---

### Post by CelticWarrior on 2020-05-02
[https://www.amazon.co.uk/ask/questions/asin/B00NGDV4BW/ref=ask_atf_aqp_dp](https://www.amazon.co.uk/ask/questions/asin/B00NGDV4BW/ref=ask_atf_aqp_dp)

---

### Post by ChrisOfBristol on 2020-05-02
Lol! If you read my post before yours, you will see that I had done just that. I'd trust something I read on here more though :p. For example, she was told by customer services that both the Andoer USB2 and another one she is looking at, the Logitech C270 work on Linux, but the answer to a question about the Logitech C270 below was posted by an Argos employee!

The latter is on the list [http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/) mentioned above, so that's probably good enough, I expect she'll go for that one. 
Thanks again!

---

### Post by anthonyl2019 on 2020-05-09
> **mörgæs said:**
> This might help both posters: The command **lsusb** gives an output like
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. RTS5138 Card Reader Controller
Bus 002 Device 002: ID [COLOR=#ff0000]05ca:181d[/COLOR] Ricoh Co., Ltd Laptop_Integrated_Webcam_FHD
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0cf3:3005 Qualcomm Atheros Communications AR3011 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

which shows that my camera has the ID printed in red. Googling your ID number (possibly in quotes) should send you in the right direction.

Thanks, I had already tried that expecting to see HP Webcam, so I then investigated the one device I didn't recognise.

```

Bus 001 Device 005: ID 04f2:b15e Chicony Electronics Co., Ltd 

```

which turns out to be the Webcam in my HP!!

[https://h-node.org/notebooks/view/en/309/EliteBook-8440p](https://h-node.org/notebooks/view/en/309/EliteBook-8440p)

---

### Post by him610 on 2020-05-09
My two cents -
Just about any USB device made by Logitech just works be it webcams, mice, keyboards, etc.

---

### Post by ChrisOfBristol on 2020-05-10
It's become a bit academic - my friend tells me she can't get the webcam she wants anyway. Since the lockdown they've all been bought for videoconferencing :mad:

---

