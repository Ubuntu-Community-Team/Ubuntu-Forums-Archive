---
title: "Skanlite does not start after every computer restart (Canon Pixma MP270)"
date: 2016-01-30
forum: Hardware
---

### Post by janjaromirhorak on 2016-01-30
Hi,
I'm trying to use my Canon Pixma MP270 scanner on Kubuntu 15.10, but when I try to start Skanlite, it says "Scanning for devices", then this little popup disappears and nothing happens. In [this older thread]("http://ubuntuforums.org/showthread.php?t=2308394") it seemed to be only "first-use" problem, but the same thing happens after every time I restart my computer.

I have the same issue also with xsane and Simpleimage.

The device seems to be properly connected:
```
scanimage -L
device `pixma:04A9173B' is a CANON Canon PIXMA MP270 multi-function peripheral
```

If I tried to make a test scan with "scanimage -T", i get this message:
```
scanimage: open of device pixma:04A9173B failed: Device busy
```

I discovered, it was probably because Skanlite was still doing something in the background (without any visible effect). After killing it and trying the "scanimage -T" for second time I get this message:
```
scanimage: scanning image of size 638x877 pixels at 24 bits/pixel
scanimage: acquiring RGB frame, 8 bits/sample
scanimage: reading one scanline, 1914 bytes...  FAIL Error: Error during device I/O
```

Any advice?

---

