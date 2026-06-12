---
title: "Bar code reader"
date: 2009-03-28
forum: Hardware
---

### Post by Dailydog on 2009-03-28
Hi

I have a later large collection of books that I'd like to catalogue efficiently. So, I was thinking about a bar code reader.

Do you have any experience with them? Could you tell me which ones work well with Ubuntu and what software you use?

I really don't know a single thing about those scanners, so any input to help me narrow down my Google search, is highly appreaciated.

---

### Post by roadowl on 2009-05-13
Just last weekend I came across a Datalogic Heron D130 linear barcode scanner (USB version) at a thrift store. Manual included. Cost about $5, so brought it home.

Plugged it into my ubuntu (9.04) box, and watched kern.log spit out this:

[ 5232.912370] input: © Datalogic 2002 Datalogic Bar Code Scanner as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input6
[ 5232.941093] generic-usb 0003:080C:0300.0002: input,hidraw1: USB HID v1.10 Keyboard [@ Datalogic 2002 Datalogic Bar Code Scanner] on usb-0000:00:1a.0-1/input0

From the manual, scanned the 'USB-KBD' interface method (keyboard wedge). This way, any barcode scanned is pushed into the keyboard driver. The result is that, for instance within a terminal, when a barcode scan is made, you get:

$> <making some barcode scan here ...>
$> 4033100009235
-bash: 4033100009235: command not found
$>

Very nice. Of course, when having a database open, the code will be automatically appear in the currently
active cell.

So, to sum up: this barcode scanner at least works out of the box. :-)

bjd

---

### Post by Dailydog on 2009-06-24
Thanks!

---

