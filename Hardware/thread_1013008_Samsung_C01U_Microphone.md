---
title: "Samsung C01U Microphone"
date: 2008-12-16
forum: Hardware
---

### Post by jstgtpaid on 2008-12-16
I would like to get my Samsung C01U USB microphone working on Ubuntu 8.10 so I can stop using it on a windows box.

I have found a thread that details this microphone install on an older version of ubuntu and it describes the use of JACK.  I find that JACK interferes with the default Audio programs.  Mind you, I was not able to get it working using the JACK instructions either.

Has anyone got this microphone working on 8.10 with the default apps?  If yes, how does one do that?  

Ultimately, I would like to be able to select the Samsung as an input for any of the audio programs in Ubuntu.

thanks in advance,
Steven

---

### Post by Enselic on 2009-01-05
I have struggled with this for a few hours now but I eventually figured it out:

First do

```
arecord -l
```

to get the card number of the mic. The -l flag means "list the devices". My output looks like this:

```
martin@ltop:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [Samson C01U              ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

There we can see that the C01U is 'card 1'. Now adjust the recording level. For me the recording level was on 0% for the and this was the problem:

```
alsamixer -c 1
```

The argument -c 1 means "use alsamixer on card 1". Once you have increased the microphone output level you should be able to record. You might need to tweak a few more things but the alsamixer -c 1 thing was the tricky part for me to figure out.

---

### Post by jstgtpaid on 2009-01-05
Thank you very much for the reply.  My issue is now resolved...  You are fantastic...

---

