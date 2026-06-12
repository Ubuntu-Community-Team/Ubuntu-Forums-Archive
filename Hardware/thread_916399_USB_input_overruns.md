---
title: "USB input overruns"
date: 2008-09-10
forum: Hardware
---

### Post by Catalept on 2008-09-10
I am attempting to read data from a USB device via an FT232R chip, using a Java application and the RxTx comms library. The data is streaming at a constant rate of about 3000 bytes per second, and must be processed fairly heavily.

Everything is working well, except when CPU usage spikes. During this time, the thread reading from the serial port (/dev/ttyUSBx) becomes CPU-starved briefly and the input buffer overflows. The spikes only last one or two seconds, but the input buffer only seems to be able to hold about 1 second's worth of data before overflowing. RxTx's SetInputBufferSize call seems to be a stub, and certainly has no effect. Ideally, I'd like the buffer to be able to hold about 10 second's worth of data (i.e. 32k or more)

Is it possible to increase the size of the input buffer for the /dev/ttyUSBx devices managed by ftdi_sio?

I'm happy to alter the JNI-side code in RxTx, or even patch ftdi_sio if that's what it takes.

---

### Post by DoctorMO on 2008-09-11
You might like to take your question to the usb kernel mailing list. They'll more easily be able to help for such an advanced topic.

---

