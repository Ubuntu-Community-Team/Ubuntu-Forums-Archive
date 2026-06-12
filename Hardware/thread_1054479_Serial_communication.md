---
title: "Serial communication"
date: 2009-01-29
forum: Hardware
---

### Post by calvarymanagua on 2009-01-29
Hi all,

I am trying to write simple scripts to communicate with a CNC Mill through a rs232 port.  My ultimate goal is to make a web based program that can send and recieve files to a CNC mill or lathe. 

I thought I would start with finding a command line rs232 communications program and making scripts.  I looked a sjinn.  It looks like what I want, but I cannot seem to get it to work.

I am very new at doing this and probably doing something wrong.  Does anybody have any ideas of where i can find information on this or have a better idea?

Thanks
Brian

---

### Post by ieee488 on 2009-01-29
I'd try to see if you can at least communicate with your equipment via minicom first such as sending a query and reading the answer.
This makes sure that the port is working, etc especially if you are using some kind of USB-to-serial converter.

---

### Post by Canuckelhead on 2009-01-29
I've used the PYSerial library in the past to communicate with microcontrollers.  Ultimately you could develop a web based app that way without too much problems.

---

