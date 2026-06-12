---
title: "Driver for Epson TM-T88iii Serial, or Raw for Serial"
date: 2010-02-19
forum: Hardware
---

### Post by Steve Roscio on 2010-02-19
Howdy -

Anyone have CUPS drivers (PPDs/filters) for the Epson TM-T88iii (not iv) thermal receipt printer?  I've dug around to no avail, even at linuxprinting.org.  I've contacted Epson and they gave me an early release for the TM-T88iv, but it uses a new command set not supported by the iii.  Result is garbage printed.  I asked for something for the ii, or the source so I could downgrade it, but no go on either.

Alternately:  I can have my app create the raw ESC/POS stream.  (If I copy this stream to the tty, it works).  How then would I use CUPS just for the queuing/spooling?  What device would I open in my app to print to this queue?  Sorry, I'm a novice at CUPS/lpr stuff.

Thanx in advance,
- Steve

---

### Post by Steve Roscio on 2010-02-19
Idea #3:  If someone could get me started with a simple raster converter (source code), I'd be willing to write the back-half that takes the raster image in memory and emits the proper ESC/POS commands for the printer.  I found this:  [http://www.cups.org/documentation.php/doc-1.4/spec-raster.html](http://www.cups.org/documentation.php/doc-1.4/spec-raster.html) and it doesn't look too hard to work with.

- Steve

---

### Post by Steve Roscio on 2010-02-19
Duh - Raw printing (idea #2) - that was really easy:  lp command.  Got that working.
But I'd still like a real CUPS driver for the printer, or if someone could point me to source code for a generic raster converter.  Thanx.

---

### Post by moboticdes on 2011-03-26
> **Steve Roscio said:**
> Duh - Raw printing (idea #2) - that was really easy:  lp command.  Got that working.
But I'd still like a real CUPS driver for the printer, or if someone could point me to source code for a generic raster converter.  Thanx.

could you please post the code to print a sample line with lpr command? thank you!

---

### Post by aquarat on 2011-07-14
Any progress on this ? ;)

---

### Post by aquarat on 2011-07-16
Hi

I've managed to get a TM-T88II working with Citizen's CBM-1000 ESC/POS driver. It looks like it rasterizes everything and then sends that to the printer.

I've attached the source code, the PPD and the result of compilation on my machine using the following command :
```

gcc -Wl,-rpath,/usr/lib -Wall -fPIC -O2 -o rastertocbm1k rastertocbm1k.c -lcupsimage -lcups

```

---

### Post by martowan on 2012-11-15
Hi AQUARAT,
I have installed my printer using the drivers you have provided above. After i finish installing, an error occurred that i should not use the printer before i install "/usr/lib/cups/filter/rastertocbmlk" . is this not exporting the path?If yes how can i do it on Kubuntu 12.04 32bit.

kind regards.

---

