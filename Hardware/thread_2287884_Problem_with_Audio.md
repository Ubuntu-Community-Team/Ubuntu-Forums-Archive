---
title: "Problem with Audio"
date: 2015-07-23
forum: Hardware
---

### Post by Tim_Sabin on 2015-07-23
Hello,
I am using Ubuntu 15.04 on a System 76 system from a few tears ago. I'm having trouble with the audio. Human speech is muffled, while accompanying music is so loud it overpowers the speech and makes the audio useless. The specs of my machine:
Memory: 3.8GiB
Processor: Intel Atom CPU D510 1.66GHz x 4
Graphics: Intel IGD
OS Type: 64-bit
Disk: 482.3 GB

Audio specs:
Output Volume: 100%
Headphones (Built-in Audio)

---

### Post by Yellow Pasque on 2015-07-23
Take a look at alsamixer and see if there are any volume controls maxed out.
```
alsamixer
```
If you can't get it undistorted, give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

