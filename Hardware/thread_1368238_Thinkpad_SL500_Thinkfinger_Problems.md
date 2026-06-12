---
title: "Thinkpad SL500 Thinkfinger Problems"
date: 2009-12-30
forum: Hardware
---

### Post by SpanDence on 2009-12-30
Hey,

Just got a new laptop (Lenovo SL500 - 2.2GHz Centrino Duo, Intel GMA4500MHD) with a fingerprint reader. I'm using 9.10 64bit and can't seem to work the fingerprint reader to work.

I compiled and installed the thinkfinger software but when I use the command:

```
sudo tf-tool --acquire
```

I get the output:

```
Initializing...USB device not found
```

I was wondering if anybody had managed to get the fingerprint reader (Thinkfinger) working, and if so, they could give me any pointers. I'm unsure as whether or not I've installed the drivers correctly, they were compiled and installed by source. *thinkfinger-tools* and its prerequisites installed fine through Synaptic, so I've no idea what's up :S Any help would be greatly appreciated.

Thanks :)

---

### Post by sandgren on 2010-04-24
I tried the drivers found here [http://www.upek.com/solutions/pc_and_networking/sdks/linux/DownloadBSAPI.asp](http://www.upek.com/solutions/pc_and_networking/sdks/linux/DownloadBSAPI.asp)

I worked perfectly, though the login sequence could be much butter. But maybe one can tweak them :)

---

### Post by themedome on 2010-05-15
Hello!

I bought a Lenovo SL500 too, and I love it, but I can't use my fingerprint in Ubuntu Linux... :(

I'm very happy that I found this forum, but my problem is that I cant install this UPEK Driver from a tar.gz file.

Can you help me? I would really like to use my fingerprint in ubuntu too!

Thank you in advance!

---

