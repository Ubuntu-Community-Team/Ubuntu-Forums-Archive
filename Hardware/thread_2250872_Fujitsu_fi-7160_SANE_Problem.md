---
title: "Fujitsu fi-7160 SANE Problem"
date: 2014-10-31
forum: Hardware
---

### Post by diogo8 on 2014-10-31
Hi :)

I'm trying to scan a document with my Fujitsu fi-7160 using the SANE library (1.0.25) but i'm having some problems.
First of all when i run the command 'sudo scanimage -L' it only find the scanner at the second try, strange right? But that isn't bothering me at all.

The main problem is when i type 'sudo scanimage --test' or some command with scanimage and any options. The scanner reacts and moves the paper very quickly.
When i look at the terminal this is the result:

```
(...)
[fujitsu] cmd: writing 31 bytes, timeout 30000
[fujitsu] cmd: wrote 31 bytes, retVal 0
[fujitsu] in: reading 262032 bytes, timeout 30000
[fujitsu] in: retVal 0
[fujitsu] in: read 32 bytes
[fujitsu] in: short read, 32/262032
[fujitsu] stat: reading 13 bytes, timeout 30000
[fujitsu] stat: read 13 bytes, retVal 0
[fujitsu] do_usb_cmd: finish
[fujitsu] read_from_scanner: got GOOD/EOF, returning GOOD
[fujitsu] read_from_scanner: read 32 bytes
[fujitsu] copy_buffer: start
[fujitsu] copy_buffer: finish
[fujitsu] read_from_scanner: finish
[fujitsu] read_from_buffer: start
[fujitsu] read_from_buffer: si:0 re:32 ml:32768 by:32
[fujitsu] read_from_buffer: img to:1049400 rx:32 tx:0
[fujitsu] read_from_buffer: buf to:262144 rx:32 tx:0
[fujitsu] read_from_buffer: finish
[fujitsu] sane_read: reset buffers
[fujitsu] check_for_cancel: start 1 0
[fujitsu] check_for_cancel: finish 0
[fujitsu] sane_read: finish 0
[fujitsu] sane_read: start
[fujitsu] read_from_scanner: start 0
[fujitsu] read_from_scanner: si:0 re:1049368 bs:262144 by:262032 av:262144
[fujitsu] read_from_scanner: img to:1049400 rx:32 tx:32 li:0
[fujitsu] read_from_scanner: buf to:262144 rx:0 tx:0
[fujitsu] do_usb_cmd: start
[fujitsu] cmd: writing 31 bytes, timeout 30000
[fujitsu] cmd: wrote 31 bytes, retVal 0
[fujitsu] in: reading 262032 bytes, timeout 30000
[fujitsu] in: retVal 0
[fujitsu] in: read 13 bytes
[fujitsu] in: short read, 13/262032
[fujitsu] stat: reading 13 bytes, timeout 30000
[[B]fujitsu] stat: read 0 bytes, retVal 5
[fujitsu] stat: got EOF, returning IO_ERROR
[fujitsu] read_from_scanner: error reading data block status = 9
[fujitsu] read_from_scanner: read 0 bytes[/B]
[fujitsu] read_from_scanner: finish
[fujitsu] sane_read: side 0 returning 9
scanimage: sane_read: Error during device I/O
[fujitsu] sane_cancel: start
[fujitsu] sane_cancel: finish
[fujitsu] sane_close: start
[fujitsu] mode_select_buff: start
[fujitsu] do_usb_cmd: start
[fujitsu] cmd: writing 31 bytes, timeout 30000
[fujitsu] cmd: wrote 31 bytes, retVal 0
[fujitsu] out: writing 12 bytes, timeout 30000
[fujitsu] out: wrote 12 bytes, retVal 0
[fujitsu] stat: reading 13 bytes, timeout 30000
[fujitsu] stat: read 0 bytes, retVal 5
**[fujitsu] stat: got EOF, returning IO_ERROR**
[fujitsu] mode_select_buff: finish
```

And i don't get any output file. I think that the bold lines are responsible for this malfunction. 
I've tried to change the buffer size but the result is the same. I've tried also with diferent versions of the SANE library but nothing changes. This weekend i'll try with another scan models.
I really need to put this working and i would be very appreciated if you could help me here.

Thank you.

---

### Post by diogo8 on 2014-10-31
I have updates :)

Some linux guru told me that USB 3.0 ports may be unstable using the SANE library.
So i plugged the cable in the only usb 2.0 port (the gray one, not the blue ones).
With this change i got different results, this time the scanner doesn't react when i execute the scanimage command and the result of the log is this:

```
(...)
init_serial: found sn 11093
[fujitsu] init_serial: serial_name: fi-7160:11093
[fujitsu] init_serial: finish
[fujitsu] disconnect_fd: start
[fujitsu] disconnecting usb device
[fujitsu] disconnect_fd: finish
[fujitsu] attach_one: finish
[fujitsu] sane_get_devices: looking for 'usb 0x04c5 0x132f'
[fujitsu] sane_get_devices: found scanner libusb:001:014
[fujitsu] sane_get_devices: found 1 scanner(s)
[fujitsu] sane_get_devices: finish
[fujitsu] sane_open: start
[fujitsu] sane_open: searching currently attached scanners
[fujitsu] sane_open: device fi-7160:11093 requested
[fujitsu] sane_open: device fi-7160:11093 found
[fujitsu] connect_fd: start
[fujitsu] connect_fd: opening USB device
[fujitsu] wait_scanner: start
[fujitsu] do_usb_cmd: start
[fujitsu] stat: return error 'Error during device I/O'
[fujitsu] WARNING: Brain-dead scanner. Hitting with stick
[fujitsu] do_usb_cmd: start
[fujitsu] stat: return error 'Error during device I/O'
[fujitsu] WARNING: Brain-dead scanner. Hitting with stick again
[fujitsu] do_usb_cmd: start
[fujitsu] stat: return error 'Error during device I/O'
[fujitsu] wait_scanner: error 'Error during device I/O'
[fujitsu] wait_scanner: finish
[fujitsu] connect_fd: could not wait_scanner
[fujitsu] disconnect_fd: start
[fujitsu] disconnecting usb device
[fujitsu] disconnect_fd: finish
[fujitsu] connect_fd: finish
scanimage: open of device fujitsu:fi-7160:11093 failed: Error during device I/O

```

Thank you :)

---

